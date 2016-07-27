---
layout: post
title:  "sublime text usage"
date:   2016-07-27 14:17:00 +0800
categories: jekyll update
---

#sublime text3

###一、从官网下载sublimetext3安装包
sublimetext官网地址：http://www.sublimetext.com/3  
下载最新版本sublimetext3 deb安装包，把安装包copy到目标机上。
###二、安装sublimetext3 deb安装包
执行如下命令：  
```bash
$ sudo dpkg -i sublime-text_build-3059_amd64.deb
```
###三、安装Package Control
Package control是必装插件，所有其他的插件和主题都可以通过它来安装。  
（1）简单的安装方法
打开sublimetext3，点击View->Show Console菜单打开命令行，粘贴如下代码：
```bash
import urllib.request,os; pf = 'Package Control.sublime-package'; ipp =      sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); open(os.path.join(ipp, pf), 'wb').write(urllib.request.urlopen( 'http://sublime.wbond.net/' + pf.replace(' ','%20')).read())
```
（2）手动安装
可能由于各种原因，无法使用代码安装，那可以通过以下步骤手动安装Package Control：    
* 1. 点击Preferences > Browse Packages菜单
* 2. 进入打开的目录的上层目录，然后再进入Installed Packages/目录
* 3. 下载Package Control.sublime-package并复制到Installed Packages/目录
* 4. 重启Sublime Text。

安装成功，此时就可以在Preferences菜单下看到Package Settings和Package Control两个菜单了。

###四、安装SublimeLinter
这个插件帮你找到代码中的错误。它支持很多语言：PHP, Python, Java, CoffeScript, CSS, HTML, JavaScript, Perl, C/C++, Ruby, XML等。
#####（一）安装SublimeLinter包
快捷键 Ctrl+Shift+P（菜单 – Tools – Command Paletter），打开命令面板。输入 install 选中Install Package并回车。    
[[downloads/packagecontrol.png]]    
输入或选择你需要的插件回车就安装了，这里我们输入“SublimeLinter”。    
[[downloads/installplugin.png]]    
 <font color="red">注意左下角的小文字变化，正在安装插件！</font>      
[[downloads/installpackage.png]]  
 <font color="red">注意左下角的小文字变化，插件安装成功！</font> 
[[downloads/successfullyinstalled.png]]   
[[downloads/sublimelinter.png]]  
此时就可以看到Preferences – Package Settings – SublimeLinter菜单，或者右键也可以看到SublimeLinter菜单了，这样SublimeLinter包就已经安装完成。  
#####（二）参数配置
打开 SublimeLinter 的配置文件，Preferences – Package Settings – SublimeLinter – Settings - User，或者右键 – SublimeLinter – Open User Settings进行如下配置：    
(1)运行模式   
"lint-mode":SublimeLinter 的运行模式，总共有四种，含义分别如下：
* 1. "background" - 在用户输入时在后台进行即时校验；
* 2. "load-save" - 当文件加载和保存的时候进行校验；
* 3. "save-only" - 当文件被保存的时候进行校验；  
* 4. "manual" - 只有在你手动执行测试程序的时候进行校验；
  
推荐设置为 “save-only”，这样只在编写完代码，保存的时候才校验，Sublime Text 运行会更加流畅。  
(2)展示错误    
"show_errors_on_save":保存时是否显示错误：  
* 1. "true" - 在界面正上方以对话框形式显示错误信息；  
* 2. "false" - 不以对话框形式显示错误信息；  
  
推荐设置为 “true”，这样可以在保存的时候方便知道代码错误原因。

###五、安装SublimeLinter-cppcheck 
参考：https://github.com/SublimeLinter/SublimeLinter-cppcheck   
这个插件为sublimelinter提供了一个对应cppcheck的接口，用来检查被sublime text 3打开的工程文件的C++句法。
使用该插件前，你必须确认sublimeLinter 3已经安装，如果还没有安装，请参考sublimelinter plugin的手册部分
安装。   
另外你还要确认你的系统里已经安装了cppcheck，如果没有，请按照下述命令安装：  
```bash
$ sudo apt-get install cppcheck    
```
使用Package Control包安装插件的方法安装cppcheck插件。（方法同安装sublimelinter）   
参数配置   
SublimeLinter 的配置文件中关于cppcheck的配置如下：   
```xml
"linters": {
            "cppcheck": {
                "@disable": false,
                "args": [],
                "enable": "style",
                "excludes": [],
                "std": []
            },
            ...
           }
```   
* 1. "@disable": 是否关闭cppcheck检查功能，false：不关闭，true：关闭。
* 2. "enable":一个逗号分隔的列表关于启用的检查项。默认为"style"。   
* 3. "std":设置使用的程序语言标准，如：["c89", "c99"]

如下图，在我们修改完自己的代码，最后要保存的时候，sublimelinter提示了源文件中的错误。<font color="red">（红色箭头所指） </font>   
[[downloads/cppcheck.png]]

###六、安装cpplint (不建议使用)
参考：https://github.com/SublimeLinter/SublimeLinter-cpplint  
1.安装python工具 setuptools 
```bash
$ sudo apt-get install python-setuptools
``` 
2.安装cpplint(iauto改进版)  
（1）下载cpplint iauto改进版安装压缩包 下载链接：[[cpplint_iauto-0.0.3.zip|downloads/cpplint_iauto-0.0.3.zip]]   
（2）解压压缩包  
```bash
$ unzip iauto_cpplint-0.1.0.zip
```
（3）在iauto_cpplint-0.1.0目录下运行如下安装命令安装cpplint  
```bash
$ sudo python setup.py build
$ sudo python setup.py install
``` 
3.使用Package Control包安装插件的方法安装cpplint插件。（方法同安装sublimelinter）  
 SublimeLinter 的配置文件中关于cpplint的配置如下：   
```xml
"linters": {
            "cpplint": {
                "@disable": false,
                "args": [],
                "excludes": [],
                "filter": ""
            },
```
4.使用默认配置即可，打开一个c++文件，保存；即会提示cpplint错误如下图：  
[[downloads/cpplint_sublime_text.png]]

###七、安装Cscope
参考：https://github.com/ameyp/CscopeSublime   
Cscope能够完成的功能，简单的列举几条：
* 1. 在函数调用点快速跳转到函数定义处，反之亦然。如果有多个调用点，会以列表形式给出。
* 2. 在函数声明处快速跳转到函数定义处，反之亦然。
* 3. 快速查找全工程里出现光标所在处的单词的地方。
* 4. 查找本函数调用的函数。
* 5. 查找本函数被调用的地方。   
 
首先使用apt-get命令安装cscope
```bash
$ sudo apt-get install cscope
```
到你的源代码所在的目录,运行如下命令，就会生成cscope.out文件。
```bash
$ cscope -Rbq
```
打开命令面板，输入cscope，我们可以看到有好几个功能：  
[[downloads/cscope_cscopefile.png]]
我们以look up symbol为列查询函数callfunction
[[downloads/cscope_find_object.png]]  
界面显示了symbol：callfunction在目录中所处的位置。
[[downloads/cscope_locate_object.png]]  
###八、安装sublimerge  
参考：https://github.com/borysf/Sublimerge  
sublimerge插件提供了如下功能：  
（1）.同步比较行代码，sublimerge会展示两个窗口显示你所比较的两个文件每一行的不同。  
（2）.比较和合并两个文件的代码。  
（3）.比较和合并两个目录的文件。  
（4）.自带git，svn等版本控制的命令。  
（5）.比较键盘输入的内容。  
（6）.创建，管理和比较代码快照。  
（7）.比较两个文件被选中部分的不同。  

[[downloads/sublmerge_operation.png]]
如上图在视图框中右键选择sublimerge可以看到如下选项：  
* 1.Go to previous change：光标移动到前一个不同的地方。   
* 2.Go to next change：光标移动到下一个不同的地方。  
* 3.Merge Right to Left：把右边视图的内容合并到左边。  
* 4.Merge Left to Right：把左边视图的内容合并到右边。  
* 5.Merge All:Right to Left：把所有右边视图的内容合并到左边。  
* 6.Merge All:Left to Right：把所有左边视图的内容合并到右边。  
* 7.Enter Edit Mode：进入编辑模式，可以对比较的文件进行编辑。  
* 8.ignore CR/LF：忽视换行符的不同。   
* 9.ignore whitespace：忽视空格符的不同。  
* 10.ignore case：忽视大小写的不同。  
* 11.separate Missing Blocks
* 12.Intraline Analysis
* 13.Swap view：左右交换视图。 

###九、安装all autocomplete
参考：https://github.com/alienhard/SublimeAllAutocomplete  
AutoComplete控件就是指用户在文本框输入前几个字母或是汉字的时候，该控件就能从存放数据的文本或是数据库里将所有以这些字母开头的数据提示给用户，供用户选择，提供方便。
###十、安装git
参考：https://github.com/kemayo/sublime-text-git  
Git版本控制系统，如果你每天要使用Git，那这个插件对你来说必不可少了。
使用Package Control下载后，你只需要调出命令面板(Shift+Ctrl+P 或者Tools->Command palette)，输入Git，便能找到所有常用的功能。  
[[downloads/plugin_git.png]] 
###十一、安装ctag  
首先使用apt-get命令安装ctags：
```bash
$ sudo apt-get install ctags
```
到源代码所在目录下运行如下命令：  
```bash
$ ctags –R *  
```  
“-R”表示递归创建，也就包括源代码根目录（当前目录）下的所有子目录。   
“*”表示所有文件。这条命令会在当前目录下产生一个“tags”文件，当用户在当前目录中运行vi时，会自动载入此tags文件。  
Tags文件中包括这些对象的列表：    
* 1.用#define定义的宏
* 2.枚举型变量的值
* 3.函数的定义、原型和声明
* 4.名字空间（namespace）
* 5.类型定义（typedefs）
* 6.变量（包括定义和声明）
* 7.类（class）、结构（struct）、枚举类型（enum）和联合（union）类、结构和联合中成员变量或函数    
vim可以用这个“tags”文件来定位上面这些做了标记的对象。
定位这些对象：在包含有tags文件的目录下运行如下命令：
```bash
$ vim –t tag
```
“tag”即是你所要定位的对象名，如函数名：callfunction，变量名：value，等等，vim就会自动打开该对象所在的源文件，并将光标定位到那一行。

sublime text 3中如何使用ctags功能：
用sublime text 3打开工作目录，我们以一个简单的test目录为例说明ctags插件的使用。
打开命令面板，输入“ctags：rebuild tags”，回车。
[[downloads/ctags_rebuildctags.png]]
可以看到ctags插件创建了两个.tags文件，其中。.tags_sorted_by_file是对标记对象按照文件排序过的。
[[downloads/ctags_choosedir.png]]
然后，我们可以定位目录中的对象，打开命令控制台，输入“ctags：show Symbols(all)”，回车。
[[downloads/ctags_ctagsfile.png]]
在如下图的对话框中输入你想定位的对象标签名，如：callfunction（）。sublime text 3就会打开该函数定义所在的源文件。
[[downloads/ctags_locateobject.png]]

