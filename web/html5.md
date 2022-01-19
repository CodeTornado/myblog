Html5

# html5 新增类型

email. url、 number、 range、date(date, month,Week,time, datetime datetime-loca)、 search、 color、tel等



# 记住输入 autocomplete

关闭记住输入

1. 去除记住后的黄色背景 form 标签上autocomplete="off"
2. 通过样式去除黄色背景

```css
input: -webkit-autofill{
-webkit-box-shadow: 0 0 0px 1000px#2390cc inset

}
```



# 下拉表单标签 dataList

![image-20211022144810931](https://shimmerimg.oss-cn-beijing.aliyuncs.com/blog/screenshot/20211022144811.png)

# 表单验证

输入框灰色提示 placeholder

元素必填 required

正则校验 Pattern

忽略必填 novalidatep或者 formnovalidate

Label标签添加 for 属性指定 input 的 id，点击 label 标签包裹的文字会选中 input



## H5约束验证

wilValidate属性 

validity属性 

validationmessage属性 

check Validity0方法 

set Customvalidity0方法