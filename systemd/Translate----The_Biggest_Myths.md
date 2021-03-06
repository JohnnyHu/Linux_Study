# The Biggest Myths #
*POSTED ON SA 26 JANUAR 2013*

Since we first proposed [systemd](https://www.freedesktop.org/wiki/Software/systemd/) for inclusion in the distributions it has been frequently discussed in many forums, mailing lists and conferences. In these discussions one can often hear certain myths about systemd, that are repeated over and over again, but certainly don't gain any truth by constant repetition. Let's take the time to debunk a few of them:

# Lennart谈对于systemd认知的最大误区 #
*[原文](http://0pointer.de/blog/projects/the-biggest-myths.html)于2013年1月26日发布*

从我们首次提出将[systemd](https://www.freedesktop.org/wiki/Software/systemd/)纳入发行版以来，它就在诸多论坛，邮件列表和会议上已经进行了无数次的讨论。在这些讨论中，经常可以听到systemd的某些断言，它们被重复了一次又一次，但可以肯定的是不会通过这些不间断重复的断言就获得任何的事实真相， 让我们花点时间来揭穿其中的一些：


#### 1.Myth:systemd is monolithic. ####
> If you build systemd with all configuration options enabled you will build 69 individual binaries. These binaries all serve different tasks, and are neatly separated for a number of reasons. For example, we designed systemd with security in mind, hence most daemons run at minimal privileges (using kernel capabilities, for example) and are responsible for very specific tasks only, to minimize their security surface and impact. Also, systemd parallelizes the boot more than any prior solution. This parallization happens by running more processes in parallel. Thus it is essential that systemd is nicely split up into many binaries and thus processes. In fact, many of these binaries[1] are separated out so nicely, that they are very useful outside of systemd, too.
> 
> A package involving 69 individual binaries can hardly be called monolithic. What is different from prior solutions however, is that we ship more components in a single tarball, and maintain them upstream in a single repository with a unified release cycle.

#### 误区1： systemd是庞大的单一体 ####
> 如果构建systemd时启用所有的配置选项，会得到69个独立的二进制文件。由于多方面的原因这些文件被清楚的划分，以执行不同的任务。比如，在设计systemd时我们就将安全性考虑其中，因此，大部分的守护进程(daemons)是以最小权限运行的(比如，使用内核的功能)，和只负责非常具体的功能，以最小化他们的安全层面和影响。此外，systemd在系统启动时以并行的方式boot而非之前以优先级方式。这个并行化方式通过并行运行多个进程来实现。 因此，systemd被很好的分解成多个二进制文件及多个进程就很重要。事实上，这些二进制[1]的文件被很好的分离出来，以至于他们在除了systemd之外的其他地方也变得非常有用。
> 
> 一个包含了69个独立二进制的软件包很难认为是单一的。然而，不同于以往的优先级解决方案，我们将更多的组件置入到单独的tarball中。在统一的发布周期内，在上游维护他们在一个单一的代码库中。


#### 2.Myth: systemd is about speed. ####
> Yes, systemd is fast (A pretty complete userspace boot-up in ~900ms, anyone?), but that's primarily just a side-effect of doing things right. In fact, we never really sat down and optimized the last tiny bit of performance out of systemd. Instead, we actually frequently knowingly picked the slightly slower code paths in order to keep the code more readable. This doesn't mean being fast was irrelevant for us, but reducing systemd to its speed is certainly quite a misconception, since that is certainly not anywhere near the top of our list of goals.

#### 误区2：关于systemd的速度 ####
> 是的， systemd是非常快的(一个相对完整的用户空间启动引导时间在900毫秒内，难道这不快吗？)， 但它的首要目标是做正确事，速度快只是一个自然而然的结果。我们从没有专门优化过systemd的一点点性能。相反，为了保持代码的可读性，我们有意识的选择代码性能不是最高的编码方式。这并不意味着速度快对我们来说无关紧要，但就此认为我们有意识降低systemd的速度则是一个相当大的误解，只不过它们不在我们目标列表的最顶层罢了。
l

#### 3.Myth: systemd's fast boot-up is irrelevant for servers. ####
> That is just completely not true. Many administrators actually are keen on reduced downtimes during maintenance windows. In High Availability setups it's kinda nice if the failed machine comes back up really fast. In cloud setups with a large number of VMs or containers the price of slow boots multiplies with the number of instances. Spending minutes of CPU and IO on really slow boots of hundreds of VMs or containers reduces your system's density drastically, heck, it even costs you more energy. Slow boots can be quite financially expensive. Then, fast booting of containers allows you to implement a logic such as [socket activated containers](http://0pointer.de/blog/projects/socket-activated-containers.html), allowing you to drastically increase the density of your cloud system.
> 
> Of course, in many server setups boot-up is indeed irrelevant, but systemd is supposed to cover the whole range. And yes, I am aware that often it is the server firmware that costs the most time at boot-up, and the OS anyways fast compared to that, but well, systemd is still supposed to cover the whole range (see above...), and no, not all servers have such bad firmware, and certainly not VMs and containers, which are servers of a kind, too.[2]

#### 误区3：对服务器来说systemd的快速启动是无关紧要的 ####
> 这肯定是不正确的。实际上，许多管理人员都倾向于缩短维护期的停机时间。在高可用的情况下，启动发生故障的机器肯定是越快越好。在以时间计费的云设置中，慢启动的代价与云中实际的虚拟机或容器的的数量成正比。在成百上千个虚拟中，由于慢启动所花费的CPU和IO的时间，大大降低了系统的密度，要命的是，它会花费你更多的时间和精力。在云系统中，从经济层面来讲，慢启动代价十分昂贵。而快启动的容器则允许你实现诸如激活socket等的逻辑，从而可以大幅度提高你系统的密度。
>
> 当然，在许多服务器设置中，开机启动确实没那么重要，但systemd确保涵盖更广的范围。是的，我知道无论操作启动启动多快，服务器的硬件总是在开机时花费的时间最多。但是，systemd仍然应该覆盖整个的范围(如上所述....). 因为并不是所有的服务器硬件都那么差，也并不是所有的服务器都是虚拟机和容器。
 

#### 4.Myth: systemd is incompatible with shell scripts. ####
> This is entirely bogus. We just don't use them for the boot process, because we believe they aren't the best tool for that specific purpose, but that doesn't mean systemd was incompatible with them. You can easily run shell scripts as systemd services, heck, you can run scripts written in any language as systemd services, systemd doesn't care the slightest bit what's inside your executable. Moreover, we heavily use shell scripts for our own purposes, for installing, building, testing systemd. And you can stick your scripts in the early boot process, use them for normal services, you can run them at latest shutdown, there are practically no limits.

#### 误区4：systemd同shell脚本不兼容 ####
> 这简直是胡扯，我们只是在开机进程中不用它而已，对systemd来说，我们相信它不是最好的工具，但这并不意味着不兼容它们。你可以运行shell脚本作为systmed的服务，你甚至可以运行用任何语言写的脚本服务，systemd并不在乎你的可执行文件里面有什么。另外，我们在安装，构建和测试systemd等步骤时也大量的使用脚本。所以，你可以自由的使用脚本在早期的启动进程中，将它们用于正常的服务，或者用在最后的关机中，这实际上是没有任何的限制的。


#### 5.Myth: systemd is difficult. ####
> This also is entire non-sense. A systemd platform is actually much simpler than traditional Linuxes because it unifies system objects and their dependencies as systemd units. The configuration file language is very simple, and redundant configuration files we got rid of. We provide uniform tools for much of the configuration of the system. The system is much less conglomerate than traditional Linuxes are. We also have pretty comprehensive documentation ([all linked from the homepage](http://www.freedesktop.org/wiki/Software/systemd)) about pretty much every detail of systemd, and this not only covers admin/user-facing interfaces, but also developer APIs.
> 
> systemd certainly comes with a learning curve. Everything does. However, we like to believe that it is actually simpler to understand systemd than a Shell-based boot for most people. Surprised we say that? Well, as it turns out, Shell is not a pretty language to learn, it's syntax is arcane and complex. systemd unit files are substantially easier to understand, they do not expose a programming language, but are simple and declarative by nature. That all said, if you are experienced in shell, then yes, adopting systemd will take a bit of learning.
> 
> To make learning easy we tried hard to provide the maximum compatibility to previous solutions. But not only that, on many distributions you'll find that some of the traditional tools will now even tell you -- while executing what you are asking for -- how you could do it with the newer tools instead, in a possibly nicer way.
> 
> Anyway, the take-away is probably that systemd is probably as simple as such a system can be, and that we try hard to make it easy to learn. But yes, if you know sysvinit then adopting systemd will require a bit learning, but quite frankly if you mastered sysvinit, then systemd should be easy for you.

#### 误区5. systemd很难 ####
> 还真不能这么说。有systemd平台的Linux实际上比传统的Linuxes更为简单，因为它统一将系统对象和它的依赖作为systemd单元。它的配置文件语言非常简单，我们摒弃了那些冗余的配置。我们为系统的大部分工具提供了统一的工具。系统也比传统的Linux要小的多。我们也提供了关于systemd的每一个细节([所有连接主页](http://www.freedesktop.org/wiki/Software/systemd))的非常全面的文档， 这不仅涵盖了管理员/用户面的接口，也有面向开发者的API。
>
> systemd肯定有一个学习曲线, 任何事情都如此。然而，我们也相信对于大部分人来说，理解systemd实际上比理解基于shell脚本的启动更为简单。很吃惊是吧？ 嗯，由于已经证实，其实Shell是一门不太好掌握的语言，它的语法晦涩难懂且复杂。systemd unit文件基本上更容易去理解，他们不依赖与一个特定的编程语言，其本质上是简单的和声明性的。这一切都表明，如果你在shell方面有经验，采用systemd确实需要花费一点时间去学习。
>
> 为了使学习systemd更为容易，我们尽力去兼容旧有的解决方案。不仅如此，在许多分发版上，你会发现当你在执行请求时，一些传统的工具甚至会告诉你，怎样用一个新的工具以一种更好的方式去替代旧有的工具。
>
> 无论如何，这个系统足够简单，我们尽力使它易于学习。 是的，如果你知道sysinit，那么你需要花一点时间来掌握systemd，但坦率的来说,如果你掌握了sysinit，那么学习systemd也是更容易的。


#### 6.Myth: systemd is not modular. ####
> Not true at all. At compile time you have a number of configure switches to select what you want to build, and what not. And [we document](http://freedesktop.org/wiki/Software/systemd/MinimalBuilds) how you can select in even more detail what you need, going beyond our configure switches.
> 
> This modularity is not totally unlike the one of the Linux kernel, where you can select many features individually at compile time. If the kernel is modular enough for you then systemd should be pretty close, too.

#### 误区6：systemd是非模块化的 ####
> 当然不是这样的。在编译期间，有许多配置选项开关供你选择哪些需要build，哪些不需要。并且，我们的[文档](http://freedesktop.org/wiki/Software/systemd/MinimalBuilds)也记录了比配置选项开关更多的细节，你可以找到你所需的。
> 
> 这种模块化方式与kernel的模块化方式完全不同，systemd在编译时可以单独选择诸多功能，如果你认为kernel足够模块化，那么systemd也应该非常接近了。


#### 7.Myth: systemd is only for desktops. ####
> That is certainly not true. With systemd we try to cover pretty much the same range as Linux itself does. While we care for desktop uses, we also care pretty much the same way for server uses, and embedded uses as well. You can bet that Red Hat wouldn't make it a core piece of RHEL7 if it wasn't the best option for managing services on servers.
> 
> People from numerous companies work on systemd. Car manufactureres build it into cars, Red Hat uses it for a server operating system, and GNOME uses many of its interfaces for improving the desktop. You find it in toys, in space telescopes, and in wind turbines.
> 
> Most features I most recently worked on are probably relevant primarily on servers, such as [container support](http://0pointer.de/blog/projects/socket-activated-containers.html), [resource management](http://0pointer.de/blog/projects/resources.html) or the [security features](http://0pointer.de/blog/projects/security.html). We cover desktop systems pretty well already, and there are number of companies doing systemd development for embedded, some even offer consulting services in it.

#### 误区7：systemd仅适用于桌面版系统 ####
> 这当然也不是真的，我们尽力使systemd的覆盖范围同Linux本身的范围一样广。虽然我们关注桌面版linux的使用，当我们也同样方式关心其在Linux服务器及其嵌入式方面的使用。你能够想到，如果它在服务管理方面不是最佳的管理服务程序，Red Hat不会把它作为RHEL7的核心模块。
> 
> 来自众多公司的人员在systemd上工作，汽车提供商把它放进汽车系统中， Ret Hat在服务器操作系统总使用它，GNOME使用它的许多接口去改善桌面程序，甚至你可以在玩具，太空望远镜和风力涡轮机中找到它。
>
> 我最近的工作中的大部分功能可能大部分主要用于服务器上，比如：[容器支持](http://0pointer.de/blog/projects/socket-activated-containers.html)、[资源管理](http://0pointer.de/blog/projects/resources.html)和[安全功能](http://0pointer.de/blog/projects/security.html)。我们已经很好地覆盖了桌面系统，而且有很多公司使用systedmd开发他们的嵌入式系统，有些甚至提供咨询服务。

#### 8.Myth: systemd was created as result of the NIH syndrome. ####
> This is not true. Before we began working on systemd we were pushing for Canonical's Upstart to be widely adopted (and Fedora/RHEL used it too for a while). However, we eventually came to the conclusion that its design was inherently flawed at its core (at least in our eyes: most fundamentally, it leaves dependency management to the admin/developer, instead of solving this hard problem in code), and if something's wrong in the core you better replace it, rather than fix it. This was hardly the only reason though, other things that came into play, such as the licensing/contribution agreement mess around it. NIH wasn't one of the reasons, though...[3]

#### 误区8：systemd是NIH综合征的结果。 ####
> 不是这样的，在我们开始开发systemd之前，我们曾推动Canonical的Upstart被广泛采用（Fedora/RHEL也已经使用了它一段时间了）,然而，我们最终得出的结论是，它的设计本质上是有缺陷的（至少在我们的眼中： 它将依赖管理留给admin/developer,而不是在代码中解决这个难题）, 其如果在core中出错，你最好是替换它，而不是去修复它。这并不是唯一的原因，其他一些是围绕它的许可协议的混乱等等。 NIH不是唯一的理由，尽管...[3]


#### 9.Myth: systemd is a freedesktop.org project. ####
> Well, systemd is certainly hosted at fdo, but freedesktop.org is little else but a repository for code and documentation. Pretty much any coder can request a repository there and dump his stuff there (as long as it's somewhat relevant for the infrastructure of free systems). There's no cabal involved, no "standardization" scheme, no project vetting, nothing. It's just a nice, free, reliable place to have your repository. In that regard it's a bit like SourceForge, github, kernel.org, just not commercial and without over-the-top requirements, and hence a good place to keep our stuff.
> 
> So yes, we host our stuff at fdo, but the implied assumption of this myth in that there was a group of people who meet and then agree on how the future free systems look like, is entirely bogus.

#### 误区9： systemd是a freedesktop.org的一个项目 ####
>嗯，systemd是托管在fdo, 但freedesktop.org也仅仅是托管代码的库和文档而已，几乎任何的coder都可以在那里请求一个代码仓库，用于存储他的东西(只要它是与自由系统架构相关的一些东西)。没有涉及任何的阴谋，没有任何"标准化"的计划，没有项目审查，都没有。这仅仅是一个不错的，免费其可靠的可以存储你代码库的地方。在这方面，它有点像SourceForge, github, kernel.org，只是它是非商业的，且没有过度的顶级要求，因此它是存储我们东西的一个好地方。
>
>所以，是的，我们是吧systemd的所有东西存放在了fdo上，但是这个误区成立的隐含条件是，一群人聚在一起，一致认为未来的自由系统会是怎样的，这完全是胡扯。

#### 10.Myth: systemd is not UNIX. ####
> There's certainly some truth in that. systemd's sources do not contain a single line of code originating from original UNIX. However, we derive inspiration from UNIX, and thus there's a ton of UNIX in systemd. For example, the UNIX idea of "everything is a file" finds reflection in that in systemd all services are exposed at runtime in a kernel file system, the cgroupfs. Then, one of the original features of UNIX was multi-seat support, based on built-in terminal support. Text terminals are hardly the state of the art how you interface with your computer these days however. With systemd we brought native [multi-seat](http://0pointer.de/blog/projects/multi-seat.html) support back, but this time with full support for today's hardware, covering graphics, mice, audio, webcams and more, and all that fully automatic, hotplug-capable and without configuration. In fact the design of systemd as a suite of integrated tools that each have their individual purposes but when used together are more than just the sum of the parts, that's pretty much at the core of UNIX philosophy. Then, the way our project is handled (i.e. maintaining much of the core OS in a single git repository) is much closer to the BSD model (which is a true UNIX, unlike Linux) of doing things (where most of the core OS is kept in a single CVS/SVN repository) than things on Linux ever were.
> 
> Ultimately, UNIX is something different for everybody. For us systemd maintainers it is something we derive inspiration from. For others it is a religion, and much like the other world religions there are different readings and understandings of it. Some define UNIX based on specific pieces of code heritage, others see it just as a set of ideas, others as a set of commands or APIs, and even others as a definition of behaviours. Of course, it is impossible to ever make all these people happy.
> 
> Ultimately the question whether something is UNIX or not matters very little. Being technically excellent is hardly exclusive to UNIX. For us, UNIX is a major influence (heck, the biggest one), but we also have other influences. Hence in some areas systemd will be very UNIXy, and in others a little bit less.

#### 误区10：systemd不是Unix的 ####
> 这是有一定道理的。systemd的源码没有一行是从原始的UNIX总获取的。然而，我们从UNIX中获取灵感，因此systemd中也有大量的UNIX。比如，UNIX的思想"一起皆文件"映射到systemd中就是，所有的服务在运行时都置于linux内核文件系统cgroupfs中。UNIX的原始特征之一是基于内建终端的多席位支持，然而，现今文本终端已经不是与计算机进行接口的最流行的方式了，对于systemd我们带来了原生的[多席位](http://0pointer.de/blog/projects/multi-seat.html)支持，且这一次全面支持今天的硬件，覆盖图形，鼠标，音频，网络摄像头等，以及所有这些全自动，热插拔功能，无需配置。事实上，systemd作为一套集成工具的设计，每个工具都有其特定的目的，但是如果一起使用，就不仅仅是各个部分的总和，它很好的展现了UNIX理念的核心。因此我们项目的处理方式(比如：维护诸多的OS的内核在单一的git仓库中)相比Linux曾经的方式来说更接近BSD模型（这是一个真正的UNIX，不像Linux）。
> 
> 最终，UNIX对每个人来说都是不同的。对于我们systemd的维护者来说确实是有一些灵感来自它，当这是一个仁者见仁，智者见智的问题。 有些人基于Unix特定的代码遗产来定义它，有些人将它视为一种思想，而另一些人则认为它是命令集和API的集合，甚至有人将其视为一种行为的定义。当然，让所有这些满意是不可能的。
> 
> 对于最终的问题它是不是UNIX的其实一点也不重要。技术上的优秀对于UNIX来说并不是专有的。对于我们来说，UNIX是一个主要的影响（最大的影响），但是我们也有其他的影响。 因此，systemd在一些地方会很UNIXy，而在其他地方就有点少。


#### 11.Myth: systemd is complex. ####
> There's certainly some truth in that. Modern computers are complex beasts, and the OS running on it will hence have to be complex too. However, systemd is certainly not more complex than prior implementations of the same components. Much rather, it's simpler, and has less redundancy (see above). Moreover, building a simple OS based on systemd will involve much fewer packages than a traditional Linux did. Fewer packages makes it easier to build your system, gets rid of interdependencies and of much of the different behaviour of every component involved.

#### 误区11：systemd很复杂 ####
> 这是有一定道理的。现代计算机就是复杂的怪兽，也就不奇怪运行在它上面的操作系统复杂了。但systemd没有比它们比之前同样功能的组件更复杂。确切的说，它更简单，少冗余(如上所述)。此外，构建一个基本systemd的简单的操作系统，将比之前传统的Linux包含更少的包。更少的包意味着构建系统更简单，减少了依赖和避免陷入不同组件有不同行为的漩涡。


#### 12.Myth: systemd is bloated. ####
> Well, bloated certainly has many different definitions. But in most definitions systemd is probably the opposite of bloat. Since systemd components share a common code base, they tend to share much more code for common code paths. Here's an example: in a traditional Linux setup, sysvinit, start-stop-daemon, inetd, cron, dbus, all implemented a scheme to execute processes with various configuration options in a certain, hopefully clean environment. On systemd the code paths for all of this, for the configuration parsing, as well as the actual execution is shared. This means less code, less place for mistakes, less memory and cache pressure, and is thus a very good thing. And as a side-effect you actually get a ton more functionality for it...
> 
> As mentioned above, systemd is also pretty modular. You can choose at build time which components you need, and which you don't need. People can hence specifically choose the level of "bloat" they want.
> 
> When you build systemd, it only requires three dependencies: glibc, libcap and dbus. That's it. It can make use of more dependencies, but these are entirely optional.
> 
> So, yeah, whichever way you look at it, it's really not bloated.

#### 误区12： systemd是臃肿的 ####
> 嗯，臃肿有许多不同的定义。在大多数定义下里systemd可能臃肿的反面。由于systemd的组件共享一个共同的代码库，他们倾向于为共同的代码路径共享更多的代码。这儿有个例子：在传统的Linux设置中，sysvinit, start-stop-daemon, inetd, cron, dbus都希望在一个干净的环境中实现了一个方案来执行具有各种配置选项的进程。 在systemd中，所有的代码路径，配置解析以及实际执行都是共享的。这意味着更少的代码，更少的错误，更少的内存和缓存压力，因此是一件非常好的事情。 而另一方面，你实际上得到了更多的功能。
> 
> 正如上面提到的，systemd是相当的模块化的。你可以在编译期间选项你需要的和不需要的。因此，人们可以专门选择他们想要的“臃肿”等级。
> 
> 当你构建systemd时，唯一需要的三个依赖就是：glibc， libcap和dbus,仅此而已。它可以利用更多的依赖，但是这些都是可选的。
>
> 所以，无论从哪方面来看它都不会臃肿。

#### 13.Myth: systemd being Linux-only is not nice to the BSDs. ####
> Completely wrong. The BSD folks are pretty much uninterested in systemd. If systemd was portable, this would change nothing, they still wouldn't adopt it. And the same is true for the other Unixes in the world. Solaris has SMF, BSD has their own "rc" system, and they always maintained it separately from Linux. The init system is very close to the core of the entire OS. And these other operating systems hence define themselves among other things by their core userspace. The assumption that they'd adopt our core userspace if we just made it portable, is completely without any foundation.

#### > 误区13：systemd是仅限于Linux的，对于BSD来说并不友好。 ####
> 完全错误，BSD的拥趸对systemd完全不敢兴趣。即使systemd是可移植的，这仍然不会有任何有何改变，他们仍然不会采用它。在其他Unix世界中也一样，Solaris有SMF，BSD有它自己的“RC”系统，且它们都是和Linux分开维护的。init系统非常靠近整个OS的内核。而这些其他的操作系统因此也是由它们的核心用户空间定义的。 假设他们将我们的核心用户空间，这种假设建立如果我们使得systemd是可移植的，它们就采用我们的核心用户空间，这完全是没有任何基础。


#### 14.Myth: systemd being Linux-only makes it impossible for Debian to adopt it as default. ####
> Debian supports non-Linux kernels in their distribution. systemd won't run on those. Is that a problem though, and should that hinder them to adopt system as default? Not really. The folks who ported Debian to these other kernels were willing to invest time in a massive porting effort, they set up test and build systems, and patched and built numerous packages for their goal. The maintainance of both a systemd unit file and a classic init script for the packaged services is a negligable amount of work compared to that, especially since those scripts more often than not exist already.

#### 误区14：systemd是仅限于Linux，这使得Debian无法将其作为默认设置。 ####
> Debian在它们的分发版中支持非Linux的内核。systemd不能够在这些上面运行。这里的问题就是，是否就应该应该阻碍他们采用系统的默认？并不是这样的。将Debian移植到其他内核的人们愿意投入大量时间进行大量的移植工作，他们建立了测试和构建系统，并为他们的目标修补和构建了大量的软件包。对于打包服务来说，systemd单元文件和经典的init脚本之间的维护与此相比是一个可以忽略的工作量，特别是因为这些脚本已经存在了。


#### 15.Myth: systemd could be ported to other kernels if its maintainers just wanted to. ####
> That is simply not true. Porting systemd to other kernel is not feasible. We just use too many Linux-specific interfaces. For a few one might find replacements on other kernels, some features one might want to turn off, but for most this is nor really possible. Here's a small, very incomprehensive list: *cgroups, fanotify, umount2(), /proc/self/mountinfo* (including notification), */dev/swaps* (same), *udev, netlink*, the structure of */sys, /proc/$PID/comm, /proc/$PID/cmdline, /proc/$PID/loginuid, /proc/$PID/stat, /proc/$PID/session, /proc/$PID/exe, /proc/$PID/fd, tmpfs, devtmpfs,* capabilities, namespaces of all kinds, various *prctl()s*, numerous *ioctls*, the *mount()* system call and its semantics, *selinux, audit, inotify, statfs, O_DIRECTORY, O_NOATIME, /proc/$PID/root, waitid(), SCM_CREDENTIALS, SCM_RIGHTS, mkostemp(), /dev/input, ...*
> 
> And no, if you look at this list and pick out the few where you can think of obvious counterparts on other kernels, then think again, and look at the others you didn't pick, and the complexity of replacing them.


#### 误区15： 如果systemd的维护者愿意，它就能够移植到其他内核中 ####
> 这根本不是真的。将systemd移植到其他内核是不可行的。我们使用了太多Linux专有的接口。少量的一些可以在其他内核中找到替代者，一些功能可能要关闭，但大多数是不可能的。这里有一个小而不完整的清单： *cgroups, fanotify, umount2(), /proc/self/mountinfo* (包含通知), */dev/swaps* (same), *udev, netlink*, the structure of */sys, /proc/$PID/comm, /proc/$PID/cmdline, /proc/$PID/loginuid, /proc/$PID/stat, /proc/$PID/session, /proc/$PID/exe, /proc/$PID/fd, tmpfs, devtmpfs,* capabilities, 各式种类的命名空间, 多种 *prctl()s*, 众多的 *ioctls*, *mount()* 系统调用和它的语义, *selinux, audit, inotify, statfs, O_DIRECTORY, O_NOATIME, /proc/$PID/root, waitid(), SCM_CREDENTIALS, SCM_RIGHTS, mkostemp(), /dev/input, ...*等等。


#### 16.Myth: systemd is not portable for no reason. ####
> Non-sense! We use the Linux-specific functionality because we need it to implement what we want. Linux has so many features that UNIX/POSIX didn't have, and we want to empower the user with them. These features are incredibly useful, but only if they are actually exposed in a friendly way to the user, and that's what we do with systemd.

#### 误区16：systemd无法移植没有任何缘由 ####
> 废话！ 我们使用Linux专有的功能是因为我们需要它去实现我们想要的。Linux有许多功能是UNIX/POSIX没有的，我们希望把它呈现给用户。但只有当这些功能以友好的方式呈现给用户时，才会发觉它的优异性，这也正是systemd所做的。


#### 17.Myth: systemd uses binary configuration files. ####
> No idea who came up with this crazy myth, but it's absolutely not true. systemd is configured pretty much exclusively via simple text files. A few settings you can also alter with the kernel command line and via environment variables. There's nothing binary in its configuration (not even XML). Just plain, simple, easy-to-read text files.

#### 误区17：systemd使用二进制的配置文件。 ####
> 不知道谁创造了这个疯狂的谣言，这绝对不是真的。systemd几乎完全通过简单的文本文件进行配置。一些配置你可以选择使用内核命令行或者环境变量。这里没有二进制的配置（甚至没有XML）。 只是普通的，简单的，易于阅读的文本文件。


#### 18.Myth: systemd is a feature creep. ####
> Well, systemd certainly covers more ground that it used to. It's not just an init system anymore, but the basic userspace building block to build an OS from, but we carefully make sure to keep most of the features optional. You can turn a lot off at compile time, and even more at runtime. Thus you can choose freely how much feature creeping you want.

#### 误区18： systemd是一个典型的功能蔓延(feature creep) ####
*译注：功能蔓延（feature creep），有时也被称为需求蔓延（requirements creep）或范围蔓延（scope creep），它是指在发展过程中产品或设计的需求增加大大超过他们原来预期的趋势，导致其功能不是原本计划的并且要承担产品质量或生产进度的风险。功能蔓延可能是由于客户期望功能的增加或由于开发者自身发现了改善产品的机会而导致的。为了控制功能蔓延，设计管理工具有时被提倡使用，比如需求稳定性索引（RSI）。*

> 嗯，systemd在过去的基础上，确实涵盖了更多。它不仅仅是一个init系统，而是构建系统的基本用户空间的基础构建模块。但我们确保其大部分功能都是可选的， 你可以在编译期间关掉大部分它的功能，甚至在运行期间。这样你就可以自由选择你想要的feature creeping 。

#### 19.Myth: systemd forces you to do something. ####
> systemd is not the mafia. It's Free Software, you can do with it whatever you want, and that includes not using it. That's pretty much the opposite of "forcing".

#### 误区19： systemd强迫你去做某些事 ####
systemd不是黑手党。它是自由软件，你可以选项你想要的或者不想要的。这正是"强迫"的反面。


#### 20.Myth: systemd makes it impossible to run syslog. ####
> Not true, we carefully made sure when we [introduced the journal](http://0pointer.de/blog/projects/the-journal.html) that all data is also passed on to any syslog daemon running. In fact, if something changed, then only that syslog gets more complete data now than it got before, since we now cover early boot stuff as well as STDOUT/STDERR of any system service.

#### 误区20： systemd使得运行syslog变成不可能 ####
> 这完全是误解，在我们介绍[journal](http://0pointer.de/blog/projects/the-journal.html)是已经非常小心的确保说明所有的数据也会被传到任何真在运行的syslog守护进程。事实上，如果事情发生了变化，那么现在只有syslog获得比以前更完整的数据，因为现在我们涵盖了早期boot的一些东西及任何系统服务的STDOUT/STDERR。


#### 21.Myth: systemd is incompatible. ####
> We try very hard to provide the best possible compatibility with sysvinit. In fact, the vast majority of init scripts should work just fine on systemd, unmodified. However, there actually are indeed a few incompatibilities, but we try to [document these](http://www.freedesktop.org/wiki/Software/systemd/Incompatibilities) and explain what to do about them. Ultimately every system that is not actually sysvinit itself will have a certain amount of incompatibilities with it since it will not share the exect same code paths.
> 
> It is our goal to ensure that differences between the various distributions are kept at a minimum. That means unit files usually work just fine on a different distribution than you wrote it on, which is a big improvement over classic init scripts which are very hard to write in a way that they run on multiple Linux distributions, due to numerous incompatibilities between them.

#### 误区21: systemd是不兼容的  ####
> 我们尽最大的可能性使systmed同sysvinit兼容。实际上， 绝大多数脚本不做任何修改就应该能够运行在systemd上，然而，确实有一些不兼容。但我们尽力去[文档化](http://www.freedesktop.org/wiki/Software/systemd/Incompatibilities)这些和解释它们到底是什么原因导致的。最终，实际上不是sysvinit本身的每个系统都会有一定的不兼容性，只是因为它不会共享相同的代码路径。
>
> 我们的目标是在多种发行版之间的差异保持最小化。这就意味着单元文件通常能够在不同的发行版上正常工作。这与传统的初始化脚本相比，有很大的改进。由于LInux多个发行版之间的不兼容性，让他们以统一的方式运行是非常困难的。


#### 22.Myth: systemd is not scriptable, because of its D-Bus use. ####
> Not true. Pretty much every single D-Bus interface systemd provides is also available in a command line tool, for example in [systemctl](http://www.freedesktop.org/software/systemd/man/systemctl.html), [loginctl](http://www.freedesktop.org/software/systemd/man/loginctl.html), [timedatectl](http://www.freedesktop.org/software/systemd/man/timedatectl.html), [hostnamectl](http://www.freedesktop.org/software/systemd/man/hostnamectl.html), [localectl](http://www.freedesktop.org/software/systemd/man/localectl.html) and suchlike. You can easily call these tools from shell scripts, they open up pretty much the entire API from the command line with easy-to-use commands.
> 
> That said, D-Bus actually has bindings for almost any scripting language this world knows. Even from the shell you can invoke arbitrary D-Bus methods with [dbus-send](http://dbus.freedesktop.org/doc/dbus-send.1.html) or [gdbus](http://developer.gnome.org/gio/unstable/gdbus.html). If anything, this improves scriptability due to the good support of D-Bus in the various scripting languages.

#### 误区22：由于D-Bus的使用，systemd不能编写脚本。 ####
> 不是这样的。systemd接口提供的每个D-BUS接口几乎都在可以在命令行工具中找到。比如：[systemctl](http://www.freedesktop.org/software/systemd/man/systemctl.html), [loginctl](http://www.freedesktop.org/software/systemd/man/loginctl.html), [timedatectl](http://www.freedesktop.org/software/systemd/man/timedatectl.html), [hostnamectl](http://www.freedesktop.org/software/systemd/man/hostnamectl.html), [localectl](http://www.freedesktop.org/software/systemd/man/localectl.html)等等，你也可以很容易的在脚本中调用这些工具。它们使用易于使用的命令行几乎能够打开所有的API。
> 
> 这就是说，D-Bus实际上已经绑定了大部分这个世界上知道的脚本语言。甚至在shell中你可以使用[dbus-send](http://dbus.freedesktop.org/doc/dbus-send.1.html)和[gdbus](http://developer.gnome.org/gio/unstable/gdbus.html)调用任何的D-BUS方法。由于D-BUS对各种脚本提供了很好的支持，这甚至可以改善脚本化的能力。


#### 23.Myth: systemd requires you to use some arcane configuration tools instead of allowing you to edit your configuration files directly. ####
> Not true at all. We offer some configuration tools, and using them gets you a bit of additional functionality (for example, command line completion for all settings!), but there's no need at all to use them. You can always edit the files in question directly if you wish, and that's fully supported. Of course sometimes you need to explicitly reload configuration of some daemon after editing the configuration, but that's pretty much true for most UNIX services.

#### 误区23：systemd要求你使用一些神秘的配置工具，而不是让你直接编辑你的配置文件 ####
> 这根本不是真的。我们提供了配置工具，当你使用他们的时候可以获得一些额外的功能(比如：利用命令行就完成所有配置)，但是没有必要全部都使用他们。如果你想，你当然可以直接编辑这些文件，这些都是支持的。当然，有时候你需要在编辑配置之后明确地重新加载一些守护进程的配置，但是对于大多数UNIX服务来说，情况确实如此。


#### 24.Myth: systemd is unstable and buggy. ####
> Certainly not according to our data. We have been monitoring the Fedora bug tracker (and 
> some others) closely for a long long time. The number of bugs is very low for such a central component of the OS, especially if you discount the numerous RFE bugs we track for the project. We are pretty good in keeping systemd out of the list of blocker bugs of the distribution. We have a relatively fast development cycle with mostly incremental changes to keep quality and stability high.

#### 误区24： systemd即不稳定又古怪 ####
> 当然不是根据我们的数据。我们一直在密切关注Fedorabug跟踪器（以及其他一些）。对于这样一个操作系统的核心组件来说，bug的数量是非常低的，尤其是如果你忽略我们为这个项目追踪的众多RFE bug。我们非常擅长将systemd程序错误列从发行版中清除出去。 我们有一个相对较快的发展周期，大部分是渐进的变化，以保持高质量和稳定性。


#### 25.Myth: systemd is not debuggable. ####
> False. Some people try to imply that the shell was a good debugger. Well, it isn't really. In systemd we provide you with actual debugging features instead. For example: interactive debugging, verbose tracing, the ability to mask any component during boot, and more. Also, we provide documentation for it.
> 
> It's certainly well debuggable, we needed that for our own development work, after all. But we'll grant you one thing: it uses different debugging tools, we believe more appropriate ones for the purpose, though.

#### 误区25：systemd不是可以调试的 ####
> 错误，有些人试图表明shell是一个很好的调试器。但它并不是。在systemd我们提供了调试功能来代替shell调试。比如：交互式调试，详细跟踪，在引导期间屏任何组件的能力等等。 另外，我们为它提供文档。
>
> 他当然是可调试的，毕竟，我们需要为我们的开发工作而调试。我们要告诉你的一件事是：它可以使用不同的调试工具，但我们相信哪方式是最好的选择。


#### 26.Myth: systemd makes changes for the changes' sake. ####
> Very much untrue. We pretty much exclusively have technical reasons for the changes we make, and we explain them in the various pieces of documentation, wiki pages, blog articles, mailing list announcements. We try hard to avoid making incompatible changes, and if we do we try to document the why and how in detail. And if you wonder about something, just ask us!

#### 误区26： systemd为了改变而改变的 ####
> 很不真实。对于所做的改变，我们完全有技术上的原因。这样做的原因我们在文档，wiki页，博文，邮件列表中均有说明。我们尽力避免不兼容的改变，如果我们做了改变，我们一定在文档中记录为什么和怎样改变的一些细节。如果你想知道一些事情，尽管来问问我们！


#### 27.Myth: systemd is a Red-Hat-only project, is private property of some smart-ass developers, who use it to push their views to the world.  ####
> Not true. Currently, there are 16 hackers with commit powers to the systemd git tree. Of these 16 only six are employed by Red Hat. The 10 others are folks from ArchLinux, from Debian, from Intel, even from Canonical, Mandriva, Pantheon and a number of community folks with full commit rights. And they frequently commit big stuff, major changes. Then, there are 374 individuals with patches in our tree, and they too came from a number of different companies and backgrounds, and many of those have way more than one patch in the tree. The discussions about where we want to take systemd are done in the open, on our IRC channel (#systemd on freenode, you are always weclome), on our [mailing list](http://lists.freedesktop.org/mailman/listinfo/systemd-devel), and on public hackfests ([such as our next one in Brno](https://plus.google.com/events/cnklef88b85tb6tgf6ue3hn32lg), you are invited). We regularly attend various conferences, to collect feedback, to explain what we are doing and why, like few others do. We [maintain blogs](http://0pointer.de/blog), engage in social networks ([we actually have some pretty interesting content on Google+](https://plus.google.com/104232583922197692623/posts), and [our Google+ Community is pretty alive, too](https://plus.google.com/communities/114587707547576757881).), and try really hard to explain the why and the how how we do things, and to listen to feedback and figure out where the current issues are (for example, from that feedback we compiled this lists of often heard myths about systemd...).
> 
> What most systemd contributors probably share is a rough idea how a good OS should look like, and the desire to make it happen. However, by the very nature of the project being Open Source, and rooted in the community systemd is just what people want it to be, and if it's not what they want then they can drive the direction with patches and code, and if that's not feasible, then there are numerous other options to use, too, systemd is never exclusive.
> 
> One goal of systemd is to unify the dispersed Linux landscape a bit. We try to get rid of many of the more pointless differences of the various distributions in various areas of the core OS. As part of that we sometimes adopt schemes that were previously used by only one of the distributions and push it to a level where it's the default of systemd, trying to gently push everybody towards the same set of basic configuration. This is never exclusive though, distributions can continue to deviate from that if they wish, however, if they end-up using the well-supported default their work becomes much easier and they might gain a feature or two. Now, as it turns out, more frequently than not we actually adopted schemes that where Debianisms, rather than Fedoraisms/Redhatisms as best supported scheme by systemd. For example, systems running systemd now generally store their hostname in /etc/hostname, something that used to be specific to Debian and now is used across distributions.
> 
> One thing we'll grant you though, we sometimes can be smart-asses. We try to be prepared whenever we open our mouth, in order to be able to back-up with facts what we claim. That might make us appear as smart-asses.
> 
> But in general, yes, some of the more influental contributors of systemd work for Red Hat, but they are in the minority, and systemd is a healthy, open community with different interests, different backgrounds, just unified by a few rough ideas where the trip should go, a community where code and its design counts, and certainly not company affiliation.

#### 误区27：systemd是一个独有Red Hat项目，是一些聪明的开发者的私有财产，被用它来把他们的观点推向世界。 ####
> 不是真的，目前，有16个极客对于git tree具有提交的权利，16个人当中仅有6个是Red Hat的，其他的10个人分别来自ArchLinux,Debian和Intel.即使来自Canonical, Mandriva, Pantheon和许多社区的人们也完全具有提交的权利。它们经常提交大的模块，做大的改变。到目前为止，在我们的项目树中已经有374个独立的补丁包，他们分别来自具体不同背景的公司。而它们中的有的人已经不止一次提交了。关于讨ystemd应该有哪些功能的讨论完全是开放的，在我们的IRC频道上(#其中的sytemd板块，随时欢迎你的到来)。我们的[邮件列表](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)及公共的极客省会(比如在Brno的[our next on](https://plus.google.com/events/cnklef88b85tb6tgf6ue3hn32lg),也邀请你来参加)。 我们经常参加各种会议，收集反馈意见，解释我们正在做什么及为什么要这么做，先其他项目一样。 我们[维护博客](http://0pointer.de/blog)，参与社交网络（我们在[Google+上实际上有一些非常有趣的内容](https://plus.google.com/104232583922197692623/posts)，而且[我们的Google+社区也非常活跃](https://plus.google.com/communities/114587707547576757881)），并且我们非常努力的去解释为什么和如何做我们正在做的事（例如，根据这些反馈，我们编制了这个经常听到的关于systemd的这个误区清单）。
>
> 大多数的systemd贡献者可能会粗略的分享一个好系统应该是怎样的想法，且他们也渴望系统真的能这样做。然而，由于开源系统本质，systemd仅仅只是社区的人们想要的功能，如果它不是你想要的，你可以通过驱动或者补丁的方式去修改它，如果这样做还不行，可能也还有其他更多的选择，systemd永远不是唯一的。
> 
> systemd的一个目标就是统一分散的systemd环境，我们试图摆脱各种分发版系统在操作系统核心中各种无意义的差异，我们以前采用的方案的一部分就是，现在一个发行版上使用的，并把它作为systemd的默认级别，试图慢慢的推广使得每一个发行版都有一组相关的基本配置。然而，这绝不是排他性的，发行版仍可以也他们想要的方式运行，但是，如果你使用了默认的良好的功能，可以使他们的工作变得更容易，获得的功能也会不止一两个。现在，事实证明，更多的我们采取的方案式Debian化的，而非RedHat化的或者Fedora化的作为最好的systemd支持。比如，系统运行systemd一般会存储他们的hostname到/etc/hostname下，以前是Debian特有的东西，现在被用于所有的分发系统上。
> 
> 有一件事我们会支持你看法，那就是有时我们可能是聪明的笨驴。 每当我们开口说话时，我们都尽力做好准备，以便能够用事实来支持我们所宣称的事情。 这可能会使我们看起来很聪明。
> 
> 总的来说。是的，一些更有影响力的贡献是在为RedHat工作，但他们是少数的，systmed是一个健康，开放的社区，那里人有着不同兴趣，不同背景的人，唯一统一他们的其实的就是船究竟该往哪开的哪些粗略的想法。这个社区是靠着代码和它的设计来联系而不是以公司的方式。


#### 28.Myth: systemd doesn't support /usr split from the root directory. ####
> Non-sense. Since its beginnings systemd supports the *--with-rootprefix=* option to its *configure* script which allows you to tell systemd to neatly split up the stuff needed for early boot and the stuff needed for later on. All this logic is fully present and we keep it up-to-date right there in systemd's build system.
> 
> Of course, we still don't think that [actually booting with **/usr** unavailable is a good idea](http://freedesktop.org/wiki/Software/systemd/separate-usr-is-broken), but we support this just fine in our build system. This won't fix the inherent problems of the scheme that you'll encounter all across the board, but you can't blame that on systemd, because in systemd we support this just fine.

#### 误区28：systemd不支持从root目录中拆分/usr ####
> 废话。从一开始，systemd就在它的配置脚本中支持--with-rootprefix=选项，这允许你告诉systemd整洁的区分早期启动之前和之后所需的一些东西，所有这些逻辑都完全存在并且在我们构建systemd时保持更新。
> 
> 当然，我们始终不认为[在实际的启动中/usr目录不可用](http://freedesktop.org/wiki/Software/systemd/separate-usr-is-broken)的是一个好的Idea, 但我们仍然在我们的构建系统中支持它，这并不能解决你会遇到的所有问题，但是你不能就此指责systemd，因为在systemd中我们支持这个很好。


#### 29.Myth: systemd doesn't allow your to replace its components. ####
> Not true, you can turn off and replace pretty much any part of systemd, with very few exceptions. And those exceptions (such as journald) generally allow you to run an alternative side by side to it, while cooperating nicely with it.

#### 误区29： systemd不允许你替换它的组件 ####
> 不是这样的，你可以关掉或者替换systemd的大部分组件，只有少数例外. 这些例外(比如：journald)，一般通常允许你同时并行运行替换方案，同时与之配合良好。


#### 30.Myth: systemd's use of D-Bus instead of sockets makes it intransparent. ####
> This claim is already contradictory in itself: D-Bus uses sockets as transport, too. Hence whenever D-Bus is used to send something around, a socket is used for that too. D-Bus is mostly a standardized serialization of messages to send over these sockets. If anything this makes it more transparent, since this serialization is well documented, understood and there are numerous tracing tools and language bindings for it. This is very much unlike the usual homegrown protocols the various classic UNIX daemons use to communicate locally.

#### 误区30：systemd使用D-Bus而不是套接字使得它不透明。 ####
> 这个说法本身就自相矛盾，D-Bus也是使用sockets作为传输的。因此，无论何时使用D-Bus发送一些东西，都会用到sockets。 D-Bus发送给sockets的大多是标准化序列化的消息。如果有什么都能使它更加的透明化的话， 那么这些序列话就要有很好的被文档化，被解释并且有许多跟踪工具和语言绑定。这与用于本地通信的各种经典UNIX守护程序的常见自主协议是非常不同。

Hmm, did I write I just wanted to debunk a "few" myths? Maybe these were more than just a few... Anyway, I hope I managed to clear up a couple of misconceptions. Thanks for your time.

> 嗯。我只写了我想揭穿的对systemd认知的误区，也许远不至这些，无论如何，我希望我能够澄清了其中一些误解，谢谢你的时间。

#### Footnotes ####
* [1] For example,[ systemd-detect-virt](http://www.freedesktop.org/software/systemd/man/systemd-detect-virt.html), [systemd-tmpfiles](http://www.freedesktop.org/software/systemd/man/systemd-tmpfiles.html), [systemd-udevd](http://www.freedesktop.org/software/systemd/man/systemd-udevd.service.html) are.
* [2] Also, we are trying to do our little part on maybe making this better. By exposing boot-time performance of the firmware more prominently in systemd's boot output we hope to shame the firmware writers to clean up their stuff.
* [3] And anyways, guess which project includes a library "libnih" -- Upstart or systemd?
* [4] Hint: it's not systemd!

#### 注脚 ####
* [1] 例如， [systemd-detect-virt](http://www.freedesktop.org/software/systemd/man/systemd-detect-virt.html), [systemd-tmpfiles](http://www.freedesktop.org/software/systemd/man/systemd-tmpfiles.html), [systemd-udevd](http://www.freedesktop.org/software/systemd/man/systemd-udevd.service.html) 等等.
* [2] 也许，我们尽量做好的这部分会让整个系统变得更好。通过在systemd的启动时间中显著的暴露硬件启动时间的耗时，我们希望可以督促固件编写者更好的优化它们的工程。
* [3] 无论如何，猜猜哪个项目包含库“*libnih*” - Upstart或systemd？
* [4] 提示：这不是sysemd!



