封装好的c++ string快速处理工具,主要实现了类似js的Split功能，类似py的format功能，以及Replace字符串替换功能。
使用c++17以上的版本，经测试可以在windows和linux平台上运行

```cpp
	建议的引入方式：
	#include "String_Utils.hpp"
	namespace su = String_Utils;

	string str = "12345678888889123456789ab\ncde88888fghijklmnopq88888rstuvwxyz";

	//Split参数1为待处理的字符串，参数二类型是vector<string> 传入要将哪些字符串作为分割的标志
	vector<string> list = su::Split(str, {"888","777","x","z"});

	int i = 100;
	//类似python的format功能，参数一为待处理的字符串，
	//字符串中“{}”作为待填入参数的位置，
	//参数二为字符串列表，同Split函数，
	//“_S”宏定义就是to_string函数，可以快速将任意类型变量变成字符串。
	//字符串列表中的参数先后对应到“{}”标记中
	//{}里面的类型支持int、size_t、string、char*类型，代码会自动转换为string类型，非常方便
	string str2 = su::fmt("hello_{}_{}_{}.sh\n___{}", {1,i+10,_S(i),"123456"});


	//字符串替换，自动查找要替换的字符串，然后替换成目标字符串，字符串长度可以任意
	//参数一为待处理的字符串
	//参数二为要替换的字符串
	//参数三为替换的目标字符串
	string str3 = su::Replace(str,"888","___");

```
