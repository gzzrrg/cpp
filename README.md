### c++

# 1. c++基础语法

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



# 3.string字符串

### 3.4.1  to_string   字符串拼接

~~~c++
string name = "小黑";
int age = 21;
double height = 174.50;
string msg = "我是:" + name + ",身高：" + to_string(height) + "cm,年龄：" + to_string(age) + "岁。";
~~~

### 3.2 getline 自定义字符串输入

~~~c++
// 读取直到换行符（默认）
std::istream& getline(std::istream& is, std::string& str);

// 读取直到指定的分隔符
std::istream& getline(std::istream& is, std::string& str, char delim);
~~~

### 3.3 size 字符串长度

一个中文占3个字符

### 3.4 迭代器iterator（类似数组下标）

可以大小比较，或++ --。

begin() 返回字符串第一个字符

end() 返回字符串最后一个字符下一位置

~~~c++
for(string::iterator t = a1.begin();t <= a1.end()-1;t++){
        cout<< *t ;
    }
~~~

### 3.5 push_back() 尾插插入z字符串

~~~c+
a1.push_back('a');
~~~

### 3.6 pop_back() 删除尾部一个字符

### 3.7 insert(a,b,c) a位置前插入b个c字符,b可省略

### 3.7 find函数

找到返回第一次下标出现的位置

未找到:npos

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
typedef 55struct Stu{
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

对子类释放内存需要写虚析构

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
- 如果子类没有**堆区数据**，可以不写虚析构或纯虚析构
- 使用`纯虚析构`该类属于抽象类，无法实例化对象
- 纯虚析构需在类外实现

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

### 5.2.3 文件是否存在  `文件对象名.is_open()`

### 5.2.4 清空文件

写文件，打开后直接关闭

~~~c
ofstream ofs(“文件地址”,ios::out);
ofs.close();
~~~

### 5.2.5 文件是否为空 `文件对象名.eof()`



# 6.模版

**范形编程** --- 实现思想主要技术就是模版

如果重名，优先调用普通函数

## 6.1函数模版 

- Typename 可以替换成class

~~~c
template<typename T>
函数声明或定义应用:
~~~

- 能自动类型推导 (不会自动类型转换)
- 显示指定类型 (会自动类型转换)

~~~cpp
func <int>(a,b);//a:cahr b:int
~~~

### 6.1.1调用规则

优先调用普通函数，可以使用空模版参数列表强制优先调用函数模版

~~~c
// 通用模板
template<class T> bool Compare(T& a, T& b){
    if (a == b)
        return true;
    return false;
}
//具体化模版
template<> bool Compare(Person& a1,Person& a2){
    if (a1.m_name == a2.m_name && a1.m_ang == a2.m_ang)
        return true;
    else
        return false;
}
~~~

### 6.1.2模版特化

优先调用已定义的数据

~~~c
template<class T>
int myCompare(T T1,T T2){
    if(T1 == T2)
        return 1;
    return 0;
}
template<> int myCompare(Person T1,Person T2){
    if (T1.a == T2.a && T1.b == T2.b){
        return 1;
    }
    return 0;
}
//调用myCompare(p1,p2)  <-- Person p1,p2;
~~~



## 6.2 类模版 

- ==不会自动类型推倒==，只能显示指定类型
- 可以有默认参数

~~~c
template<class type1, class type2 = int>//带默参数，调用可以省略
template<class type1, class type2> //不带有默认参数
class Person{
  pubilc:
  	type1 m_name;
  	type2 m_age;
  	Person(type1 f,type2 s):m_name(f), m_age(s) {}//有参构造
}
//函数声明或定义应用:
~~~

### 6.2.1 类模版成员函数创建时机

- 成员函数调用时候才创建

~~~c
class Person1{
public:
    void showPerson1(){
        cout << "Person1 show" <<endl;
    }
};
class Person2{
public:
    void showPerson2(){
        cout << "Person2 show" <<endl;
    }
};

template<class T>
class MyClass{
public:
    T obj;
    void func1(){
        obj.showPerson1();
    }
    void func2(){
        obj.showPerson2();
    }
}; //调用时候传入哪个类参数调用哪个类下的成员函数
~~~

### 6.2.2类模版对象作函数参数 

- Typeid(类名字).name() 可以输出类型名

~~~c
void func(Person<string, int>& p1);  //*指定传入类型

template <clase T1,class T2>				 //参数模版化
void func(Person<T1, T2>& p1);

template <class T>									//整个类模板化
void func(T& p1);
~~~



### 6.2.3类模版与继承

~~~c
template<class T>
class Person{
public:
    T m_a;
};
template<class T1,class T2>		
class One:public Person<T1>{  //T1 =string T2=int
public:
    T2 m_b;
};										//调用 One<string , int> p1;
~~~

### 6.2.4 类模版类外实现

~~~c
template<class T1,class T2>
class Person{
public:
    T1 m_ang;
    T2 m_name;
    void func();
};

template<class T1,class T2> //类模版类外实现
void Person<T1, T2>::func() {
    cout<< "hello" <<endl;
}
~~~

成员函数调用

**类模版分文件编写 .hpp**

- 将类模版与类模版类外实现写一起，后缀改为hpp

### 6.2.5类模版与友元

- 空模板参数列表

~~~c
//类内实现
template<class T1,class T2>
class Person{
    friend void printPerson(Person<T1,T2>& p){ //类内友元
      cout<< p.m_name << p.m_age <<endl;
    }
public:
    T1 m_name;
    T2 m_age;
    Person(T1 name, T2 age):m_name(name), m_age(age){}
};
//类外实现
template<class T1,class T2>
class Person;
template<class T1,class T2>
void printPerson(Person<T1,T2>& p){ //类外友元
    cout<< p.m_name << p.m_age <<endl;
}

template<class T1,class T2>
class Person{
    friend void printPerson<>(Person<T1,T2>& p);
private:
    T1 m_name;
    T2 m_age;
public:
    Person(T1 name, T2 age):m_name(name), m_age(age){}
};
~~~



在模版类中返回*this的时 函数返回值 --> 对象名& 不用像调用时候 对象名<T>

# 7.STL

stabdard  标准模版库

容器 算法(Algorithms) 迭代器

几乎所有STL代码都采用模版类或模版函数



## 7.1 STL六大组件

容器  算法  迭代器 仿函数  适配器(配接器)  空间配置器



- 容器  vector、list、deque、set、map  (数据结构)
- 算法  sort、find、copy、for_each  (算法，排序、查找..)
- 迭代器 容器算法之间胶合
- 仿函数 行为函数，作为算法的某种策略
- 适配器 一种用来修饰容器或仿函数或迭代器接口的东西
- 空间配置器 负责空间的配置与管理



### 7.1.1 容器，算法，迭代器

**容器**

序列式容器 -- 存储元素的序列，允许双向遍历。

关联式容器 -- 存储键值对，每个元素都有一个键（key）和一个值（value），并且通过键来组织元素。

无序容器  -- 哈希表，支持快速的查找、插入和删除

**算法** Algorithms

STL 提供了大量的算法，用于对容器中的元素进行各种操作，包括排序、搜索、复制、移动、变换等。这些算法在使用时不需要关心容器的具体类型，只需要指定要操作的范围即可。

**迭代器** iterator

遍历容器中的元素，允许以统一的方式访问容器中的元素，而不用关心容器的内部实现细节。STL 提供了多种类型的迭代器，包括随机访问迭代器、双向迭代器、前向迭代器和输入输出迭代器等。







~~~c++
~~~





类似于指针

| 种类           | 功能                     | 支持 |
| -------------- | ------------------------ | ---- |
| 输入迭代器     |                          | 只读 |
| 输出迭代器     |                          | 只写 |
| 前向迭代器     |                          | 读写 |
| 双向迭代器     |                          | 读写 |
| 随机访问迭代器 | 读写，可以跳跃的方式访问 | 读写 |

## 7.2 容器

### 序列容器

1. std::vector 动态顺序表，支持快速随机访问。

    - size -- 返回有效元素
    - 名称[n] --支持下标访问，类似数组
    - empty --返回是否为空
    - begin / end --迭代器，遍历使用，可以++或--。左闭右开，
    - push_back / pop_back 尾插，尾删
    - front / back 返回首元素，返回尾元素
    - resize
    - clear

    ~~~c++
    vector<int> a1;
    vector<int> a2(10);
    vector<int> a3(10,3);
    vector<string> a;
    vector<vector<int>> c;
    vector<int> a5[8];
    cout<<  a2.size() << endl;
    
    函数调用时 -传递引用
    void print(vector<int>& a){}
    使用迭代器访问值
        vector<int>::iterator v = vec.begin(); //可以使用auto替换vector<int>::iterator
       while( v != vec.end()) {
          cout << "value of v = " << *v << endl;
          v++;
       }
    
    ~~~

2. std::list  链表，支持快速插入和删除，但不支持随机访问。

~~~c++
 
~~~



3. std::deque  双端队列，支持快速插入和删除。

### 关联容器

1. std::set  集合，不允许重复元素。

2. std::multiset  多重集合，允许多个元素具有相同的键。

3. std::map  映射，每个键映射到一个值。

4. std::multimap  多重映射，存储了键值对（pair），其中键是唯一的，但值可以重复，允许一个键映射到多个值

### 无序容器

std::unordered_set  无序集合。

std::unordered_multiset  无序多重集合。

std::unordered_map  无序映射。

std::unordered_multimap  无序多重映射。



