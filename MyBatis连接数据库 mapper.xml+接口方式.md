## 数据库建个 user 表

```sql
SET NAMES utf8mb4;
SET FOREIGN_KEY_CHECKS = 0;


DROP TABLE IF EXISTS `user`;
CREATE TABLE `user` (
  `id` int(20) NOT NULL,
  `name` varchar(30) DEFAULT NULL,
  `pwd` varchar(30) DEFAULT NULL,
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


BEGIN;
INSERT INTO `user` VALUES (1, '张三', '123456');
INSERT INTO `user` VALUES (2, '王五', '123456');
INSERT INTO `user` VALUES (3, '赵六', '12376512');
COMMIT;

SET FOREIGN_KEY_CHECKS = 1;
```





## 导入依赖,修改配置读取位置

maven pom.xml

```xml
 <dependencies>
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>5.1.46</version>
        </dependency>
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
            <version>3.5.2</version>
        </dependency>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
        </dependency>
    </dependencies>

    <build>
        <filters>
            <filter>*.xml</filter>
            <filter>*.properties</filter>
        </filters>
        <resources>
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.xml</include>
                    <include>**/*.properties</include>
                </includes>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*.xml</include>
                    <include>**/*.properties</include>
                </includes>
            </resource>
        </resources>
    </build>
```



## 制作User表对应的实体类

```java
public class User {
    private int id;
    private String name;
    private String pwd;
  //编写 get set 方法
  //重新 toString 方
}
```



## 编写User 表持久层接口类

```java
public interface UserDao {
    public List<User> getUserList();
}
```



## 编写用 xml 方式持久层接口的实现

UserMapper.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.cai.dao.UserDao">
    <select id="getUserList" resultType="com.cai.pojo.User">
      select `id`,`name`,`pwd` from `mysql_demo`.`user`
    </select>
</mapper>
```





## 制作数据库连接工具类

```java
public class MybatisSqlSessionUtil {
    private static SqlSessionFactory sqlSessionFactory = null;

    static {
        String resource = "mybatis_config.xml";
        InputStream resourceAsStream = null;
        try {
            resourceAsStream = Resources.getResourceAsStream(resource);
            sqlSessionFactory = new SqlSessionFactoryBuilder().build(resourceAsStream);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    public static SqlSession getSqlSession() {
        return sqlSessionFactory.openSession();
    }
}
```



## 制作数据库连接工具类需要的配置文件

mybatis_config.xml

放到 resources 文件中

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql://localhost:3306/mysql_demo?SSL=true&amp;useUnicode=true&amp;characterEncoding=utf-8"/>
                <property name="username" value="root"/>
                <property name="password" value="12345678"/>
            </dataSource>
        </environment>
    </environments>
    <mappers>
        <mapper resource="com/cai/dao/UserMapper.xml"/>
    </mappers>
</configuration>
```

其中用 `mappers>mapper` 声明自定义`Mapper.xml`需要加载到sqlSession的 mappers中的

先有` mapper.xml+字符串`方式操作数据库

后有` mapper.xml+mapper关联接口类`方式操作数据库



使用`mapper.xml+接口类`方式对比之前更方便、规范的使用操作数据库



## 测试Mybatis获取User 表全部数据

```java
@Test
public void getUserList() {
    SqlSession sqlSession = MybatisSqlSessionUtil.getSqlSession();
    UserDao userDao = sqlSession.getMapper(UserDao.class);
    List<User> userList = userDao.getUserList();
    for (User user : userList) {
        System.out.println("user = " + user);
    }
}
```

