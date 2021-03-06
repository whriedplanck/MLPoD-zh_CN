## Linux 在桌面领域的主要问题（2020）

**目录表**

  * [前言](https://github.com/whriedplanck/major-linux-problems-zh-cn/blob/master/translations-full.md#前言)
  * Desktop Linux Problems and Major Shortcomings
  * **[摘要](https://github.com/whriedplanck/major-linux-problems-zh-cn/blob/master/translations-full.md#摘要)**（太长不看版）
  * [“Linux Works for Me™，这篇文章是在胡扯！“ 云云](https://github.com/whriedplanck/major-linux-problems-zh-cn/blob/master/translations-full.md#这篇文章是胡扯-linux-能给我我的祖父姨妈等等人用-云云)
  * Commentary from the Author
  * Windows 10 vs. Linux
  * Solving Linux
  * Comments

### 前言

在这篇定期却鲜少更新的文章里，无疑有着整个互联网上有关 _Linux 发行版的难题_ 最全的列表，我们仅讨论这些发行版的主要难题和缺点（这些问题和缺点或许是一些人说 Linux 发行版还没在桌面领域准备好的原因）。而大家也应该要记得，Linux 在一些方面要比其他操作系统优秀：一个发行版中有出色的软件包管理，开箱即有的多平台和多架构支持，而且_通常_具有出色的稳定性，没有广泛传播的病毒或者恶意软件，几乎从不需要重装完整系统。此外，Linux 的可定制性也相当高，容易脚本化，而且它是自由的，就像啤酒一样。

笔者再重申一下, 本文主要关于的是 _Linux 发行版_ ，但是，下文列出的 _许多问题_ 同样会影响 Linux 内核（即各种 Linux 发行版和 Android 的核心）。

这篇文章 _不是_ 特意要拿 Windows 和 Linux 做比较，但是读者还是会发现文中拿了 Windows 或者 macOS 进行比较以作为参考（毕竟，这两者的市场占有率要比 Linux 高一个数量级）。下文列出的大多数问题本质上是技术性的，但是也有些是“政治性”的（这不是笔者的观点 —— 是别人这么说的）—— 例如，当商业公司拒绝公布或者只公布部分的硬件数据表时，Linux 用户会因此无法发挥电脑的全部功能、或者个别驱动程序存在问题，而这在 Linux 社区中几乎没人可以解决。

笔者还想要说清楚一件事情 —— [Windows](https://itvision.altervista.org/why-windows-10-sucks.html)，在某些方面，甚至比 Linux 更糟，它 _自己也有一些严重问题_ 。笔者想说的是 Windows 以下几个极具破坏性的问题：
   * Windows rot（新软件安装和磁盘碎片会显著降低系统响应速度，即“越用越慢”）
   * 没有强制的文件系统和注册表层次结构（笔者还没有找到一个可以严格完全干净地卸载的应用程序）
   * 没有真正的安全模式，用户就是系统管理员（因此病毒/恶意软件肆虐 —— 大多数用户 _不了解也不会去_ 了解 UAC 警告）
   * 没有良好的软件打包机制（MSI 脆弱且令人憎恶）
   * 没有系统范围的更新机制（包括第三方软件）
   * Windows 调试难度极其高
   * Windows 的引导问题往往是致命而无法解决的，除非全新重装系统
   * Windows 很依赖硬件（尤其是从 UEFI 运行时）
   * SSD 磁盘上的文件系统碎片过多
   * Windows 更新很不可靠，也很浪费磁盘空间，等等



可能你已经很多次听过这样的说法：Linux 已经通过 Android 征服了整个世界，因为后者运行在大多数智能手机上（确实有少数专用计算机安装着 Android，但它们不是所谓[台式机](http://mobile.slashdot.org/comments.pl?sid=2772729&cid=39611863)）。然而请记住两个重点 - 首先，Android [不](https://itvision.altervista.org/files/android_is_not_linux.png)[是](http://arstechnica.com/gadgets/2009/02/an-introduction-to-google-android-for-developers/) [Linux](http://www.gnu.org/gnu/gnu-linux-faq.html#linuxsyswithoutgnu)（此外，有谁见过有人在自己的台式机或笔记本上运行 Android 的吗？）。Android 包含的 Linux 的组件仅仅是其内核罢了（再补充一点，还是完全由谷歌维护和提供支持的几个固定的旧版本（截至 2016 年有 3.0.x、3.4.x 或 3.10.x））。其次， Android 并不是桌面级操作系统，而是用于手机、平板电脑和其他触屏设备的操作系统。所以，这篇文章和 Android **没有关系**，它和[成群的](http://distrowatch.com/) _Linux 发行版_ （以下简称“发行版”）和其中包含的开源软件有关。

随时在评论部分表达您的不满。

**注意事项:**

列表上标为绿色的条目（译者注：由于 GitHub 不支持彩色 Markdown 格式，这部分内容会以文字方式指出）表示已解决了一部分，或者不是很关键、很有问题，或者是有解决方案。

这份列表迫切需要重新组织内容，因为里面有些问题是至关重要的，有些则不是。作为一名（Linux）用户，你可能_很幸运地_不会遇到任何一个这些问题（如果你有 _对口_ 的硬件，永远不会折腾坏自己的系统，并且 _仅仅_ 使用发行版包含的 _数量相当有限_ 的软件）。

在开始阅读前还有几点重要的考虑事项：

  * 如果你相信 Linux 是完美无缺的，请关掉这个网页。
  * 如果你觉得任何对 Linux 的批评都只是毫无根据的谩骂，那请关掉这个网页。
  * 如果你认为这篇文章的目的是要表达“_没有什么在 Linux 中是能正常工作的_”或者 “_Linux 几乎没有可用性_”这样的观点，那就错了，还是请你离开吧。
  * 如果你相信 Linux 和 Linux 用户可以脱离商业软件和游戏的情况下，也能正常工作或生活，请关掉这个网页。
  * 如果你觉得笔者是在这推销 Windows 或者 macOS，请关掉这个网页。
  * 如果你认为笔者我是在这里散播有关 Linux 的谣言（甚至觉得是在贩卖恐慌，挑拨观点）的话，恕我丑话，请你 _马上滚蛋不要再来_！吃饱了没事干的话，请把气焰烧在战争和中伤别人上吧。

请谨记，这份列表的目的，是为了说明白 Linux 需要修复的问题，而不是挑刺。


### 桌面级 Linux 的问题和主要缺点

（照顾讨厌阅读长文的读者，下面有一篇“[太长不看版](https://github.com/whriedplanck/major-linux-problems-zh-cn/blob/master/translations-full.md#摘要)”）。所以 Linux 差劲的原因是 ...

  * **硬件支持**：
    
    1. 视频加速（另请参见 X 系统部分）。
      * ! 大多数笔记本计算机所使用的 NVIDIA Optimus 技术在 Linux 中的工作状态常常不太好。人们应付着画面撕裂、新内核更新（带来的驱动）等问题。
      * ! 开源驱动有某些有时非常严重的问题（[Intel](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel)-[!](https://bugs.freedesktop.org/show_bug.cgi?id=30364 "poor 3d performance in deep c-states: CLOSED WONT FIX - WAIT WHAT?!!!") 和 [AMD](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati) 都有）：
        * ! 因为不完善的电源管理，开源的 NVIDIA 驱动比其专有驱动慢得多（最高可达二十倍，这都是 NVIDIA 的错，它不给 Nouveau 项目提供需要的固件） 。
        * ! 开源 NVIDIA 驱动 Nouveau 不能正确、完全地支持电源管理功能和风扇速度管理（这也主要是 NVIDIA 的锅）。
        * ! 专有 NVIDIA 驱动有保持 GPU （长期）在高性能水平而使电量消耗显著升高的[讨厌习惯](https://devtalk.nvidia.com/default/topic/1002912/linux/very-slow-ramp-down-from-high-to-low-clock-speeds-leading-to-a-significantly-increased-power-consumption/)，并且特别是对移动用户，这大大降低电池的寿命。NVIDIA 在 2017 年 7 月收到 Bug 报告，虽然他们在 2019 年才做出改进，但这个问题依旧存在。
        * !! 据一位不愿透露姓名的 NVIDIA 工程师所述，“According to an anonymous NVIDIA engineer, "Nearly Every Game Ships Broken ... In some cases, we're talking about blatant violations of API rules ... There are lots of optional patches already in the driver that are simply toggled on or off as per-game settings, and then hacks that are more specific to games ... Ever wondered why nearly every major game release is accompanied by a matching driver release from AMD and/or NVIDIA?". The open source community simply doesn't have the resources to implement similar hacks to fix broken games, which means that at least for complex AAA games, proprietary drivers will remain the only option.
      * ! 在非标准显示分辨率、超高显示分辨率（也叫 HiDPI）和自定义刷新率方面，Linux 版本的驱动通常比 Windows/Mac OS（macOS）版本的更糟（需要大量的微调，即手动配置）
      * ! Under Linux, setting multi-monitor configurations especially using multiple GPUs running binary NVIDIA drivers can be a major PITA.
      * （对于大多数用户不是问题但依旧要说）NVIDIA 的 GPU 很可能不会支持 GPU 电压调节了，意味着没有合适的超频方法，也没有降频方法来节约电量
      * !! Extremely poor state and usability of the tools for monitoring and controlling GPU parameters like frequency, voltage and fan curves (akin to MSI Afterburner or GPU-Z in Windows), performance overlay (Fraps, RivaTuner Statistics Server), recording game sessions and streaming.
    2. 音频子系统：
      * PulseAudio 不适宜[多用户情景模式](http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/SystemWide/)  —— 没错，很多人会共享他们的电脑（[这里](https://rudd-o.com/linux-and-free-software/how-to-make-pulseaudio-run-once-at-boot-for-all-your-users)有一个未经测试的解决方案）。
      * ! 没有可靠的[回声](https://bbs.archlinux.org/viewtopic.php?id=183166 "pulseaudio + skype = echo")[抑制机制](http://blogs.gnome.org/uraeus/2010/10/07/echo-cancellation-on-linux/)（如果使用普通的麦克风和扬声器，很多情况下将无法正常使用 Skype 和其他 VoIP 服务）。Windows、Android 和 MacOS（macOS）则有系统层级的实现方式。有一个适用于 PulseAudio 的[解决方法](https://thenerdshow.com/audio.html) —— 希望以后能被默认启用或者/并且有更容易使用的方式。
      * 不用[控制台（终端）](https://medium.com/@gamunu/enable-high-quality-audio-on-linux-6f16f3fe7e1f)通常无法配置高解析音频支持（>= 96KHz, >= 24bit），这也是让很多音频专业用户望而却步的因素。
      * 多数发行版默认不包含/不启用各种[音效](https://github.com/swh/ladspa)（比如音量规格化）。
    3. 打印机、扫描仪等这样那样的周边设备：
      *  Linux 还有很多打印机仍然完全不支持或者只有少量支持 —— 有些人反驳说用户应该在购买硬件前弄清其 Linux 兼容性。但是如果用户是已经有了硬件并从 Windows 转入 Linux 的呢？人们在买下 Windows 电脑时会弄清所有东西吗？不会，他们会一开始就想当然地认为所有东西都可开箱即用。
      * 不少打印机的功能只有在 Windows 驱动中才能实现。
      * Some models of scanners and (web-)cameras are still inadequately supported (again many features from Windows drivers are missing) or not supported at all.
      * Incomplete or unstable drivers for some hardware. Problems setting up some hardware (like touchpads in newest laptops, web cameras or Wi-Fi cards, for instance, 802.11ac and USB Wi-Fi adapters are barely supported under Linux and in many cases they are just unusable). Broadcom network adapters are often usable out of the box for a lot of Linux distors (to be honest the company seemingly hates Open Source).
    4. Laptops, tablets, 2 in 1 devices, etc.: 
      * Incomplete or missing support for certain power-saving features modern laptops employ (like e.g. PCIe ASPM, proper video decoding acceleration, deep power-saving states, etc.) thus under Linux you won't get the same battery life as under Windows or MacOS and your laptop will run a lot hotter. ~~[Jupiter](http://jupiter.sourceforge.net/ "Jupiter is a light weight power and hardware control applet for Linux.  It is designed to improve battery life of a portable Linux computer by integrating with the operating system and changing parameters of the computer based on battery or powered connection.")~~ (discontinued unfortunately), see [Advanced Power Management for Linux](https://github.com/linrunner/TLP "TLP brings you the benefits of advanced power management for Linux without the need to understand every technical detail. TLP comes with a default configuration already optimized for battery life, so you may just install and forget it. Nevertheless TLP is highly customizable to fulfil your specific requirements."). Edit July 19, 2018: If you're running supported hardware with Fedora 28 and Linux 4.17 and later, power management must be excellent under Linux aside from watching videos (both online and offline: video decoding acceleration in Linux is still a very sad story).
      * !! Oftentimes you just cannot use new portable devices in Linux because proper support for certain features gets impletemented too late and distros pick up this support even later.
      * Laptops/notebooks often have special buttons and features that don't work (e.g. Fn + F1-F12 combination or special power-saving modes).
    5. ! Resume after suspend in Linux is [unstable](http://news.softpedia.com/news/valve-drops-suspend-function-for-steamos-due-to-poor-support-in-linux-graphics-stack-489396.shtml) and oftentimes doesn't work.
6. ! Often [regressions](http://www.datamation.com/open-source/linux-kernel-developers-detail-top-gripes.html) are introduced in the Linux kernel, when some hardware stops working inexplicably in new kernel versions. I have personally reported two serious audio playback regressions, which have been consequently resolved, however _most users don't know how to file bugs, how to bisect regressions, how to identify faulty components._
   
  * **Software support** : 
    1. X system (current primary video output server in Linux): 
      * X.org is [largely](http://linux.slashdot.org/comments.pl?sid=2969319&cid=40603337) [outdated](http://tech.slashdot.org/story/12/04/06/0538250/update-on-wayland-and-x11-support), [unsuitable](http://lanyrd.com/2013/linuxconfau/scctrd/ "The real story behind Wayland and X") [and](https://www.phoronix.com/scan.php?page=article&item=x_wayland_situation&num=1 "The Wayland Situation: Facts About X vs. Wayland") [even](http://www.x.org/wiki/Development/X12#Errors.2C_Oversights_and_Omissions) [very](http://blog.martin-graesslin.com/blog/2015/01/why-screen-lockers-on-x11-cannot-be-secure/) [much](http://lists.x.org/archives/xorg-announce/2014-December/002500.html) [insecure](http://www.jwz.org/xscreensaver/faq.html#no-ctl-alt-bs) for [modern](http://linux.slashdot.org/comments.pl?sid=3041123&cid=40955973) PCs and applications.
      * No high level, _stable, sane (truly forward and backward compatible) and standardized_ API for developing GUI applications (like core Win32 API - most Windows 95 applications still run fine in Windows 10 - that's **24 years of binary compatibility** ). Both GTK and Qt (incompatible GTK versions 1, 2, [3](http://igurublog.wordpress.com/2012/11/05/gnome-et-al-rotting-in-threes/ "GNOME \(et al\): Rotting In Threes"), [4](https://blogs.gnome.org/desrt/2016/06/13/gtk-4-0-is-not-gtk-4/) and incompatible Qt versions 4, 5, 6 just for the last decade) don't strive to be backwards compatible. The Qt company also changed the licensing model for their toolkit which makes using the library under Linux [problematic](https://www.qt.io/blog/qt-offering-changes-2020) to say the least.
      * ! Keyboard shortcut handling for people using local keyboard layouts is [broken](https://bugs.freedesktop.org/show_bug.cgi?id=865) (this bug is now **15 years old** ).
      * ! X.org [doesn't automatically switch](https://bugs.freedesktop.org/show_bug.cgi?id=14255) between desktop resolutions if you have a full screen application with a custom resolution running - strangely some Linux developers [oppose](https://mail.gnome.org/archives/wm-spec-list/2012-October/msg00003.html "Martin Gräßlin: Re: Proposing _NET_WM_STATE_FULLSCREEN_EXCLUSIVE") to the whole idea of games on Linux. ~~But since Linux is not a gaming platform and no one is interested in Linux as a gaming platform this problem's importance is debatable~~. Valve has released Steam for Linux and they are now porting their games for Linux - but that's a drop in the bucket.
      * ! X.org doesn't restore gamma (which can be perceived as increased brightness) settings on application exit. If you play Valve/Wine games and experience this problem run `xgamma -1` in a terminal. You can thank me by clicking the ad at the top of the page ;-)
      * ! Scrolling in various applications causes [artifacts](https://bugs.freedesktop.org/show_bug.cgi?id=25497).
      * ! X.org allows applications to [exclusively grab](https://bugs.freedesktop.org/show_bug.cgi?id=21141) keyboard and mouse input. If such applications misbehave you are left with a system you cannot manage, you cannot even switch to text terminals.
      * ! Keyboard handling in X.org is broken by design - when you have a pop up or an open menu, global keyboard shortcuts/​keybindings [don't](https://bugzilla.gnome.org/show_bug.cgi?id=344059 "Ways to make global keybindings work during grabs") (GTK) [work](https://bugs.kde.org/show_bug.cgi?id=70063 "global shortcuts don't work when any popup is active") (QT).
      * ! For VM applications keyboard handling is [incomplete](http://askubuntu.com/questions/54814/how-can-i-ctrl-alt-f-to-get-to-a-tty-in-a-qemu-session) and passing keypresses to guest OS'es is outright [broken](https://www.berrange.com/posts/2010/07/04/more-than-you-or-i-ever-wanted-to-know-about-virtual-keyboard-handling/).
      * ! X.org architecture is inherently insecure - even if you run a desktop GUI application under a different user in your desktop session, e.g. using sudo and xhost, then that "foreign" application can grab any input events and also make screenshots of the entire screen.
      * ! X.org server currently has no means of permanently storing and restoring settings changed by the user (xrender settings, Xv settings, etc.). NVIDIA and ATI proprietary drivers both employ custom utilities for this purpose.
      * !! X.org has no means of providing a tear-free experience, it's only available if you're running a compositing window manager in the OpenGL mode with vsync-to-blank enabled.
      * !! X.org is not [multithreaded](https://www.youtube.com/watch?v=RIctzAQOe44&t=1390). Certain applications running intensive graphical operations can easily freeze your desktop (a simple easily reproducible example: run Adobe Photoshop 7.0 under Wine, open a big enough image and apply a sophisticated filter - see your graphical session die completely until Photoshop finishes its operation).
      * ! There's currently no way to [configure](https://bugs.launchpad.net/gtk/+bug/124440) [mouse scroll](http://lists.x.org/archives/xorg-devel/2010-September/012517.html) speed/acceleration under X.org. Some mice models scroll [erratically](https://bugs.launchpad.net/ubuntu/+bug/971321) under X.org.
      * There's no way to replace/​upgrade/​downgrade X.org graphics drivers on the fly (simply put - to restart X server while retaining a user session and running applications).
      * No true [safe mode](http://libv.livejournal.com/22968.html) for the X.org server (likewise for KMS - read below). Misconfiguration and broken drivers can leave you with a non-functional system, where sometimes you cannot access text virtual consoles to rectify the situation (in 2013 it became almost a non-issue since quite often nowadays X.org no longer drives your GPU - the kernel does that via KMS).
      * Adding custom monitor modelines in Linux is a major PITA.
      * X.org does not support different scaling modes for different monitors.
      * X.org [totally sucks](http://lists.x.org/archives/xorg-devel/2014-January/040139.html "How do we want to deal with 4k tiled displays?") (IOW doesn't work at all in regard to old applications) when it comes to supporting tiled displays, for instance 4K displays (Dell UP3214Q, Dell UP2414Q, ASUS PQ321QE, Seiko TVs and others). This is yet another architectural limitation.
      * HiDPI support is often a huge issue (many older applications don't scale at all).
      * ! Fast user-switching (and also concurrent users' sessions) under X.org works very badly and is implemented as a dirty hack: for every user a new X.org server is started. It's possible to login twice under the same account while not being able to run many applications due to errors caused by concurrent access to the same files. Fast user switching is best implemented in KDE followed by Gnome. 

Related problems:  
1) Concurrently logged in users cannot access the same USB flash drive(s).  
2) There are reports that problems exists with configuring audio mixer volume
levels.

```markdown
2. Wayland: 
  * !! Applications (or GUI toolkits) must implement their own font antialiasing - there's no API for setting system-wide font rendering. Most sane and advanced windowing systems work exactly this way - Windows, Android, Mac OS X. In Wayland all clients (read applications) are totally independent.
  * !! Applications (or GUI toolkits) must implement their own DPI scaling.
  * The above issues are actually the result of not having one unified graphical toolkit/API (and Wayland developers [will not implement](https://bugs.freedesktop.org/show_bug.cgi?id=93794) it). Alas, no one is currently working towards making existing toolkits share one common configuration for setting font antialiasing, DPI scaling and windows shadowing. At least in theory these issues can be easily solved, in practice we already have three independent toolkits for Wayland (GTK3/Qt5/Enlightenment).
  * !! Wayland works through rasterization of pixels which brings about two very bad critical problems which will never be solved: 
```

Firstly, forget about performance/bandwidth efficient RDP protocol (it's already implemented but it works by sending the updates of large chunks of the screen, i.e. a lot like old highly inefficient VNC), forget about OpenGL pass-through, forget about raw compressed video pass-through. In case you're
interested all these features work in [Microsoft's RDP](https://en.wikipedia.org/wiki/Remote_Desktop_Protocol#Features).

Secondly, forget about proper output[rotation/scaling/ratio](https://www.reddit.com/r/oculus/comments/1zt497/i_am_concerned_about_waylands_premature/ "Reddit: I am concerned about Wayland's premature rasterization because of the Rift") change.

```markdown
  * !! Wayland doesn't allow XWayland applications to change display resolution which could make running games slower as the compositor needs to upscale each game frame. Also software upscaling might not be the best option.
  * !! Screensharing doesn't yet work out of the box (likely to be fixed in 2020).
  * !! Wayland lacks APIs for global keyboard shortcuts.
  * !! Wayland doesn't allow applications to [exclusively grab](https://wiki.archlinux.org/index.php/Wayland#Input_grabbing_in_games,_remote_desktop_and_VM_windows) mouse/keyboard which is required for games and applications like VMs.
  * !! Wayland lacks APIs for sending remote input which makes Wayland unsuitable for remote desktoping.
  * !! Applies to the X server/protocol as well: neither X.org, nor Wayland offer a way to extend/modify window's title bars and File Open/Save dialogs. This is a very powerful feature which can be very useful in many situations. Again it's a result of the fact that there's no unified toolkit and no unified window manager (or protocol).
  * !! Wayland compositors don't have a universal method of storing and configuring screen/session/keyboard/mouse settings.
  * Currently there's no standard way to remap keys under Wayland.
  * XWayland refresh rate is [locked to 60Hz](https://bugs.freedesktop.org/show_bug.cgi?id=103282) \- that's actually a serious problem since most games for Linux use the X11 protocol.
  * Wayland applications cannot run without a Wayland compositor and in case it crashes, all the running apps die. Under X.org/Microsoft Windows there's no such issue.
  * An assortment of various other [general](https://hansdegoede.livejournal.com/21944.html) and [KDE specific](https://community.kde.org/Plasma/Wayland_Showstoppers) issues.
3. Font rendering (which is implemented via high level GUI libraries) issues: 
  * ! ClearType fonts are not properly supported out of the box. Even though the ClearType font rendering technology is now supported, you have no means of properly tuning it thus ClearType fonts from Windows look ugly.
  * Quite often default fonts look [ugly](http://news.slashdot.org/comments.pl?sid=3253653&cid=41995395), due to missing good (catered to the LCD screen - subpixel RGB full hinting) default fontconfig settings.
  * Font antialiasing settings cannot be applied on-the-fly under many DEs. This issue is impossible to solve unless we have a high level GUI library which is shared between all tooklits and desktop environments.
4. The Linux kernel: 
  * ! The kernel cannot recover from [video](http://tech.slashdot.org/comments.pl?sid=3002453&cid=40762441), sound and network drivers' crashes (I'm very sorry for drawing a comparison with Windows Vista/7/8/10 where this feature has been implemented for ages and works beautifully in a lot of cases).
  * [KMS](https://wiki.archlinux.org/index.php/Kernel_Mode_Setting) exclusively grabs video output and [disallows](https://bugs.freedesktop.org/show_bug.cgi?id=26878) VESA graphics modes (thus it's impossible to switch different versions of graphics drivers on the fly).
  * KMS video drivers cannot be unloaded or reloaded.
  * !! KMS has **no safe mode** : sometimes KMS cannot properly [initialize](https://www.google.com/search?q=kms+black+screen&hl=en) your display and you have a dead system you cannot access at all (a kernel option "nomodeset" can save you, but it prevents KMS drivers from working at all - so either you have 80x25 text console or you have a perfectly dead display).
  * Traditional Linux/Unix (ext4/​reiser/​xfs/​jfs/​btrfs/etc.) filesystems can be [problematic](https://bugzilla.kernel.org/show_bug.cgi?id=15875) when being used on mass media storage.
  * File descriptors and network sockets [cannot](https://bugzilla.kernel.org/show_bug.cgi?id=14505) be forcibly [close](https://github.com/blackhole89/force-unmount "A crazy hack/workaround which unfortunately won't work if a mount point contains e.g. an ISO image also mounted somewhere")d \- it's indeed unsafe to remove USB sticks without unmounting them first as it leads to stale mount points, and in certain cases to oopses and crashes. For the same reason you cannot modify your partitions table and resize/move the root partition on the fly.
  * In most cases kernel crashes (= panics) are invisible if you are running an X session. Moreover KMS prevents the kernel from switching to plain 640x480 or 80x25 (text) VGA modes to print error messages. As of 2020 there's work underway to implement kernel error logging under KMS.
  * !! Very incomplete hardware sensors support, for instance, HWiNFO64 detects and shows ten hardware sensor sources on my average desktop PC and over fifty sensors, whilst lm-sensors detect and present just four sources and twenty sensors. This situation is even worse on laptops - sometimes the only readings you get from lm-sensors are cpu cores' temperatures.
  * ! A number (sometimes up to dozens) of regressions in every kernel release due to the inability of kernel developers to test their changes on all possible software and hardware configurations. Even "stable" x.y.Z kernel updates sometimes have serious regressions.
  * ! The Linux kernel is [extremely difficult](https://web.archive.org/web/20150214230010/http://codemonkey.org.uk/2014/11/03/thoughts-crashdumps/ "Dave Jones: Thoughts on crashdumps") and cumbersome to debug even for the people who develop it.
  * Under some circumstances the system or X.org's GUI may become very slow and unresponsive due to various problems with video acceleration or lack of it and also due to notorious bug [12309](https://bugzilla.kernel.org/show_bug.cgi?id=12309) \- it's ostensibly fixed but some people still experience it). This bug can be easily reproduced under Android (which employs the Linux kernel) even in 2020: run any disk intensive application (e.g. under any Android terminal _'cat /dev/zero > /sdcard/testfile'_) and enjoy total UI unresponsiveness.
  * !! Critical bug reports filed against the Linux kernel often get zero attention and may linger for years before being noticed and resolved. Posts to [LKML](https://en.wikipedia.org/wiki/Linux_kernel_mailing_list) oftentimes get lost if the respective developer is not attentive or is busy with his own life.
  * The Linux kernel contains a whole lot of very [low quality code](https://linux.slashdot.org/comments.pl?sid=12556308&threshold=4&commentsort=0&mode=thread&cid=57235812) and when coupled with unstable APIs it makes development for Linux a very difficult error prone process.
  * The Linux kernel forbids to write to [CPU MSRs](https://en.wikipedia.org/wiki/Model-specific_register) in secure UEFI mode which makes it impossible to [fine-tune](https://github.com/georgewhewell/undervolt) your CPU power profile. This is perfectly possible under Windows 10.
  * Memory management under Linux leaves a [lot to be desired](https://www.reddit.com/r/linux/comments/aqd9mh/memory_management_more_effective_on_windows_than/): under low memory conditions your system may become completely unresponsive. This can be alleviated by certain user-space daemons like earlyoom.
5. Problems stemming from the vast number of Linux distributions: 
  * ! No unified configuration system for various system daemons, computer settings and devices. The issue has been more or less solved in regard to network settings (after distors standardized on NetworkManager) and system services (due to systemd which has become a standard).
  * ! No unified installer/package manager/universal packaging format/dependency tracking across all distros (The [GNU Guix](https://savannah.gnu.org/projects/guix/) project, which is meant to solve this problem, is now under development \- but we are yet to see whether it will be incorporated by major distros). Consider RPM (which has several _incompatible_ versions, yeah), deb, portage, tar.gz, sources, etc. It adds to the cost of software development.
  * ! Distros' repositories do not contain all available open source software (libraries' conflicts don't even allow that luxury). The user should never be bothered with using ./configure && make && make install (besides, it's insecure, can break things in a major way, and it sometimes simply doesn't work because the user cannot install/configure dependencies properly). It should be possible to install any software by downloading a package and double clicking it (yes, like in Windows, but probably prompting for a user/administrator password). ![Linux distros. ©2000 Microsoft Germany \[Microsoft_Linux_ad\]](Main%20Linux%20problems%20on%20the%20desktop,%202020%20edition%20or%20why%20Linux%20sucks_files/distros.png)
  * ! Applications development is a major PITA. Different distros can use a) different library versions, b) different compiler flags, c) different compilers. This leads to a number of problems raised to the third power. Packaging all dependent libraries is **not** a solution, because in this case your application may depend on older versions of libraries which contain serious remotely exploitable vulnerabilities.
  * ! Two most popular open source desktops, KDE and Gnome, can configure only a few settings by themselves thus each distro creates its own bicycle (applications/utilities) for configuring a boot loader/​firewall/​users and groups, services, etc.
  * Linux is a hell for ISP/ISV support personnel. Within the organization you can force a single distro on anyone, but it cannot be accomplished when your clients have the freedom to choose.
6. Linux as a gaming platform issues (it's great we now have Proton/Wine/DXVK but): 
  * ! No plug-and-play support for a lot of input devices like joysticks and steering wheels. Many require editing of cryptic configuration files.
  * ! No universal simple to use GUI application which implements an on-screen HUD with CPU, GPU, RAM use, FPS and frame timing. A number of half-solutions exist, including using environment variables but they are not user-friendly. Luckily there's [MangoHud](https://github.com/flightlessmango/MangoHud) which is yet to be included by major Linux distros and which is lacking GUI for configuration. At least it works and exists.
  * ! No universal vendor-neutral alternative to MSI Afterburner - an app for monitoring, overclocking, downclocking/undervolting your GPU.
  * ! Many anti-cheat protections fail to work under Linux. Besides in Linux it's near impossible to guarantee that game assets haven't been tinkered with (think of transparent walls for first-person competitive shooters like Counter Strike Global Offensive, Valorant or Apex Legends).
  * ! No advanced Windows drivers features, like NVIDIA FreeStyle, low-latency input, FPS limiting, half VSync refresh rate and many many others.
  * ! Performance/smoothness/stuttering issues due to the translation overhead between Win32 APIs/Direct3D and Linux APIs/Vulkan.
7. ! It should be possible to configure _pretty much everything_ via GUI (in the end Windows and Mac OS allow this) which is still not a case for some situations and operations.
8. No polish and universally followed conventions. Different applications may have totally different shortcuts for the same actions, UI elements may be placed and look differently.
```

  * **Problems stemming from low Linux popularity and open source nature** : 
    1. ! Few software titles, inability to run familiar Windows software (some applications which don't work in [Wine](http://bugs.winehq.org/describekeywords.cgi "Over 3000 regressions on the 20th of October, 2012") \- look at the lines which contain the word "regression" - have zero Linux equivalents).
    2. ! No equivalent of some hardcore Windows [software](http://linux.slashdot.org/comments.pl?sid=2820335&cid=39846935) like ArchiCAD, 3ds Max, Adobe products like Premier and Photoshop, Corel Draw, Quicken, video authoring applications/etc. Home and enterprise users just won't bother installing Linux until they can get their work done.
    3. ! A [small](http://apple.slashdot.org/story/11/11/11/0233227/whats-keeping-you-on-windows) number of native [games](http://linux.slashdot.org/comments.pl?sid=2820335&cid=39846881) and few native AAA [games](https://web.archive.org/web/20120914200659/http://developer.ubuntu.com/2012/09/top-10-ubuntu-app-downloads-for-august-2012 "8 out of 10 top paid applications on Ubuntu App center are games") for the past six years. The number of available Linux games **overall** is less than 10% of games for Windows. Steam shows a better picture: 25% of games over there have Linux ports (in February 2020: [Windows](https://store.steampowered.com/search/?os=win) 69601 titles vs. [Linux](https://store.steampowered.com/search/?os=linux) 13666 titles) but over **98% out of them are Indies** ; i.e. AAA titles, especially the recent ones, are a rarity in Linux. Luckily nowadays it's possible to run a large number of Windows games in Wine/DXVK and Steam/Proton.
    4. [Questionable](http://news.slashdot.org/comments.pl?sid=2829619&cid=39897163) patents and legality status. [USA](http://www.cerias.purdue.edu/site/blog/post/legit-linux-codecs-in-the-us/ "Legit Linux Codecs In the U.S.") [Linux](http://www.linuxinsider.com/story/70035.html?wlc=1274437690 "Linux Distros and the Codec Conundrum") [users](http://www.datamation.com/article.php/3689726 "Illegal Codecs Put Me Off Linux") in 2020 cannot play many popular audio and video formats until they purchase appropriate codecs or enable third-party repos.

  * **General Linux problems** : 
    1. !! There's no concept of drivers in Linux aside from proprietary drivers for NVIDIA/AMD GPUs which are separate packages: almost all drivers are already either in the kernel or various complementary packages (like foomatic/sane/etc). It's impossible for the user to understand whether their hardware is indeed supported by the running Linux distro and whether all the required drivers are indeed installed and working properly (e.g. all the firmware files are available and loaded or necessary printer filters are installed).
    2. !! There's **no** guarantee whatsoever that your system will (re)boot successfully after GRUB (bootloader) or [kernel](http://www.theinquirer.net/inquirer/feature/2200761/how-to-fix-a-broken-mageia-kernel-upgrade) updates - sometimes even minor kernel updates break the boot process (except for Windows 10 - but that's a new paradigm for Microsoft). For instance Microsoft and Apple regularly update ntoskrnl.exe and mach_kernel respectively for security fixes, but it's unheard of that these updates ever compromised the boot process. GRUB updates have broken the boot process on the PCs around me at least ten times. (Also see compatibility issues below).
    3. !! LTS distros are unusable on the desktop because they poorly support or don't support new hardware, specifically GPUs (as well as Wi-Fi adapters, NICs, sound cards, hardware sensors, etc.). Oftentimes you cannot use new software in LTS distros (normally without miscellaneous hacks like backports, PPAs, chroots, etc.), due to outdated libraries. A not so recent example is Google Chrome on RHEL 6/CentOS 6.
    4. !! Linux developers have a tendency to a) [suppress](http://archive.is/HEkC "Linus Torvalds: Re: \[stable\] Linux 2.6.25.10, Jul 14, 7:27 pm 2008 \(http://kerneltrap.org/Linux/Security_Bugs_and_Full_Disclosure\)") [news](http://www.internetnews.com/blog/skerner/did-linus-jump-the-gun-on-a-kernel-security-fix.html "Did Linus Jump the Gun on a Kernel security fix?") of security holes b) not notify the public when the said holes have been fixed c) miscategorize arbitrary code execution bugs as "possible denial of service" (thanks to [Gullible Jones](http://www.wilderssecurity.com/showthread.php?t=347172) for reminding me of this practice - I wanted to mention it aeons ago, but I kept forgetting about that).  

Here's a full quote by Torvalds himself: _"So I personally consider security bugs to be just "normal bugs". I don't cover them up, but I also don't have any reason what-so-ever to think it's a good idea to track them and announce them as something special."_

Year 2014 was the most damning in regard to Linux security: critical remotely-exploitable vulnerabilities were found in many basic Open Source projects, like bash ([shellshock](https://en.wikipedia.org/wiki/Shellshock_%28software_bug%29)), OpenSSL ([heartbleed](https://en.wikipedia.org/wiki/Heartbleed)), kernel and others. So much for "everyone can read the code thus it's invulnerable". In the beginning of 2015 a new critical remotely exploitable vulnerability was found, called [GHOST](http://arstechnica.com/security/2015/01/highly-critical-ghost-allowing-code-execution-affects-most-linux-systems/).

Year 2015 welcomed us with **134 vulnerabilities** in one package alone: WebKitGTK+ [WSA-2015-0002](https://www.google.com/search?q=WSA-2015-0002). I'm not implying that Linux is worse than Windows/MacOS proprietary/closed software - I'm just saying that the mantra that open source is more secure by definition because everyone can read the code is apparently totally wrong.

Year 2016 pleased us with several local root Linux kernel vulnerabilities as well as countless other critical vulnerabilities. In 2016 Linux turned out to be significantly more [insecure](https://www.lifehacker.com.au/2017/01/which-software-had-the-most-vulnerabilities-in-2016/) than often-ridiculed and laughed-at Microsoft Windows.

The Linux kernel consistently remains one of the most vulnerable pieces of software in the entire world. In 2017 it had [453 vulnerabilities](https://www.cvedetails.com/top-50-products.php?year=2017) vs. 268 in the entire Windows 10 OS. No wonder Google [intends](https://www.bloomberg.com/news/articles/2018-07-19/google-team-is-said-to-plot-android-successor-draw-skepticism) to replace Linux with its own kernel.

Many Linux [developers](http://mjg59.dreamwidth.org/38158.html "Matthew Garret: Why improving kernel security is important") [are](http://openwall.com/lists/kernel-hardening/2015/11/05/1 "Kees Cook: Kernel Self Protection Project") [concerned](http://www.washingtonpost.com/sf/business/2015/11/05/net-of-insecurity-the-kernel-of-the-argument/) with the state of security in Linux because it is simply lacking.

```markdown
5. Linux servers **might be** a lot [less secure](https://www.virusbtn.com/virusbulletin/archive/2014/07/vb201407-Mayhem "Mayhem – a hidden threat for *nix web servers") than ... Windows servers, "The vast majority of webmasters and system administrators have to update their software manually and test that their infrastructure works correctly".   
```

Seems like there are lots of uniquely gifted people out there thinking I'm an idiot to write about this. Let me clarify this issue: whereas in Windows security updates are mandatory and they are usually installed automatically, Linux is usually administered via SSH and there's no indication of any updates at all. In Windows most server applications can be updated seamlessly without breaking services configuration. In Linux in a lot of cases new software releases require manual reconfiguration (here are a few examples: ngnix, apache, exim, postfix). The above two causes lead to a situation when hundreds of thousands of Linux installations **never receive any updates** , because their respective administrators don't bother to update anything since they're afraid that something will break.

August 2016 report from Kaspersky [corroborates](http://fudzilla.com/news/41256-the-rise-of-the-linux-botnets) my thesis: in the first seven months of 2016 the number of infected Linux **servers** increased by 70%.

Ubuntu, starting with version 16.04 LTS, applies security updates [automatically](https://wiki.ubuntu.com/Security/Features) except for the Linux kernel updates which require reboot (it can be eliminated as well but it's tricky). Hopefully other distros will follow.

```markdown
6. ! Fixed applications versions during a distro life-cycle (except Firefox/Thundebird/Chromium). Say, you use DistroX v18.10 which comes with certain software. Before DistroX 20.10 gets released some applications get updated, get new exciting features but you cannot officially install, nor use them.
7. ! Let's expand on the previous point. Most Linux distros are made such a way you cannot upgrade their individual **core** components (like kernel, glibc, Xorg, Xorg video drivers, Mesa drivers, etc.) without upgrading your [whole system](https://bugs.launchpad.net/ubuntu/+bug/578045 "Upgrading packaged Ubuntu application unreasonably involves upgrading entire OS"). Also if you have brand new hardware oftentimes you cannot install current Linux distros because almost all of them (aside from rare exceptions) don't incorporate the newest kernel release, so either you have to use alpha/development versions of your distro or you have to employ various hacks in order to install the said kernel.
8. Some people argue that one of the problems that severely hampers the progress and expansion of Linux is that Linux doesn't have a clear separation between the core system and user-space applications. In other words (mentioned throughout the article) third-party developers cannot rely on a fixed set of libraries and programming interfaces (API/ABI) - in most other OSes you can expect your application to work for years without recompilation and extra fixes - it's often not possible in Linux.
9. No native or/and simple solutions for really simple encrypted file sharing in the local network with password authentication (Samba is **not** native, it's a reverse engineered SMB implementation, it's very difficult for the average Joe to manage and set up. Samba 4 reimplements so many Linux network services/daemons - it looks like a Swiss knife solution from outer space).
10. ~~Glibc by[design](https://bugzilla.redhat.com/show_bug.cgi?id=843478) "leaks" memory (due to [heap fragmentation](https://en.wikipedia.org/wiki/C_dynamic_memory_allocation#Heap-based)). [Firefox](https://www.squarefree.com/2007/09/20/firefox-memory-usage-and-memory-leak-news/ "http://digg.com/news/technology/Firefox_Memory_Leak_Problem_Explored") for Linux now uses its own memory allocator. KDE [Konsole](https://bugs.kde.org/show_bug.cgi?id=176974) application uses its own memory allocation routines.~~ Neil Skrypuch posted an excellent explanation of this issue [here](https://bugs.kde.org/show_bug.cgi?id=176974#c70).
11. ! [Just](http://blogs.gnome.org/otte/2012/07/27/staring-into-the-abyss/) (Gnome) not [enough](https://bugs.kde.org/show_bug.cgi?id=259335#c21) (KDE) [manpower](http://lists.x.org/archives/xorg-devel/2012-May/031006.html) (X.org) - three major Open Source projects are seriously understaffed.
12. ! It's a major problem in the tech industry at large but I'll mention it anyways because it's serious: Linux/open source developers are often not interested in fixing bugs if they cannot easily reproduce them (for instance when your environment substantially differs from the developer's environment). This problem plagues virtually all Open Source projects and it's more serious in regard to Linux because Linux has fewer users and fewer developers. Open Source developers often don't get paid to solve bugs so there's little incentive for them to try to replicate and squash difficult to reproduce bugs.
13. ! A galore of software bugs across all applications. Just look into KDE or Gnome bugzilla's - some bugs are now over ten years old with over several dozens of duplicates and no one is working on them. KDE/Gnome/etc. developers are busy adding new features and breaking old APIs. Fixing bugs is of course a tedious and difficult chore.
14. ! Steep learning curve (even today you oftentimes need to use a CLI to complete some trivial or non-trivial tasks, e.g. when installing third [party software](http://askubuntu.com/a/79284 "How to install Chrome browser properly via command line?")).
15. ! [Incomplete](https://www.phoronix.com/vr.php?view=13622) or [sometimes missing](https://www.phoronix.com/scan.php?page=article&item=linux_2630) [regression](http://lwn.net/Articles/469719/) testing in the Linux kernel (and, alas, in [other](http://blog.martin-graesslin.com/blog/2012/08/this-week-in-kwin-2012-week-31-and-32/) Open Source [software](http://blog.martin-graesslin.com/blog/2012/09/this-week-in-kwin-2012-week-36/) too) leading to a situation when new kernels may become totally unusable for some hardware configurations (software suspend doesn't work, crashes, unable to boot, networking problems, video tearing, etc.)
16. GUI network manager in Linux has [serious problems](https://bugzilla.redhat.com/buglist.cgi?query_format=advanced&bug_status=NEW&bug_status=ASSIGNED&component=NetworkManager&product=Fedora&classification=Fedora).
17. Poor interoperability between the kernel and user-space applications. E.g. many kernel features get a decent user-space implementation years after introduction.
18. ! Linux security/permissions management is a bloody mess: PAM, SeLinux, Udev, HAL (replaced with udisk/upower/libudev), PolicyKit, ConsoleKit and usual Unix permissions (/etc/passwd, /etc/group) all have their separate incompatible permissions management systems spread all over the file system. Quite often people cannot use their digital devices unless they switch to a super user.
19. No sandbox with easy to use GUI (like Sandboxie in Windows).
20. ! CLI (command line interface) errors for user applications. All GUI applications should have a visible error representation.
21. ! Certain Linux components have [very poor](http://libv.livejournal.com/22968.html) documentation and lack good manuals.
22. ! No unified widely used system for packages signing and verification (thus it becomes increasingly problematic to verify packages which are not included by your distro). No central body to issue certificates and to sign packages.
23. There are no native antivirus solutions or similar software for Linux ( **the existing ones are made for finding Windows viruses and analyzing Windows executives** \- i.e. they are more or less useless for Linux). Say, you want to install new software which is not included by your distro - currently there's no way to check if it's malicious or not.
24. !! Most Linux distributions do not audit included packages which means a rogue evil application or a rogue evil patch can easily make it into most distros, thus endangering the end user (it has happened several times already).
25. ! Very bad [backwards](http://linux.slashdot.org/comments.pl?sid=2379392&cid=37090032) and [forward](http://insanecoding.blogspot.ie/2012/07/creating-portable-linux-binaries.html) [compatibility](http://linux.slashdot.org/comments.pl?sid=2820335&cid=39847015). 
  * ! Due to [unstable](http://linux.slashdot.org/comments.pl?sid=2921223&cid=40354019) and constantly changing [kernel APIs/ABIs](https://itvision.altervista.org/files/kernel_api.png) Linux is a hell for companies which cannot push their drivers upstream into the kernel for various reasons like their closeness (NVIDIA, ATI, Broadcom, etc.), or inability to control development or co-develop (VirtualBox/​Oracle, VMWare/​Workstation, etc.), or licensing issues (4Front Technologies/OSS).
  * Old applications rarely work in new Linux distros (glibc [incompatibilities](https://bugzilla.redhat.com/show_bug.cgi?id=638477) (double-free errors, memory corruption, etc.), missing libraries, wrong/new libraries versions). Abandoned Linux GUI software generally doesn't work in newer Linux distros. Most well written GUI applications for Windows 95 will work in Windows 10 (24 years of binary level compatibility).
  * New applications linked _only against_ lib C will refuse to work in old distros (even though they are 100% source compatible with old distros).
  * New library versions [bugs, regressions and incompatibilities](https://web.archive.org/web/20140413195014/http://blog.linuxgamepublishing.com/2009/02/08/our-new-way-to-meet-the-lgpl/).
  * Distro upgrade can render your system unusable (kernel might not boot, some features may stop working).
  * There's a myth that backwards compatibility is a non-issue in Linux because all the software has sources. However a lot of software just cannot be compiled on newer Linux distros due to 1) outdated, conflicting, no longer available libraries and dependencies 2) every GCC release becoming much stricter about C/C++ syntax 3) Users just won't bother compiling old software because they don't know how to 'compile' - nor they should they need to know how to do that.
  * DE developers (KDE/Gnome) routinely cardinally change UI elements, configuration, behaviour, etc.
  * Open Source developers usually [don't care](http://www.tomshardware.com/reviews/fedora-16-gnome-3-review,3155-27.html) about application behaviour beyond their [own usage](http://linux.slashdot.org/comments.pl?sid=2820335&cid=39847007) scenarios. I.e. coreutils developers for no good reasons have broken head/tail functionality which is used by the Loki installer.
  * Quite often you cannot run new applications in LTS distros. Recent examples: GTK3 based software (there's no official way to use it in RHEL6), and Google Chrome (Google decided to abandon LTS distros).
26. Linux has a 255 bytes limitation for file names (this translates to just **63 four-byte characters** in UTF-8) - not a great deal but copying or using files or directories with long names from your Windows PC can become a serious challenge.
27. Certain applications that exist both for Windows and Linux start up faster in Windows than in Linux, sometimes several times faster. It's worth noting though that SSD disk users are mostly unaffected.
28. All native Linux filesystems (except ext4) are case sensitive about filenames which utterly confuses most users. This wonderful peculiarity doesn't have any sensible rationale. Less than 0.01% of users in the Linux world depend on this feature.
29. (Not a big issue anymore since users are slowly migrating to SSD drives) Most Linux filesystem cannot be _fully_ defragmented unless you compact and expand your partition which is very dangerous. Ext4fs supports defragmentation but only for _individual files_. You cannot combine data and turn free space into one continuous area. XFS supports full defragmentation though, but by default most distros offer Ext4 and there's no official safe way to convert ext4 to XFS.
30. Linux preserves file creation time only for certain filesystems (ext4, NTFS, fat). Another issue is that user space utilities currently [cannot view](http://lists.gnu.org/archive/html/coreutils/2010-08/msg00047.html) or modify this time (ext4 `debugfs` works only under root).
31. A lot of [UNIX problems](http://web.mit.edu/simsong/www/ugh.pdf) (PDF, 3MB) apply to Linux/GNU as well.
32. There's a lot of [hostility](https://plus.google.com/+LennartPoetteringTheOneAndOnly/posts/J2TZrTvu7vd "Much of the Open Source community tries to advertise the community as one happy ...") in the open source community.
33. This is so [freaking "amazing"](https://mjg59.dreamwidth.org/41085.html "Matthew Garrett: There's more than one way to exploit the commons"), you absolutely [have to read it](https://www.jwz.org/blog/2016/04/i-would-like-debian-to-stop-shipping-xscreensaver/) \- the developer behind XScreenSaver [fought](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=819703 "xscreensaver: please disable 'This version of XScreenSaver is very old! Please upgrade!' message") with Debian developers.
34. Random ramblings or why you may hate Linux (some are severely outdated/irrelevant/fixed but they are left for posterity to see the innards of the open source movement and community):  
```

1) [KDE: troubleshooting kded4 bugs](https://kdepepo.wordpress.com/2011/05/11/troubleshooting-kded4-bugs/).  
2) [A big discussion](https://apple.slashdot.org/story/11/11/11/0233227/whats-keeping-you-on-windows) on Slashdot as to why people still prefer Windows over Linux.
3) [Another big discussion](https://linux.slashdot.org/story/12/03/21/0341218/why-linux-cant-sell-on-the-desktop) on Slashdot as to why Linux still lacks.
4) ~~Any KDE plasmoid can[freeze](http://lamarque-lvs.blogspot.com/2012/03/desktop-freezes-in-48x.html) the entire KDE desktop~~ - seems to be fixed in KDE5.
5) [Why Desktop Linux Hasn't Taken Off](https://linux.slashdot.org/story/12/04/30/1616200/why-desktop-linux-hasnt-taken-off) - Slashdot.
6) [Torvalds Slams NVIDIA's Linux Support](https://linux.slashdot.org/story/12/06/17/1415250/torvalds-slams-nvidias-linux-support) - Slashdot.
7) [Are Open-Source Desktops Losing Competitiveness?](https://developers.slashdot.org/story/12/06/26/1940250/are-open-source-desktops-losing-competitiveness) - Slashdot (A general consensus - No).
8) Broadcom Wi-Fi adapters under Linux are a PITA.
9) A Gnome developer laments [the state of Gnome 3 development](http://blogs.gnome.org/otte/2012/07/27/staring-into-the-abyss/)
10) Fuck LTS distros: [Google Says Red Hat Enterprise Linux 6 Is Obsolete](https://web.archive.org/web/20130816055110/http://www.muktware.com/5203/google-says-red-hat-enterprise-linux-6-obsolete) (WTF?! Really?!).
11) A rant about [Gnome 3 APIs](http://igurublog.wordpress.com/2012/11/05/gnome-et-al-rotting-in-threes/ "GNOME \(et al\): Rotting In Threes").
12) OMFG: Ubuntu has announced [Mir](https://web.archive.org/web/20130306104754/https://wiki.ubuntu.com/MirSpec), an alternative to X.org/Wayland.
13) KDE's mail client [cannot properly](http://dilfridge.blogspot.ru/2013/05/personal-experience-and-opinion-kmail2.html) handle IMAP mail accounts.
14) Desktop Linux security is a [mess](https://itvision.altervista.org/files/Assessing.the.Linux.Desktop.Security-Ilja.van.Sprundel.zip) (zipped MS Powerpoint presentation, 1.3MB) + [13 HID vulnerabilities](http://www.openwall.com/lists/oss-security/2013/08/28/13 "Subject: Linux HID security flaws").
15) Yet another Gnome developer concurs that Gnome 3 was a [big mistake](http://geekyogre.com/moving-on/).
16) Gnome developers keep [fucking](http://igurublog.wordpress.com/2014/03/22/gtk-3-10-drops-menu-icons-and-mnemonics/ "GTK 3.10 Drops Menu Icons and Mnemonics") [hard](http://redmine.audacious-media-player.org/boards/1/topics/1135) their users.
17) Fixed now: ~~KDE developers'[yet](https://bugs.kde.org/show_bug.cgi?id=331932) [another](https://bugs.kde.org/show_bug.cgi?id=332195) [fuck up](https://bugs.kde.org/show_bug.cgi?id=333774) called, "You want to disable files indexing? Really? Fuck you! Eat what we're giving you." ~~
18) Linux "security" is a mess. For the past six months two local root exploits have been discovered in the Linux kernel. Six critical issues have been discovered in OpenSSL (which allow remote exploitation, information disclosure and MITM).
19) Skype developers [dropped support](http://blogs.skype.com/2014/06/18/skype-4-3-for-linux/ "Skype 4.3 for Linux") for ALSA. Wow, great, fuck compatibility, fuck old distros, fuck the people for whom PulseAudio is not an option.
20) Well, fuck compatibility, there are now [three versions](https://web.archive.org/web/20170222134929/http://article.gmane.org/gmane.os.openbsd.tech/37174 "boringssl and such") of OpenSSL in the wild: OpenSSL itself, BoringSSL by Google, LibReSSL by OpenBSD. All with incompatible APIs/ABIs (OpenSSL itself breaks API/ABIs quite often).  
21) ~~KDE developers decided to[remove support](http://blog.martin-graesslin.com/blog/2014/06/where-are-my-systray-icons/ "Where are my systray icons?") for the [xembed](https://github.com/davidedmundson/xembed-sni-proxy) based system tray, so your old applications will not have a system tray icon, unless you patch your system. Wonder-fuck-you-ful.~~ The feature has finally been reintroduced in Plasma 5.5.5 after two years (!!) of users' remonstrance.
22) KDE developers/maintainers silently delete unpleasant user comments on dot.kde.org. KDE developers ignore bugs posted at bugs.kde.org.
23) Welcome: [PulseAudio emulation](https://github.com/i-rinat/apulse) for Skype. Audio is not fucked up in Linux you said?
24) UDP connections monitoring is a [hell on earth](http://serverfault.com/questions/192893/how-i-can-identify-which-process-is-making-udp-traffic-on-linux).
25) Linux has become way [too complex](http://changelog.complete.org/archives/9299-has-modern-linux-lost-its-way-some-thoughts-on-jessie) even for ... Linux developers.
26) Linux developers gave up on maintaining API/ABI compatibility even among modern distros and decided to bundle a full Linux stack with every app to [virtualize it](http://blogs.gnome.org/alexl/2015/02/17/first-fully-sandboxed-linux-desktop-app/). This is so f*cked up, I've got no words. Oh, Wayland is required for that, so this thing is not going to take off any time soon.
27) Out of 20 most played/popular games in Steam only three [are available](http://arstechnica.com/gaming/2015/03/steam-gauge-measuring-the-most-popular-steam-games-of-2014/3/) for Linux. I'm not saying it's bad, it's just what it is.
28) This article is getting unwieldy but fuck it, even [Linus admits](https://www.youtube.com/watch?v=5PmHRSeA2c8#t=357 "DebConf14: QA with Linus Torvalds") that API/ABI compatibility in Linux is beyond fucked up: "making binaries for Linux desktop applications is a major fucking pain in the ass. You don’t make binaries for Linux, you make binaries for Fedora 19, Fedora 20, maybe even RHEL5 from 10 years ago. You make binaries for Debian Stable…well actually no, you don't make binaries for Debian Stable because Debian Stable has libraries that are so old that anything built in the last century doesn’t work."
29) KDE is spiralling out of control (besides, its code quality is beyond horrible - several crucial parts of the KDE SC, like KMail/akonadi, are barely functional): people [refuse to maintain](https://lists.fedoraproject.org/pipermail/kde/2015-October/016315.html "Kevin Kofler kevin.kofler at chello.at: Stepping down from KDE SIG") literally hundreds of KDE packages.
30) Google Chrome [stopped supporting 32bit](http://linux.slashdot.org/story/15/12/01/1524259/google-to-drop-chrome-support-for-32-bit-linux) distros starting March 2016. They don't care that 64bit distros and applications in some cases require up to 40% more RAM.
31) Let's have some fun! ... or hatred maybe? Native Linux games do ... **not** [work under Linux](http://blogg.forteller.net/2016/humble-test/). Fuck compatibility. Fuck it! This "OS" is a fucking joke.
32) QA/QC in Linux you say? Oh, [really](http://lkml.iu.edu/hypermail/linux/kernel/1702.2/05171.html "Re:\[git pull\] drm for v4.11 - main pull request; Thu Feb 23 2017 - 20:50:55 EST")? Like you're not [joking](http://lkml.iu.edu/hypermail/linux/kernel/1702.2/05174.html)?
33) In April 2017 Canonical (the company behind Ubuntu) [axed](https://insights.ubuntu.com/2017/04/05/growing-ubuntu-for-cloud-and-iot-rather-than-phone-and-convergence/) the development of their own desktop environment Unity and their own display manager Mir. A lot of people questioned their decision to migrate to [Gnome 3](https://linux.slashdot.org/story/17/04/05/1812232/canonical-killing-unity-for-ubuntu-linux-will-switch-to-the-superior-gnome) which is not perceived as a PC-friendly desktop environment by the Linux community.
34) This is so brilliant it will leave you speechless. This is how open source projects should interact more often (it's a sad joke). [KWin + Wayland vs. Qt 5.8/5.9](https://blog.martin-graesslin.com/blog/2017/07/plasma-wayland-and-qt-5-9-and-beyond/), fight!
35) In 2018 Gnome developers decided that applications must replace [title bars with header bars](https://tech.slashdot.org/story/18/01/27/2245240/should-apps-replace-title-bars-with-header-bars).
36) This is quite damning: [Linux.com admits](https://www.linux.com/blog/learn/2018/2/which-linux-kernel-version-stable) that there are no stable Linux kernels, "The most we can do is to unhelpfully state that they are "differently stable"".
37) Ubuntu in its feat of idiotic brilliance decided to deprecate 32bit support in Ubuntu. After Valve decided to pull Ubuntu support in Steam, Ubuntu reneged on its decision but the damage has been done. Ubuntu/Mark Shuttleworth don't care that there are literally thousands of 32bit exceptionally useful applications including games which will never be ported to 64bit.

  * **Software development under and for Linux**
    1. ! [Stable API](http://www.kroah.com/log/linux/stable_api_nonsense.html) [nonsense](http://www.h-online.com/open/news/item/New-Linux-drivers-for-old-kernel-versions-1667811.html "The H Open: New Linux drivers for old kernel versions"): you [cannot](https://itvision.altervista.org/files/kernel_api.png) develop kernel drivers out of the kernel tree, because they will soon [become](http://linux.slashdot.org/comments.pl?sid=2927755&cid=40386251) [incompatible](http://tech.slashdot.org/comments.pl?sid=2359610&cid=36956564) with mainline. That's the sole reason why RHEL and other LTS distros are so popular in enterprise. This is why Google is currently developing an [alternative](https://en.wikipedia.org/wiki/Google_Fuchsia) to the Linux kernel - even they don't have enough resources and willpower to maintain their own Linux fork.
    2. Games development: no [complete](http://www.codeweavers.com/about/blogs/jwhite/2012/6/5/whining-about-wine) multimedia framework.
    3. ! Hostility towards third-party developers: many open source projects are extremely self-contained, i.e. if you try to develop your open source [project](https://plus.google.com/+DirkHohndel/posts/MwiTc3cHKgi) using open source [library X](https://www.youtube.com/watch?v=gGZyVSOnqm0 "Youtube: Gtk to Qt - a strange journey") or if you try to bring your suggestions to some open source [project](http://lwn.net/Articles/578209/ "Bug#727708: init system other points, and conclusion"), you'll be met with extreme hostility.
    4. A lot of points mentioned above apply to this category, they won't be reiterated.
  * **Enterprise level Linux problems:**
    1. Most distros don't allow you to easily set up a server with e.g. such a configuration: Samba, SMTP/POP3, Apache HTTP Auth and FTP where all users are **virtual**. [LDAP](https://news.ycombinator.com/item?id=1274544 "Why nobody uses LDAP | Hacker News") is a PITA. Authentication against MySQL/any other DB is also a PITA.
    2. ! No software (group) policies.
    3. ! No standard way of software deployment (pushing software via SSH is indeed an option, but it's in no way standard, easy to use or obvious - you can use a sledgehammer to crack nuts the same way).
    4. ! No [CIFS/AD](http://apple.slashdot.org/story/11/11/11/0233227/whats-keeping-you-on-windows) level replacement/​equivalent (SAMBA doesn't count for many reasons): 1) Centralized and easily manageable user directory. 2) Simple file sharing. 3) Simple (LAN) computer discovery and browsing.
    5. No _native production-ready_ filesystem with de-duplication, data and metadata checksumming and file compression (please [support](https://www.patreon.com/bcachefs) [bcachefs](https://bcache.evilpiepirate.org/) \- it has it all). No filesystems at all to support per-file encryption (ext4fs implements encryption for _directories_ starting from Linux 4.1 but it will take months before desktop environments start supporting this feature).
    6. !! No proper RDP/Terminal Services alternative (built-in, standardized across distros, high level of compression, low latency, needs zero effort to be set up, integrated with Linux PAM, totally encrypted: authentication + traffic, digital signature like SSH).



### 摘要

  * **不[稳定性](http://alien.slackbook.org/blog/kde-update-4-14-2-no-kde5-updates-yet-devs-need-to-get-their-act-together/ "KDE update: 4.14.2. No KDE5 updates yet – devs need to get their act together")，[各种 Bug](http://www.dedoimedo.com/computers/fedora-18-kde.html "Fedora 18 Spherical Cow review - Bad bad bad")，[倒退](https://www.google.com/search?hl=en&q=regression+site%3Alkml.org "Linux kernel regressions")、[倒退](https://www.google.com/search?hl=en&q=regression+site%3Afreedesktop.org "X.org and related projects' regressions")，[还是](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/966744 "\[i965\] Resume from suspend leaves me with black screen or a screen of the desktop before it suspended.")[倒退](https://bugs.kde.org/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=&content=regression "KDE regressions")：**  以前能工作的东西意外地坏了，意味着有 _大_ 量的（性能等）[滑坡（regressions，本段中的“倒退”、”回退“和“倒车”均指该词）](https://web.archive.org/web/20170222135049/https://plus.google.com/111104121194250082892/posts/aCiB7kTLXTh "Alan Cox - So Fedora 18 seems to be the worst Red Hat distro I've ever seen.")（[内核](https://web.archive.org/web/20130915022931/http://codemonkey.org.uk/2013/03/01/39-merge-window-fallout/)和用户空间的应用都有此问题）；有些“坡”还会“滑”到[数据](http://neil.brown.name/blog/20120615073245 "A Nasty md/raid bug")[丢失](https://lkml.org/lkml/2012/10/23/690 "Re: Apparent serious progressive ext4 data corruption bug in 3.6.3 \(and other stable branches?\)")。 _多数_ 开源项目中（包括内核）基本上既没有[质量控制](http://www.h-online.com/open/features/Kernel-Comment-Get-testing-1669920.html "Linux users should test the latest kernel from time to time - if they don't, they shouldn't be surprised if something important gets broken the next time a major update is released.")（[QA/QC](https://www.google.com/search?q=ext4+corruption+linux+4.0)）也没有回退测试 —— 举个例子，微软[报告](http://techcrunch.com/2012/10/25/microsoft-launches-windows-8-after-1-24b-hours-of-testing-available-on-over-1000-certified-devices/) Windows 8 接受了 _12 4000 0000_ 小时的测试，然而新发布的内核，我猜不到 1 0000 小时 —— 而且每次 Linux 内核的发布都可以比拟一个新的 Windows 版本。妨碍正常工作流的严重 Bug 能花上好几年来解决。很多重要硬件（例如 GPU、Wi-Fi 网卡）不能很好地被支持。即使 Linux 开发者们坚持一定要马上升级到某个”稳定的“ x.y.Z 内核更新，但是一些“倒车”往往是从这里“开”出来的。
  * **硬件问题：** 在 Linux 下很多设备的功能支持相当匮乏，或者根本没有支持。一些硬件（比如博通的 WiFi 适配器） _无法_ 使用，除非已有可用的网络连接。新硬件往往要在上市几个月后才逐渐[被支持](http://apple.slashdot.org/story/12/08/16/1741235/linux-is-a-lemon-on-the-retina-macbook-pro)。管理设备的专用软件，比如打印机、扫描仪、照相机、网络摄像头、音频播放器和智能手机等等，大多数[不存在](https://www.phoronix.com/scan.php?page=news_item&px=MTEyNDA "Phoronix.com: Linux Driver Support Still Leaves A Lot To Desire")。 —— 所以你没有办法能完全控制你的新电子设备并升级固件。Linux 的图形支持也是“泣血”之痛，因为内核或 X.org 的 API 或 ABI 的频繁变动，让英伟达或者博通等公司不想只是为开源软件中这些疯狂的变更来分配额外的资源而浪费资金。
  * **缺乏的[标准化](http://www.itwire.com/business-it-news/open-source/65402-torvalds-says-he-has-no-strong-opinions-on-systemd "Linus Torvalds: The current packaging model is certainly broken for third-party applications")、碎片化、不必要且过度的变化，以及不同发行版之间没有共同的方向或愿景：** _太多_  Linux [发行版](http://linux.slashdot.org/comments.pl?sid=2737589&cid=39424927)的配置、打包系统不兼容也不相似，库也彼此不相容。 不同的发行版采用 _完全不同_ 的桌面环境、不同的图形和控制台应用来配置计算机设置。例如，基于 Debian 的发行版要求使用严格基于文本的 `dpkg-reconfigure` 实用程序来执行某些与系统相关的维护任务（译者注：有些发行版仅使用了 Debian 的 `dpkg/apt` 工具，例如 AOSC，它们不基于 Debian 也不是 Debian 系发行版，未必和 Debian 相同的实用程序） 。
  * **开源开发者之间的[合作](https://lkml.org/lkml/2012/10/3/484 "Re: udev breakages - was: Re: Need of an .async_probe\(\) type of callback at driver's core")缺乏和[内部](https://web.archive.org/web/20150107231839/http://permalink.gmane.org/gmane.linux.gentoo.devel/81901 "eudev project announcement: udev often breaks compatibility with older systems")[斗争](https://lists.gnu.org/archive/html/help-smalltalk/2012-12/msg00014.html "I am less pleased to announce that I am resigning from maintenance of GNU sed \(after 8 years\) as well as GNU grep \(after 3\)."):** 没有一个中心机构来组织开源开源（软件）栈不同部分的开发，这往往导致了一种情况：一个项目引入了更新，[破坏了](https://bugzilla.redhat.com/show_bug.cgi?id=638477 "Strange sound on mp3 flash website")另外的项目（这个问题在下文中的“不稳定的 APIs/ABIs” 一节处也有反映）。即使开源运动缺乏人力，但不同的 Linux 发行版仍能找到足够的资源复刻各种项目（Gentoo 开发者正在开发 udev 的替代方案；libav 的出现源于 ffmpeg 中的一场矛盾；围绕 Open Office 和 Libre Office 的一系列情况；以及 Mir —— 一个新的 X.org/Wayland 替代品）并使用他们自己的解决方案。
  * **又多又快的[变更](http://theoden48.wordpress.com/2012/07/22/ive-gone-back-to-windows/ "I've Gone Back To Windows")：** 多数 Linux 发行版升级/发布周期非常[短](https://news.ycombinator.com/item?id=3716884 "Nobody wants to bother with something which will be obsolete half a year down the road")（有时候短到 _六个月_ ，或者例如 Arch 这样的滚动发行版，或者 Fedora 这样的每六个月就有升级的），因此你得受到各种不期望或不想要的变更的狂轰滥炸。LTS（长期支持）发行版因其维持应用版本的策略，多数情况下 _不适合_ 桌面用户（而且通常没有官方认可的方法来安装处于存亡边缘的应用 - _请不要让我想起 PPA 和 Backport - 这些黑科技不受官方支持，也不保证可用_ )。LTS 发行版另一个让人却步的问题是 LTS 内核往往不支持新硬件。
  * **[不稳定的](http://upstream.rosalinux.ru/) [APIs](https://itvision.altervista.org/files/history_api_break.png "Timeline of 'unintentional' API breaks")/[ABIs](https://itvision.altervista.org/files/abi_breaks.png "Statistics of ABI breaks in C/C++ libraries") 和[真正](http://developerblog.redhat.com/2015/02/10/gcc-5-in-fedora/)[兼容性](http://tech.slashdot.org/comments.pl?sid=3010389&cid=40798035)的[缺乏](https://wiki.archlinux.org/index.php/Steam#Steam_runtime_issues) :** 在新发行版里使用旧的 _开源_ 和闭源软件是很[困难](https://web.archive.org/web/20140910085118/http://weblogs.mozillazine.org/asa/archives/008499.html "asa dotzler: linux not ready for the desktop")的（而由于像内核、GCC 或者 glibc 这样的 Linux 关键组件发生变动，许多情况下也变成了不可能的事）。几近[不存在的](https://www.youtube.com/watch?v=5PmHRSeA2c8#t=357 "DebConf14: QA with Linus Torvalds")向后兼容性使得为 Linux 发行版创建闭源软件难于登天、花销巨大。如果由于更早版本的运行库过时而不再提供而无法满足其依赖关系，没有活跃开发者和维护者的开源软件就会被丢弃。由于这个原因，举个例子，**即使不**存在替代品，很多 KDE3/Qt3 应用也不再可用了。在 Linux 主内核树之外开发驱动程序是一件非常费力的事情。没有适用于 Linux 的 [WinSxS](https://en.wikipedia.org/wiki/Side-by-side_assembly) 等效品 —— 因此没有简单的方法来安装冲突的库。**在 2015 年，Debian 放弃了对 Linux Standard Base（LSB）的支持。万岁，不兼容！**
  * **软件问题：** 没有多少**原生**游戏（主要是独立游戏）和原生 3A 游戏（Valve 和游戏开发商的努力与合作使得许多游戏进来面向 Linux 发行，但每年仍有 _数千款_ 游戏只面向 Windows 发行 *****。超过 98% 的现有和即将上市的 AAA 游戏在 Linux 中仍不可玩)。（Linux 中）没有熟悉的 Windows 软件，没有 Microsoft Office（Libre Office 目前在打开 [Microsoft Office](http://www.zdnet.com/article/huge-savings-prompt-italian-city-to-dump-openoffice-for-microsoft-after-four-years/) 生产的文档仍有大麻烦），没有原生的[CIFS](https://en.wikipedia.org/wiki/Server_Message_Block)（ _易于配置和使用、同时有密码保护和加密的_ 网络文件共享）的对应软件，没有活动目录（Active Directory）或与之相当的功能。
  * **资金、热情、动力和责任：** 几年前笔者就预测过，一旦自由和开源软件（FOSS）不再是游乐场，FOSS 开发者就会开始逐渐远离这一平台，（因为）它需要可持续的精力和时间，意思就是：**游戏结束了**，开发者们想要真金白银来完成艰难的工作。背后缺乏财政撑腰的 FOSS 开发表现出疲态和幻灭的现实。毕竟，FOSS 平台需要有**经济驱动**的开发者，因为资金不足的[项目](http://ksensors.sourceforge.net/ "There's no equivalent of KSensors in KDE 4 and no one wants to port this pretty simple and necessary application to the new platform")[开始](https://www.phoronix.com/scan.php?page=news_item&px=MTEyNjI "Mesa's Rate Of Git Development Is Slowing")[逐渐衰退](http://ppenz.blogspot.nl/2012/06/dolphin-21.html "Dolphin 2.1: a developer departure"),[关键的](https://bugs.kde.org/duplicates.cgi?sortby=count&reverse=1&sortvisible=0&maxrows=50&changedsince=7&openonly=1) Bug 会持续存在很多年。有人可能会说“甩掉包袱“了，但是问题在于这些垂死的项目往往没有其他替代，或者功能相似的继任者。
  * 没有[打磨](http://linux.slashdot.org/comments.pl?sid=2608362&threshold=5&commentsort=0&mode=thread&cid=38619928)，没有[一致性](http://linux.slashdot.org/comments.pl?sid=2608362&threshold=5&commentsort=0&mode=thread&cid=38623292)，也没有遵守[人性化界面指南](https://en.wikipedia.org/wiki/Human_interface_guidelines "Human interface guidelines - unified and consistent graphical user interface")（甚至 KDE 的开发者都[这样承认](http://lamarque-lvs.blogspot.com/2012/02/new-qml-shutdown-dialog-in-490.html?showComment=1330091928115#c3431625452916542616)）。
  * 与 Windows 和 Mac OS X（macOS）等其他桌面操作系统相比，各 Linux 组件间的联系并不紧密，这意味着同样一项任务在 Linux 上执行要消耗多得多的能量（电源），这样的结果是运行 Linux 的笔记本用户的电池寿命更差。从日常生活中举一些例子：编辑文档、听音乐、观看 YouTube 视频或甚至是玩游戏。另外举个桌面渲染的简单任务的例子：Windows 会为与渲染屏幕图像有关的许多任务使用并规划 GPU 加速，然而 Linux 通常什么也没用。



### “这篇文章是胡扯！ Linux 能给我/我的祖父/姨妈/等等人用” 云云

嘿，笔者很中意有人这么说，然而这里还是有一列表的问题深深地影响着每一位 Linux 用户。

  * 无论是 Mozilla Firefox 还是 Google [Chrome](http://linux.slashdot.org/story/14/03/04/1926233/google-wont-enable-chrome-video-acceleration-because-of-linux-gpu-bugs) 在 Linux 中都没有使用视频解码和输出加速，因此在 YouTube 上刷小视频，比如相比于 Windows，会更快“吸干”笔记本的电量。
  * NVIDIA Optimus 是多数 Linux 发行版之痛，而且对于绝大多数人来说，它在 UEFI 安全模式下完全无法工作。
  * 对于使用当地键盘布局的人来说，快捷键处理是[残缺的](https://bugs.freedesktop.org/show_bug.cgi?id=865)（这个问题到现在有 **15 年之久** 了）。不是所有人都生活在说英语的国家。
  * X.org 中的键盘处理设计残缺 —— 当遇到悬浮窗口或打开的菜单时，全局键盘快捷键/键绑定[不](https://bugzilla.gnome.org/show_bug.cgi?id=344059 "Ways to make global keybindings work during grabs")（GTK）[工作](https://bugs.kde.org/show_bug.cgi?id=70063 "global shortcuts don't work when any popup is active")（Qt）。
  * 没有比较容易的方法使用发行版仓库以外的软件，尤其是只有源码可用的软件。对于非 IT 专业的普通用户，那更是毫无门道。
  * 你不玩游戏，对吗？Linux 拥有的[原生 3A 游戏依旧很少](https://store.steampowered.com/linux)：在过去三年里号称 3A 的可玩游戏不足 12 个。坦诚地说，可以通过 DirectX 到 Vulkan/OpenGL 转译（Wine、Proton 和 Steam for Linux）来运行成百上千的 Windows 游戏，但是这样带来了（额外的）转译成本，有时也会显著降低性能表现。游戏可能会崩溃，并且和 Windows 中表现也会有不同。反作弊保护通常也无法在 Linux 中工作。
  * Microsoft Office 不适用于 Linux。而 Libre Office 在正确打开、渲染或保存在 Microsoft Office 创建的文档等上经常遇到大麻烦（更别说后者是商业界标准）。除此之外，Libre Office（套件）的用户界面（相比 Microsoft Office）完全不同，并且许多功能的工作方式也不一样。Linux 本身不提供 Windows 本统字体，这往往导致格式问题。
  * Linux 下有几大 Windows 软件不能用：Quicken、Aodobe 创作产品（Photoshop、Audition 等）、Corel 创作产品（CorelDraw 和其他软件）、Autodesk 的软件（3ds Max、Autocad 等）、严肃的 BluRay/DVD 创作产品和专业音像应用（CuBase、SoundForge 等）。
  * 2020 年了，Windows 网络文件共享（易于配置、发现、加密和有密码保护的网络文件共享）依旧没有替代品。NFS 和 SSHFS 是两个糟糕且完全不用户友好的选择。
  * Linux 没有工作可靠的、轻松无忧且快速的原生（可通过内核直接挂载；FUSE [不裁剪（阉割）其功能](http://sourceforge.net/p/libmtp/code/ci/master/tree/README "GIT README")）[MTP](https://en.wikipedia.org/wiki/Media_Transfer_Protocol) 实现。为了能和你的设备配合工作，比如 ... 基于 Linux 的 Android 手机，最好还得用 ... Windows 或者 Mac OS X（macOS）。**更新**：一位俄罗斯程序员在被 libmtp 惹得极度愤怒的情况下，用 Qt 写了一个自己的完整的软件，使用 libusb 直接与内核通信。来认识 [Android-File-Transfer-Linux](https://github.com/whoozle/android-file-transfer-linux)。
  * Linux 中有太多东西需要用文本文件手动配置了：只举几个例子，NVIDIA Optimus 可切换显卡、自定义显示刷新率、一机多用配置（译者注：即一台主机为多位用户提供图形界面使用）、USB 3G/LTE/4G 调制解调器（猫），还有各种守护程序配置，以及高级音频配置等等。
  * 请忘记如何管理电子设备吧（尤其是智能手机，iPhone 在 Linux 下就如同板砖）。很多情况下，你也会忘记打印机的一些高级功能，比如墨水量报告。

是啊，我们也许能考虑将 Linux 作为可用于桌面的操作系统吧 :-)（苦笑）。


### Commentary From the Author

A lot of people who are new to Linux or those who use a very tiny subset of applications are quick to disregard the entire list saying things like, _"Audio in Linux works just fine for me."_ or _"I've never had any troubles with video in Linux."_ Guess what, there are thousands of users who [![Linux car analogy. Click to view the fullimage](Main%20Linux%20problems%20on%20the%20desktop,%202020%20edition%20or%20why%20Linux%20sucks_files/linux-car-kit.jpg)](https://itvision.altervista.org/files/linux-car-kit.jpg) have immense problems because they have a different set of hardware or software. Do yourself a favour - come and visit Ubuntu or Linux.com forums and count the number of threads which contain _"I have erased PulseAudio and only now audio works for me"_ or _"I have finally discovered I can use nouveau instead of [NVIDIA binary](https://devtalk.nvidia.com/default/board/98/linux/) drivers (or vice versa) and my problems are gone."_

There's another important thing that critics fail to understand. If something doesn't work in Linux, people will not care whose fault it is, they will automatically and rightly assume it's Linux's fault. For the average Joe, Linux is **just another operating system**. He or she doesn't care if a particular company ABC chose not to support Linux or not to release fully-functional drivers for Linux - their hard earned hardware just doesn't work, i.e. **Linux doesn't work.** People won't care if Skype crashes every five minutes under some circumstances - even though in reality Skype is an awful piece of software which has tonnes of glitches and sometimes crashes even under Windows and MacOS.

I want to refute a common misconception, that support for older hardware in Linux is a lot better than in Windows. It's partly true but it's also false. For instance neither nouveau nor proprietary NVIDIA drivers have good support for older NVIDIA GPUs. Nouveau's OpenGL acceleration speed is lacking, NVIDIA's blob doesn't support many crucial features found in Xrandr or features required for proper acceleration of modern Linux GUIs (like Gnome 3 or KDE4). In case your old hardware is magically still supported, Linux drivers almost always offer only a small subset of features found in Windows drivers, so saying that Linux hardware support is better, just because you don't have to spend 20 minutes installing drivers, is unfair at best.

Some comments just [astonish](http://www.reddit.com/r/LinuxActionShow/comments/tx5id/very_nice_write_up_which_breaks_down_the_problems/) me: _"This was terrible. I mean, it's full of half-truths and opinions. NVIDIA Optimus (Then don't use it, go with Intel or something else)."_ No shit, sir! I've bought my laptop to enjoy games in Wine/dualboot and you dare tell me I shouldn't have bought in the first place? I kindly suggest that you not impose your opinion on other people who can actually get pleasure from playing high quality games. Saying that SSHFS is a replacement for Windows File Sharing is the most ridiculous thing that I've heard in my entire life.

It's worth noting that the most vocal participants of the Open Source community are extremely [bitchy](http://games.slashdot.org/story/12/04/25/1241241/phoronix-confirms-gnulinux-steam-and-source-engine-clients) and overly [idealistic](https://itvision.altervista.org/files/expo_02_010_full.jpg) people peremptorily requiring everything to be open source and free or it has no right to exist at all in Linux. With an attitude like this, it's no surprise that a lot of companies completely disregard and shun the Linux desktop. Linus Torvalds once [talked](http://www.linux-mag.com/id/7439) about this: _There are "extremists" in the free software world, but that's one major reason why I don't call what I do "free software" any more. I don't want to be associated with the people for whom it's about exclusion and hatred._

Most importantly **this list is not an opinion**. Almost every listed point has links to appropriate articles, threads and discussions centered on it, proving that I haven't pulled it out of my < expletive >. And please always check your "facts".

I'm not really sorry for citing slashdot comments as a proof of what I'm writing about here, since I have one very strong justification for doing that - the /. crowd is very large, it mostly consists of smart people, IT specialists, scientists, etc. - and if a comment over there gets promoted to +5 insightful it usually* means that many people share the same opinion or have the same experience. This article was discussed on [Slashdot](http://linux.slashdot.org/story/15/12/30/1737235/list-of-major-linux-desktop-problems-updated-for-2016), [Reddit](https://www.reddit.com/r/linux/comments/3yyx8b/major_linux_problems_on_the_desktop_2016_edition/), [Hacker News](https://news.ycombinator.com/item?id=10812214) and [Lobste.rs](https://lobste.rs/s/fdug0z/main_linux_problems_on_desktop_2017) in 2017.
* I previously said " _certainly_ " instead of " _usually_ " but after this text was called "[hysterical nonsense](http://tech.slashdot.org/comments.pl?sid=3089033&cid=41208613)" (a rebuttal is here) I decided not to use this word any more.

**On a positive note**

If you get an impression that Linux sucks - you are largely wrong. For a limited or/and non-professional use Linux indeed shines as a desktop OS - when you run it you can be sure that you are malware free. You can safely install and uninstall software without fearing that your system will break up. At the same time innate Windows problems (listed at the beginning of the article) are almost impossible to fix unless Microsoft starts from scratch - Linux problems are indeed approachable. What's more, Linux, unlike Windows 10, doesn't collect data on you and doesn't send it anywhere.

Also there are several projects underway which are intended to simplify, modernize and unify the Linux desktop. They are NetworkManager, systemd, Wayland, file system unification first proposed and implemented by Fedora, and others. Unfortunately no one is working towards stabilizing Linux, so the only alternative to Windows in the Linux world is Red Hat Enterprise Linux and its derivative (CentOS).

Many top tier 3D game engines now support Linux natively (with [reservations](http://itvision.altervista.org/why.linux.is.not.ready.for.the.desktop.current.html#comment-2922521418 "Alex Barringer: shimmed libraries")): [CryEngine](http://cryengine.com/news/update-from-the-team-cryengine-381-is-here-adding-opengl-linux-and-oculus-rift-support), [Unreal Engine 4](https://www.unrealengine.com/blog/unreal-engine-4-and-linux), [Unity Engine](https://unity3d.com/unity/multiplatform), [Source Engine 2.0](https://steamdb.info/blog/source2-announcement/) and others.

Valve Software released Steam for Linux (alas, it only [works well](https://wiki.archlinux.org/index.php/Steam#Steam_runtime_issues) under SteamOS and it has compatibility issues with modern Linux distros) and ported the Source engine for Linux and also they developed a [Steam gaming machine](http://store.steampowered.com/livingroom/SteamOS/) which is based on Linux. Valve's efforts have resulted in a number of AAA game titles having been made available natively for Linux, e.g. Metro Last Light. Valve since then have ported a lot of their games to Linux.

NVIDIA made their drivers more compatible with bumblebee, however NVIDIA themselves don't want to support Optimus under Linux - maybe because X.org/kernel architectures are not very suitable for that. Also NVIDIA started to provide certain very limited [documentation](https://web.archive.org/web/20170222134848/http://article.gmane.org/gmane.comp.freedesktop.xorg.nouveau/14293) for their GPUs.

Linus Torvalds [believes](https://itvision.altervista.org/files/linus_on_linux_APIs.txt) Linux APIs have recently become much more stable - however I don't share his optimism ;).

Ubuntu developers listened to me and created a new unified packaging format. More on it [here](https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037074.html) and [here](https://wiki.ubuntu.com/AppDevUploadProcess). Fedora developers decided to follow Ubuntu's lead and they're contemplating making the installation of [third-party non-free software](http://lwn.net/Articles/581478/) easy and trouble free.

The Linux Foundation formed a [new initiative](http://www.linuxfoundation.org/news-media/announcements/2014/04/amazon-web-services-cisco-dell-facebook-fujitsu-google-ibm-intel) to support critical Open Source Projects.

An application level firewall named [Douane](https://github.com/Douane/) has been graciously donated to the Linux community. Thanks a lot to its author!

Starting March 2017 you can watch [Netflix in Linux](https://www.theregister.co.uk/2017/03/22/netflix_on_linux/).

In 2018 thanks to the [DXVK](https://github.com/doitsujin/dxvk) project Linux
gamers are now able to run DirectX 11 Windows games on Linux - Wine's own implementation is severly lacking and will probably be replaced with DXVK.

In August 2018 Valve released [Proton for Steam](https://steamcommunity.com/games/221410#announcements/detail/1696055855739350561): this compatibility layer based on Wine, allows you to run native Windows games from the Steam catalogue in Linux without using any tricks with almost native speed. Its only drawback is that it requires a modern enough GPU which supports Vulkan.

More and more games are now coded using the [Vulkan API](https://en.wikipedia.org/wiki/Vulkan_\(API\)#Games) and they work just fine under Linux.

**Rant**

Sometimes I have reasons to say that indeed [Linux f*cking sucks shit](https://itvision.altervista.org/files/20160313-linux-sucks.txt) and I do hate it. _"I'm a developer - I know better how users want to use their software and systems"_ , says the average Linux developer. The end result is that most innovations draw universal anger and loathing - Gnome and KDE are the perfect examples of this tendency of screwing Linux users.

Linux has a tendency to mess with your data. Over the past several years there have been found at least three critical errors which led to data loss. I'm sorry to say that but that's utterly unacceptable. Also ext4fs sees a scary number of changes in every kernel release.

There are two different camps in regard to the intrinsic security of open and closed source applications. My stance is quite clear: Linux security leaves a lot to be desired. There are no code analyzers/antiviruses so you have no way to check if a certain application, which is published as a source code or binaries, is safe to use. Also time and again we've seen that open source projects are hardly reviewed/scrutinized at all which also means that an attacker can send a patch to Linus Torvalds and add a backdoor to the Linux kernel.

Critical bugs which make it impossible to use your hardware/software in Linux stay open for years! I reported the fact that my webcam is broken (completely
black output under certain video modes) [in 2013(!!)](https://bugzilla.kernel.org/show_bug.cgi?id=67551). This webcam is one of the most popular - no one bats an eye. For my new Skylake laptop I filed eight bug reports and seven of them remain open. Six of them have received no response at all. Nil. No one gives a damn.

True inter-distro compatibility? "WTF are you talking about?", ask Linux distro developers. Debian dropped LSB support in 2015. Recently Ubuntu developers decided to make it possible to [run new software in old distros](https://insights.ubuntu.com/2016/04/13/snaps-for-classic-ubuntu/) by using the [SNAPPY packaging format](https://developer.ubuntu.com/en/snappy/) which is basically an application emulation layer. Wow. Effing great. I mean it's great such a thing has been finally implemented but it's the wrong way, guys!

Font problems: in case you've reached this page and you still want good/best/top/free fonts for Linux, download them [from here](https://itvision.altervista.org/). It seems like many people come to this website looking for the [best desktop linux distro in 2020](https://itvision.altervista.org/best-linux-distro-this-year.html).


### Solving Linux

A lot of people wonder if Linux can be "solved", i.e. if there's anything that might be done to make Linux a real alternative to Windows and Mac OS X on the desktop. I have to admit that this will be a tall order and at least two well-known companies have already failed: the most recent example is a company from Africa, Ubuntu, and you might be surprised to know that Corel also tried at the beginning of the 21'st century (google for Corel Linux).

Without further ado let's describe the process:

At first, you have to have very deep pockets: we are talking about at least a billion USD in cash for the first five years. When you have that kind of money you create a Linux company.

Then you hire at least 90% of open source developers. You'll have to poach quite a lot of them from RedHat/Intel/Ubuntu/etc., including Linus Torvalds.

Then you start developing a Linux platform while sticking to these principles (also outlined [here](https://itvision.altervista.org/why.linux.is.not.ready.for.the.desktop.current.html#comment-3212058157) and [here](https://itvision.altervista.org/why.linux.is.not.ready.for.the.desktop.current.html#comment-2791751797)):

![The Linux distors zoo. Credit: MuseScore \(CC BY 2.0\)](Main%20Linux%20problems%20on%20the%20desktop,%202020%20edition%20or%20why%20Linux%20sucks_files/16793281720_49418bc05d.jpg)

  * Implement a stringent QA/QC process.
  * Closely work with IHVs/ISVs while listening to what they want.
  * Create an extensible [base platform](https://gitlab.com/probono/platformissues/blob/master/README.md) (IDE/libraries/kernel/etc.) with a strict set of APIs/ABIs which are adhered to for at least five to ten years.
  * Create a universal packaging format for bundling software which supports signatures, weak dependencies, isolation (aka sandboxing/virtualization), clean uninstallation and standard APIs to make it possible to integrate an application with your DE.
  * Create an open application store where applications and libraries could be published and sold. This store must be integrated with GitHub or any other development platform to make it possible to fetch application sources, file bug reports and request new features.
  * Certain Linux subsystems must be abandoned/reworked/created from the ground up:   
• Audio (ALSA/PulseAudio);
• Security model;
• The X.org server (IMO, Wayland is not the right solution);
• Linux kernel must gain microkernel abilities (safe drivers reloading in case of their crash);
• Font rendering;
• Hardware accelerated video encoding/decoding;  
• Window manager [(?)](https://en.wikipedia.org/wiki/Window_manager);
• Common extensible controls for file open/save as dialogs, window title bars, system tray, etc.;
• A full set of rich APIs for creating games;
• Simple encrypted local file sharing (akin to CIFS) and many others.

  * Other distros may actually exist but must contain all the defaults this _Linux One_ distro sets by default: libraries (APIs), sound system, graphical server, desktop environment, etc.



### Windows 10 vs. Linux

If you or your company are seriously thinking about the ramifications of installing [Windows 10](https://itvision.altervista.org/why-windows-10-sucks.html) and you're pretty scared of the prospects of running the OS which invades your privacy and deprives you of the control of its crucial features (for instance you cannot _officially_ disable telemetry, windows updates, cortana or windows defender) then I guess you're asking yourself a question: what should we do?

First of all, if you're running Windows 8.1 you're safe at least until [year 2023](http://windows.microsoft.com/en-us/windows/lifecycle). I would **not** recommend leaving these OS'es because I'm quite sure they work just fine for you and you have almost zero issues with them, specially if you're a large company and your workstations are locked down so there's no point in migrating to something new and untested just yet.

At the same time if you're buying and deploying new workstations you might consider [installing Linux](https://itvision.altervista.org/best-linux-distro-this-year.html). By doing so you'll be helping the open source community by increasing the userbase and possibly finding, reporting and even eliminating bugs in case you have software developers in your organization. Of course, you might want to run applications which have no equivalents under Linux. In this case you have two options: you may either run Windows as a virtual machine or you may try using [Wine](https://www.winehq.org/). Wine is very powerful software which allows you to run Windows applications under Linux at near native speed (sometimes even faster).

© 2009-2020 Artem S. Tashkinov. Last revised: August 9, 2020. The most current version can be found [here](https://itvision.altervista.org/why.linux.is.not.ready.for.the.desktop.current.html).



Additions to and _well-grounded critiques_ of this list are welcomed. Mind that irrational comments lacking substance or factual information might be removed. Anonymous comments are ~~**pre-moderated**~~ disabled. I'm tired of anonymous haters who have nothing to say. Besides, Disqus sports authentification via Google/Twitter/Facebook and if you don't have any of these accounts then I'm sorry for your seclusion. You might as well not exist at all.

This ~~is~~ isn't a work in progress any longer (however I update this list from time to time). There is nothing serious left that I can think of.

Please, excuse me for grammatical and spelling errors. I'm not a native English speaker. ;-) It'd be amazing if someone proof read this article and sent me the result.

In case there are dead links in this article, you can find their live versions via [WayBack Machine](https://archive.org/web/ "Internet Archive"), [archive.is](https://archive.is/ "Internet Archive") or by Googling respective page titles.

About the author: _Artem S. Tashkinov is an avid supporter of the Open Source movement and Open Source projects. He has helped to resolve numerous bugs across many open source projects such as the
[Linux](https://git.kernel.org/cgit/linux/kernel/git/torvalds/linux.git/log/?qt=grep&q=tashkinov) kernel, [KDE](https://bugs.kde.org/buglist.cgi?email1=aros%40gmx.com&emailtype1=exact&emailassigned_to1=1&emailreporter1=1), [Wine](http://bugs.winehq.org/buglist.cgi?email1=aros%40gmx.com&emailtype1=exact&emailreporter1=1), [GCC](https://gcc.gnu.org/bugzilla/buglist.cgi?email2=aros%40gmx.com&emailreporter2=1&emailtype2=substring&order=Importance&query_format=advanced), [Midnight Commander](https://www.midnight-commander.org/query?reporter=birdie), X.org and many others. He's been using Linux exclusively since 1999._

I'm searching for a permanent job (with relocation) as a systems administrator in Down Under; you can download my stripped (for security reasons) CV [here](https://itvision.altervista.org/files/cv.zip).

© 2009-2020 Artem S. Tashkinov \- all rights reserved. You can reproduce any part of this text verbatim, but you **must** retain the authorship **and** provide a link to this document. The archive of this page can be found [here](http://web.archive.org/web/*/http://itvision.altervista.org/why.linux.is.not.ready.for.the.desktop.current.html).


You can read the previous [old archived version here](https://itvision.altervista.org/why.linux.is.not.ready.for.the.desktop.html).

  * [Windows rot]: Significant slow down caused by the installation of new software and disk fragmentation
    *[GUI]: Graphical user interface
    *[DEs]: Desktop Environment, e.g. KDE or Gnome
    *[PITA]: pain in the ass
    *[GCC]: GNU compilers collection - the main compiler for Linux
    *[LTS]: Long term support (distros  like Debian, Ubuntu LTS, RHEL and its derivatives, SLES)
    *[Enterprise level]: *Not* directly related to Linux on the desktop, but still *immensely* important
    *[ rapid]: One can even say 'rabid'
    *[Linus Torvalds]: The Linux creator

