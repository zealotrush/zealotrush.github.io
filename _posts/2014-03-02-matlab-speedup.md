---
layout: post
title: "MATLAB 启动加速"
date: 2014-03-02 12:01:24
---

我真傻！真的！我一直以为 MATLAB 本就应该这么慢的……当然不是！如果你也像我一样，饱受 MATLAB 启动速度的煎熬，那么这篇博客就是专门为你而写。Here we go!

声明
----

本文只适用于 Windows 7。对于 Windows XP 用户，我只能说声抱歉——连亲爹微软都撒手不管了，我也爱莫能助。对于 Linux/Mac 用户，这问题可能压根就不存在——至少在我这边不存在。

诊断
----

如果你想知道 MATLAB 究竟有多慢，可以使用 `-timing` flag。请运行如下命令

    matlab -timing

并等待 MATLAB 完全启动。你会在 MATLAB 命令行中得到其启动耗时的详细报告。

原因
----

我尝试搜索了一整个上午，调查 MATLAB 启动太慢的原因。结果众说纷纭，连 MathWorks 官方都没有个统一的说法。曾见到过的说法有：

- 工具包缓存需要更新
- 启动路径不能包含太多文件
- License 问题
- MATLAB path 中包含慢速网络连接

等等等等，可惜无一奏效。直到在 MathWorks 论坛中找到[这篇帖子][post]，有人提到「断网」这个方案，问题才算有了眉目。经测，断网后 MATLAB 启动的确飞快！

所以，问题解决？不行！断网太麻烦了！

尝试
----

用防火墙将 MATLAB 屏蔽，让它无法联网就行了。

Windows 7 有个不错的防火墙。我尝试将 `matlab.exe` 加入了 Inbound 和 Outbound 的阻止名单，但没有效果。想到之前有人提到 License 问题，我又把 MATLAB 的 License 管理工具 `lmtools.exe` 也加入阻止名单，依旧无果。MATLAB 安装目录下共有156个可执行文件，而 Windows 7 的防火墙没有提供批量添加规则的功能，总不能一个一个手动添加吧。

解决
----

批处理！

没错，用批处理文件可以一次添加多个规则。不需要自己动手，一位叫 [Charles de Havilland][charles] 的英国人，已经在他的 [Google Site][googlesite] 上提供了我所需要的批处理文件。不过该页面已被墙，我将其保存在自己地盘上，方便大家下载。

以下是具体的步骤：

- 下载文件 [addfwrs.bat.txt][bat]
- 把该文件重命名为 addfwrs.bat
- 把该文件移动至 MATLAB 安装路径下，例如：`C:\Program Files\MATLAB\R2012a`
- 用 Administrator 权限打开命令行
  - 点击「开始」，键入 `cmd`，在 `cmd.exe` 上右键，选择 Run as administrator
- cd 至 MATLAB 安装路径
- 执行 `addfwrs block_matlab_all`

其中，block\_matlab\_all 是规则名称的前缀，可以任意修改，目的是为了方便以后在防火墙规则中查找。

等批处理运行完毕，再去试着启动 MATLAB 吧！生活，原来可以更美的！

参考
----

- [Why is R2012a Matlab so very, very slow at starting up? - MATLAB Answers - MATLAB Central][post]
- [Charles de Havilland | LinkedIn][charles]
- [Allow/Block Multiple Programs Through Windows 7 Firewall - Stuff >][googlesite]

[post]: http://www.mathworks.com/matlabcentral/answers/50660-why-is-r2012a-matlab-so-very-very-slow-at-starting-up "Why is R2012a Matlab so very, very slow at starting up? - MATLAB Answers - MATLAB Central"
[charles]: http://www.linkedin.com/in/charlesdehavilland "Charles de Havilland | LinkedIn"
[googlesite]: https://sites.google.com/site/mytools4000/home/allow-block-multiple-programs-through-windows-7-firewall "Allow/Block Multiple Programs Through Windows 7 Firewall - Stuff >"
[bat]: /assets/files/addfwrs.bat.txt
