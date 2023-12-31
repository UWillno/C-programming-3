# 程序设计基础 上机3 数组的应用

一、实验目的及要求

1、熟悉CodeBlocks集成环境，掌握在该环境下进行程序编写和调试的步骤和方法。

2、掌握C语言中基本数据类型的使用方法。

3、掌握C语言中定义变量及对它们进行赋值的方法。

4、掌握C语言的各种类型的运算符、表达式的正确使用方法。

5、掌握基本的输入/输出函数的使用方法。

二、实验设备（环境）及要求

1、CodeBlocks集成开发环境

2、PTA程序设计类实验辅助教学平台www.pintia.cn

三、实验内容与步骤 

 1、一维数组应用  

（1）题目     

给整型一维数组 b[10]输入10个数据，计算并输出数组中所有正数之和、所有负数之和。

（2）源代码     

```c
#include<stdio.h>

int main(void) {
	int b[10], zSum = 0, fSum = 0;
	for (int i = 0; i < 10; i++)
		scanf("%d", &b[i]);
	for (int i = 0; i < 10; i++)
	{
		if (b[i]>0)
		{
			zSum += b[i];
		}
		else
		{
			fSum += b[i];
		}
	}
	printf("%d %d", zSum, fSum);
	return 0;
}
```

（3）运行结果截屏     

2、评委打分  

（1）题目     

**青年歌手参加歌曲大奖赛，有10个评委进行打分，将评分按降序排列。试编程求这位选手的平均得分(去掉一个最高分和一个最低分)。**

*【指导】这道题的核心是排序。将评委所打的10个分数利用数组按降序排列，计算数组中除第一个和最后一个分数以外的数的平均分。*

（2）源代码     

```c
#include<stdio.h>

int main(void) {
	int a[10];
	float sum=0, b;
	for (int i = 0; i < 10; i++)
	{
		scanf("%d", &a[i]);
	}
	for (int i = 0; i < 9; i++)
	{
		for (int j = 0; j < 9-i; j++)
		{
			if (a[j] > a[j + 1])
			{
				int temp;
				temp = a[j + 1];
				a[j + 1] = a[j];
				a[j] = temp;
			}
		}
	}
	a[0] = 0;
	a[9] = 0;
	for (int i = 0; i < 10; i++)
	{
		sum += a[i];
	}
	b = sum / 8;
	printf("%.1f", b);

	return 0;
}
```

（3）运行结果截屏    

 3、输出所有的大写字母  

（1）题目     

顺序输出给定字符串中所出现过的大写英文字母；若无大写英文字母则输出“Not Found”。

（2）源代码     

```c
#include<iostream>
#include<string>
using namespace std;
int main()
{
	char a[81];
	cin.getline(a, sizeof(a));
	int count = 0;
	for (int i = 0; i < 81; i++)
	{
		if (a[i] >= 'A' && a[i] <= 'Z')
		{
			cout << a[i];
			count++;
		}
		if (count==0)
		{
			cout << "Not Found" << endl;
			return 0;
		}
	}
	return 0;
}
```

（3）运行结果截屏    

 4、电文的密文与原文  

（1）题目     

有一电文，字符串长度N<=80，已按下列规律译成译码：
A→Z a→z
B→Y b→y
C→X c→x
… …
即第一个字母变成第26个字母，第i个字母变成第(26-i+1)个字母，非字母字符不变。编写一个程序将密码译成原文，并输出原文。

（2）源代码     

```c
#include<iostream>
#include<string>
using namespace std;
int main()
{
	char a[81];
	cin.getline(a, sizeof(a));
	int count = 0;
	for (int i = 0; i < 81; i++)
	{
		if (a[i] >= 'A' && a[i] <= 'Z')
		{
			cout << a[i];
			count++;
		}
		if (count==0)
		{
			cout << "Not Found" << endl;
			return 0;
		}
	}
	return 0;
}
```

（3）运行结果截屏     

5、求二维数组的鞍点  

（1）题目     

求二维数组 arr[5][4]中的鞍点。鞍点是指数组arr中arr[i][j]元素值在第i行中最小，且在第j列中最大。试编写一程序找出数组arr中所有的鞍点，并输出其下标值。如果没有鞍点，打印输出Not Found。

（2）源代码     

```c
#include<iostream>
using namespace std;
int a[5][6], BD = 0;
int rowmin(int i) {
	if (a[i][0]<a[i][1]&&a[i][0]<a[i][2]&&a[i][0]<a[i][3])
	{
		return 0;
	}
	else if (a[i][1] < a[i][0] && a[i][1] < a[i][2] && a[i][1] < a[i][3])
	{
		return 1;
	}
	else if (a[i][2] < a[i][1] && a[i][2] < a[i][0] && a[i][2] < a[i][3])
	{
		return 2;
	}
	else
	{
		return 3;
	}

}
int main()
{

	for (int i = 0; i < 5; i++)
	{
		for (int j = 0; j < 4; j++)
		{
			cin >> a[i][j];
		}
	}	

	for (int i = 0; i < 5; i++)
	{
		int j;
		j = rowmin(i);
		if ((i==0)&&(a[i][j]>a[i+1][j])&& (a[i][j] > a[i + 2][j])&& (a[i][j] > a[i + 3][j])&&(a[i][j]>a[i+4][j]))
		{
			cout << a[i][j] << " " << "[" << i << "," << j << "]" << endl;
			BD++;
		}
		if ((i == 1) && (a[i][j] > a[i + 1][j]) && (a[i][j] > a[i + 2][j] ) && (a[i][j] > a[i-1][j]) &&( a[i][j] > a[i + 3][j]))
		{
			cout << a[i][j] << " " << "[" << i << "," << j << "]" << endl;
			BD++;
		}
		if ((i == 2) && (a[i][j] > a[i + 1][j] ) && (a[i][j] > a[i-2][j] )&&( a[i][j] > a[i - 1][j])&& (a[i][j] > a[i + 1][j]))
		{
			cout << a[i][j] << " " << "[" << i << "," << j << "]" << endl;
			BD++;
		}
		if ((i == 3)&& (a[i][j] > a[i -3][j] )&& (a[i][j] > a[i - 2][j]) && (a[i][j] > a[i - 1][j]) && (a[i][j] > a[i + 1][j]))
		{
			cout << a[i][j] << " " << "[" << i << "," << j << "]" << endl;
			BD++;
		}
		if ((i == 4) && (a[i][j] > a[i - 3][j]) && (a[i][j] > a[i - 2][j]) && (a[i][j] > a[i - 1][j] )&& (a[i][j] > a[i -4][j]))
		{
			cout << a[i][j] << " " << "[" << i << "," << j << "]" << endl;
			BD++;
		}
		
		
	}
	if (BD == 0)
	{
		cout << "Not Found" << endl;
	}
	return 0;

}
```

（3）运行结果截屏     
