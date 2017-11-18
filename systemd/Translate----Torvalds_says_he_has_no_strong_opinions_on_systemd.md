# Torvalds says he has no strong opinions on systemd #
**Linux creator Linus Torvalds is well-known for his strong opinions on many technical things. But when it comes to systemd, the init system that has caused a fair degree of angst in the Linux world, Torvalds is neutral.**

"When it comes to systemd, you may expect me to have lots of colourful opinions, and I just don't," Torvalds told iTWire in an interview. "I don't personally mind systemd, and in fact my main desktop and laptop both run it.

In a reference to [a spat he had with Kay Sievers](http://www.theregister.co.uk/2014/04/05/torvalds_sievers_dust_up/), one of the main developers of systemd, Torvalds added: "Now, I don't get along with some of the developers and think they are a bit too cavalier about bugs and compatibility, but I'm also very much not in the camp of people who hate the very thought of systemd."

Torvalds also answered a number of other questions, both technical and general, in his usual straightforward no-nonsense way. An edited transcript follows. Thanks are due to my UNIX guru[ Peter Giorgilli](http://www.iscient.com.au/) who suggested a number of questions.


# Torvalds说他对systemd没有什么特别的看法 #
**Linux的创始人Linus Torvalds一向以对一些技术人上的问题有强烈的看法而著称。但是在对systemd看法上，Torvalds是持中立的意见， systemd作为初始化系统在Linux的世界中引起了相当程度的抵制。**

"当谈及systemd时，你可能希望我有许多主观色彩的意见看法，但是我没有." 再一次采访中Torvalds告诉iTWire。 "我个人并不介意systemd， 实际上我主要的桌面电脑和比较本都在运行它"。

在提到他与systemd的主要开发人员[Kay Sievers的口水战](http://www.theregister.co.uk/2014/04/05/torvalds_sievers_dust_up/)时，Torvalds补充道：我不赞同某些开发者是因为他们在错误和兼容性上太过傲慢。但我也肯定不是在讨厌systemd一切设计思想的人们阵营里面。

Torvalds还以他一贯的直白的方式回答了其他许多技术问题和一般问题。记录编辑如下， 感谢我的UNIX专家[Peter Giorgilli](http://www.iscient.com.au/)提出的一些问题。


iTWire: Systemd seems to depart to a large extent from the original idea of simplicity that was a hallmark of UNIX systems. Would you agree? And is this a good or a bad thing?
Linus Torvalds: So I think many of the "original ideals" of UNIX are these days more of a mindset issue than necessarily reflecting reality of the situation.

There's still value in understanding the traditional UNIX "do one thing and do it well" model where many workflows can be done as a pipeline of simple tools each adding their own value, but let's face it, it's not how complex systems really work, and it's not how major applications have been working or been designed for a long time. It's a useful simplification, and it's still true at *some* level, but I think it's also clear that it doesn't really describe most of reality.

It might describe some particular case, though, and I do think it's a useful teaching tool. People obviously still do those traditional pipelines of processes and file descriptors that UNIX is perhaps associated with, but there's a *lot* of cases where you have big complex unified systems.

And systemd is in no way the piece that breaks with old UNIX legacy. Graphical applications seldom worked that way (there are certainly _echoes_ of it in things like "LyX", but I think it's the exception rather than the rule), and then there's obviously the traditional counter-example of GNU emacs, where it really was not about the "simple UNIX model", but a whole new big infrastructure thing. Like systemd.

Now, I'm still old-fashioned enough that I like my log-files in text, not binary, so I think sometimes systemd hasn't necessarily had the best of taste, but hey, details..

问题一：
Systemd似乎很大程度上脱离了UNIX系统标志的简单性。你同意这样做吗？ 这是好事还是坏事？

Linus Torvalds: 嗯，我认为UNIX的许多“原始的ideals”现在来看更多是一个心态问题，而不能够完全反映现实情况。

在理解传统的Unix模式"多一件事并把它作好"来说，这仍然是有价值的。许多工作流可以作为简单工具的管道，这样每个工具都有自己的价值，但现在我们面对的问题是，这在一些更复杂的系统中并不能工作的很好。所以它不能作为一些大型程序工作的方式或者设计已经很长一段时间了。这是一个有用的简化，在某些层面上仍然是正确的，但是我认为这也很清楚，它并不能真实地描述大部分的现实。

它(systemd)也许就描述了这些特定的情况，因而，我认为这是一个非常有用的范例工具。人们仍然在使用与Unix相关的传统的一些管道如进程和文件描述符。但是，在一个非常大且复杂的统一系统里，有很多特定的情况。

且systemd绝不是Unix遗留下来的哪些碎片。图形应用程序很少以这种方式工作（在“LyX”这样的东西中肯定有它的意思，但我认为这是一个例外而不是规则），与这种传统想违的反例还有就是GNU emacs. 它绝不是传统的Unix的模型，而是一个全新的大的架构。 就像systemd一样。

现在，我仍然很老套，我喜欢用文本的方式记录日志而非二进制，所以有时我认为systemd的设计未必是最好的味道，但嘿，这是细节的地方了....

Have you seen similar situations before - right from 1991 when you first put Linux up for download - where the introduction of a new way of doing things caused such a lot of bitterness and extreme reactions?


问题二：
你以前见过类似的情况吗 - 从1991年开始，当你把Linux第一次上传供他人下载的时候 - 引入了一种新的做事方式引起了如此多的痛苦和极端的反应？

Oh, there's been bitter fights before. Just think about the emacs vs vi wars. Or, closer to systemd, the whole "SysV init" vs "BSD init" differences certainly ended up being things that people had "heated discussions" about. Or think about the desktop comparisons.

I'm not really sure how different the systemd brawls are from those. It's technical, but admittedly the systemd developers have also been really good at alienating people on a purely personal level too. Not that that is anything particularly new under the sun _either_: the (very) bitter wars between the GPL and the BSD license camps during late-80s and early-90s were almost certainly more about the persons involved and how they pissed off people than necessarily deeply about other differences (which existed, obviously, but still).

What would you say if someone argued that systemd has created a single point of failure which makes a system unbootable if it fails? It centralises a lot of services in itself and if one fails, then the system is pretty much useless.

I think people are digging for excuses. I mean, if that is a reason to not use a piece of software, then you shouldn't use the kernel either.

Of course, the kernel is special, and kernel engineers are just better people. Everybody knows that. So maybe comparing other more mundane projects to something as lofty as the kernel is unfair. But look at plodding projects like glibc etc - when they screw up, everybody gets hurt too. So I dunno.

I raised this because I have seen articles from people calling for a move to the BSDs on servers, rather than Linux. I haven't seen that level of extreme behaviour before - but then I have only been using Linux since 1998.

So I have to admit that I don't generally try to follow storms like this, but I also think that one thing that is changing is that you have this culture of shrill populistic panic that I think people are perhaps taking too seriously. It's obviously not just in the tech press (I'm sure you can point - like I can - to tons of allegedly serious world-news sites that do the same thing), but the tech world certainly also has a lot of "opinion pieces" and related puffery.

And there's a classic term for it in the BSD camps: "bikeshed painting", which is very much about how random people can feel like they have the ability to discuss superficial issues, because everybody feels that they can give an opinion on the color choice. So issues that are superficial get a lot more noise. Then when it comes to actual hard and deep technical decisions, people (sometimes) realise that they just don't know enough, and they won't give that the same kind of mouth-time.

Have you read the new document by Lennart Poettering about organising distributions with the Btrfs filesystem as default? If so, what do you think of it?


问题三：
您是否阅读过Lennart Poettering有关将Btrfs文件系统作为组织发行版中为默认文件系统新文档？ 如果是这样，你怎么看待它？

I'm not at all sure that's necessarily the right way to go about things, but I'm actually very happy that people are working in that direction. The current packaging model is certainly broken for third-party applications, and I'm not convinced it's all that great even for projects that are distributed by Linux distributions as part of the core distro.

Are the exact details of how you use Btrfs to implement this the right thing? I have absolutely no idea. It's a complex problem, and it's not going to be solved overnight with some radical new thing, and I'm rather suspicious of fancy new models that change everything and claim it solves things (maybe the newness and complexity and fancy details just make it hard to say that it _doesn't_ have the problems existing systems have, so then that is seen as an argument that the problems no longer exist - not because they truly went away, but simply because they got too hard to argue about because so much changed).

But I think it's very much a problem worth looking at.

After using Git for nearly a decade now, are there any features that have been added down the years that have surprised you?

问题四：
在使用Git近十年以来，这些年以来有什么新加的功能是惊讶到你了吗？

Well, there really haven't been that many core changes. It's very recognisably the same thing, just polished and done better. Most of the really core concepts are totally unchanged.

No, the _surprises_ have been in how quickly it ended up becoming so popular. People were complaining about how hard it was to use, and more importantly, people really fundamentally didn't "get it" when it came to distribution, and when it came to some other things that git did fundamentally differently (but much better). Like the whole way git does renaming and how "git blame" can follow the history of some piece of code even across code movements not just on a "file" basis, but between files.

Those were things that people were very actively arguing about not that long ago. The "old model" (really CVS in various disguises) still had a huge sway over the mindset of how things were supposed to work.

And then github happened, and a lot of random projects started using git (the ruby community seemed to bring in a lot of random people from the web into git), and then fairly suddenly, really, it all went from "outrageous" to "accepted". No, not universally, but the new model really seemed to switch over to where people "got it", and there are still complaints about random things, but they've certainly become more muted.

I guess it wasn't really sudden, it was more of an issue of getting sufficient critical mass that you'd find people explaining to each other what was going on, but it _felt_ sudden to me. Git went from a fairly niche use (the kernel, some other really core projects) to a much wider audience, and now to the point where it's almost the default SCM (source code management system) for any open source project, and for a lot of non-OSS ones too. There's git plugins (and often native support) for just about any development environment out there these days.

What has been your experience of IT education in schools attended by your children?
To be honest, my kids haven't really ever seemed very interested in computers except as users, so while they are certainly no Luddites, I also don't really have any feel for the IT education. It has been interesting to see how the fact that they are using Linux on their laptops at school really hasn't been a problem. OpenOffice and various webby things just work fine, and I was worried there would be some situation where it would cause big problems. Nothing so far, although I'm sure they've had their own issues.
Our local school used Linux and OpenOffice (not exclusively, but still) even before we moved here, so that probably is part of it.

Following on from this, do you have any views regarding how IT is taught in schools, or more generally on the place of IT in education? (For example, the use of devices such as tablets in the classroom.)

问题五：
以上所述，你对于如何在校教授IT，或者更一般地说在教育领域的IT发展有什么意见？ （例如，在教室中使用平板电脑等设备。）

I'm not a huge fan of tablets, except as pure consumption devices. Don't get me wrong, I use a tablet myself, and use it daily for just reading email when not at the computer (along with my phone), but I want a keyboard if I want to *create* something. And I think that's true in education too. Sure, a lot of it is "consumption", and being able to show animations instead of static pictures can certainly be a powerful teaching tool that any electronic media has going for it over a traditional book, but Patricia just wanted a book for school _as_ a book, rather than on kindle, because she wanted to do highlights and sticky notes etc. And sure, you can do that on electronic media too, but not necessarily better. And when you actually *create* something, I just suspect a laptop would be much better.

And in the end, I don't think the real problem in education is IT or the lack of IT.  I strongly think that a good teacher that actually gets to teach (and not just for tests and having to meet some arbitrary benchmarks, which seems to be so common) is what matters *so* much more. And even aside from the teacher, one of the things we looked for for our kids was not just to find a good school, but move to an area where our peers (and thus the kids peers) appreciated education.

IT? Not special. It can help, it can hurt. I think it's a fun and rewarding area of employment, and I'm happy that it pays well. I like IT, but it's not something primary (ok, except if you're a tech company, and your #1 job is literally to do the IT part). I may be a huge computer nerd, but even so I don't think education should be about computers. Not as a subject, and not as a classroom resource either.

What do you think about providing laptops to kids in schools at an early age - like the OLPC calls for? Does it help in education or is it a hindrance?

问题六：
你如何看待在OLPC所要求的给在校的孩子们提供便携式笔记本电脑的问题？ 这对教育是帮助还是阻碍呢？


I don't think the OLPC was so much about "early age" as "widely available". As in poor areas that just didn't have access to computers *regardless* of age.

And that "access" thing I'm actually a huge believer in. The reason I got into computers is largely my grandfather, who gave me access to one back in the early 80's, when most kids my age certainly didn't have that access. And you can find similar stories about a lot of computer people: many got started early because they had parents or schools or something that made it possible to play around with equipment and learn.

I think the Raspberry PI is a great project for that reason too, exactly because it can give access to people to tinker. And I really think "tinker" in many ways is more important than "use". People who learn to *use* a computer certainly learn something important too, but I think that kids who learn to *tinker* with technology actually learn a much deeper and more important thing.

But I really don't see "tinkering classes" as being something that makes sense in a school setting. I really think that you cannot possibly grade "tinkering", I don't think you can make it into some organised thing without destroying the value of it. I think you want to offer resources and make it possible, but almost leave it at that.

So support tinkering by any means: have internet and the computers to access it in school libraries, and show the kids to search for things other than just kitten videos or porn.  Encourage more relaxed settings for tinkering: clubs for programming, robotics, 3D printing, whatever. Have the kids build a weather balloon and take pictures half-way to space. Encourage "geeky" things the same way you encourage soccer or whatever.

There are resources on the web for kids to learn, if they are interested. Show them those, and let them be. Not everybody will be interested, and you can't force it without destroying the tinkering, I think.

Do you think you're a better programmer today than you were, say, 10 years ago?

问题七：
相比十年前来说，你是否认为自己变成了一个更好的程序员?


Well, I certainly did a lot *more* programming ten years ago than I do today, so I'd have to say "no". I was clearly a more productive programmer back when I did more programming.

I still wouldn't call myself a "manager" - I certainly haven't fallen that far, and I don't do quarterly budgets etc - but at the same time I'm not really a programmer any more either. "Technical lead". You need to know programming in order to be able to judge what works and what doesn't, but I write more "how about solving it this way" kind of emails than I actually write code.

Do you find it any more difficult to program the older you get?

问题八：
你是否觉得年龄越大越在难以编程？

Yes and no. It's not that it's more difficult to program per se, but especially as a top-level maintainer I can simply not concentrate on one particular area the way you really need to do in order to be able to really solve knotty problems. I just don't get to be that specialised any more, and I really can't afford to get in the "zone" and work on just one very particular problem for a week or two (or month. Or whatever). And programming is all about the details, and getting them right, and you really need to sit down and be very intimate with one particular issue.

And don't get me wrong, I'm not entirely sure I want to do some of it any more. I've done device driver programming, and it's really interesting to have a spec-sheet in front of you, and just try to get some random very specific piece of hardware to work. There's nothing quite like it, making hardware come to life. But at the same time, I *have* done it, I'm over it, and I'm pretty certain that if I never ever have to write another device driver in my life any more, I'll be just as happy. Because it really is such a nitty-gritty detailed-oriented thing that you have to really go into this place where you don't care about much anything else.

So I'm pretty happy being a technical lead. Part of me misses the fact that I really don't have the time or possibility to just dig into one tiny thing any more. But a bigger part of me enjoys the "overview".

I think one of the reasons I still enjoy doing what I do is that what I do today is different from what I did 10 years ago, and that is in turn very different from what I did 20 years ago. There is that whole history of continuity within the project, but at the same time, things have certainly changed.

Do you enjoy managing such a large bunch of often unwieldy individuals or is there more tearing our of hair than the public is witness to?

问题九：
你是否喜欢管理如此庞大且难以控制的社群？ 是否有比公众目睹更多撕逼的事件？


I do enjoy it, and I actually think that there is much *less* tearing out of hair than the public witnesses.

People see the stories of the storms and the vocal arguments. You're writing about one for systemd, but I can point you to numerous ones about my cursing at people, and if you're outside, those may be the only ones you've seen about the process. Because they are, again, the puffery, the opinion pieces, the things that take flight. Very few people write about deep and interesting technical discussions about some random area, and the people who do (like LWN etc) don't get he social media spread _unless_ they then write a piece about something else that everybody can have an opinion on.

Is it stressful being a technical lead for a big project? Yes, it can be, and it's not always fun. But *most* of the time things actually work well, most of the time I really like all the people working with me, and most of the time it's just a lot of fun. The occasional flare-up isn't necessarily horribly bad either. I don't know about you, but I personally get more stressed out over "constant low-grade friction" than about some occasional big shouting match where people really call each other names.

If you were starting out again to write a UNIX-like kernel, would you still use the "C" programming language?

问题十：
如果让你重新再写一次类UNIX的内核，你是否会仍然使用C编程语言？


Absolutely. That's one thing that definitely hasn't changed.
Assuming you followed the "Snowden" revelations - was there anything in particular that surprised you regarding the reported extent of mass surveillance being undertaken by the NSA?

Not really wrt the surveillance, no. The misguided outrage by politicians (ie outrage against Snowden, not about the things he exposed) I guess shouldn't have been a surprise either, but it still was. Sad. The hypocrisy of (California Senator Dianne) Feinstein in particular wrt the whole spying saga was just too disgusting for words.

