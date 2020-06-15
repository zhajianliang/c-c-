#### 常见c/c++语言经典实例

##### 1.求两个数的最大公约数

~~~c
#include<stdio.h>
//用户输入两个数，求这两个数的最大公约数

void test01()
{
	int num1, num2, gcd;
	printf("请输入两个正整数：");
	scanf("%d %d", &num1, &num2);
	for (int i = 1; i <= num1&&i <= num2; i++)
	{
		//找到最大公约数
		if (num1%i == 0 && num2%i == 0)
		{
			gcd = i;
		}
	}
	printf("%d和%d的最大公约数是：%d", num1, num2,gcd);
}
//第二种方法
void test02()
{
	int num1, num2, gcd;
	printf("请输入两个正整数：");
	scanf("%d %d", &num1, &num2);
	while (num1 != num2)
	{
		if (num1 > num2)
		{
			num1 -= num2;
		}
		else
			num2 -= num1;
	}
	printf("%d和%d的最大公约数是：%d", num1, num2, num1);
}
int main()
{
	test01();
	puts("");
	test02();
	puts("");
	system("pause");
	return 0;
}
~~~

##### 2.求两个数的最小公倍数

```c
#include<stdio.h>
//用户输入两个数，求这两个数的最小公倍数。
void test01()
{
	int num1, num2, a, b;
	printf("请输入两个正整数：");
	scanf("%d %d", &num1, &num2);
	a = num1;
	b = num2;
	while (num1 != num2)
	{
		if (num1 > num2)
			num1 -= num2;
		else
			num2 -= num1;
	}
	int result = a * b / num1;
	printf("%d和%d的最小公倍数是：%d", a, b, result);
}
//方法2
void test02()
{
	int num1, num2,maxnum;
	printf("请输入两个正整数：");
	scanf("%d %d", &num1, &num2);
	maxnum = (num1 > num2) ? num1 : num2;
	while (1)
	{
		if (maxnum%num1 == 0 && maxnum%num2 == 0)
		{
			printf("%d和%d的最小公倍数是：%d",num1,num2,maxnum);
			break;
		}
		maxnum++;
	}
}
int main()
{
	test01();
	puts("");
	test02();
	puts("");
	system("pause");
	return 0;
}
```

##### 3.输出九九乘法口诀表

~~~c
#include<stdio.h>
//使用嵌套 for 循环输出九九乘法口诀表
int main()
{
	for (int i = 1; i < 10; i++)
	{
		for (int j = 1; j <=i; j++)
		{
			printf("%d*%d=%d\t", i, j, i*j);
		}
		puts("");
	}
	system("pause");
	return 0;
}
~~~

##### 4.二进制和十进制的转换

~~~c
#include<stdio.h>
#include<math.h>
//二进制转换为十进制
void test01()
{
	int i = 0, result = 0, rem;
	printf("请输入一个二进制数：");
	int num;
	scanf("%11d", &num);
	while (num != 0)
	{
		rem = num % 10;
		num /= 10;
		result += rem * pow(2, i);
		i++;
	}
	printf("二进制转换为十进制为%d\n", result);
}
//十进制转换为二进制
void test02()
{
	printf("请输入一个十进制数：");
	int num;
	scanf("%d", &num);
	int rem, result = 0, i = 1;
	while (num != 0)
	{
		rem = num % 2;
		num /= 2;
		result += rem * i;
		i *= 10;
	}
	printf("十进制数转换为二进制数为%d\n", result);
}
int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}

~~~

##### 5.八进制和十进制的相互转化

~~~c
#include<stdio.h>
#include<math.h>
//八进制转换为十进制
void test01()
{
	int rem, i = 0, result = 0;
	printf("请输入一个八进制数：");
	int num;
	scanf("%d", &num);
	while (num != 0)
	{
		rem = num % 10;
		num /= 10;
		result += rem * pow(8, i);
		i++;
	}
	printf("八进制数转换为十进制数为：%d\n", result);
}
//十进制数转换为八进制数
void test02()
{
	int rem, i = 1, result = 0;
	printf("请输入一个十进制数：");
	int num;
	scanf("%d", &num);
	while (num != 0)
	{
		rem = num % 8;
		num /= 8;
		result += rem * i;
		i *= 10;
	}
	printf("十进制转换为八进制数为：%d\n", result);
}
int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}

~~~

##### 6.二进制和八进制的相互转换

~~~c
#include<stdio.h>
#include<math.h>
//二进制转换为八进制
void test01()
{
	int result1 = 0, result2 = 0, i = 0;
	printf("请输入一个二进制数：");
	int num;
	scanf("%d", &num);
	//将二进制转换为十进制
	while (num != 0)
	{
		result1 += (num % 10)*pow(2, i);
		num /= 10;
		i++;

	}
	printf("二进制转换为十进制数为：%d\n", result1);
	//将十进制数转换为八进制数
	i = 1;
	while (result1 != 0)
	{
		result2 += (result1 % 8)*i;
		result1 /= 8;
		i *= 10;
	}
	printf("二进制数转换为八进制数为：%d\n", result2);
}
//八进制数转换为二进制数
void test02()
{
	int i = 0, result1 = 0, result2 = 0;
	printf("请输入一个八进制数：");
	int num;
	scanf("%d", &num);
	//先将八进制转换为十进制
	while (num != 0)
	{
		result1 += (num % 10)*pow(8, i);
		num /= 10;
		i++;

	}
	printf("八进制转换为十进制为：%d\n",result1);
	//将十进制转换为二进制
	i = 1;
	while (result1 != 0)
	{
		result2 += (result1 % 2)*i;
		result1 /= 2;
		i *= 10;
	}
	printf("八进制数转换为二进制数为：%d\n", result2);
}
int main()
{
	test01();
	test02();
	system("pause");
	return 0;
}
~~~

##### 7.表格形式输出数据

~~~c
#include<stdio.h>
//表格显示输出数据
void test01()
{
	int i, j, k;
	for (i = 0; i < 10; i++)
	{
		for (j = 0; j <= 100; j += 10)
		{
			printf("%3d  ", j);
		}
	printf("\n");
	}
}
int main()
{
	test01();
	system("pause");
	return 0;
}

~~~

##### 8.斐波那契数列的输出

~~~c
//斐波那契数列指的是这样一个数列 1, 1, 2, 3, 5, 8, 13。。。。。
//这个数列从第3项开始，每一项都等于前两项之和。
#include<stdio.h>

//输出指定数字前的斐波那契数列
void test01()
{
	printf("请输入一个正整数：");
	int num, t1 = 0, t2 = 1;
	scanf("%d", &num);
	printf("%d前面的斐波那契数列为：%d %d ", num, t1, t2);
	while (t1 + t2 < num)
	{
		int sum = t1 + t2;
		printf("%d ", sum);
		t1 = t2;
		t2 = sum;
	}
}
// 输出指定数量的斐波那契数列
int main()
{
	int n, t1 = 0, t2 = 1, nextTerm;
	printf("请输入输出斐波那契数列的项数：");
	scanf("%d", &n);
	printf("斐波那契数列：");
	for (int i = 1; i <= n; i++)
	{
		printf("%d  ", t1);
		nextTerm = t1 + t2;
		
		t1 = t2;
		t2 = nextTerm;
	}
	puts("");
	test01();
	puts("");
	system("pause");
	return 0;
}
~~~

##### 9.回文数01

~~~c
#include<stdio.h>
//回文数
void test01()
{
	int num, temp;
	int rem, rev = 0;
	printf("请输入一个整数：");
	scanf("%d", &num);
	temp = num;
	//翻转
	while (num != 0)
	{
		rem = num % 10;
		rev = rev * 10 + rem;
		num /= 10;
	}
	if (rev == temp)
	{
		printf("%d是回文数", temp);
	}
	else
		printf("%d不是回文数", temp);
}
int main()
{
	test01();
	puts("");
	system("pause");
	return 0;
}
~~~

##### 10.简单的计算器

~~~c
#include<stdio.h>
//计算器
void test01()
{
	printf("请输入一个运算符（+、-、*、/）：");
	char c;
	int num1, num2;
	scanf("%c", &c);
	printf("i请输入两个整数：");
	scanf("%d %d", &num1, &num2);
	switch (c)
	{
	case '+':
		printf("%d+%d=%d", num1, num2, num1 + num2);
		break;
	case '-':
		printf("%d-%d=%d", num1, num2, num1 - num2);
		break;
	case '*':
		printf("%d*%d=%d", num1, num2, num1 * num2);
		break;
	case '/':
		printf("%d/%d=%d", num1, num2, num1 / num2);
		break;
	default:
		break;
	}
}
int main()
{
	test01();
	system("pause");
	return 0;
}
~~~

有问题疑问请留言，我会第一时间解答，谢谢

由于空间有限剩下的请访问：

[https://github.com/zhajianliang/c-c-.git](https://github.com/zhajianliang/c-c-.git)

转载求标明出处：

[https://github.com/zhajianliang/c-c-.git](https://github.com/zhajianliang/c-c-.git)

[https://zhajianliang.github.io](https://zhajinliang.github.io)