# Shell数组

* 数组中可以存放多个值。Bash Shell 只支持一维数组（不支持多维数组），初始化时不需要定义数组大小（与 PHP 类似）。

## 1. 数组的创建与赋值

* 数组元素的下标从0开始
* Shell 数组的创建
  * 使用括号，元素用"空格"符号分割开，语法格式为：`array_name=(value1 ... valuen)`
  * 使用下标来定义数组:

```sh
array_name[0]=value0
array_name[1]=value1
array_name[2]=value2
```

## 2. 读取数组

* 读取数组元素值的一般格式是：${array_name[index]}

```sh
#!/bin/bash

my_array=(A B "C" D)

echo "第一个元素为: ${my_array[0]}"
echo "第二个元素为: ${my_array[1]}"
echo "第三个元素为: ${my_array[2]}"
echo "第四个元素为: ${my_array[3]}"

#第一个元素为: A
#第二个元素为: B
#第三个元素为: C
#第四个元素为: D
```

* 获取数组中的所有元素,使用 @ 或 * 可以获取数组中的所有元素，例如：

```sh
#!/bin/bash

my_array[0]=A
my_array[1]=B
my_array[2]=C
my_array[3]=D

echo "数组的元素为: ${my_array[*]}"
echo "数组的元素为: ${my_array[@]}"
```

* 获取数组长度的方法与获取字符串长度的方法相同，例如：

```sh
#!/bin/bash

my_array[0]=A
my_array[1]=B
my_array[2]=C
my_array[3]=D

echo "数组元素个数为: ${#my_array[*]}"
echo "数组元素个数为: ${#my_array[@]}"
```

### 数组添加
Shell数组支持在数组中添加元素，有以下几种方式：
1. 使用+=号添加，可以添加任意元素，例如：
   ```sh
   array=(0 1 2)
   array+=(4 5 6)
   for i in $(seq 0 5); do
      printf "${array[${i}]} "
   done
   ```
   输出为：
   ```
   0 1 2 3 4 5 6
   ```
2. 使用下标添加，此时添加的元素可以不连续，例如：
   ```sh
   array=(0 1 2)
   array[5]=5
   echo "${array[@]}"
   ```
   输出为:
   ```
   0 1 2 5
   ```
3. 