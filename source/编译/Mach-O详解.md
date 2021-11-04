#### 一、Mach-O说明：
> Mach-O 是 Mach Object 文件格式的缩写，是 mac 以及 iOS 上可执行文件的格式

##### 1.常见 Mach-O 文件：
a.目标文件：.o
b.库文件：.a、.lib、framework
c.可执行文件：dyld、.dsym
##### 2.文件格式：
Mach-O 可以是多架构的二进制文件，称之为 [通用二进制文件] 或者 [Fat Binary]。Mach-O 支持多架构在一个包中，如：armv7、arm64等，iOS实际下载安装的只会用其中一个架构。
##### 3.拆分、重组 Mach-O     
```
// 使用lipo -info 可以查看MachO文件包含的架构
$ lipo -info MachO文件
// 使用lipo –thin 拆分某种架构
$ lipo MachO文件 –thin 架构 –output 输出文件路径
// 使用lipo -create  合并多种架构
$ lipo -create MachO1  MachO2  -output 输出文件路径
```
#### 二、Mach-O的文件结构
Mach-O分为三部分：Header、Load_Commands、Data。
##### 1.Header
> Header 描述了 Mach-O 的 CPU 类型，文件类型、加载命令的数量和大小等。

###### Header 结构：
```
struct mach_header_64 {
	uint32_t	magic;		/* 0xfeedface是32位，0xfeedfacf是64位 */
	cpu_type_t	cputype;	/* CPU类型 */
	cpu_subtype_t	cpusubtype;	/* machine specifier */
	uint32_t	filetype;	/* 文件类型（执行文件、库文件、Core、内核扩展...） */
	uint32_t	ncmds;		/* 加载命令的个数 */
	uint32_t	sizeofcmds;	/* 加载命令的长度 */
	uint32_t	flags;		/* dyld加载时需要的标志位 */
	uint32_t	reserved;	/* reserved */
};
```
###### FileType 类型：
Mach-O文件不仅仅用来实现可执行文件，同时还用来实现其他内容

| FileType       | 用处              | 例子                     |
|----------------|-----------------|------------------------|
| MH_OBJECT      | 编译过程中产生的*.obj文件 | Gcc -c xxx.c 生成xxx.o文件 |
| MH_EXECUTABLE  | 可执行二进制文件        | /usr/bin/git           |
| MH_CORE        | CoreDump        | 崩溃时Dump文件              |
| MH_DYLIB       | 动态库             | /usr/lib/里面那些库         |
| MH_DYLINKER    | 链接器linker       | /usr/lib/dyld文件        |
| MH_KEXT_BUNDLE | 内核扩展文件          | 自己开发的简单内核模块    |

###### Flag Type 说明：

| Flag Type                                                               | 含义                         |
|-------------------------------------------------------------------------|----------------------------|
| MH_NOUNDEFS<span class="Apple-tab-span" style="white-space:pre"></span> | 目标没有未定义的符号，不存在链接依赖         |
| MH_DYLDLINK                                                             | 该目标文件是dyld的输入文件，无法被再次的静态链接 |
| MH_PIE                                                                  | 允许随机的地址空间                  |
| MH_ALLOW_STACK_EXECUTION                                                | 栈内存可执行代码，一般是默认关闭           |
| MH_NO_HEAP_EXECUTION                                                    | 堆内存无法执行代码                  |

##### Load Commands
> Commands 所有占用内存的总和在 Mach-O Header里已经给出。在加载过 Header 之后就是通过解析 LoadCommand 来加载接下来的数据。

###### LoadCommand 结构：
```
struct load_command {
	uint32_t cmd;		/* 加载命令的类型 */
	uint32_t cmdsize;	/* 命令的总大小，byte位单位 */
};
```
###### cmd字段：

| Command类型                | 处理函数                | 用途                         |
|--------------------------|---------------------|----------------------------|
| LC_SEGMENT；LC_SEGMENT_64 | load_segment        | 将segment中的数据加载并映射到进程的内存空间去 |
| LC_LOAD_DYLINKER         | load_dylinker       | 调用/usr/lib/dyld程序          |
| LC_UUID                  | load_uuid           | 载128-bit的唯一ID              |
| LC_THREAD                | load_thread         | 开启一个MACH线程，但是不分配栈空间。       |
| LC_UNIXTHREAD            | load_unixthread     | 开启一个UNIX线程                 |
| LC_CODE_SIGNATURE        | load_code_signature | 进行数字签名                     |
| LC_ENCRYPTION_INFO       | set_code_unprotect  | 加密二进制文件                    |


