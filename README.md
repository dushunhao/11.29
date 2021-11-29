#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>

void menu()
{

	printf("***********************\n");
	printf("*****1.Add  2.Sub *****\n");
	printf("*****3.Mul  4.Div *****\n");
	printf("******  0.exit  *******\n");
	printf("***********************\n");
}
int Add(int x, int y)
{

	return x + y;
}
int Sub(int x, int y)
{

	return x - y;
}
int Mul(int x, int y)
{

	return x * y;
}
int Div(int x, int y)
{

	return x / y;
}
int main()
{

	int input = 0;
	do
	{
  
		menu();
		//pfArr就是函数指针数组
		//转移表
		int (*pfArr[5])(int, int) = { NULL, Add,Sub,Mul,Div };
		int x = 0;
		int y = 0;
		int ret = 0;
		printf("请选择:>");
		scanf("%d", &input);
		if (input >= 1&& input <= 4)
		{
			printf("请输入两个操作数>:");
			scanf("%d %d", &x, &y);
			ret = (pfArr[input])(x, y);
			printf("ret = %d\n", ret);
		}
		else if (0 == input)
		{
			printf("推出程序\n");
		}
		else
		{
			printf("选择错误，请重新选择\n");
		}
	} while (input);
	return 0;
  
}


void menu()
{

	printf("***********************\n");
	printf("*****1.Add  2.Sub *****\n");
	printf("*****3.Mul  4.Div *****\n");
	printf("******  0.exit  *******\n");
	printf("***********************\n");
}
int Add(int x, int y)
{

	return x + y;
}
int Sub(int x, int y)
{

	return x - y;
}
int Mul(int x, int y)
{

	return x * y;
}
int Div(int x, int y)
{

	return x / y;
}
int Calc(int (*pf)(int, int))
{

	int x = 0;
	int y = 0;
	printf("请输入2个操作数>:");
	scanf("%d %d", &x, &y);
	return pf(x, y);
}
int main()
{

	int input = 0;
	//计算器-计算整型变量的加、减、乘、除

	do {
		menu();

		int ret = 0;
		printf("请选择:>");
		scanf("%d", &input);

		switch (input)
		{
    
		case 1:
			ret = Calc(Add);
			printf("ret = %d\n", ret);
			break;
		case 2:
			ret = Calc(Sub);
			printf("ret = %d\n", ret);
			break;
		case 3:
			ret = Calc(Mul);//
			printf("ret = %d\n", ret);
			break;
		case 4:
			ret = Calc(Div);//
			printf("ret = %d\n", ret);
			break;
		case 0:
			printf("退出程序\n");
			break;
		default:
			printf("选择错误，重新选择!\n");
			break;
		}

	} while (input);
	return 0;
}


冒泡排序
不通用
void print(int arr[], int sz)
{

	int i = 0;
	for (i = 0; i < sz; i++)
	{
		printf("%d ", arr[i]);
	}
	printf("\n");
}
void bubble_sort(int arr[], int sz)
{

	int i = 0;
	int j = 0;
	//趟数
	for (i = 0; i < sz - 1; i++)
	{
		//一趟冒泡排序
		for (j = 0; j < sz - 1 - i; j++)
		{
			if (arr[j] > arr[j + 1])
			{
				//交换
				int tmp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = tmp;
			}
		}

	}
}
int main()
{

	//升序
	int i = 0;
	int arr[10] = { 5,6,4,2,1,3,9,7,0,8 };
	int sz = sizeof(arr) / sizeof(arr[0]);
	print(arr, sz);
	bubble_sort(arr,sz);
	print(arr, sz);
	return 0;
}

qsotr - 快速排序 库函数 头文件#include<stdlib.h>

任意类型数据

void qsort(void* base, //base中存放的是待排序数据中第一个对象的地址

	       size_t num, //排序数据元素的个数
	       
	       size_t size,//排序数据中一个元素的大小，单位是字节
	       
	       int (*cmp)(const void*, const void*)//函数指针 用来比较待排序数据中的两个元素的函数
	       
           );
	   
#include<stdlib.h>
#include<string.h>
int cmp_int(const void* e1, const void* e2)
{

	return *(int*)e1 - *(int*)e2;//降序改变e1 e2位置，改变逻辑就可以了
}
void print(int arr[], int sz)
{

	int i = 0;
	for (i = 0; i < sz; i++)
	{
		printf("%d ", arr[i]);
	}
	printf("\n");
}
void test1()
{

	int arr[] = { 9,8,7,6,5,4,3,2,1,0 };
	int sz = sizeof(arr) / sizeof(arr[0]);
	排序
	qsort(arr, sz, sizeof(arr[0]), cmp_int);
	print(arr, sz);
}

int sort_age(const void* e1, const void* e2)
{

	return ((struct Stu*)e1)->age - ((struct Stu*)e2)->age;
}
int sort_by_name(const void* e1, const void* e2)
{

	return strcmp(((struct Stu*)e1)->name, ((struct Stu*)e2)->name);
}
struct Stu
{

	char name[20];
	int age;
};
void test2()
{

	使用qsort函数排序结构体数据
	struct Stu s[3] = { {"zhangsan",30,},{"lisi",34},{"wangwu",20} };
	int sz = sizeof(s) / sizeof(s[0]);
	按照年龄排序
	qsort(s, sz, sizeof(s[0]), sort_by_age);
	按名字排序
	qsort(s, sz, sizeof(s[0]), sort_by_name);  
}
int main()
{

	test1();
	test2();
	return 0;
}
