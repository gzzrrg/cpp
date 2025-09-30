### c++



## 1. c++基础语法

### 1.1 符号常量    #define 标识符(名称) 常量

### 1.2 变量 

- 浮点数默认是double

~~~c
int a = 10;
float b = 3.14;
char c = 'a';
string d = "xiaomin";

~~~

### 1.3  转义字符

~~~c++
\n				换行
\t				水平制表
\\				代表一个反斜杆字符
\'				代表一个单引号字符
\"				代表一个双引号字符
~~~

### 1.4  布尔型

~~~c++
bool		true 或 false		1/0
~~~

### 1.5 c++ 使用字符串的多种方式

~~~c
char S[] = "abc"; 	//不可改变变量的值
char *s = "bc";  		//指针模式
string s = "abc";  	//字符串模式
~~~



## 2.  c++核心语法

### 2.1算术运算符

~~~c
+					正号/加
-					负号/减
*					乘
/					除
%					取模(取余)
++				前置/后置递增
--				前置/后置递减
~~~

### 2.2  赋值运算符

~~~c++
 =					赋值
+=					加等于
-=					减等于
*=					乘等于
/=					除等于
%=					模等于
~~~

### 2.3  比较运算符

~~~c
==				相等
!=				不等于
<					小于
>					大于
<=				小于等于
>=				大于等于
~~~

### 2.4 逻辑运算符

~~~c
&&			与					一假则假
||			或					一真则真
!				非					假变真
~~~

### 2.5  三元运算符

表达式 ? 值1 : 值2 ;

~~~c++
num1>num2 ? "A" : "B";
~~~

### 2.6  判断语句

##### 2.6.1 if 判断

~~~c++
if(条件){
  //code
}else if(条件){
  //code
  
}else{
  //code
}
~~~

##### 2.6 switch 控制 (选择)语句

~~~c++
switch(expression){
    case expression_1:
    //code
    break;
    case expression_2:
    //code
    break;
    ....
  default:
  //code
}
~~~

### 2.7枚举

~~~c++
enum 枚举名{
  枚举元素1； //默认0
  枚举元素2； //默认1
  ···
};
~~~

### 2.8 循环语句

- while
- do while 循环
- for 循环

### 2.9 中断语句

- continue 跳过当前循环
- break 跳出循环
- return 结束程序

### 2.9 go  to 跳转语句

任意跳转，无条件



## 3. 字面量

### 3.1 无符号 unsignet 

- 有符号 signed (默认)
- 实形不支持无符号

~~~c
unsignet int a = 10; //等同于 u_int a =10;
~~~

### 3.2 小数 (实形)显

~~~c++
cout << fixed;//设置为小数
cout.width(5);//设置显示的最大宽度
~~~

### 3.3 sizeof 字面量

大小写均可

|  U   |      无符号数      |
| :--: | :----------------: |
|  L   |      long类型      |
|  UL  |   unsignet long    |
| UUL  | unsignet long long |
|  F   |       float        |
|  D   |       double       |

### 3.4  to_string   字符串拼接

~~~c++
string name = "小黑";
int age = 21;
double height = 174.50;
string msg = "我是:" + name + ",身高：" + to_string(height) + "cm,年龄：" + to_string(age) + "岁。";
~~~

### 3.5  cin 数据输入

~~~c
int num;
cin >> num;

double num2;
cin >> num2;

string num3;
cin >> num3;
~~~

### 3.6  随机数 

~~~c++
#include <random>

int get_random_num(int min,int max){
//创建一个随机数生成器
random_device rd;
mt19937 gen(rd());
//定义一个均匀分布的整数范围
uniform_int_distribution<> dis(min, max);
//生成随机数
int random_number = dis(gen);
return random_number;
}

int num = get_random_num(0, 10);//0~10范围内的随机数
~~~

### 3.7 Static 静态变量

把数据存放在全局区，数据不受局部变量影响

~~~c
static int a = 10;
~~~





# 4.数组

## 4.1 开辟数组

~~~c++
int* pArr = new int[5] {1,2,3,4,5};//动态内存分配
delete[] pArr;
~~~



# 5.函数

## 5.1函数传参

~~~c++
//函数传参
void prin(int a);  //值传递
void prin(int* p); //指针传递  prin(&p)
void prin(SL& a);  //引用传递	 prin(a)     别名
//函数数组传参
void prin(int arr[]); //指针
void prin(int* arr);
void prin(int (&arr)[N]);
void prin(int std::array<int, 5>& arr);//编译时候确定大小
void prin(int std::vector<int>& arr);//运行时动态大小
//结构体传参数
void prin(SL p);		//值传递
void prin(SL& p);		//引用传递
void prin(SL* p);		//指针传递
//结构体数组传参
void prin(SL arr[]); //指针
void prin(SL* arr);
void prin(SL (&arr)[N]); //引用
~~~

## 5.2 函数重载 c++独有

相同函数名，函数参数不同，顺序或个数不同调用函数不同

~~~c++
int &s = a;
const int &s = 15;
~~~



# 6.指针

## 6.1 nullptr 空指针 

~~~c
int *p = nullptr
~~~

## 6.2 野指针

声明未赋值的指针

## 6.3  指针运算

~~~c++
int num = 10;
int *p = &num; // 0x16b506b14
p++;					 // 0x16b506b18
~~~

## 6.4 指针悬挂

概念：将指针变量赋值给另外一个指针变量。

不要轻易进行指针间赋值

一但用delete，确保该内存区域不再使用

## 6.5 常量指针

### const 指向的指针

~~~c++
const int* p;指向常量的指针，值不可变，指针可修改指向
int* const p =地址; 值可修改，指针不可修改
const int* const p =地址; 存储的值和指针的指向，均不可修改
~~~



# 7.动态内存管理

## 7.1  new  分配内存并提供内存地址

- **new type** 申请普通变量空间
- **new type[n]** 申请数组空间 

## 7.2  delete  释放内存

- **delete 指针**  删除普通变量空间
- **delete[ ] 指针**  删除数组变量空间



# 8.结构体

## 8.1 声明

~~~c++
struct 结构体类型{
  成员类型 成员名称;
  ...
};
~~~

## 8.2 结构体数组

~~~c++
typedef struct Stu{
    int num;
    int age;
}ST;
//声明赋值同时
ST arr[2] = {
  {13,14},
  {12,43}
};

//声明赋值分开
ST arr[2];
arr[0] = {13, 14};
arr[1] = {14,31};
~~~

## 8.3 结构体指针

~~~c++
typedef struct Stu{
    int num;
    int age;
}ST;
//
ST stu = {12, 14};
ST *p = &stu;
//动态开辟内存
ST *p = new Stu {12,16};
delete[] p;
~~~



# 9. c++核心编程

## 1.1 new 操作符

- 堆区开辟数据，由程序员手动开辟，手动释放，释放操作符delete
- 利用new创建的数据，会返回该数据的指针

~~~c++
int* p = new int;
int* p = new int(10); //开辟int并且赋值为10
int* p = new int[10]; //创建10个整型的数组
~~~

## 1.2 & 引用

- 给变量起别名
- 函数 返回值 参数
- 指针常量



## 9.3  : 

- 封装中 初始化默认值
- 继承
- 

~~~
class Person {
public:
	int m_a;
	string name;
	int* age;
	Person():m_a(20),name("张三")age(new int(5)) {}
};
~~~

## 9.4 : :   作用域

~~~
class Person {
public:
	int m_a;
	Person(); //占位
	void func(); //占位
}

Person::Person(){  //::
	cou<< "Person构造" <<endl;
}

void Person::func(){ //::
	cou<< m_a <<endl;
}
~~~

# 10.类和对象

- **抽象类**:是指包含至少一个**纯虚函数**的类。抽象类不能被实例化（不能创建对象），它主要作为基类为其他类提供接口和基本实现。
- 面向对象:   封装、继承、多态
- 属性---成员属性---成员变量， 行为---成员方法---成员函数
- 方法---属性+成员
- 类包括class和成员变量成员方法...      对象好比main中创建一个对象



## 10.1  封装

将属性和行为作为一个整体，表现生活中的事物

将属性和行为加以权限控制

### 10.1.1  访问权限：

- public		公共权限  成员类内可访问，类外可访问
- private	       私有权限  成员类内可以访问，类外不可访问 (儿子可访问)
- protected	  保护权限  成员类内可以访问，类外不可访问  (儿子不可访问)

### 10.1.2 struct和class区别

struct    默认puilc 公有权限

class     默认private 私有权限



~~~c++
//类名
class Stu{
public: //权限
  	//属性
    string name;
    int id;
  	//行为 
    void Mycin(){
        cout << "请输入姓名:";
        cin >> name;
        cout << "请输入学号:";
        cin >> id;
    }
};
~~~



### 10.1.3 对象的初始化和清理

#### 10.1.3.1 构造函数和析构函数

构造函数和析构函数都是必须有的，如果我们自己不提供编译器会提供一个空实现

**构造函数**  类名( ) { }

- 没有返回值不用写void 
- 可有参数，可重载
- 调用对象自动调用析构，只会调用一次

**析构函数**  ~类名( ){ }

- 没有返回值不用写void 
- 不可以有参数，不可以发生重载
- 对象销毁前自动调用析构，只会调用一次 (用在对象开辟内存空间销毁等)

#### 10.1.3.2 拷贝构造函数的分类及调用

- 括号法
- 显示法
- 隐式转换法

~~~c++
Person(){}
Person(const Person &p){
  as = p.as;
}
//默认构造函数
Person s1;
  
//括号法
Person s2(20);有参构造函数
Person s2(s1);拷贝构造函数   
  
//显示法
Person s2 = Person (20);有参
Person s2 = Person (s1);拷贝
  
//隐式转换法
Person s2 = 10;相当于 Person s2 = Person (10);有参构造
Person s3 = s2;拷贝
~~~

#### 10.1.3.3 拷贝构造函数调用的时机

- 使用一个已经创建完毕的对象来初始化一个新对象
- 值传递的方式给函数参数传值
- 用值的方式返回局部对象

### 10.1.3  构造函数调用规则

默认情况下，编译器至少给一个类添加3个函数

- 默认构造函数(无参，函数体为空)
- 默认析构函数(无参，函数体为空)
- 默认拷贝函数，对属性进行值拷贝

1. 写了有参构造函数，编译器就不在提供默认构造函数，依然提供拷贝构造函数
2. 写了拷贝构造函数，编译器就不再提供其他普通构造函数

### 10.1.5  深拷贝与浅拷贝

浅拷贝：简单赋值操作

深拷贝：在堆区重新申请空间，进行拷贝操作

<img src="/Users/zir/Library/Mobile Documents/com~apple~CloudDocs/Documents/笔记/Typora/图片/IMG_0501.jpg" alt="IMG_0501" style="zoom:50%;" />

~~~c
Person(const Person &p ){
        a = p.a;
  			height = p.height //height是指针 浅拷贝
        //深拷贝
        height = new int(*p.height);
        cout << "拷贝构造函数" <<endl;
    }
~~~



### 10.2.6 初始化列表

~~~c++
Student(int a, int b, int c) :m_a(a), m_b(b), m_c(c){}//方法

Student s1(10,20,30);//调用
~~~

### 10.2.7 类对象作为类成员

当其他类对象作为本类成员，构造时候先构造类对象，再构造自身

~~~c++
class Phone{
  string m_phone;
};
class Person{
    string Name;
    Phone m_phone; //类对象作为类成员
};
~~~

### 10.2.8 静态成员 static

**静态成员变量**

- 所有对象都共享同一份数据
- 类内声明，类外初始化
- 有访问权限

~~~c++
class Person{
public:
    static int m_a;  
};
int Preson::m_a = 100; //赋值 静态成员
//通过对象访问
Person s1;
cout << s1.m_a <<endl;
//通过类名访问
cout << Person::m_a <<endl;
~~~

**静态成员函数**

- 静态成员函数只能访问静态成员变量
- 所有对象共享同一个函数
- 有访问权限

~~~c++
class Person{
public:    
    static void func (){
        cout << “静态函数调用” << endl;
    }
};

//通过对象访问
Person s1;
s1.func();

//通过类名访问
Person::func();
~~~



### 10.3.1 对象模型和this指针

#### 10.3.1.1 成员变量和成员函数分开存储

- 只有`非静态成员变量`才属于类的对象
- 空对象占用空间 **1字节**

#### 10.3.1.2 this指针概念

this指针指向被调用的成员函数所属的对象

- 解决名称冲突
- 返回对象本身`*this`

~~~c++
//形参和成员变量同名时，可用this指针区分
class Person{
public:
    int age;
    Person(int age){
        this->age = age;
    }
};
//返回对象
Person& PersonArr(Person &p){
        this->age += p.age;
        return *this;
    }
~~~

### 10.3.3 空指针访问成员函数

~~~c++
class Person{
public:
    int age;
 void shouclassname(){
        if (this == NULL){
            return;
        }
	 cout << age << endl;
    }
};

Person * p = NULL;
~~~

### 10.3.4 `const` 修饰成员函数

常函数

常函数内不可以修改成员属性

成员属性声明时加关键字`mutable`后，在常函数中依然可以修改

~~~c++
class Person{
public:
    int m_a;
    void showPerson(){ const
//      m_a = 100; 不可更改
        mutable m_a = 100;
    }
};
~~~

常对象

声明对象前面加const称该对象为常对象

- 常对象只能调用常函数


~~~c++
const Person p;
p.func;
~~~

## 10.4 友元 friend

#### 10.4.1 全局函数做友元

  ~~~c++
  class Person{
      friend void goodGay(Person *building); //全局函数
  public:
      Person(){
          room_SittingRoom = "客厅";
          redroom = "卧室";
      }
  public:
      string room_SittingRoom;
  private:
      string redroom;
  
  };
  void goodGay(Person *building){ //全局函数
      cout << building->room_SittingRoom << endl;
      cout << building->redroom << endl;
  }
  ~~~

#### 10.4.2 类做友元

~~~c
class Building{
    friend class GoodGay;  //类做友元
public:
    string m_SittingRoom;
    GoodGay():m_SittingRoom("客厅"),m_BedRoom("卧室") {}
private:
    string m_BedRoom;
};

class GoodGay{
public:
   Building* building;
  GoodGay(){
   building = new Building;
  }
  void visit(){
    cout << building->m_BedRoom << endl; //访问私有成员变量
  }
};
~~~

#### 10.4.3成员函数做友元

- 编译器还不知道GoodGay类里面有哪些函数，所以后友元
- 类内声明类外实现

~~~c
class Building; //前向声明
class GoodGay{
public:
    Building* building;
    GoodGay();
    void visit01();
};
class Building{
    friend void GoodGay::visit01();
public:
    Building():m_SittingRoom("客厅"),m_BedRoom("卧室") {}
    std::string m_SittingRoom; //客厅
private:
    std::string m_BedRoom; //卧室
};

GoodGay::GoodGay() {
    building = new Building;
}

void GoodGay::visit01() {
        std::cout<< building->m_BedRoom <<std::endl;
}
~~~



## 10.5 运算符重载 函数也可以重载  operator关键字

### 10.5.1加号运算符重载    operator+  



**为什么函数内创建对象能返回值**

~~~c
//编译器会将其优化为：

// 概念上的优化（伪代码）
Person p3;  // 直接在外层构造
p3.m_a = p1.m_a + p2.m_a;
p3.m_b = p1.m_b + p2.m_b;
~~~



- 本质 s1.operator+(s2)   ||    operator+(s1,s2)  ==  s1 + s2

~~~cpp
class Person{
public:
    int m_a;
    int m_b;

    Person():m_a(0), m_b(0) {}
    Person(int a,int b) : m_a(a),m_b(b) {}

    //成员函数重载
    Person operator+(Person &p){
        Person Temp;
        Temp.m_a = this->m_a + p.m_a;
        Temp.m_b = this->m_b + p.m_b;
        return Temp;
    }
}; // s3 = s1+s2;

//全局函数重载
Person operator+(Person& p1, Person& p2){
    Person Temp;
    Temp.m_a = p1.m_a + p2.m_a;
    Temp.m_b = p1.m_b + p2.m_b;
    return Temp;
}
//s3 = s1+s2;
~~~

#### 10.5.2 左移运算符重载  

- operator<< 

- 全局函数重载

~~~c
ostream& operator<<(ostream& cout,Person& p){
    cout << p.m_a << p.m_b;
    return cout;
} //cout<< p3;


std::ostream& operator<<(std::ostream& cout,Person& p){
    cout << p.m_a << p.m_b;
    return cout;
} //std::cout<< p3;

~~~



### 10.5.3 递增运算符重载 ++ --

- 前置递增返回引用，后置递增返回值

~~~c
//前置递增
Person& operator++(){
        m_a++;
        return *this;
    } //++s1;
//后置递增
Person operator++(int){
        person temp = *this;
        m_a++;
        return temp;
    } //s1++
~~~

### 10.5.4 赋值运算符重载

- 深拷贝浅拷贝问题 
- 编译器会自动添加浅拷贝
- 浅拷贝就是拷贝同一块地址
- 深拷贝如果地址为空 开辟地址进行值拷贝，地址不为空拷贝值进行拷贝



~~~
Person& operator=(const Person& p){
		//方法一存在清除后重新开辟空间拷贝值
        if (m_age != NULL){
            delete(m_age);
            m_age =NULL;
        }
        m_age = new int(*p.m_age);
        return *this;
		//方法二存在替换值，不存在新开辟空间拷贝值
				if (m_a == NULL){
            m_a = new int (*p.m_a);
            return *this;
        }else
            *m_a = *p.m_a;
        return *this;
}//s1=s2=s3
~~~

### 10.5.5 关系运算符重载

~~~c
//==
bool operator==(Person& p){
        if (this->m_a == p.m_a && this->m_b == p.m_b)
            return true;
        return false;
    }
~~~

### 10.5.6 函数调用运算符重载

类似创建函数 重载 `()`

- 仿函数
- 没有固定写法很灵活

~~~c
class hello{
public:
    
    int operator()(int a,int b){
        return a+b;
    }
  	void operator()(string pp){
        cout <<pp << endl;
    }
};
		//调用
		hello he;

    he(5,6); 
   	hello()(5,6);//匿名对象

		he("nihao");
		hello()("nihao");
~~~



## 10.6 继承

### 10.6.1继承方式

- 代码冗余  父类—基类  子类—派生类
- 公有继承 pubilc    能访问父类pubilc protected权限不变
- 保护继承 protected 能访问父类pubilc protected权限变为protected
- 私有继承 private 能访问父类pubilc protected权限变为private

~~~cpp
class BasePage{
public:
    //代码
};
class java : public BasePage{ //公有继承
public:
    //代码
};

~~~

### 10.6.2 对象模型

- 父类中所有的非静态成员都会被子类继承

### 10.6.3 继承析构

继承中先构造父类，先析构子类 

- 父类构造->子类构造 ->析构子类 ->析构父类

~~~c
class person{
public:
    person(){
        cout<<"person构造" <<endl;
    }
    ~person(){
        cout << "person析构" <<endl;
    }
};
class pro:public person{
public:
    pro(){
        cout<<"pro构造" <<endl;
    }
    ~pro(){
        cout << "pro析构" <<endl;
    }
};

pro s1;
/*
person构造
pro构造
pro析构
person析构
*/
~~~

### 10.6.4 同名 (成员/静态成员) (属性/函数) 处理

- 不同名直接调用，调用同名父类 成员/方法  `加作用域`
- 静态成员可以通过类名直接访问 父类同名成员被隐藏

~~~c
class person{
public:
    void func(){}
};

class pro:public person{
public:
    void func(){}
};
pro s1;
    s1.func();					//子类调用
    s1.person::func();	//父类调用
~~~

### 10.6.5 多继承 菱形继承 virtual

- 不建议使用 
- 使用 虚继承 `virtual`

~~~c
class 子类:继承方式 父类1,继承方式 父类2 ...{};

class Animal{
public:
    int m_a;
};
class Sheep:virtual public Animal{}; //虚继承
class Tuo:virtual public Animal{}; //虚继承

class SheepTuo:public Sheep,public Tuo{};
~~~

## 10.7多态

**一个接口有多种形态-多态**

**满足关系**

- 有继承关系
- 子类重写父类

**动态多肽使用条件**

- 父类的指针或引用指向子类对象
- 重写:函数的返回值类型 函数名 参数列表 完全一致称为重写

### 静态多肽 

- 本质上想调用cat小猫在说话，实际输出动物在说话
- 原因是**地址早绑定**，在编译阶段确定函数地址
- vfptr -- 隐函数指针   vftable -- 隐函数表

~~~c
class Animal{
public:
    void speak(){
        cout<< "动物在说话!" <<endl;
    }
  	
};
class Cat:public Animal{
public:
    void speak(){
        cout<< "小猫在说话" <<endl;
    }
};
void dospeake(Animal& animal){
    animal.speak();
}

Cat cat;
dospeake(cat); //动物在说话
~~~

### 动态多肽

- 通过`virtual`实现重写虚函数，重写函数
- 地址晚绑定

~~~c
class Animal{
public:
    virtual void speak(){          //晚绑定地址
        cout<< "动物在说话!" <<endl;
    }
};
class Cat:public Animal{
public:
    void speak(){
        cout<< "小猫在说话" <<endl;
    }
};
void dospeake(Animal& animal){
    animal.speak();
}

Cat cat;
dospeake(cat); //小猫在说话
~~~

### 10.7.1纯虚函数

只要有**一个纯虚函数**，这个类称为**抽象类**，抽象类的特点:

1. 无法实例化对象
2. 子类必须要重写父类中的纯虚函数，否则无法实例化对象

~~~cpp
virtual void prt() = 0;
~~~

## 10.7.2虚析构和纯虚析构

- 用来解决父类释放子类对象
- 子类没有**堆区数据**，可以不写虚析构或纯虚析构
- 使用`纯虚析构`该类属于抽象类，无法实例化对象

~~~c
//虚析构
class Animal{
public:
  	string* m_n;
  
    virtual void spake() = 0;
    Animal(){
        cout<<"Animal构造函数调用" <<endl;
    }
    virtual ~Animal(){
        cout<<"Anima析构函数调用" <<endl;
    }
};
class cat:public Animal{
public:
    virtual void spake(){
        cout<< *m_n <<"小猫在说话" <<endl;
        cout<< "cat构造函数调用" <<endl;
    }
    cat(string name){ //有参构造函数
       m_n =  new string(name);
    }
    ~cat(){
        if (m_n != NULL){
            delete m_n;
            m_n = NULL;
            cout<< "cat析构函数调用" << endl;
        }
    }
};
//Anima析构函数 不使用虚析构会导致

//纯虚析构
virtual ~Animal() = 0; //声明

Animal::~Animal(){ //实现
    cout<< "Animal纯析构函数调用" << endl;
}

~~~

# 5.文件操作

头文件 `#include<fstream>`

| 打开方式      | 解释                       |
| ------------- | -------------------------- |
| `ios::in`     | 读文件                     |
| `ios::out`    | 写文件                     |
| `ios::ate`    | 初始位置: 文件尾           |
| `ios::app`    | 追加方式写文件             |
| `ios::trunc`  | 如果文件存在先删除，再创建 |
| `ios::binary` | 二进制方式                 |

二进制文件**打开方式配合 `|` 操作符**

## 5.1标准读写文件

### 5.1.1 写文件 `ofstream`

~~~c
ofstream ofs; //创建文件对象
ofs.open("text.txt",ios::out); //(文件路径，打开方式)
ofs << "nihao"; //写数据
ofs.close(); //关闭文件对象
~~~

### 5.1.2 读文件  `ifstream`  或 `fstream` 类

~~~c
//创建文件对象
ifstream ifs;
//打开文件
  ifs.open("test.txt",ios::in);
  //读取数据四种方式
  char buf[1024] = {0};
  while (ifs >> buf){
      cout<< buf <<endl;
  }
	//
  char buf[1024] = {0};
  while (ifs.getline(buf,1024)){
      cout<< buf << endl;
  }
	//
  string buf;
  while (getline(ifs,buf)){
      cout<< buf <<endl;
  }
	//单个字符读取
  char c;
  while ( (c = ifs.get()) != EOF){
      cout << c;
  }
	//关闭文件
  ifs.close();
~~~

## 5.2  二进制文件

### 5.2.1 写文件 `ofstream`



二进制方式写文件:  `ios::binary | ios::out`

~~~c
class person{
public:
    char m_name[20];
    int age;
}; 
//创建对象流
ofstream ofs;
//打开文件
ofs.open("person.txt",ios::out | ios::binary);

Person p = {"张三",18};
ofs.write((const char*)&p, sizeof(p));

ofs.close();
~~~

### 5.2.2 读文件 `ifstream`

~~~c
class person{
public:
    char m_name[20];
    int age;
};

		ifstream ofs;
    ofs.open("hello.txt",ios::in | ios::binary);
    person p1;
    ofs.read((char*)&p1,sizeof(p1));

    cout<< p1.m_name << p1.age <<endl;
    ofs.close();
~~~

