# lovecode

> 本项目是基于小编的开发经验与心得，分享小编的平时的开发经验及编程经验


## 一、目录

1. 领域模型是什么？
2. 为什么要进行领域模型设计?
3. 领域模型具体怎么去做？

## 二、正文

### 1. 领域模型是什么？

如果你是第一次听到这个词,嗯,多么恐怖的一件事情呀! 什么是领域模型,一种新的技术吗? 领域模型到底有什么用呢? 
为什么那么多大佬都在讲领域模型。网络上充斥着着各种高端的解释,各种高大上的名字,各种复杂的系统设计图。

fuck ! 
身边总是有这样一群人的出现。总喜欢中文里加载者英文,英文中夹杂着中文,仿佛这样能使他们更加自信一样。把你讲懵了,他就自信了。 very fuck !

身为技术人,尽量想把一种事情给将清楚,说明白。而不是用各种抽象的晦涩难懂但看上去高大上的名词给解释。

在讲清楚领域模型之前我们先来看引入一个词汇 **“贫血模型”** ，读到这里不要怕。只是一个词汇而已。是对我们平时的项目代码结构的一个形容词。相信无论面前的你
是一个大牛，还是一个刚入行的小菜鸟。你都一定写过这样的代码:

- dao层: 负责持久化
- model层: 数据模型
- service层: 服务层
- web层: 提供对UI层的访问

嗯。这就是一个典型的贫血模型, 哇,真的好形象,这是谁想出来的词汇,真想给他说一句 fuck you!  但是，但是，你还有更好的词汇来形容这种项目结构吗? 如果没有我们只能闭嘴了。

往往我们入行的初期我们都是在这样的项目结构中进行编程的,那个时候我们的业务往往都是简单的,对于那个时候的我们来说,这样的代码结构真是太好用了。清晰易懂。甚至想说一声 i love code !!!

这个时期,我们的关注点往往不是业务的复杂度,而是技术的使用,语法的使用。代码是否能编译通过。

**贫血模型优点:**

1. 被许多程序员所掌握，对于初学者，这种模型很自然，甚至被很多人认为是java中最正统的模型。
2. 它非常简单，对于并不复杂的业务(转帐业务)，它工作得很好，开发起来非常迅速。它似乎也不需要对领域的充分了解，只要给出要实现功能的每一个步骤，就能实现它。
3. 事务边界相当清楚，一般来说service的每个方法都可以看成一个事务。

随着发际线推移,随着历史的变迁,随着候鸟的迁徙。不知不觉我们的业务越来越复杂了。万恶的资本家,总想让我们一夜之间开发一个淘宝,一夜之间开发一个百度,一夜之间开发一个QQ。于是我们的service层,不断的
不断的增加。代码量从100行,200行,300行,10000行刹不住车了。终于小张忍不住了,辞职走了。留下了孤独的你独自承受这忧伤。

这样代码是什么意思？ 这样代码能不能删？这行代码怎么没有走？这样代码能不能拆出去? 这样改万一项目上线崩溃了怎么办? 想一想老婆,望一望孩子。哎,算了吧。于是乎service复杂度指数般的递增。这就是贫血模型的缺点。

**贫血模型缺点:**

1. 所有的业务都在service中处理，当业越来越复杂时，service会变得越来越庞大，最终难以理解和维护，轻则项目组解散，重则妻离子散。
2. 将所有的业务放在无状态的service中实际上是一个过程化的设计,这于面向对象的编程风格,相向而行。(你转身离开分手说不出来,海鸟跟鱼相爱只是一场意外)
3. 项目代码写的不少,重用的不多。(fuck and fuck = double kill)


**领域模型就是要解决service越来越臃肿的办法。 对service中的复杂的业务逻辑进行拆分,根据领域来进行拆分。用面向对象的思想去重新设计service。**
有人给他起了一个高大上的词汇: 领域模型

<text color="red">所以关于领域模型,我们只要知道, 领域模型就是要用面向对象的思想去重新设计充斥着复杂业务逻辑的service层即可。</text>


