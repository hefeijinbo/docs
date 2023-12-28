# windows api
```
WinDef.h 基本数据类型
WinBase. 内核有关定义(kernel)
WinGdi.h 图形设备接口有关定义
WinUser.h 用户界面有关定义
```

# WinMain
主函数 

Windows程序入口函数

原型如下:
```
int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPSTR lpCmdLine,int nCmdShow );
```

WinMain函数接收4个参数，这些参数都是在系统调用WinMain函数时，传递给应用程序的。

### hInstance:

1. 表示`该程序当前运行的实例句柄`，是一个`数值标识`。当程序在Windows下运行时，它`唯一标识运行中的实例`（注意，只有运行中的程序实例，才有实例句柄）。一个应用程序可以运行多个实例，每运行一个实例，系统都会给该实例分配一个实例句柄，并通过hInstance参数传递给WinMain函数。
2. 表示模块, 模块代表一个运行中的.exe或.dll文件, 表示这个文件的所有代码和资源, 磁盘上的文件不是模块,载入内存后运行时才成为模块.
3. 每个模块都有一个唯一的模块句柄来标识,模块句柄实际上就是一个内存基地址,系统将.exe或.dll文件加载到地址空间的这个位置

### hPrevInstance:

表示当前实例的前一个实例的句柄。通过查看MSDN我们可以知道，在Win32环境下，这个参数总是NULL，`在Win32环境下，这个参数不再起作用`。

### lpCmdLine

是一个以空字符结尾的字符串，内容为`命令行的参数`。

### nCmdShow

指定程序的`窗口应该如何显示`，例如最大化、最小化、隐藏等。这个参数的值由该程序的调用者所指定，应用程序通常不需要去理会这个参数的值。

# MessageBox 
对话框
```
int WINAPI MessageBox(
    HWND hWnd, // 消息框的所有者(拥有者)的窗口句柄
    LPCTSTR lpText, // 要显示的消息内容
    LPCTSTR lpCaption, // 消息框的标题
    UINT uType, // 消息框的图标样式和暗流样式
)

MessageBox(NULL, TEXT("用户点击了按钮"), TEXT("caption"), MB_OK);
```

```
WinMain函数前的修饰符WINAPI，其实就是__stdcall。表示函数压栈方式和函数调用约定
```
# 字符编码ASCII, 扩展ASCII DBCS Unicode 和 ANSI
- ASCII: 表示数字,大小写字母,标点符号,运算符号
- 扩展ASCII:  在 ASCII基础上,支持框线,音标和其他欧洲非英语系字母
- DBCS: 双字节字符集, 用2个字节表示除ASCII以外的字符,常见的就是我国的GB系列编码,也可以用双字节表示日语, 韩语等编码
- Unicode: 表示不同国家和地区的语言, 只有一个字符集, 包含了世界上任何一个国家和地区的语言所用的字符, 定义了所有的主要语言中使用的字母,符号和标点.Unicode有三种编码形式,允许字符以字节,字和双字格式存储
    - UTF8 字符编码为1字节,有的字符编码为双字节,有的字符编码为3字节
    - UTF16 将每个字符编码为2字节,在谈到Unicode,除非特殊声明,都是指UTF16编码,因为固定位16字节,所以编码和计算长度速度快
    - UTF32 将每个字符都编码为4字节,用于不太关心存储空间的环境中,一般很少用到这种编码
  # ANSI Unicode
  - ANSI 不同编码间不兼容,表示具体国家的多字节字符集
  - Unicode : 统一的字符集

# 字符和字符串处理
- char: 单字节组成的字符
- wchat_t: 宽字节,一般指UTF16, 统一用两字节来表示一个字符, 是现代计算机默认编码方式
  占用空间比多字节多,但是处理速度快
```
wchat_t wc = L'A';
wchat_t *pwStr = L"Hello";
wchat_t szwStr[] = L"Hello";
```

# sizeof
返回变量,对象或数据类型所占用的`字节数`
```
char ch = 'A'; // 1
wchar_t wch = L'A'; // 2
char str[] = "c语言"; // 6, C 占用1字节,语言占用4字节,还有1字节结束符号
wchar_t wstr[] = L"C语言"; // 8, 一个字符占用两个字节, 还有2字节的字符串结束标志
printf("ch = %d, wch = %d, str = %d, wstr = %d\n", sizeof(ch), sizeof(wch), sizeof(str), sizeof(wstr));
```

# TCHAR
Windows 在winnt.h 头文件中定义了自己的字符和宽字符数据类型
```
typedef char CHAR: // 字符
ifndef _MAC
    typedef wchart_t WCHAR; // 宽字符
#else 
    // 苹果Mac 编译器没有定义wchar_t数据类型,宽字符被定义为16位整数
    typedef unsigned short WCHAR;
#endif
```
VS 创建项目的时候,默认使用unicode字符集, 右键点击项目名称->属性->配置属性->C/C++->命令行,可以看到UNICODE和_UNICODE都被定义了, 如果把项目属性设置为多字符字符集,这两个宏都会被取消定义

根据项目是否使用`Unicode字符集`, TCHAR被解释为CHAR(char)或WCHAR(wchar_t)数据类型

# TEXT 宏
winnt.h头文件定义了宏
```
#ifdef UNICODE
    #define __TEXT(quote) L##quote
#else 
    #define __TEXT(quote) quote
#endif
```
`##` 被称为令牌粘贴,表示把字母L和宏参数拼接到一起,假设quoto是Hello, L#quoto就是 L"Helllo"了, L表示宽字符
# 字符串数据类型
winnt.h 头文件中定义了许多字符串数据类型, 例如
```
typedef char CHAR;
typedef CHAR *NPSTR,*LPSTR,*PSTR;
typedef CONST CHAR *LPCSTR,*PCSTR;
typedef WCHAR *NWPSTR, *LPWSTR,*PWSTR;
typedef CONST WCHAR *LPCWSTR, *PCWSTR;

#ifdef UNICODE
    typedef LPWSTR PTSTR,LPTSTR;
    typedef LPCWSTR PCTSTR,LPCTSTR;
#else 
    typedef LPSTR PTSTR,LPTSTR,PUTSTR,LPUTSTR;
    typedef LPCSTR PCTSTR,LPCTSTR,PCUTSTR,LPCUTSTR;
```
C表示const, 
如果希望我们的程序支持ANSI和Unicode版本,通过编写两套代码分别实现ANSI和Unicode版本,有了这些宏,能实现对两种编码的`通用编程`(通用版本)

# 通用入口点函数
```
int WINAPI _tWinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPTSTR lpCmdLine, int nCmdShow);
```
根据是否定义了UNICODE,入口点函数会被解释为
```
int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPTSTR lpCmdLine, int nCmdShow);

int WINAPI wWinMain(HINSTANCE hInstance, HINSTANCE hPrevInstance, LPTSTR lpCmdLine, int nCmdShow);
```
本书中都使用 WinMain,如果使用 _tWinMain, 那么必须包含 tchar.h

# 常用字符串处理函数
1. 获取字符串长度
strlen wcslen(针对宽字符,返回宽字符数量)
它两的`通用版本`是 `_tcslen`
```
#ifdef _UNICODE
    #define _tcslen wcslen
#else 
    #define _tcslen strlen
#endif
```
# 查找字符串首次出现的指定`字符`
strchr(首次出现), 通用版本是 _tcschar
strrchr(最后出现), 通用版本是 _tcsrchr

# 在一个字符串中查找另一个`字符串``
strstr
wcsstr(宽字符)

通用版本:
_tcsstr

# 从一个字符串中查找另一个字符串中的任何一个字符
strpbrk
wcspbrk
通用版本:
_tcspbrk

# 转换`字符串`大小写
转换成大写: _strupr和_wcsupr
转换成小写: _strlwr和_wcslwr
通用版本: _tcsupr 和 _tcslwr

另外一个`字符`转换成大写字母的函数是 touppper 和 towupper,通用版本是 _touppper

`字符`转换成小写字母的函数是 tolower 和 towlower, 通用版本是 _totlower

# 字符串拼接
strcat wcscat, 通用版本是 _tcscat, 建议使用安全版本的 _tcscat_s

# 字符串复制
strcpy 和 wcscpy

安全版本是 strcpy_s 和 wcscpy_s

通用版本是 _tcscpy_s

也可以使用 `StringCchCopy` 函数代替 _tcscopy_s,更加安全,`不会`出现`缓冲区溢出`问题

也可以是用内存复制函数 `memcpy_s`, 该函数可以指定目标缓冲区和原缓冲区的字节数,`不会`出现`缓冲区溢出`问题

# 字符串比较
strcmpy 和 wcscmp

通用版本是 _tcscmp

```
int strcmp(const char *string1, const char *string2);

int wcscmp(const wchar_t *string1, const wchar_t *string2);
```
函数对 string1 和 string2 执行序号(`ASCII码值`)比较并返回一个指示他们关系的值, 返回值指明 string1 和 string2 的大小关系, (比较的时候区分大小写)

# 分割字符串
strtok,wcstok 和 _tcstok

安全版本是 strtok_s wcstok_s 和 _tcstok_s

函数声明如下
```
char* strtok_s(
    char * strToken, // 要分割的字符串
    const char *strDelimit, // 分隔符字符串, 分隔符字符串中的每个字符均为分隔符

)
```

# 窗口相关
RegisterClassEx 注册窗口类

注册后就可以使用注册的窗口类去创建具体的窗口类了
CreateWindowEX

ShowWindows 创建之后窗口只是再内存中，在屏幕上显示窗口

UpdateWindow 刷新窗口别的布局 通过向窗口发送WM_PAINT 消息来更新窗口