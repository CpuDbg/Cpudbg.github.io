<!-- article-title样式为居中 -->
<!-- no-number标记后该标题不会自动生成编号 -->

<h1 class="article-title no-number">第一章 界面和菜单</h1>

<h1 class="article-title no-number">第二章 界面和菜单</h1>

<h1 class="article-title no-number">第三章 界面和菜单</h1>

# 菜单
<img src="..\Img\菜单展示.png" style="zoom:100%;" />

主菜单下一般会有八个菜单项. 它们分别是:


>  - **File**(文件)
>  - **View**(视图)
>  - **Debug**(调试)
>  - **Plugins**(插件)(截图中没有, 后面插件章节会详细介绍)
>  - **Options**(选项)
>  - **Windows**(窗口)
>  - **Help**(帮助)
>  - **发布日期以及软件版本号**

## File
<img src="..\Img\File.png" style="zoom:100%;" />

File菜单下一般会有如下几个子菜单项, 它们分别是:

> - **Open** (打开调试目标)
> - **Attach** (附加进程)
> - **Exit** (关闭调试器)
> - **Clear Invalid History** (清除无效的历史调试纪录)
> - **Clear All History** (清除所有的历史调试纪录)
> - **历史调试纪录**

### Open
<img src="..\Img\打开调试目标.png" style="zoom:100%;" />

> * **文件名** 输入要调试的目标路径(绝对路径)
> * **文件类型** 选择指定类型的文件(其它的过滤不显示)
  
<img src="..\Img\文件类型.png" style="zoom:100%;" />

> * **参数** 调试目标运行时选定的运行参数. (一般调试类似 记事本之类的软件会用到.)
> * **运行目录** 为调试目标设置一个运行目录.

### Attach
<img src="..\Img\Attach.png" style="zoom:100%;"/>


点击附加弹出如上附加进程窗口.
对着指定进程右键, 弹出对话框.


> * **PID (Decimalism)** 勾选和取消 列表中的进程 会以10进制和16进制之间有切换.
> * **Refresh Big endian** 进程列表以大端序排列 (最后运行的进程在列表最前面.下同)
> * **Refresh Little endian** 小端序排列
> * **Attach** 调试器附加进程
> * **Inject Dll** 选定的进程注入模块.
> * **Go to Windows** 跳转至进程窗口
> * **Go to PE** 跳转至PE窗口
> * **Go to Memory** 跳转至内存窗口
> * **Go to Module** 跳转至模块窗口
> * **Go to Handle** 跳转至句柄窗口
> * **Go to Thread** 跳转至线程窗口
> * **Pause Process** 暂停选定进程
> * **Terminate Process** 结束选定进程
> * **Open the folder** 打开选定进程的文件夹





# CPU窗口
>  一级标题的内容

# 日志窗口
>  一级标题的内容

# 模块窗口
>  一级标题的内容

# 内存窗口
>  一级标题的内容

# 进程窗口
>  一级标题的内容

# 线程窗口
>  一级标题的内容

# 监视窗口
>  一级标题的内容

# 追踪窗口
>  一级标题的内容

# 补丁窗口
>  一级标题的内容

# 断点窗口
>  一级标题的内容

# 源码窗口
>  一级标题的内容

# 插件窗口
>  一级标题的内容

# 句柄窗口
>  一级标题的内容

# xxx窗口
>  一级标题的内容

# xxx窗口
>  一级标题的内容

# xxx窗口
>  一级标题的内容

# xxx窗口
>  一级标题的内容

# xxx窗口
>  一级标题的内容

# xxx窗口
>  一级标题的内容






示例代码如下：

```asm
004132FB  |.  8940 04       |MOV DWORD PTR [EAX+0x4],EAX
004132FE  |.  83C0 08       |ADD EAX,0x8
00413301  |.  4A            |DEC EDX                                 ;  内存访问.<ModuleEntryPoint>
00413302  |.^ 75 F4         \JNZ SHORT 内存访问.004132F8
00413304  |.  8BFB          MOV EDI,EBX
00413306  |.  6A 04         PUSH 0x4                                 ; /Protect = PAGE_READWRITE
00413308  |.  C1E7 0F       SHL EDI,0xF                              ; |
0041330B  |.  0379 0C       ADD EDI,DWORD PTR [ECX+0xC]              ; |
0041330E  |.  68 00100000   PUSH 0x1000                              ; |AllocationType = MEM_COMMIT
00413313  |.  68 00800000   PUSH 0x8000                              ; |Size = 8000 (32768.)
00413318  |.  57            PUSH EDI                                 ; |Address = 内存访问.<ModuleEntryPoint>
00413319  |.  FF15 FCF14300 CALL DWORD PTR [<&KERNEL32.VirtualAlloc>>; \VirtualAlloc
0041331F  |.  85C0          TEST EAX,EAX
00413321  |.  75 08         JNZ SHORT 内存访问.0041332B
00413323  |.  83C8 FF       OR EAX,0xFFFFFFFF
00413326  |.  E9 93000000   JMP 内存访问.004133BE
0041332B  |>  8D97 00700000 LEA EDX,DWORD PTR [EDI+0x7000]
00413331  |.  3BFA          CMP EDI,EDX                              ;  内存访问.<ModuleEntryPoint>
00413333  |.  77 3C         JA SHORT 内存访问.00413371
00413335  |.  8D47 10       LEA EAX,DWORD PTR [EDI+0x10]
00413338  |>  8348 F8 FF    /OR DWORD PTR [EAX-0x8],0xFFFFFFFF
0041333C  |.  8388 EC0F0000>|OR DWORD PTR [EAX+0xFEC],0xFFFFFFFF
00413343  |.  8D88 FC0F0000 |LEA ECX,DWORD PTR [EAX+0xFFC]
00413349  |.  C740 FC F00F0>|MOV DWORD PTR [EAX-0x4],0xFF0
00413350  |.  8908          |MOV DWORD PTR [EAX],ECX
00413352  |.  8D88 FCEFFFFF |LEA ECX,DWORD PTR [EAX-0x1004]
00413358  |.  8948 04       |MOV DWORD PTR [EAX+0x4],ECX
0041335B  |.  C780 E80F0000>|MOV DWORD PTR [EAX+0xFE8],0xFF0
00413365  |.  05 00100000   |ADD EAX,0x1000
0041336A  |.  8D48 F0       |LEA ECX,DWORD PTR [EAX-0x10]
0041336D  |.  3BCA          |CMP ECX,EDX                             ;  内存访问.<ModuleEntryPoint>
0041336F  |.^ 76 C7         \JBE SHORT 内存访问.00413338
00413371  |>  8B45 FC       MOV EAX,DWORD PTR [EBP-0x4]              ;  kernel32.BaseThreadInitThunk
00413374  |.  8D4F 0C       LEA ECX,DWORD PTR [EDI+0xC]
00413377  |.  05 F8010000   ADD EAX,0x1F8
0041337C  |.  6A 01         PUSH 0x1
0041337E  |.  5F            POP EDI                                  ;  kernel32.7649FE09
0041337F  |.  8948 04       MOV DWORD PTR [EAX+0x4],ECX
00413382  |.  8941 08       MOV DWORD PTR [ECX+0x8],EAX
00413385  |.  8D4A 0C       LEA ECX,DWORD PTR [EDX+0xC]
00413388  |.  8948 08       MOV DWORD PTR [EAX+0x8],ECX
0041338B  |.  8941 04       MOV DWORD PTR [ECX+0x4],EAX
0041338E  |.  83649E 44 00  AND DWORD PTR [ESI+EBX*4+0x44],0x0
00413393  |.  89BC9E C40000>MOV DWORD PTR [ESI+EBX*4+0xC4],EDI       ;  内存访问.<ModuleEntryPoint>
0041339A  |.  8A46 43       MOV AL,BYTE PTR [ESI+0x43]
0041339D  |.  8AC8          MOV CL,AL
0041339F  |.  FEC1          INC CL
004133A1  |.  84C0          TEST AL,AL
004133A3  |.  8B45 08       MOV EAX,DWORD PTR [EBP+0x8]
004133A6  |.  884E 43       MOV BYTE PTR [ESI+0x43],CL
004133A9  |.  75 03         JNZ SHORT 内存访问.004133AE
004133AB  |.  0978 04       OR DWORD PTR [EAX+0x4],EDI               ;  内存访问.<ModuleEntryPoint>
004133AE  |>  BA 00000080   MOV EDX,0x80000000
004133B3  |.  8BCB          MOV ECX,EBX
004133B5  |.  D3EA          SHR EDX,CL
004133B7  |.  F7D2          NOT EDX                                  ;  内存访问.<ModuleEntryPoint>
004133B9  |.  2150 08       AND DWORD PTR [EAX+0x8],EDX              ;  内存访问.<ModuleEntryPoint>
004133BC  |.  8BC3          MOV EAX,EBX
004133BE  |>  5F            POP EDI                                  ;  kernel32.7649FE09
004133BF  |.  5E            POP ESI                                  ;  kernel32.7649FE09
004133C0  |.  5B            POP EBX                                  ;  kernel32.7649FE09
004133C1  |.  C9            LEAVE
004133C2  \.  C3            RETN
```

JS 代码：

```js
console.log('Hello World!');
```

C 代码：

```c
printf('Hello World!');
```

Python 代码：

```python
print('Hello World!')
```

Java 代码：

```java
System.out.print('Hello World!');
```
