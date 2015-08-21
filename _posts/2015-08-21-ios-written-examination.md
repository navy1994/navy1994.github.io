---
layout: post
title: iOS-笔试题【90%的选中率】
date: 2015-08-21 13:45:12
category: "iOS"
---
	

面试能力要求：精通iphone的UI开发，能熟练操作复杂表视图，熟练使用图层技术， 可以自定义UI控件，使用类别扩展系统控件功能;  

擅长通讯技术，熟悉各种通信协议，精通xml, json, 二进制或其他形式的自定义解析，能架设服务器实现客户端与服务器的通讯以提交开发效率; 

熟练掌握各种数据存储技术，如core data, sqlite,  对象序列化，文件读写操作，熟悉数据库的设计。  

精通 object-c，java， c  等编程语言, 熟悉c++，对于 面向对象编程思想有深入理解，熟悉常见设计模式的应用，

1.objective-c中的数字对象都有哪些，简述它们与基本数据类型的区别是什么
2.用NSLog函数输出一个浮点类型，结果四舍五入，并保留一位小数
3.截取字符串”20｜http://www.621life.com“ 中 ‘｜’字符前面及后面的数据，分别输出它们
4.objective-c中的词典对象、可变词典对象是哪个，初始化一个含有两个键值对的可变词典对象，并动态的添加和删除一条记录，输出第一条记录
5.获取项目根路径，并在其下创建一个名称为userData的目录。
6.在一个对象的方法里面:self.name = “object”;和name ＝”object”有什么不同吗?
7.定义属性时，什么情况使用copy，assign，和retain

8.ViewController 的viewDidLoad,viewWillAppear,viewDidUnload,dealloc
分别是在什么时候调用，在自定义ViewController的时候这几个函数里面应该做什么工作？

9.简述objective-c内存管理的实现机制，并简述什么时候由你负责释放对象，什么时候不由你释放
10.类的定义及声明文件以什么为后缀名？
11.怎样自动生成属性的获取方法和设置方法
12.声明一个静态方法和一个实例方法
13.写一个发送同步http请求，并获得返回结果的方法
14.怎样启动一个新线程，子线程怎样刷新主UI
15.什么是MVC，你工作时怎样运用它

第3题：
NSRange range = [responseString rangeOfString:@"|"];
int location = range.location;
NSString *str1 = [responseString substringToIndex:location];
NSString *str2 = [responseString substringFromIndex:location+1];

第4题：
NSDictionary NSMutableDictionary
NSMutableDictionary *dic = [NSMutableDictionary dictionaryWithObjectsAndKeys:@"value1",@"key1",@"value2",@"key2",nil];
[dic setObject:@"value3" forKey:@"key3"];
[dic removeObjectForKey:@"key3"];
[dic objectForKey:@"key1"];

第5题：
// 获取根路径
NSArray *paths =NSSearchPathForDirectoriesInDomains(NSDocumentDirectory,NSUserDomainMask, YES);
NSString *documentsDirectory = [paths objectAtIndex:];
// 创建文件系统管理器
NSFileManager *fileManager = [[NSFileManager alloc] init];
// 判断userData目录是否存在
if(![fileManager fileExistsAtPath:[NSString stringWithFormat:@"%@/userData", documentsDirectory]]) {
// 不存在,创建一个userData目录
[fileManager createDirectoryAtPath:[NSString stringWithFormat:@"%@/userData", documentsDirectory]withIntermediateDirectories:false attributes:nil error:nil];
}

第6题：
self.name = “object”会调用对象的setName()方法，
name = “object”会直接把object赋值给当前对象的name 属性。
并且 self.name 这样retainCount会加１,而name就不会。

第7题：
assign用于简单数据类型，如NSInteger,double,bool,retain 和copy用户对象，copy用于当 a指向一个对象，b也想指向同样的对象的时候，如果用assign，a如果释放，再调用b会crash,如果用copy 的方式，a和b各自有自己的内存，就可以解决这个问题。retain 会使计数器加一，也可以解决assign的问题。另外：tomic和nonatomic用来决定编译器生成的getter和setter是否为原子操作。在多线程环境下，原子操作是必要的，否则有可能引起错误的结果。

对于大型项目有一定的架构能力。


###最近的

C++面试题：

######1.#define SQUAKE(a)((a)*(a))

######int a=5;

######int b;

######b = SQUAKE(a++);

######此时：b=_____

答案    30

解析： #define SQUAKE(a)((5)*(6))


######2.进程间通信的方式有______


（1）管道（Pipe）：管道可用于具有亲缘关系进程间的通信，允许一个进程和另一个与它有共同祖先的进程之间进行通信。

（2）命名管道（named pipe）：命名管道克服了管道没有名字的限制，因此，除具有管道所具有的功能外，它还允许无亲缘关系进程间的通信。命名管道在文件系统中有对应的文件名。命名管道通过命令mkfifo或系统调用mkfifo来创建。

（3）信号（Signal）：信号是比较复杂的通信方式，用于通知接受进程有某种事件发生，除了用于进程间通信外，进程还可以发送信号给进程本身；linux除了支持Unix早期信号语义函数sigal外，还支持语义符合Posix.1标准的信号函数sigaction（实际上，该函数是基于BSD的，BSD为了实现可靠信号机制，又能够统一对外接口，用sigaction函数重新实现了signal函数）。

（4）消息（Message）队列：消息队列是消息的链接表，包括Posix消息队列system V消息队列。有足够权限的进程可以向队列中添加消息，被赋予读权限的进程则可以读走队列中的消息。消息队列克服了信号承载信息量少，管道只能承载无格式字节流以及缓冲区大小受限等缺

（5）共享内存：使得多个进程可以访问同一块内存空间，是最快的可用IPC形式。是针对其他通信机制运行效率较低而设计的。往往与其它通信机制，如信号量结合使用，来达到进程间的同步及互斥。

（6）内存映射（mapped memory）：内存映射允许任何多个进程间通信，每一个使用该机制的进程通过把一个共享的文件映射到自己的进程地址空间来实现它。

（7）信号量（semaphore）：主要作为进程间以及同一进程不同线程之间的同步手段。

（8）套接口（Socket）：更为一般的进程间通信机制，可用于不同机器之间的进程间通信。起初是由Unix系统的BSD分支开发出来的，但现在一般可以移植到其它类Unix系统上：Linux和System V的变种都支持套接字。

######3.将一个头指针为head且带头结点的单链表反向排列，求算法


	//头插法，逆序链表
	#include
	#include
	using namespace std;
	
	typedef struct _NODE{

     int x;

     struct _NODE *pNext;

	}NODE;

	#define LEN_NODE ( sizeof(NODE) )

	NODE *pHead = (NODE *) malloc (LEN_NODE);


	void fun( NODE *p )

	{

      NODE *pCur,     //curten node of old list

	  *pNewCur;    //curten node of new list
	  pCur = pHead->pNext;

	  pHead->pNext = NULL;

	while( pCur )
	{

	   if( pHead->pNext != NULL )
	   {//link other node

	      pNewCur = pHead->pNext;

	      pHead->pNext = pCur;

		  pCur = pCur->pNext;

	      pHead->pNext->pNext = pNewCur;

	  }

	  else

	  {//Link first node

	    pHead->pNext = pCur;

	    pCur = pCur->pNext;

	    pHead->pNext->pNext = NULL;

	   }  

    }



		//test print
	
		pCur = pHead->pNext;

		while( pCur )

		{

	  		printf("%d\n", pCur->x );
	
	  		pCur = pCur->pNext; 

		}

	}

		
	void main()

	{
	
			NODE *pCur = pHead;

			int i = 10;

		while( i-- )
		{
			pCur->pNext = (NODE *) malloc (LEN_NODE);

			pCur = pCur->pNext;

			pCur->x = i + 1;

		}

	pCur->pNext = NULL;

	pCur = pHead->pNext;

		while( pCur )
		{

			printf("%d\n", pCur->x );

			pCur = pCur->pNext; 

		}


		//TEST
		
		fun(pHead);

	}


######4.C语言中讲讲static变量和static函数有什么作用

static关键字有两种意思,你看上下文来判断

1,表示变量是静态存储变量 
表示变量存放在静态存储区. 
2,表示该变量是内部连接 
(这种情况是指该变量不在任何{}之内,就象全局变量那样,这时候加上static) 
,也就是说在其它的.cpp文件中,该变量是不可见的(你不能用).

当static加在函数前面的时候 
表示该函数是内部连接,之在本文件中有效,别的文件中不能应用该函数. 
不加static的函数默认为是全局的. 
也就是说在其他的.cpp中只要申明一下这个函数,就可以使用它. 

1、static全局变量与普通的全局变量有什么区别？static局部变量和普通局部变量有什么区别？static函数与普通函数有什么区别？
    答：全局变量(外部变量)的说明之前再冠以static 就构成了静态的全局变量。全局变量本身就是静态存储方式， 静态全局变量当然也是静态存储方式。 这两者在存储方式上并无不同。这两者的区别虽在于非静态全局变量的作用域是整个源程序，当一个源程序由多个源文件组成时，非静态的全局变量在各个源文件中都是有效的。 而静态全局变量则限制了其作用域， 即只在定义该变量的源文件内有效， 在同一源程序的其它源文件中不能使用它。由于静态全局变量的作用域局限于一个源文件内，只能为该源文件内的函数公用， 因此可以避免在其它源文件中引起错误。
    从以上分析可以看出， 把局部变量改变为静态变量后是改变了它的存储方式即改变了它的生存期。把全局变量改变为静态变量后是改变了它的作用域， 限制了它的使用范围。
    static函数与普通函数作用域不同。static函数仅在本文件中使用。只在当前源文件中使用的函数应该说明为内部函数(static)，内部函数应该在当前源文件中说明和定义。对于可在当前源文件以外使用的函数，应该在一个头文件中说明，要使用这些函数的源文件要包含这个头文件
    static全局变量与普通的全局变量有什么区别：static全局变量只初使化一次，防止在其他文件单元中被引用;
    static局部变量和普通局部变量有什么区别：static局部变量只被初始化一次，下一次依据上一次结果值；
    static函数与普通函数有什么区别：static函数在内存中只有一份，普通函数在每个被调用中维持一份拷贝

2、如何引用一个已经定义过的全局变量？
     答：extern
     可以用引用头文件的方式，也可以用extern关键字，如果用引用头文件方式来引用某个在头文件中声明的全局变理，假定你将那个变写错了，那么在编译期间 会报错，如果你用extern方式引用时，假定你犯了同样的错误，那么在编译期间不会报错，而在连接期间报错。

3、全局变量可不可以定义在可被多个.C文件包含的头文件中？为什么？
    答：可以，在不同的C文件中以static形式来声明同名全局变量。
    可以在不同的C文件中声明同名的全局变量，前提是其中只能有一个C文件中对此变量赋初值，此时连接不会出错。






######1. ViewController的didReceiveMemoryWarning怎么被调用：

[supper didReceiveMemoryWarning];

######2.什么时候用delegate,什么时候用Notification?

delegate针对one-to-one关系，用于sender接受到reciever的某个功能反馈值。

notification针对one-to-one/many/none,reciver,用于通知多个object某个事件。

 

######3.用预处理指令#define声明一个常数，用以表明1年中有多少秒（忽略闰年问题）


 #define SECONDS_PER_YEAR (60 * 60 * 24 * 365)UL  
我在这想看到几件事情：  
 #define 语法的基本知识（例如：不能以分号结束，括号的使用，等等）  
 懂得预处理器将为你计算常数表达式的值，因此，直接写出你是如何计算一年中有多少秒而不是计算出实际的值，是更清晰而没有代价的。
 
 意识到这个表达式将使一个16位机的整型数溢出-因此要用到长整型符号L,告诉编译器这个常数是的长整型数。  
 如果你在你的表达式中用到UL（表示无符号长整型），那么你有了一个好的起点。记住，第一印象很重要。

 

_写一个"标准"宏MIN ，这个宏输入两个参数并返回较小的一个。_

 
 #define MIN(A,B) （（A） <= (B) ? (A) : (B))  
这个测试是为下面的目的而设的：  

标识#define在宏中应用的基本知识。这是很重要的，因为直到嵌入(inline)操作符变为标准C的一部分，宏是方便产生嵌入代码的唯一方
法，
对于嵌入式系统来说，为了能达到要求的性能，嵌入代码经常是必须的方法。  

三重条件操作符的知识。这个操作符存在C语言中的原因是它使得编译器能产生比 if-then-else 更优化的代码，了解这个用法是很重要的。
 

 懂得在宏中小心地把参数用括号括起来  
 我也用这个问题开始讨论宏的副作用，例如：当你写下面的代码时会发生什么事？  
 
least = MIN(*p++, b);

 

结果是：
((*p++) <= (b) ? (*p++) : (*p++))
这个表达式会产生副作用，指针p会作三次++自增操作。

 

######4.写一个委托的 interface

@protocol MyDelegate;

 
@interface MyClass: NSObject

{

    id delegate;

}

// 委托方法

@protocol MyDelegate

- (void)didJobs:(NSArray *)args;

@end

 

######5. 写一个NSString类的实现

+ (id)initWithCString:(const char *)nullTerminatedCString encoding:(NSStringEncoding)encoding;

+ (id) stringWithCString: (const char*)nullTerminatedCString
            encoding: (NSStringEncoding)encoding
{
  NSString  *obj;

  obj = [self allocWithZone: NSDefaultMallocZone()];
  obj = [obj initWithCString: nullTerminatedCString encoding: encoding];
  return AUTORELEASE(obj);
}

######6.obj-c有多重继承么?不是的话有什么替代方法?


cocoa 中所有的类都是NSObject 的子类

多继承在这里是用protocol 委托代理 来实现的
你不用去考虑繁琐的多继承 ,虚基类的概念.
ood的多态特性  在 obj-c 中通过委托来实现.

 

######7.obj-c有私有方法么?私有变量呢

 objective-c - 类里面的方法只有两种, 静态方法和实例方法. 这似乎就不是完整的面向对象了,按照OO的原则就是一个对象只暴露有用的东西. 如果没有了私有方法的话, 对于一些小范围的代码重用就不那么顺手了. 在类里面声名一个私有方法

@interface Controller : NSObject {

　　 NSString *something;

}

+ (void)thisIsAStaticMethod;

- (void)thisIsAnInstanceMethod;

@end

@interface Controller (private)

-(void)thisIsAPrivateMethod;

@end

 
@private可以用来修饰私有变量

在Objective‐C中，所有实例变量默认都是私有的，所有实例方法默认都是公有的。

######8.关键字const有什么含意？修饰类呢?static的作用,用于类呢?还有extern c的作用

const 意味着"只读"，下面的声明都是什么意思？  
const int a;  
int const a;  
const int *a;  
int * const a;  
int const * a const;

 
前两个的作用是一样，a是一个常整型数。

第三个意味着a是一个指向常整型数的指针（也就是，整型数是不可修改的，但指针可以）。

第四个意思a是一个指向整型数的常指针（也就是说，指针指向的整型数是可以修改的，但指针是不可修改的）。

最后一个意味着a是一个指向常整型数的常指针（也就是说，指针指向的整型数是不可修改的，同时指针也是不可修改的）。

结论：

 关键字const的作用是为给读你代码的人传达非常有用的信息，实际上，声明一个参数为常量是为了告诉了用户这个参数的应用目的。

 如果你曾花很多时间清理其它人留下的垃圾，你就会很快学会感谢这点多余的信息。（当然，懂得用const的程序员很少会留下的垃圾让

 别人 来清理的。）   通过给优化器一些附加的信息，使用关键字const也许能产生更紧凑的代码。  


 合理地使用关键字const可以使编译器很自然地保护那些不希望被改变的参数，防止其被无意的代码修改。简而言之，这样可以减少bug

 的出  现。  
 

（1）欲阻止一个变量被改变，可以使用 const 关键字。在定义该 const 变量时，通常需要对它进行初
始化，因为以后就没有机会再去改变它了；
（2）对指针来说，可以指定指针本身为 const，也可以指定指针所指的数据为 const，或二者同时指
定为 const；
（3）在一个函数声明中，const 可以修饰形参，表明它是一个输入参数，在函数内部不能改变其值；
（4）对于类的成员函数，若指定其为 const 类型，则表明其是一个常函数，不能修改类的成员变量；
（5）对于类的成员函数，有时候必须指定其返回值为 const 类型，以使得其返回值不为“左值”。

######关键字volatile有什么含意?并给出三个不同的例子。

一个定义为 volatile的变量是说这变量可能会被意想不到地改变，这样，编译器就不会去假设这个变量的值了。

精确地说就是，优化器在用到这个变量时必须每次都小心地重新读取这个变量的值，而不是使用保存在寄存器里的备份。

下面是volatile变量的几个例子：

并行设备的硬件寄存器（如：状态寄存器）  
 一个中断服务子程序中会访问到的非自动变量(Non-automatic variables)  
 多线程应用中被几个任务共享的变量


 一个参数既可以是const还可以是volatile吗？解释为什么。  
 一个指针可以是volatile 吗？解释为什么。

下面是答案：  
 是的。一个例子是只读的状态寄存器。它是volatile因为它可能被意想不到地改变。它是const因为程序不应该试图去修改它。  
 是的。尽管这并不很常见。一个例子是当一个中服务子程序修该一个指向一个buffer的指针时。

######9. static 关键字的作用：

 
（1）函数体内 static 变量的作用范围为该函数体，不同于 auto 变量，该变量的内存只被分配一次，
因此其值在下次调用时仍维持上次的值；
（2）在模块内的 static 全局变量可以被模块内所用函数访问，但不能被模块外其它函数访问；
（3）在模块内的 static 函数只可被这一模块内的其它函数调用，这个函数的使用范围被限制在声明
它的模块内；
（4）在类中的 static 成员变量属于整个类所拥有，对类的所有对象只有一份拷贝；
（5）在类中的 static 成员函数属于整个类所拥有，这个函数不接收 this 指针，因而只能访问类的static 成员变量。

 extern "C" 的作用

（1）被 extern "C"限定的函数或变量是 extern 类型的；
     extern 是 C/C++语言中表明函数和全局变量作用范围（可见性）的关键字，该关键字告诉编译器，
     其声明的函数和变量可以在本模块或其它模块中使用。

（2）被 extern "C"修饰的变量和函数是按照 C 语言方式编译和连接的；
 extern "C"的惯用法

（1）在 C++中引用 C 语言中的函数和变量，在包含 C 语言头文件（假设为 cExample.h）时，需进
       行下列处理：
  extern "C"  {  
   #include "cExample.h"  
  }  
而在 C 语言的头文件中，对其外部函数只能指定为 extern 类型，C 语言中不支持 extern "C"声明，
在.c 文件中包含了 extern "C"时会出现编译语法错误。

（2）在 C 中引用 C++语言中的函数和变量时，C++的头文件需添加 extern "C"，但是在 C 语言中不
能直接引用声明了 extern "C"的该头文件，应该仅将 C 文件中将 C++中定义的 extern "C"函数声明为
extern 类型。

 

######10.为什么标准头文件都有类似以下的结构？  
   #ifndef __INCvxWorksh  
   #define __INCvxWorksh  
   #ifdef __cplusplus  
   extern "C" {  
   #endif  
    
   #ifdef __cplusplus  
   }  
   #endif  
   #endif

显然，头文件中的编译宏“#ifndef __INCvxWorksh、#define __INCvxWorksh、#endif” 的作用
是防止该头文件被重复引用。

 

######10.#import跟#include的区别,@class呢?

 @class一般用于头文件中需要声明该类的某个实例变量的时候用到，在m文件中还是需要使用#import。
 而#import比起#include的好处就是不会引起交叉编译。

 

######11.MVC模式的理解

MVC设计模式考虑三种对象：模型对象、视图对象、和控制器对象。

模型对象代表特别的知识和专业技能，它们负责保有应用程序的数据和定义操作数据的逻辑。

视图对象知道如何显示应用程序的模型数据，而且可能允许用户对其进行编辑。

控制器对象是应用程序的视图对象和模型对象之间的协调者。

######12.线程与进程的区别和联系?

进程和线程都是由操作系统所体会的程序运行的基本单元，系统利用该基本单元实现系统对应用的并发性。

进程和线程的主要差别在于它们是不同的操作系统资源管理方式。

进程有独立的地址空间，一个进程崩溃后，在保护模式下不会对其它进程产生影响，而线程只是一个进程中的不同执行路径。

线程有自己的堆栈和局部变量，但线程之间没有单独的地址空间，一个线程死掉就等于整个进程死掉。

所以多进程的程序要比多线程的程序健壮，但在进程切换时，耗费资源较大，效率要差一些。

但对于一些要求同时进行并且又要共享某些变量的并发操作，只能用线程，不能用进程。

######13.列举几种进程的同步机制，并比较其优缺点。

答案：  原子操作 信号量机制    自旋锁    管程，会合，分布式系统


_1.进程之间通信的途径_

答案：共享存储系统消息传递系统管道：以文件系统为基础


_2.进程死锁的原因_

答案：资源竞争及进程推进顺序非法


_3.死锁的4个必要条件_

答案：互斥、请求保持、不可剥夺、环路


_4.死锁的处理_

答案：鸵鸟策略、预防策略、避免策略、检测与解除死锁

 

######14.堆和栈的区别


管理方式：对于栈来讲，是由编译器自动管理，无需我们手工控制；对于堆来说，释放工作由程序员控制，容易产生memory leak。

1.申请大小：
栈： 在Windows下,栈是向低地址扩展的数据结构，是一块连续的内存的区域。这句话的意思是栈顶的地址和栈的最大容量是系统预先规定好的，在 WINDOWS下，栈的大小是2M（也有的说是1M，总之是一个编译时就确定的常数），如果申请的空间超过栈的剩余空间时，将提示 overflow。因此，能从栈获得的空间较小。


堆：堆是向高地址扩展的数据结构，是不连续的内存区域。这是由于系统是用链表来存储的空闲内存地址的，自然是不连续的，而链表的遍历方向是由低地址向高地址。堆的大小受限于计算机系统中有效的虚拟内存。由此可见，堆获得的空间比较灵活，也比较大。

2.碎片问题：对于堆来讲，频繁的new/delete势必会造成内存空间的不连续，从而造成大量的碎片，使程序效率降低。对于栈来讲，则不会存在这个问题，因为栈是先进后出的队列，他们是如此的一一对应，以至于永远都不可能有一个内存块从栈中间弹出

3.分配方式：堆都是动态分配的，没有静态分配的堆。栈有2种分配方式：静态分配和动态分配。静态分配是编译器完成的，比如局部变量的分配。动态分配由 alloca函数进行分配，但是栈的动态分配和堆是不同的，他的动态分配是由编译器进行释放，无需我们手工实现。

4.分配效率：栈是机器系统提供的数据结构，计算机会在底层对栈提供支持：分配专门的寄存器存放栈的地址，压栈出栈都有专门的指令执行，这就决定了栈的效率比较高。堆则是C/C++函数库提供的，它的机制是很复杂的。

 
######15.什么是键-值,键路径是什么

模型的性质是通过一个简单的键（通常是个字符串）来指定的。视图和控制器通过键来查找相应的属性值。

在一个给定的实体中，同一个属性的所有值具有相同的数据类型。

键-值编码技术用于进行这样的查找—它是一种间接访问对象属性的机制。

键路径是一个由用点作分隔符的键组成的字符串，用于指定一个连接在一起的对象性质序列。第一个键的
性质是由先前的性质决定的，接下来每个键的值也是相对于其前面的性质。键路径使您可以以独立于模型
实现的方式指定相关对象的性质。通过键路径，您可以指定对象图中的一个任意深度的路径，使其指向相
关对象的特定属性。

######16.c和obj-c如何混用

1）obj-c的编译器处理后缀为m的文件时，可以识别obj-c和c的代码，处理mm文件可以识别obj-c,c,c++代码，

但cpp文件必须只能用c/c++代码，而且cpp文件include的头文件中，也不能出现obj- c的代码，因为cpp只是cpp。
2) 在mm文件中混用cpp直接使用即可，所以obj-c混cpp不是问题
3）在cpp中混用obj- c其实就是使用obj-c编写的模块是我们想要的。
如果模块以类实现，那么要按照cpp class的标准写类的定义，头文件中不能出现obj-c的东西，包括#import cocoa的。

实现文件中，即类的实现代码中可以使用obj-c的东西，可以import,只是后缀是mm。
如果模块以函数实现，那么头文件要按 c的格式声明函数，实现文件中，c++函数内部可以用obj-c，但后缀还是mm或m。

总结：只要cpp文件和cpp include的文件中不包含obj-c的东西就可以用了，cpp混用obj-c的关键是使用接口，

而不能直接使用实现代码，实际上cpp混用的是 obj-c编译后的o文件，这个东西其实是无差别的，所以可以用。obj-c的编译器支持cpp.


######17.cocoa touch框架


iPhone OS 应用程序的基础 Cocoa Touch 框架重用了许多 Mac 系统的成熟模式，但是它更多地专注于触摸的接口和优化。

UIKit 为您提供了在 iPhone OS 上实现图形，事件驱动程序的基本工具，其建立在和 Mac OS X 中一样的 Foundation 框架上，

包括文件处理，网络，字符串操作等。

 
Cocoa Touch 具有和 iPhone 用户接口一致的特殊设计。有了 UIKit，您可以使用 iPhone OS 上的独特的图形接口控件，按钮，

以及全屏视图的功能，您还可以使用加速仪和多点触摸手势来控制您的应用。


各色俱全的框架 除了 UIKit 外，Cocoa Touch 包含了创建世界一流 iPhone 应用程序需要的所有框架，从三维图形，到专业音效，

甚至提供设备访问 API 以控制摄像头，或通过 GPS 获知当前位置。

Cocoa Touch 既包含只需要几行代码就可以完成全部任务的强大的 Objective-C 框架，也在需要时提供基础的 C 语言 API 来直接访问系统。这些框架包括：

Core Animation：通过 Core Animation，您就可以通过一个基于组合独立图层的简单的编程模型来创建丰富的用户体验。

Core Audio：Core Audio 是播放，处理和录制音频的专业技术，能够轻松为您的应用程序添加强大的音频功能。

Core Data：提供了一个面向对象的数据管理解决方案，它易于使用和理解，甚至可处理任何应用或大或小的数据模型。

功能列表：框架分类
下面是 Cocoa Touch 中一小部分可用的框架：

音频和视频：Core Audio ，OpenAL ，Media Library ，AV Foundation
数据管理 ：Core Data ，SQLite
图形和动画 ：Core Animation ，OpenGL ES ，Quartz 2D
网络：Bonjour ，WebKit ，BSD Sockets
用户应用：Address Book ，Core Location ，Map Kit ，Store Kit

 

######18.自动释放池是什么,如何工作

 当您向一个对象发送一个autorelease消息时，Cocoa就会将该对象的一个引用放入到最新的自动释放池。

 它仍然是个正当的对象，因此自动释放池定义的作用域内的其它对象可以向它发送消息。

 当程序执行到作用域结束的位置时，自动释放池就会被释放，池中的所有对象也就被释放。

1.  ojc-c 是通过一种"referring counting"(引用计数)的方式来管理内存的, 对象在开始分配内存(alloc)的时候引用计数为一,

     以后每当碰到有copy,retain的时候引用计数都会加一, 每当碰到release和autorelease的时候引用计数就会减一,如果此

     对象的计数变为了0, 就会被系统销毁.
2. NSAutoreleasePool 就是用来做引用计数的管理工作的,这个东西一般不用你管的.
3. autorelease和release没什么区别,只是引用计数减一的时机不同而已,autorelease会在对象的使用真正结束的时候才做引用计数减一.

######19.objc优点：
  1) Cateogies
  2) Posing
  3) 动态识别
  4) 指标计算
  5）弹性讯息传递
  6) 不是一个过度复杂的 C 衍生语言
  7) Objective-C 与 C++ 可混合编程
######objc缺点:
  1) 不支援命名空間
  2)  不支持运算符重载
  3） 不支持多重继承
  4） 使用动态运行时类型，所有的方法都是函数调用，所以很多编译时优化方法都用不到。（如内联函数等），性能低劣。

 

######20.sprintf,strcpy,memcpy使用上有什么要注意的地方

 
strcpy是一个字符串拷贝的函数，它的函数原型为strcpy(char *dst, const char *src);

将src开始的一段字符串拷贝到dst开始的内存中去，结束的标志符号为 '\0'，由于拷贝的长度不是由我们自己控制的，

所以这个字符串拷贝很容易出错。具备字符串拷贝功能的函数有memcpy，这是一个内存拷贝函数，它的函数原型

为memcpy(char *dst, const char* src, unsigned int len);

将长度为len的一段内存，从src拷贝到dst中去，这个函数的长度可控。但是会有内存叠加的问题。

sprintf是格式化函数。将一段数据通过特定的格式，格式化到一个字符串缓冲区中去。sprintf格式化的函数的长度不可控，

有可能格式化后的字符串会超出缓冲区的大小，造成溢出。

######21. 用变量a给出下面的定义

a) 一个整型数（An integer）  
b)一个指向整型数的指针（ A pointer to an integer）  
c)一个指向指针的的指针，它指向的指针是指向一个整型数（ A pointer to a pointer to an intege）r  
d)一个有10个整型数的数组（ An array of 10 integers）  
e) 一个有10个指针的数组，该指针是指向一个整型数的。（An array of 10 pointers to integers）  
f) 一个指向有10个整型数数组的指针（ A pointer to an array of 10 integers）  
g) 一个指向函数的指针，该函数有一个整型参数并返回一个整型数（A pointer to a function that takes an integer as an argument
 and returns an integer）  
h) 一个有10个指针的数组，该指针指向一个函数，该函数有一个整型参数并返回一个整型数（ An array of ten pointers to functions t
hat take an integer argument and return an integer ）  
 
答案是：  
a) int a; // An integer  
b) int *a; // A pointer to an integer  
c) int **a; // A pointer to a pointer to an integer  
d) int a[10]; // An array of 10 integers  
e) int *a[10]; // An array of 10 pointers to integers  
f) int (*a)[10]; // A pointer to an array of 10 integers  
g) int (*a)(int); // A pointer to a function a that  takes an integer argument and returns an integer  
h) int (*a[10])(int); // An array of 10 pointers to functions  that take an integer argument and return an integer

 

######22.readwrite，readonly，assign，retain，copy，nonatomic 属性的作用

@property是一个属性访问声明，扩号内支持以下几个属性：
1，getter=getterName，setter=setterName，设置setter与 getter的方法名
2，readwrite,readonly，设置可供访问级别
2，assign，setter方法直接赋值，不进行任何retain操作，为了解决原类型与环循引用问题
3，retain，setter方法对参数进行release旧值再retain新值，所有实现都是这个顺序(CC上有相关资料)
4，copy，setter方法进行Copy操作，与retain处理流程一样，先旧值release，再 Copy出新的对象，retainCount为1。

   这是为了减少对上下文的依赖而引入的机制。
5，nonatomic，非原子性访问，不加同步，多线程并发访问会提高性能。注意，如果不加此属性，则默认是两个访问方法

   都为原子型事务访问。锁被加到所属对象实例级(我是这么理解的...)。

 

######23.http和scoket通信的区别。

http是客户端用http协议进行请求，发送请求时候需要封装http请求头，并绑定请求的数据，服务器一般有web服务器配合（当然也非绝 对）。 http请求方式为客户端主动发起请求，服务器才能给响应，一次请求完毕后则断开连接，以节省资源。服务器不能主动给客户端响应（除非采取http长连接 技术）。iphone主要使用类是NSUrlConnection。


scoket是客户端跟服务器直接使用socket“套接字”进行连接，并没有规定连接后断开，所以客户端和服务器可以保持连接通道，双方 都可以主动发送数据。一般在游戏开发或股票开发这种要求即时性很强并且保持发送数据量比较大的场合使用。主要使用类是CFSocketRef。


TCP全称是Transmission Control Protocol，中文名为传输控制协议，它可以提供可靠的、面向连接的网络数据传递服务。传输控制协议主要包含下列任务和功能：
* 确保IP数据报的成功传递。
* 对程序发送的大块数据进行分段和重组。
* 确保正确排序及按顺序传递分段的数据。
* 通过计算校验和，进行传输数据的完整性检查。


######6、TCP和UDP的区别

  TCP提供的是面向连接的、可靠的数据流传输，而UDP提供的是非面向连接的、不可靠的数据流传输。
    简单的说，TCP注重数据安全，而UDP数据传输快点，但安全性一般

######24.mvc设计模式是什么？ 你还熟悉什么设计模式？

设计模式：并不是一种新技术，而是一种编码经验，使用比如java中的接口，iphone中的协议，继承关系等基本手段，

用比较成熟的逻辑去处理某一种类型的事情，总结为所谓设计模式。面向对象编程中，java已经归纳了23中设计模式。

mvc设计模式 ，模型，视图，控制器，可以将整个应用程序在思想上分成三大块，对应是的数据的存储或处理，前台的显示，

业务逻辑的控制。 Iphone本身的设计思想就是遵循mvc设计模式。其不属于23中设计模式范畴。

代理模式：代理模式给某一个对象提供一个代理对象，并由代理对象控制对源对象的引用.比如一个工厂生产了产品，

并不想直接卖给用户，而是搞了很多代理商，用户可以直接找代理商买东西，代理商从工厂进货.
常见的如QQ的自动回复就属于代理拦截，代理模式在iphone中得到广泛应用.

单例模式：说白了就是一个类不通过alloc方式创建对象，而是用一个静态方法返回这个类的对象。系统只需要拥有一个的全局对象，

这样有利于我们协调系统整体的行为，比如想获得[UIApplication sharedApplication];任何地方调用都可以得到 UIApplication的对象，

这个对象是全局唯一的。

观察者模式： 当一个物体发生变化时，会通知所有观察这个物体的观察者让其做出反应。实现起来无非就是把所有观察者的对象给这个物体，

当这个物体的发生改变，就会调用遍历所有观察者的对象调用观察者的方法从而达到通知观察者的目的。

工厂模式：


public class Factory{
　　public static Sample creator(int which){
　
　　if (which==1)
      return new SampleA();
　　else if (which==2)
      return new SampleB();
      }
 }

25.你了解svn,cvs等版本控制工具么？
版本控制 svn,cvs 是两种版控制的器,需要配套相关的svn，cvs服务器。
scm是xcode里配置版本控制的地方。版本控制的原理就是a和b同时开发一个项目，a写完当天的代码之后把代码提交给服务器，

b要做的时候先从服务器得到最新版本，就可以接着做。 如果a和b都要提交给服务器，并且同时修改了同一个方法，就会产生代码冲突，

如果a先提交，那么b提交时，服务器可以提示冲突的代码，b可以清晰的看到，并做出相应的修改或融合后再提交到服务器。

 

######26.什么是push(了解一下）。

客户端程序留下后门端口，客户端总是监听针对这个后门的请求，于是 服务器可以主动像这个端口推送消息。

 

######27.静态链接库(了解一下）

（此为.a文件，相当于java里的jar包，把一些类编译到一个包中，在不同的工程中如果导入此文件就可以使用里面的类，

  具体使用依然是#import “ xx.h”）。

 

######28.fmmpeg框架(了解一下）

（音视频编解码框架，内部使用UDP协议针对流媒体开发，内部开辟了六个端口来接受流媒体数据，完成快速接受之目的）.

 

######29.fmdb框架(了解一下)

（数据库框架，对sqllite的数据操作进行了封装，使用着可把精力都放在sql语句上面）。

 

######30.320框架（了解一下）

（ui框架，导入320工程作为框架包如同添加一个普通框架一样）。

  cover(open)   flower框架 (2d 仿射技术)，内部核心类是CATransform3D.

 

######31.什么是沙箱模型？哪些操作是属于私有api范畴?


某个iphone工程进行文件操作有此工程对应的指定的位置，不能逾越。

iphone沙箱模型的有四个文件夹，分别是什么，永久数据存储一般放在什么位置，得到模拟器的路径的简单方式是什么.

documents，tmp，app，Library。

（NSHomeDirectory()），

手动保存的文件在documents文件里

Nsuserdefaults保存的文件在tmp文件夹里

Documents 目录：您应该将所有de应用程序数据文件写入到这个目录下。这个目录用于存储用户数据或其它应该定期备份的信息。
AppName.app 目录：这是应用程序的程序包目录，包含应用程序的本身。由于应用程序必须经过签名，

所以您在运行时不能对这个目录中的内容进行修改，否则可能会使应用程序无法启动。
Library 目录：这个目录下有两个子目录：Caches 和 Preferences
Preferences 目录包含应用程序的偏好设置文件。您不应该直接创建偏好设置文件，而是应该使用NSUserDefaults类来取得和设置应用程序的偏好.
Caches 目录用于存放应用程序专用的支持文件，保存应用程序再次启动过程中需要的信息。


tmp 目录：这个目录用于存放临时文件，保存应用程序再次启动过程中不需要的信息。
获取这些目录路径的方法：
1，获取家目录路径的函数：
NSString *homeDir = NSHomeDirectory();
2，获取Documents目录路径的方法：
NSArray *paths = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES);
NSString *docDir = [paths objectAtIndex:0];
3，获取Caches目录路径的方法：
NSArray *paths = NSSearchPathForDirectoriesInDomains(NSCachesDirectory, NSUserDomainMask, YES);
NSString *cachesDir = [paths objectAtIndex:0];
4，获取tmp目录路径的方法：
NSString *tmpDir = NSTemporaryDirectory();
5，获取应用程序程序包中资源文件路径的方法：
例如获取程序包中一个图片资源（apple.png）路径的方法：
NSString *imagePath = [[NSBundle mainBundle] pathForResource:@”apple” ofType:@”png”];
UIImage *appleImage = [[UIImage alloc] initWithContentsOfFile:imagePath];
代码中的mainBundle类方法用于返回一个代表应用程序包的对象。


######文件IO写入
_1，将数据写到Documents目录：_
	
	- (BOOL)writeApplicationData:(NSData *)data toFile:(NSString *)fileName {


	NSArray *paths = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES);

	NSString *docDir = [paths objectAtIndex:0];

	if (!docDir) {

    NSLog(@”Documents directory not found!”); return NO;

	}

	NSString *filePath = [docDir stringByAppendingPathComponent:fileName];
	return [data writeToFile:filePath atomically:YES];

}


_2，从Documents目录读取数据：_
	
	- (NSData *)applicationDataFromFile:(NSString *)fileName {
		NSArray *paths = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES);

		NSString *docDir = [paths objectAtIndex:0];

		NSString *filePath = [docDir stringByAppendingPathComponent:fileName];

		NSData *data = [[[NSData alloc] initWithContentsOfFile:filePath] autorelease];

		return data;

	}
NSSearchPathForDirectoriesInDomains这个主要就是返回一个绝对路径用来存放我们需要储存的文件。


	- (NSString *)dataFilePath {

		NSArray *paths = NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES);
		NSString *documentsDirectory = [paths objectAtIndex:0];
		return [documentsDirectory stringByAppendingPathComponent:@"shoppingCar.plist"];
	}


		NSFileManager* fm=[NSFileManager defaultManager];
		if(![fm fileExistsAtPath:[self dataFilePath]]){


		//下面是对该文件进行制定路径的保存
		[fm createDirectoryAtPath:[self dataFilePath] withIntermediateDirectories:YES attributes:nil error:nil];


		//取得一个目录下得所有文件名
		NSArray *files = [fm subpathsAtPath: [self dataFilePath] ];


		//读取某个文件
		NSData *data = [fm contentsAtPath:[self dataFilePath]];


		//或者
		NSData *data = [NSData dataWithContentOfPath:[self dataFilePath]];
	}

iphone常见私有api的应用（比如直接发送短信，访问沙箱之外的磁盘文件）.

######32.你在开发项目中时，用到了哪些数据存储方式，iphone中常见的方式有哪些，各有什么区别？

数据存储五种形式的应用范围和性能区别

（core data,  sqllite,对象序列化，文件直接读写，NSUserDefault(保存数据到temp文件夹中)）
文件直接读写 >core data> 对象序列化> sqllite>NSUserDefault.


######33.线程的常见方法有哪些，你是如何处理多线程的，多线程同步问题你了解么？
线程创建的几种方式，线程的加锁，休眠，唤醒，解锁，退出，

多线程要考虑同步问题,解决同步问题的方式就是对某一资源加锁，当一个线程操作本资源时，其他线程不能操作 。

 
系统自带线程池（NSOpertionQueue）的作用：

凡是需要启动多个线程的地方都可以使用NSOpertionQueue，加入到NSOpertionQueue中的对象都需要继承NSOpertion。 NSOpertionQueue会在系统内部启动一个独立线程去执行这个被加入对象的main方法。

常用的地方是用nsoprationqueue 下载图片，文件。如果是自己创建一个线程池，无非就是启动多个线程的时候，

把这些线程对象放到一个大数组中，如果需要启动线程的时候，先从数组中找空闲线程来使用。

自己管理线程池最大的难题是不好处理当启动多个线程后，用户在多个界面的跳转的时候，对线程方法的回调管理。

而NSOpertionQueue可以很好的处理他。

 

######34.init和initwithobject区别（语法）？

   init创建的对象不带自动释放

 

######35.你连接服务器用的是什么方法，如果请求过程中，网络出了问题这么办？
NSUrlConnection 连接后，有一系列委托方法来接受来自服务器的响应和数据，

其中接受相应的方法回得到服务器要传回的数据有多大，接受数据的方法会反复调用来不断接受服务器数据，

如果网络出了问题了，会调用一个方法让你来做相关处理。


######36.你使用过json解析方式么，他们的底层是如何处理的你了解么？


json解析的用法，用框架的用法简单介绍：

底层原理遍历字符串中的字符，最终根据格式规定的特殊字符，比如{}号，[]号, : 号 等进行区分，

 {}号是一个字典的开始，[]号是一个数组的开始, : 号是字典的键和值的分水岭，最终乃是将json数据转化为字典，

字典中值可能是字典，数组，或字符串而已。

 

######37.xml解析的原理是什么，你还用过其他解析方式么？

NSXMLParser, 其他解析方式有自定义二进制解析，就是按字节去解析，电话会谈就是如此，

还可以是字符串之间用特殊符号连接的数据，将此数据用特殊符号可以分割成所用数据。

 

######38.协议是什么，有什么作用.？


协议很像java中的接口，某个类实现协议后，就必须实现协议中规定的@require的方法，比如一个类A, 一个类B都实现某“协议”后，

这个类A的对象和B的对象都可以赋值给这个协议的类型变量，比如  id<协议> 变量名 = A类或B类的对象，

于是这个变量就完成了能够指向多个不同的类的对象并调用对象中的实现协议的方法。

######39.类别有什么作用？
类别的使用 。 类别有三大作用，

1. 可以使本来需要在.h中声明的方法放到.m文件中声明，达到了可以使方法不对外公开。

2. 可以方便的扩展类，甚至系统类都可以轻易扩展，维护了代码原本的结构不受影响。

3. 类别可以写到不同的.h或.m文件中，可以分散代码到跟类别的扩展功能想关联的地方，方便查看。

######40.分线程回调主线程方法是什么，有什么作用？
	[self performSelectorOnMainThread:@selector(buttonGo2) withObject:nil waitUntilDone:YES];
	[self performSelector:@selector(buttonGo2) onThread:[NSThread mainThread] withObject:nil waitUntilDone:YES];
需要即时刷新ui控件的时候，经常使用。

######41.iphone阅读器，如果要读取一个文本文件，请问你是如何处理编码问题的？另外像pdf格式的文件，你如何读取。?

iphone手机阅读器中对于PDF格式的阅读，可以直接用UIWebView控件显示，也可以从网上下到很多直接读取pdf格式的代码

直接从pdf中得到数据。

复杂表格动画

	- (void)insertRowsAtIndexPaths:(NSArray *)indexPaths withRowAnimation:(UITableViewRowAnimation)animation; -(void)deleteRowsAtIndexPaths:(NSArray *)indexPaths withRowAnimation:(UITableViewRowAnimation)animation;
	- (void)reloadRowsAtIndexPaths:(NSArray *)indexPaths withRowAnimation:(UITableViewRowAnimation)animation;

######42.你在开发大型项目的时候，如何进行内存泄露检测的?
  可以通过xcode的自带工具run---start with performance tool里有instruments下有个leaks工具，

  启动此工具后，运行项目，工具里可以显示内存泄露的情况，双击可找到源码位置，可以帮助进行内存泄露的处理。

 

######43.你做iphone开发时候，有哪些传值方式，view和view之间是如何传值的？

 压栈。
 
 传值：可以用 block  delegate   , NSNotificationCenter  ,很少用NSUserDefaults
 

######44.让一个物体从界面中的一点运动到另外一点，有哪些方法？

四种方式：

1. beginAnimation

2. 线程

3. NSTimer

4. 图层动画（路径）


######45.你了解哪些加密方式？
   Base64, MD5, 循环右移位等.

 

######46.地图定位

CLLocationManager位置管理器  使用Core Location框架来确定iphone的位置（GPS，蜂窝基站三角网，wps三种方式）    

MKMapView提供了一套可植入的地图接口，可以让我们在应用中展示地图，并对其进行相关的操作。一般来说，我们可以指定一个展示区域，放一些标记在上面，还可以加盖一些层在上面。

MKMapView依赖Google map里面相关服务（如Google Earth API等），所以地图的左下角会有Google字样。

######47.打开url

[[UIApplication sharedApplication] openURL:[NSURL URLWithString:@"tel://8004664411"]];mailto://   sms://

 

######48. http网络通信

ASIHTTPRequest 是一个直接在CFNetwork上做的开源项目：提供直接提交(HTTP POST)文件的API，异步请求与队列，自动管理上传与下载队列管理机,ASIFormDataRequest用于适合上传文件，图片数据。

 

######49. 图片浏览

UIImagePickerController可以从相册，相机，胶卷里获得图片。


######50. 对像序列化

NSCoding    encodeWithCoder   initWithCoder

NSKeyedUnarchiver   NSKeyedArchiver

 

######51. 各种picker

UIDatePicker   UIPickerView

 

######52. 

   电影播放

   MPMoviePlayerController

   音乐播放

   MPMusicPlayerController

 

######53.线程 ？

      a. 线程的创建和使用规则?

         答：NSThread

                 三种方法

                - (id)init; // designated initializer

                - (id)initWithTarget:(id)target selector:(SEL)selector object:(id)argument;

                + (void)detachNewThreadSelector:(SEL)aSelector toTarget:(id)aTarget withObject:(id)anArgument

                 - (void)start;

       b. 主分线程

          答：启动分线程，上面已提到！加到主线程方法performSelector！

          //加到主线程addData()是主线程的方法！只有加到主线程后，才能调用主线程的方法

         [target performSelector:@selector(addData:) onThread:[NSThread mainThread] withObject:item waitUntilDone:YES];

           //[target addData:item];//没有加到主线程后，调用主线程的方法！一定会崩！

 

      c.线程锁

         答：NSCondition

                 方法：

                 [thread lock];//加锁

                 sleep(n);//线程休眠

                 [thread singnal];//相当于通知，线程启动

                 [thread unlock];//解锁

                 [thread exit];//线程退出

 

######54.各种 排序算法？

  希尔排序、快速排序、冒泡排序、

 

######55.通信底层原理

 答：OSI七层模型

  7 应用层：    ftp,smtp,http,telnet,tftp（通过各种协议，最终还是包装成TCP数据包，发送到网络中！）

  6 表现层：

  5 会话层：

  4 传输层：    tcp udp

  3 网络层：    ip,ICMP,IGRP,EIGRP,OSPF,ARP

  2 数据链路层： STP,VT

  1 物理层：

 

######56. 为什么很多内置类如UITableViewController的delegate属性都是assign而不是retain的？

答：

 会引起循环引用

 所有的引用计数系统，都存在循环应用的问题。例如下面的引用关系：

  * 对象a创建并引用到了对象b.

  * 对象b创建并引用到了对象c.

  * 对象c创建并引用到了对象b.

 
这时候b和c的引用计数分别是2和1。

  当a不再使用b，调用release释放对b的所有权，因为c还引用了b，所以b的引用计数为1，b不会被释放。

  b不释放，c的引用计数就是1，c也不会被释放。从此，b和c永远留在内存中。

这种情况，必须打断循环引用，通过其他规则来维护引用关系。我们常见的delegate往往是assign方式的属性而不是retain方式 的属性，

赋值不会增加引用计数，就是为了防止delegation两端产生不必要的循环引用。

如果一个UITableViewController 对象a通过retain获取了UITableView对象b的所有权，这个UITableView对象b的delegate又是a，

如果这个delegate是retain方式的，那基本上就没有机会释放这两个对象了。自己在设计使用delegate模式时，也要注意这点。

 

######57. 以下每行代码执行后，person对象的retain count分别是多少？

      Person *person = [[Person alloc] init]; count 1

      [person retain]; retain  count 2

      [person release];retain count 1

      [person release];retain count = 0

 

######58.在一个对象的方法里面:

######self.name = “object”;
######和
######name ＝”object”

######有什么不同吗?  

答：self.name = "object"会调用对象的setName()方法,会使object引用计数加1，name = "object"会直接把object赋值给当前对象的name 属性，引用计数不增加。


######59.readwrite，readonly，assign，retain，copy，nonatomic属性的作用？

 

@property是一个属性访问声明，扩号内支持以下几个属性： 

1. getter=getterName，setter=setterName，设置setter与getter的方法名

2. readwrite,readonly，设置可供访问级别 
3. assign，setter方法直接赋值，不进行任何retain操作，为了解决原类型与环循引用问题
4. retain，setter方法对参数进行release旧值再retain新值，所有实现都是这个顺序(CC上有相关资料) 
5. copy，setter方法进行Copy操作，与retain处理流程一样，先旧值release，再Copy出新的对象，retainCount为1。这是为了减少对上下文的依赖而引入的机制。 

6. nonatomic，非原子性访问，不加同步，多线程并发访问会提高性能。注意，如果不加此属性，则默认是两个访问方法都为原子型事务访问。锁被加到所属对象实例级(我是这么理解的…)。

7. @synthesize xxx; 来实现实际代码


######60.1.main()

######{

######int a[5]={1,2,3,4,5};

######int *ptr=(int *)(&a+1);

######printf("%d,%d",*(a+1),*(ptr-1));

######}

答：2,5

   *(a+1）就是a[1]，*(ptr-1)就是a[4],执行结果是2，5
　　&a+1不是首地址+1，系统会认为加一个a数组的偏移，是偏移了一个数组的大小（本例是5个int）
　　int *ptr=(int *)(&a+1);
　　则ptr实际是&(a[5]),也就是a+5
原因如下：

　　&a是数组指针，其类型为 int (*)[5];
　　而指针加1要根据指针类型加上一定的值，不同类型的指针+1之后增加的大小不同。
　　a是长度为5的int数组指针，所以要加 5*sizeof(int)
　　所以ptr实际是a[5]
　　但是prt与(&a+1)类型是不一样的(这点很重要)
　　所以prt-1只会减去sizeof(int*)

　   a,&a的地址是一样的，但意思不一样
     a是数组首地址，也就是a[0]的地址，&a是对象（数组）首地址，
     a+1是数组下一元素的地址，即a[1],&a+1是下一个对象的地址，即a[5].

