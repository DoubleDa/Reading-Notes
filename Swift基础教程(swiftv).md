# Swift基础教程(swiftv)

## 课程背景

1.苹果推出全新编程语言Swift取代Objective-C

2.Swift**快速**、**动态**、**强大**，必将成为iOS主流语言

## 核心内容

1.Swift语言语法和基本操作

2.使用Swift编程语言开发iOS程序

## swift基础教程

1 hello world

2 变量和常量

	import Foundation

	//变量
	var a = 1
	a = 10
	var b = 2

	//常量
	let c = a + b
	print(c)
	
3 类型

	import Foundation

	//字符串
	var str = "Hello Swift"

	//字符串（指定类型）
	var s : String = "String"
	var i : Int = 16
	var words : String = "dayongxin"

	print(words)
	
4 字符串连接

	import Foundation

	//字符串拼接
	var str = "Hello"
	//字符串与字符串拼接
	//str = str + " Swift!"
	var i = 10
	//字符串与数字拼接
	//str = "\(str),hdsjkghksfjdhgjkj,\(199)"
	str = "\(str),hdsjkghksfjdhgjkj,\(i)"
	print(str)
	
5 数组

	import Foundation

	//数组
	var arr = ["sj","ddfskjl",100,89.1]

	//空数组
	var myArr = []

	//空数组有类型
	var strArr = [String]()
	print(arr)
	print(myArr)
	print(strArr)
	
6 字典

	import Foundation

	//静态的字典
	var dict = ["key1":"value1","key2":"value2"]

	//动态的字典
	dict["key3"] = "value3"

	print(dict)

	print(dict["key2"])
	
7 循环

	import Foundation

	var arr = [String]()
	//第一种for循环
	for index in 0...100{
    	arr.append("Item\(index)")
	}

	//print(arr)

	//第二种for循环
	for value in arr{
	//    print(value)
	}

	var i = 0
	//while循环
	while i < arr.count{
    	print(arr[i])
    	i += 1
	}

	//for循环遍历字典
	var dict = ["key1":"value1","key2":"value2"]

	for (key,value) in dict{
    	print("\(key)-\(value)")
	}
	
8 流程控制

	import Foundation

	//流程控制
	//输出0-100的偶数
	for index in 0...100{
    	if index%2==0{
        	print(index)
    	}
	}

	//可选变量(?表示可选变量)
	var myName : String?="dayongxin"
	myName = nil

	if let name = myName{
    	//myName不为空的时候会走这儿
    	print("Hello \(name)")
	}
	
9 函数

	import Foundation

	//函数-无返回值
	func sayHello(name : String){
    	print("Hello \(name)")
	}

	sayHello("Swift!")

	//函数－有返回值
	func sayHelloName(myName : String) -> String
	{
    	return myName
	}

	print(sayHelloName("哒哒"))

	//返回多个值
	func getValues() -> (Int,Int,Int){
    	return (2,3,4)
	}

	let (a,b,c) = getValues()
	print(a)

	//把函数作为对象处理
	var fun = sayHello
	fun("哒哒")
	
10 面向对象

	import Foundation

	//面向对象
	class Hi{
    	func sayHi() {
        	print("dayongxin")
    	}
	}

	var hi = Hi()
	hi.sayHi()

	//继承
	class Hello : Hi{
    	var name : String
    	//构造方法
    	init(name : String) {
        	self.name = name
    	}
    	//重写某个方法
    	override func sayHi() {
        	print("哒哒:\(self.name)")
    	}
	}

	var hello = Hello(name:"啦啦")
	hello.sayHi()
	
11 开发iOS项目





		




