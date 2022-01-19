**稀疏数组**(**sparse array**)是一种只为数组中的非零元素分配内存的特殊类型数组，内存中存储 了**稀疏数组**中非零元素的下标和值。

当一个数组中大部分元素为0,或者为同一个值的数组时,可以使用稀疏数组来保存该数组。

稀疏数组的处理方法是:

1. 记录数组一共有几行几列,有多少个不同的值
2. 把具有不同值的元素的行列及值记录在一个小规模的数组中,从而缩小程序的规模

```java
package datastructure;

/**
 * 稀疏数组练习
 * 
 * 将二维数组转为稀疏数组
 * 将稀疏数组转为二维数组
 */
public class SparseArray {
    public static void main(String[] args) {
        //定义一个二维数组
        int[][] arr = new int[11][11];
        arr[0][0] = 1;
        arr[1][2] = 1;
        arr[2][3] = 2;
        arr[4][3] = 1;
        arr[6][8] = 2;
        arr[10][10] = 2;
        System.out.println("二维数组：");
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr.length; j++) {
                System.out.printf(arr[i][j] + "\t");
            }
            System.out.println();
        }
        System.out.println();


        /***
         * ░░░░░░░░░░░░░░░░░░░░░░░░▄░░
         * ░░░░░░░░░▐█░░░░░░░░░░░▄▀▒▌░
         * ░░░░░░░░▐▀▒█░░░░░░░░▄▀▒▒▒▐
         * ░░░░░░░▐▄▀▒▒▀▀▀▀▄▄▄▀▒▒▒▒▒▐
         * ░░░░░▄▄▀▒░▒▒▒▒▒▒▒▒▒█▒▒▄█▒▐
         * ░░░▄▀▒▒▒░░░▒▒▒░░░▒▒▒▀██▀▒▌
         * ░░▐▒▒▒▄▄▒▒▒▒░░░▒▒▒▒▒▒▒▀▄▒▒
         * ░░▌░░▌█▀▒▒▒▒▒▄▀█▄▒▒▒▒▒▒▒█▒▐
         * ░▐░░░▒▒▒▒▒▒▒▒▌██▀▒▒░░░▒▒▒▀▄
         * ░▌░▒▄██▄▒▒▒▒▒▒▒▒▒░░░░░░▒▒▒▒
         * ▀▒▀▐▄█▄█▌▄░▀▒▒░░░░░░░░░░▒▒▒
         * 单身狗就这样默默地看着你，一句话也不说。
         */
        //二维数组转为稀疏数组
        //统计非0元素共多少个
        int sum = 0;
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr.length; j++) {
                if (0 != arr[i][j])
                    sum++;
            }
        }
        System.out.println("非0的元素个数统计：sum = " + sum);
        //声明一个稀疏数组  数组行数为非0元素总个数+1  每行三个位置
        int[][] sparse_array = new int[sum + 1][3];
        //稀疏数组第一行保存原数组行数、列、其他元素总个数
        sparse_array[0][0] = arr.length;
        sparse_array[0][1] = arr[0].length;
        sparse_array[0][2] = sum;
        int row = 1;
        for (int i = 0; i < arr.length; i++) {
            for (int j = 0; j < arr[0].length; j++) {
                if (0 != arr[i][j]) {
                    //每行保存一个非0元素信息
                    //每行第一个位置记录 所在行
                    sparse_array[row][0] = i;
                    //每行第二个位置记录 所在列
                    sparse_array[row][1] = j;
                    //每行第三个位置记录 元素内容
                    sparse_array[row][2] = arr[i][j];
                    row++;
                }
            }
        }
        System.out.println();

        
        System.out.println("二维数组转为稀疏数组：");
        for (int i = 0; i < sparse_array.length; i++) {
            for (int j = 0; j < 3; j++) {
                System.out.printf(sparse_array[i][j] + "\t");
            }
            System.out.println();
        }

        System.out.println();

        /***
         * ░░░░░░░░░░░░░░░░░░░░░░░░▄░░
         * ░░░░░░░░░▐█░░░░░░░░░░░▄▀▒▌░
         * ░░░░░░░░▐▀▒█░░░░░░░░▄▀▒▒▒▐
         * ░░░░░░░▐▄▀▒▒▀▀▀▀▄▄▄▀▒▒▒▒▒▐
         * ░░░░░▄▄▀▒░▒▒▒▒▒▒▒▒▒█▒▒▄█▒▐
         * ░░░▄▀▒▒▒░░░▒▒▒░░░▒▒▒▀██▀▒▌
         * ░░▐▒▒▒▄▄▒▒▒▒░░░▒▒▒▒▒▒▒▀▄▒▒
         * ░░▌░░▌█▀▒▒▒▒▒▄▀█▄▒▒▒▒▒▒▒█▒▐
         * ░▐░░░▒▒▒▒▒▒▒▒▌██▀▒▒░░░▒▒▒▀▄
         * ░▌░▒▄██▄▒▒▒▒▒▒▒▒▒░░░░░░▒▒▒▒
         * ▀▒▀▐▄█▄█▌▄░▀▒▒░░░░░░░░░░▒▒▒
         * 单身狗就这样默默地看着你，一句话也不说。
         */
        //稀疏数组转为二维数组
        int[][] newarr = new int[sparse_array[0][0]][sparse_array[0][1]];
        for (int i = 1; i < sparse_array[0][2] + 1; i++) {
            newarr[sparse_array[i][0]][sparse_array[i][1]] = sparse_array[i][2];
        }

        System.out.println("稀疏数组还原为二维数组：");
        for (int i = 0; i < newarr.length; i++) {
            for (int j = 0; j < newarr.length; j++) {
                System.out.printf(newarr[i][j] + "\t");
            }
            System.out.println();
        }
    }
}
```

![点击并拖拽以移动](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)

执行结果：



```
二维数组：
1	0	0	0	0	0	0	0	0	0	0	
0	0	1	0	0	0	0	0	0	0	0	
0	0	0	2	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	0	0	0	
0	0	0	1	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	2	0	0	
0	0	0	0	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	0	0	2	

非0的元素个数统计：sum = 6

二维数组转为稀疏数组：
11	11	6	
0	0	1	
1	2	1	
2	3	2	
4	3	1	
6	8	2	
10	10	2	

稀疏数组还原为二维数组：
1	0	0	0	0	0	0	0	0	0	0	
0	0	1	0	0	0	0	0	0	0	0	
0	0	0	2	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	0	0	0	
0	0	0	1	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	2	0	0	
0	0	0	0	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	0	0	0	
0	0	0	0	0	0	0	0	0	0	2	
```



