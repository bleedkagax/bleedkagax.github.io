---
title: Refactor
name: refactor
date: 2024-09-05
draft: false
tags:
  - CS
share: "true"
---

Essentially, **refactoring is improving the design of code after it's been written**.

If you want to add a feature to a program, but find that the code isn't easy to change due to a lack of good structure, refactor that program first so that it's easier to add the feature, and then add the feature.

It is the change in **requirements** that makes refactoring necessary.

The refactoring technique is to **modify the program at a tiny pace**. If you make a mistake, it's easy to spot it.

The test of good code is how easily one can modify it.

To summarize:

The key takeaways for efficient and organized refactoring are: **Smaller steps lead to faster progress**, keep your code in a working state forever, and small changes add up to a much better system design. Refactoring is not a “silver bullet”, but it can be considered a “silver tongs”, which can help you always have good control over your code. Refactoring is a tool.

# **1. Bad taste in code **

## 1\. **Mysterious Name**

  There are only two hard things in Computer Science: cache invalidation
  and naming things\-- Phil Karlt

Naming is one of the two hardest things in programming. Because of this, renaming is probably the most commonly used refactoring technique, including changing function declarations (for renaming functions), variable renaming, and field renaming.

## 2\. **Global Data**

**Wrapped Variables**. It may not hurt to have a small amount of global data, but the larger the number, the exponentially more difficult it is to deal with.

## 3\. **Mutable Data**

Encapsulated variables can be **used to ensure that all data update operations are performed through very few functions**, making them easier to monitor and evolve.

**If a variable is used to store different things at different times, split variables can be used to split it into variables for their own different purposes, thus avoiding dangerous update operations**.

Use move statements and refine functions to try to move logic out of the code that handles update operations, separating code that has no side effects from code that performs data update operations.

When designing APIs, you can use ** to separate query functions from modification functions**.

Use **Remove set-value functions** as early as possible to narrow the variable scope.

## 4\. **Long Functions**

**Actively Decompose Functions.**

Principle: **Whenever we feel that we need to explain something in a comment, we write what we need to explain in a separate function and name it after its purpose (not how it was implemented)**.

What kind of function is too long? More than 50 lines? More than 70 lines? It's not the length of the function that matters, it's the semantic distance between the “what” and “how” of the function.

How do you determine which piece of code to refine? A good tip is to **look for comments. They usually indicate the semantic distance between what the code does and how it does it.**

**Conditional expressions and loops often signal refinement as well**. Conditional expressions can be handled using decomposition conditional expressions.

**For huge switch statements, each branch should be turned into a separate function call by refining the function. If there are multiple switch statements that branch selection based on the same condition, you should use replace conditional expressions with polymorphism.**

**Loops and code within loops should be refined into a separate function**. If you find the distilled loop hard to name, it may be because it does several different things in it. If this is the case, be brave and use a split loop to break it up into its own separate tasks.

## 5\. **Long Parameter List**

**If it is possible to launch a query on one parameter to get the value of another parameter, then this second parameter can be removed by replacing the parameter with a query.**

If you find yourself pulling a lot of data items out of an existing data structure, consider **Using the Keep Objects Intact technique to pass directly into the original data structure**. **If there are several parameters that always appear at the same time, you can combine them into a single object** by introducing a parameter object.

If a parameter is used as a flag to distinguish the behavior of a function, remove the flag parameter.

**Using classes can effectively shorten the argument list**. Introducing a class makes particular sense if multiple functions have the same few parameters. You can use functions combined into classes to make these common parameters into fields of this class.

## 6\. **Shotgun Surgery**

**If you have to make many small modifications within many different classes every time you encounter some kind of change**, the bad taste you're facing is Shotgun Surgery.

**Moving functions and moving fields puts all the code that needs to be modified into the same module**. If **there are a lot of functions that operate on similar data, you can use a combination of functions into a class**. If some functions function to transform or enrich data structures, you can use functions to combine into transformations. If the output of some functions can be combined and made available to a piece of logic that specializes in using the results of those computations, this is often useful **Split Stage (e.g., parsing an order before calculating the price of an order**)**.

A common strategy is to use refactoring related to inlining ------ such as **inline functions** (or inline classes) ------ to yank logic that shouldn't be scattered back into one place**. After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks.

## 7\. **Comments**.

**If you need comments to explain what a piece of code does, try refining the function**; **If the function has been refined but still needs comments to explain its behavior, try renaming it with a change to the function declaration**; **If you need comments to explain the specification of some system requirement, try introducing an assertion.

**When you feel the need to write comments, try refactoring first and try making all comments redundant.**

## 8\. **Data Clumps**.

Data that always appears tied together really should have objects of their own.

## 9\. Repeated Switches 

Polymorphism.

## 10\. **Lazy Element

As the refactoring progresses it gets smaller and smaller and the class ends up with only one function. Remove this class in time to use inline functions or inline classes.

## 11\. **Refused Bequest**.

Subclasses should inherit functions and data from the superclass.

If you do not want to support the interface of the superclass, you should not be false to the inheritance system, and you should use delegates (using combinations instead of inheritance) instead of subclasses or delegates instead of superclasses to draw a line in the sand.

# **2. First set of reconstructions**

## 1\. **Extract Function**

![](/img/refactor.png)

![](/img/refactor-1.png)

**Separate Intent from Implementation**: If you need to spend time browsing through a piece of code to figure out what it's actually doing, then you should distill it down to a function and name it according to what it does. Because most of the time you don't need to care about how the function accomplishes its purpose (that's what the function does inside)

Good names: in a big function, a piece of code puts a comment that distills it into a function, and the comment often suggests a good name.

**Practice***

**Create a new function: name it after “what it does”, not “how it does it”**.

Without local variables, refine directly into a function;

with local variables but read-only, passed as arguments to the target function

Local variables are assigned values: declared directly in the refining function if they are used only within the refining function; used outside the refining function as the return value of the refining function; multiple variables are modified by considering returning an object or using other refactoring techniques (querying instead of temporary variables, splitting variables)

## 2\. **Inline Function**

![](/img/refactor-2.png)

![](/img/refactor-3.png)

![](/img/refactor-4.png)

**Indirectness may help, but non-essential indirectness is always uncomfortable.**

Some functions have their contents and names clear and easy to read

A group of functions is not well organized, inline to one big function first, then refine.

## 3\. **Extract Variable**

![](/img/refactor-5.png)

![](/img/refactor-6.png)

**Variables provide the right context**: they help us break up expressions into more manageable forms, and also make it easier to understand what a portion of the code is doing.

According to The Tao of Tidy Code, “**Use explanatory variables to break up the computation into a series of well-named intermediate values**”.

## 4\. **Inline Variable**

![](/img/refactor-7.png)

![](/img/refactor-8.png)

Sometimes, **variable names are no more expressive** than the expression itself. There are also times when variables may get in the way of refactoring nearby code.

## 5\. **Rename Variable**

![](/img/refactor-9.png)

Explain what a piece of program is doing, **and be more careful naming fields whose scope extends beyond a single function call.**

## 6\. **改变函数声明（Change Function Declaration）**

![](/img/refactor-10.png)

A good name gives an immediate indication of what the **function is used for**;

The argument list of a **function** describes how the function coexists with the outside world, and modifying the argument list not only increases the scope of the function's application, but also removes unnecessary coupling by changing the conditions required to connect a module.

**"A good way to improve the name of a function: write a comment describing what the function is used for, then turn that comment into the name of the function.”**

## 7\. **Introduce Parameter Object**

![](/img/refactor-11.png)

Organize data into structures that make the **relationships** between data items clearer;

**shorter parameter list**;

**Code consistency**: all functions that use this data structure can access elements of it by the same name.

Changing the conceptual picture of the code elevates these data structures to new abstractions

## 8\. **Combine Functions into Class**

![](/img/refactor-12.png)

**If you find a group of functions that manipulate the same piece of data (usually by passing that piece of data as a parameter to the function), it's time to form a class**. Classes explicitly provide a common environment for these functions, and calling them from within an object simplifies function calls by passing many fewer arguments.

## 9\. **Split Phase**

![](/img/refactor-13.png)

A piece of code that handles two different things at **simultaneously** can be considered to be **split into its own separate modules**, because then each topic can be handled separately when it comes time to make changes.

# **3. Encapsulate**

## 1\. **Encapsulate Record**

![](/img/refactor-14.png)

Objects can hide details of the structure, **help with renaming of fields**, and are easy to expand to cope with changes.

## 2\. **Encapsulate Variable**

![](/img/refactor-15.png)

For all mutable data, as long as its scope extends beyond a single function, I encapsulate it and only allow access through the function. The larger the scope of the data, the more important encapsulation becomes.

## 3\. **Encapsulate Collection**

![](/img/refactor-16.png)

One mistake people often make when encapsulating collections is that ** only encapsulates access to the collection variables, but still lets the fetch function return the collection itself. This allows the collection's member variables to be modified directly, while the class encapsulating it is completely unaware and unable to intervene**.

Practice:

Provide methods to modify the collection on the class ------**Usually “add” and “remove” methods to unify the management**.

## 4\. **Substitute Algorithm**

![](/img/refactor-17.png)

# **3. Move Characteristics**

Another type of refactoring that is also important is **moving elements between contexts**.

## 1\. **搬移函数（Move Function）**

![](/img/refactor-18.png)

**任何函数都需要具备上下文环境才能存活**。

搬移函数最直接的一个动因是，**它频繁引用其他上下文中的元素，而对自身上下文中的元素却关心甚少**，将函数移动到联系更紧密的上下文那么系统别处就可以减少对当前模块的依赖，**获得更好的封装效果。**

整理代码时，发现需要**频繁调用一个别处的函数**；或者函数内部定义了一个帮助函数，而该帮助函数可能**在别的地方也有用处**，此时就可以将它搬移到某些更通用的地方。

**是否需要搬移函数常常不易抉择，但决定越难做，通常说明"搬移这个函数与否"的重要性也越低。**

**范例：搬移内嵌函数至顶层**

before：

计算两点之间距离的函数在别处也有调用

![](/img/refactor-19.png)

after：

![](/img/refactor-20.png)

## 2\. **搬移语句到函数（Move Statements into Function）**

![](/img/refactor-21.png)

**"消除重复"**：如果发现调用某个函数时，总有一些相同的代码也需要每次执行，则考虑将此段代码合并到函数里头。

**如果某些语句与一个函数放在一起更像一个整体**，并且更**有助于理解**，则将语句搬移到函数里去。**如果它们与函数不像一个整体**，但仍应与函数一起执行，可以用**提炼函数将语句和函数一并提炼出去**。

**五. 重新组织数据**

1\. **拆分变量（Split Variable）**

![](/img/refactor-22.png)

除"循环变量"和"结果收集变量"外，还有很多变量用于保存一段冗长代码的运算结果，以便稍后使用。这种**变量应该只被赋值一次。**如果它们被赋值超过一次，就意味它们在函数中承担了一个以上的责任。如果变量承担多个责任，它就应该被替换（分解）为多个变量，**保持职责单一**。

**范例：对输入参数赋值**

before：

![](/img/refactor-23.png)

after：

![](/img/refactor-24.png)

**六. 简化条件逻辑**

1\. **分解条件表达式（Decompose Conditional）**

![](/img/refactor-25.png)

程序之中，复杂的条件逻辑是最常导致复杂度上升的因素之一。

对于条件逻辑，**将每个分支条件分解成新函数**还可以带来更多好处：可以突出条件逻辑，更清楚地表明每个分支的作用，并且突出每个分支的原因。

注：实际上为**提炼函数**的一个应用场景。

2\. **合并条件表达式（Consolidate Conditional Expression）**

![](/img/refactor-26.png)

3\. **以卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard
Clauses）**

![](/img/refactor-27.png)

如果两条分支都是正常行为，就应该使用形如if\...else\...的条件表达式；如果某个条件极其罕见，就应该单独检查该条件，并在该条件为真时立刻从函数中返回。**这样的单独检查常常被称为"卫语句"（guard
clauses）**。

**如果使用if-then-else结构，则对if分支和else分支的重视是同等的；以卫语句取代嵌套条件表达式的精髓就是：给某一条分支以特别的重视。**

"每个函数只能有一个入口和一个出口"的观念未必有用，**保持代码清晰才是最关键的**。

**范例**

before

![](/img/refactor-28.png)

after

![](/img/refactor-29.png)

**范例：将条件反转**

初始

![](/img/refactor-30.png)

反转

![](/img/refactor-31.png)

合并条件表达式

![](/img/refactor-32.png)

删除可变变量

![](/img/refactor-33.png)

4\. **以多态取代条件表达式（Replace Conditional with Polymorphism）**

![](/img/refactor-34.png)

**七. 重构API**

**以查询取代参数（Replace Parameter with Query）**

![](/img/refactor-35.png)

**函数的参数列表应该总结该函数的可变性**，标示出函数可能体现出行为差异的主要方式。和任何代码中的语句一样，**参数列表应该尽量避免重复**，并且参数列表越短就越容易理解。

使用场景：调用函数时传入了一个值，而这个值由函数自己来获得也是同样容易

什么是"同样容易"：函数可以承担这份原本由调用方所承担的"获得正确的参数值"的责任。

什么时候不适用：移除参数可能会给函数体增加不必要的依赖关系。

**以参数取代查询（Replace Query with Parameter）**

![](/img/refactor-36.png)

好处：**改变依赖关系**，去掉令人不快的引用。

注意：**要考虑责任分配问题，会增加函数调用者的复杂度，而设计接口时又需要考虑易用性**。

**八. 处理继承关系**

**以委托取代超类（Replace Superclass with Delegate）**

![](/img/refactor-37.png)

继承：子类继承父类的特征和行为 （车-交通工具）

组合：通过对现有对象进行拼装即组合产生新的具有更复杂的功能 （车-轮胎）

以组合取代继承。

**一个经典的误用继承的例子：**

**让栈（stack）继承列表（list）**。这个想法的出发点是想复用列表类的数据存储和操作能力。虽说复用是一件好事，但这个继承关系有问题：列表类的所有操作都会出现在栈类的接口上，然而其中大部分操作对一个栈来说并不适用。**更好的做法应该是把列表作为栈的字段，把必要的操作委派给列表就行了**。

  -----------------------------------------------------------------------
  Java\
  public class Stack\<E\> extends Vector\<E\> {\
<br/>
  public E push(E item) {\
  addElement(item);\
  return item;\
  }\
<br/>
  public synchronized E pop() {\
  E obj;\
  int len = size();\
  obj = peek();\
  removeElementAt(len - 1);\
  return obj;\
  }\
  }

  -----------------------------------------------------------------------

Stack真正需要的只有四个方法，push/pop/size/isEmpty， Stack只用到了
Vector的两个方法 isEmpty 和 size，而 push 和 pop 是 Stack 自有的实现，
Vector 有大量的方法， 不适用于stack。

**所以，如果父类的一些函数对子类并不适用，就说明我不应该通过继承来获得超类的功能。**

同时也要避免走弯路：完全避免使用继承，如果符合继承关系的语义条件（超类的所有方法都适用于子类，子类的所有实例都是超类的实例），那么继承是一种简洁又高效的复用机制。

建议：**首先（尽量）使用继承，如果发现继承有问题，再使用以委托取代超类。**

**范例**

背景：

给一个古城里存放上古卷轴（scroll）的图书馆做了咨询。他们给卷轴的信息编制了一份目录（catalog），每份卷轴都有一个ID号，并记录了卷轴的标题（title）和一系列标签（tag），这些古老的卷轴需要日常清扫，因此代表卷轴的Scroll类继承了代表目录项的CatalogItem类，并扩展出与"需要清扫"相关的数据。

![](/img/refactor-38.png)

![](/img/refactor-39.png)

这就是一个常见的建模错误。真实存在的卷轴和只存在于纸面上的目录项，是完全不同的两种东西。比如说，关于"如何治疗灰鳞病"的卷轴可能有好几卷，但在目录上却只记录一个条目。这样的建模错误很多时候可以置之不理。像"标题"和"标签"这样的数据，可以认为就是目录中数据的副本。如果这些数据从不发生改变，可以接受这样的表现形式。但如果需要更新其中某处数据，就必须非常小心，确保同一个目录项对应的所有数据副本都被正确地更新。

就算没有数据更新的问题，把目录类作为卷轴类的父类，依然会让后来的开发者感到迷惑。

首先在Scroll类中创建一个属性，令其指向一个新建的CatalogItem实例。

![](/img/refactor-40.png)

然后对于子类中用到所有属于超类的函数，我要逐一为它们创建转发函数。

![](/img/refactor-41.png)

**详细笔记**

**第1章 重构，第一个示例**

本质上说，重构就是在代码写好之后改进它的设计。

如果你要给程序添加一个特性，但发现代码因缺乏良好的结构而不易于进行更改，那就先重构那个程序，使其比较容易添加该特性，然后再添加该特性。

是需求的变化使重构变得必要。

重构前，先检查自己是否有一套可靠的测试集。这些测试必须有自我检验能力。

每次想将一块代码抽取成一个函数时，遵循一个标准流程：最大程度减少犯错的可能。------**提炼函数**

重构技术就是**以微小的步伐修改程序**。如果你犯下错误，很容易便可发现它。

**营地法则**：保证离开时的代码库一定比你来时更加健康。完美的境界很难达到，但应该时时都**勤加拂拭**。

以实例展开如何重构：包括提炼函数、内联变量、搬移函数和以多态取代条件表达式等，

几个重要的阶段：将原函数分解成一组嵌套的函数、应用拆分阶段分离计算逻辑与输出格式化逻辑，以及为计算器引入多态性来处理计算逻辑。每一步都给代码添加了更多的结构，以便更好地表达代码的意图。

好代码的检验标准就是人们是否能轻而易举地修改它。

总结：

开展高效有序的重构，关键的心得是：**小的步子可以更快前进**，请保持代码永远处于可工作状态，小步修改累积起来也能大大改善系统的设计。

**第2章　重构的原则**

**为何重构**

它不是一颗"银弹"，却可以算是一把"银钳子"，可以帮你始终良好地控制自己的代码。重构是一个工具

**重构改进软件的设计**

代码结构的流失有累积效应。经常性的重构有助于代码维持自己该有的形态。消除重复代码，以确定所有事物和行为在代码中只表述一次，这正是优秀设计的根本。

**重构使软件更容易理解**

在重构上花一点点时间，就可以让代码更好地表达自己的意图------更清晰地说出我想要做的。

**重构帮助找到bug**

Kent
Beck经常形容自己的一句话："我不是一个特别好的程序员，我只是一个有着一些特别好的习惯的还不错的程序员。"

**重构提高编程速度**

![](/img/refactor-42.png)

需要添加新功能时，内部质量良好的软件让我可以很容易找到在哪里修改、如何修改。良好的模块划分使我只需要理解代码库的一小部分，就可以做出修改。如果代码很清晰，引入bug的可能性就会变小。

"设计耐久性假说"：通过投入精力改善内部设计，我们增加了软件的耐久性，从而可以更长时间地保持开发的快速。

**何时重构**

**预备性重构：让添加新功能更容易**

重构的最佳时机就在添加新功能之前。

如果把某些更新数据的逻辑与查询逻辑分开，会更容易避免造成错误的逻辑纠缠。用重构改善这些情况，在同样场合再次出现同样bug的概率也会降低。

**帮助理解的重构：使代码更易懂**

**捡垃圾式重构**

**有计划的重构和见机行事的重构**

预备性重构、帮助理解的重构、捡垃圾式重构------都是见机行事的

**长期重构**

如果想替换掉一个正在使用的库，可以先如果想替换掉一个正在使用的库，可以先引入一层新的抽象，使其兼容新旧两个库的接口。一旦调用方已经完全改为使用这层抽象，替换下面的库就会容易得多。

**复审代码时重构**

与原作者肩并肩坐在一起，一边浏览代码一边重构，体验是最佳的。这种工作方式很自然地导向结对编程：在编程的过程中持续不断地进行代码复审。

**重构的挑战**

**延缓新功能开发**

重构的唯一目的就是让我们开发更快，用更少的工作量创造更大的价值。

有时会看到一个（大规模的）重构很有必要进行，而马上要添加的功能非常小，这时应先把新功能加上，然后再做这次大规模重构。

重构不足的情况远多于重构过度的情况。换句话说，绝大多数人应该尝试多做重构。

重构的意义不在于把代码库打磨得闪闪发光，而是纯粹经济角度出发的考量。我们之所以重构，因为它能让我们更快------添加功能更快，修复bug更快。

**代码所有权**

旧的接口标记为"不推荐使用"（deprecated）。

**分支**

持续集成（Continuous Integration，CI），也叫"基于主干开发"（Trunk-Based
Development）。

**重构、架构和YAGNI**

重构对架构最大的影响在于，通过重构，我们能得到一个设计良好的代码库，使其能够优雅地应对不断变化的需求。"在编码之前先完成架构"这种做法最大的问题在于，它假设了软件的需求可以预先充分理解。

**重构与软件开发过程**

既牢固可靠又能快速响应变化的需求。

**自动化重构**

不仅能处理文本，还能处理语法树，这是IDE相比于文本编辑器更先进的地方。重构工具不仅需要理解和修改语法树，还要知道如何把修改后的代码写回编辑器视图。如果我给一个变量改名，工具会提醒我修改使用了旧名字的注释。能借助语法树来分析和重构程序代码，这是IDE与普通文本编辑器相比具有的一大优势。

**第3章　代码的坏味道**

**神秘命名（Mysterious Name）**

命名是编程中最难的两件事之一\[mf-2h\]。正因为如此，改名可能是最常用的重构手法，包括改变函数声明（用于给函数改名）、变量改名、字段改名。

**重复代码（Duplicated Code）**

**过长函数（Long Function）**

积极地分解函数.

原则：每当感觉需要以注释来说明点什么的时候，我们就把需要说明的东西写进一个独立函数中，并以其用途（而非实现手法）命名。关键不在于函数的长度，而在于函数"做什么"和"如何做"之间的语义距离。

如何确定该提炼哪一段代码呢？一个很好的技巧是：寻找注释。它们通常能指出代码用途和实现手法之间的语义距离。

条件表达式和循环常常也是提炼的信号。你可以使用分解条件表达式处理条件表达式。

对于庞大的switch语句，其中的每个分支都应该通过提炼函数变成独立的函数调用。如果有多个switch语句基于同一个条件进行分支选择，就应该使用以多态取代条件表达式。

应该将循环和循环内的代码提炼到一个独立的函数中。如果你发现提炼出的循环很难命名，可能是因为其中做了几件不同的事。如果是这种情况，请勇敢地使用拆分循环将其拆分成各自独立的任务。

**过长参数列表（Long Parameter List）**

如果可以向某个参数发起查询而获得另一个参数的值，那么就可以使用以查询取代参数去掉这第二个参数。

如果你发现自己正在从现有的数据结构中抽出很多数据项，就可以考虑使用保持对象完整手法，直接传入原来的数据结构。如果有几项参数总是同时出现，可以用引入参数对象将其合并成一个对象。

如果某个参数被用作区分函数行为的标记（flag），可以使用移除标记参数。

使用类可以有效地缩短参数列表。如果多个函数有同样的几个参数，引入一个类就尤为有意义。你可以使用函数组合成类，将这些共同的参数变成这个类的字段。

**全局数据（Global Data）**

封装变量。有少量的全局数据或许无妨，但数量越多，处理的难度就会指数上升。

**可变数据（Mutable Data）**

可以用封装变量来确保所有数据更新操作都通过很少几个函数来进行，使其更容易监控和演进。

如果一个变量在不同时候被用于存储不同的东西，可以使用拆分变量将其拆分为各自不同用途的变量，从而避免危险的更新操作。使用移动语句和提炼函数尽量把逻辑从处理更新操作的代码中搬移出来，将没有副作用的代码与执行数据更新操作的代码分开。设计API时，可以使用将查询函数和修改函数分离。

尽早使用移除设值函数，缩小变量作用域。

**发散式变化（Divergent Change）**

如果某个模块经常因为不同的原因在不同的方向上发生变化，发散式变化就出现了。

提炼拆分。

**霰弹式修改（Shotgun Surgery）**

如果每遇到某种变化，你都必须在许多不同的类内做出许多小修改，你所面临的坏味道就是霰弹式修改。

搬移函数和搬移字段把所有需要修改的代码放进同一个模块里。如果有很多函数都在操作相似的数据，可以使用函数组合成类。如果有些函数的功能是转化或者充实数据结构，可以使用函数组合成变换。如果一些函数的输出可以组合后提供给一段专门使用这些计算结果的逻辑，这种时候常常用得上拆分阶段。

一个常用的策略就是使用与内联（inline）相关的重构------如内联函数（1或是内联类------把本不该分散的逻辑拽回一处。完成内联之后，你可能会闻到过长函数或者过大的类的味道，再用与提炼相关的重构手法将其拆解成更合理的小块。

**依恋情结（Feature Envy）**

模块化，就是力求将代码分出区域，最大化区域内部的交互、最小化跨区域的交互。

一个函数跟另一个模块中的函数或者数据交流格外频繁，远胜于在自己所处模块内部的交流，这就是依恋情结的典型情况。

**数据泥团（Data Clumps）**

总是绑在一起出现的数据真应该拥有属于它们自己的对象。

**基本类型偏执（Primitive Obsession）**

把钱当作普通数字来计算的情况、计算物理量时无视单位（如把英寸与毫米相加）的情况以及大量类似if
(a \< upper && a \> lower)这样的代码。

运用以对象取代基本类型。

**重复的switch （Repeated Switches）**

多态。

**循环语句（Loops）**

？管道操作（如filter和map）

**冗赘的元素（Lazy Element）**

随着重构的进行越变越小，类最后只剩了一个函数。及时删除这个类，使用内联函数或是内联类。

**夸夸其谈通用性（Speculative Generality）**

用不上的装置只会挡你的路，所以，把它搬开吧。

**临时字段（Temporary Field）**

其内部某个字段仅为某种特定情况而设。

**过长的消息链（Message Chains）**

先观察消息链最终得到的对象是用来干什么的，看看能否以提炼函数把使用该对象的代码提炼到一个独立的函数中，再运用搬移函数把这个函数推入消息链。

**中间人（Middle Man）**

某个类的接口有一半的函数都委托给其他类，这样就是过度运用。这时应该使用移除中间人。

**内幕交易（Insider Trading）**

模块之间大量交换数据，因为这会增加模块间的耦合。

在实际情况里，一定的数据交换不可避免，但我们必须尽量减少这种情况，并把这种交换都放到明面上来。

**过大的类（Large Class）**

**异曲同工的类（Alternative Classes with Different Interfaces）**

**纯数据类（Data Class）**

纯数据类：它们拥有一些字段，以及用于访问（读写）这些字段的函数，除此之外一无长物。

**被拒绝的遗赠（Refused Bequest）**

子类应该继承超类的函数和数据。

不愿意支持超类的接口，就不要虚情假意地糊弄继承体系，应该运用以委托取代子类或者以委托取代超类彻底划清界限。

**注释（Comments）**

如果你需要注释来解释一块代码做了什么，试试提炼函数；如果函数已经提炼出来，但还是需要注释来解释其行为，试试用改变函数声明为它改名；如果你需要注释说明某些系统的需求规格，试试引入断言。

**第4章　构筑测试体系**

**自测试代码的价值**

**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试上的时间是最多的。**

一套测试就是一个强大的bug侦测器，能够大大缩减查找bug所需的时间。

撰写测试代码的最好时机是在开始动手编码之前，把注意力集中于接口而非实现。

**测试实例**

**总是确保测试不该通过时真的会失败：在代码中暂时引入一个错误。**

**探测边界条件**

输入：空集合、0、空字符串\... 预期输出：？

**考虑可能出错的边界条件**，把测试火力集中在那儿。

不要因为测试无法捕捉所有的bug就不写测试，因为测试的确可以捕捉到大多数bug。

**第5章　介绍重构名录**

本章主要作用是承上启下，略。

**第6章 第一组重构**

**提炼函数（Extract Function）**

![](/img/refactor.png)

![](/img/refactor-1.png)

**动机**

**将意图与实现分开**：如果你需要花时间浏览一段代码才能弄清它到底在干什么，那么就应该将其提炼到一个函数中，并根据它所做的事为其命名。因为大多数时候根本不需要关心函数如何达成其用途（这是函数体内干的事）

好名字：在一个大函数中，一段代码放着一句注释，提炼成函数，注释往往提示一个好名字。

**做法**

创造一个新函数：以"做什么"而非"怎么做"来命名。

无局部变量，直接提炼成函数；

有局部变量但只读，作为参数传递给目标函数

局部变量被赋值：只在提炼函数中被使用则可直接声明在提炼函数中；在提炼函数外也被使用则可作为提炼函数的返回值；多个变量被修改可考虑返回一个对象或者使用其他重构手法（以查询取代临时变量、拆分变量）

**内联函数（Inline Function）**

![](/img/refactor-2.png)

![](/img/refactor-3.png)

![](/img/refactor-4.png)

**动机**

**间接性可能带来帮助，但非必要的间接性总是让人不舒服。**

某些函数其内容和名称清晰易读

一群函数的组织不甚合理，先内联到一个大函数，再提炼。

**做法**

确定函数不具多态性

找到所有调用点执行替换（重点在于始终小步前进）

**提炼变量（Extract Variable）**

![](/img/refactor-5.png)

![](/img/refactor-6.png)

**动机**

**提供了合适的上下文**：帮助我们将表达式分解为比较容易管理的形式，也便于理解一部分代码是干什么的。

**内联变量（Inline Variable）**

![](/img/refactor-7.png)

![](/img/refactor-8.png)

**动机**

有时候，变量名字并不比表达式本身更具表现力。还有些时候，变量可能会妨碍重构附近的代码。

**改变函数声明（Change Function Declaration）**

![](/img/refactor-10.png)

**动机**

一个好名字能让人一眼看出函数的用途；

函数的参数列表阐述了函数如何与外部世界共处，修改参数列表不仅能增加函数的应用范围，还能改变连接一个模块所需的条件，从而去除不必要的耦合。

**封装变量（Encapsulate Variable）**

![](/img/refactor-15.png)

**动机**

对于所有可变的数据，只要它的作用域超出单个函数，我就会将其封装起来，只允许通过函数访问。数据的作用域越大，封装就越重要。

**变量改名（Rename Variable）**

![](/img/refactor-9.png)

**动机**

解释一段程序在干什么，**对于作用域超出一次函数调用的字段，则需要更用心命名。**

**引入参数对象（Introduce Parameter Object）**

![](/img/refactor-11.png)

**动机**

将数据组织成结构，使数据项之间的**关系更清晰**；

**缩短参数列表**；

**代码一致性**：所有使用该数据结构的函数都可以通过相同的名字来访问其中元素。

改变代码的概念图景，将这些数据结构提升为新的抽象概念

**函数组合成类（Combine Functions into Class）**

![](/img/refactor-12.png)

**动机**

如果发现一组函数形影不离地操作同一块数据（通常是将这块数据作为参数传递给函数），是时候组建一个类了。类能明确地给这些函数提供一个共用的环境，在对象内部调用这些函数可以少传许多参数，从而简化函数调用。

**函数组合成变换（Combine Functions into Transform）**

![](/img/refactor-43.png)

**动机**

在软件中，经常需要把数据"喂"给一个程序，让它**再计算出各种派生信息**。这些派生数值可能会在几个不同地方用到，因此**这些计算逻辑也常会在用到派生数据的地方重复**。把所有计算派生数据的逻辑收拢到一处，这样始终可以在固定的地方找到和更新这些逻辑，避免到处重复。

**函数组合成变换**与**函数组合成类**区别：

如果代码中会对源数据做更新，那么使用类要好得多；如果使用变换，派生数据会被存储在新生成的记录中，一旦源数据被修改，我就会遭遇数据不一致。

**拆分阶段（Split Phase）**

![](/img/refactor-13.png)

**动机**

一段代码在**同时处理两件不同的事**，可以考虑把它**拆分成各自独立的模块**，因为这样到了需要修改的时候，可以单独处理每个主题。

**例子**

重构前：

![](/img/refactor-44.png)

重构后：

提炼函数、引入中转数据结构：

![](/img/refactor-45.png)

**第七章 封装**

**封装记录（Encapsulate Record）**

![](/img/refactor-14.png)

**动机**

对象可以隐藏结构的细节，有助于字段的改名，方便拓展以应对变化。

**封装集合（Encapsulate Collection）**

![](/img/refactor-16.png)

**动机**

封装集合时人们常常犯一个错误：只对集合变量的访问进行了封装，但依然让取值函数返回集合本身。这使得集合的成员变量可以直接被修改，而封装它的类则全然不知，无法介入。

做法：

在类上提供一些修改集合的方法------通常是"添加"和"移除"方法。

**以对象取代基本类型（Replace Primitive with Object）**

![](/img/refactor-46.png)

**以查询取代临时变量（Replace Temp with Query）**

![](/img/refactor-47.png)

**提炼类（Extract Class）**

![](/img/refactor-48.png)

**动机**

如果某些数据和某些函数总是一起出现，某些数据经常同时变化甚至彼此相依，这就表示你应该将它们分离出去。

如果你发现子类化只影响类的部分特性，或如果你发现某些特性需要以一种方式来子类化，某些特性则需要以另一种方式子类化，这就意味着你需要分解原来的类。

**内联类（Inline Class）**

![](/img/refactor-49.png)

**隐藏委托关系（Hide Delegate）**

![](/img/refactor-50.png)

**移除中间人（Remove Middle Man）**

![](/img/refactor-51.png)

"合适的隐藏程度"。

**替换算法（Substitute Algorithm）**

![](/img/refactor-17.png)

**第8章　搬移特性**

另一种类型的重构也很重要，那就是**在不同的上下文之间搬移元素**。

**搬移函数（Move Function）**

![](/img/refactor-18.png)

**任何函数都需要具备上下文环境才能存活**。

搬移函数最直接的一个动因是，它频繁引用其他上下文中的元素，而对自身上下文中的元素却关心甚少，将函数移动到联系更紧密的上下文那么系统别处就可以减少对当前模块的依赖，**获得更好的封装效果。**

整理代码时，发现需要频繁调用一个别处的函数；或者函数内部定义了一个帮助函数，而该帮助函数可能在别的地方也有用处，此时就可以将它搬移到某些更通用的地方。

**是否需要搬移函数常常不易抉择，但决定越难做，通常说明"搬移这个函数与否"的重要性也越低。**

**范例：搬移内嵌函数至顶层**

before：

![](/img/refactor-19.png)

after：

![](/img/refactor-20.png)

**范例：在类之间搬移函数**

before：

![](/img/refactor-52.png)

after：

![](/img/refactor-53.png)

**搬移字段（Move Field）**

![](/img/refactor-54.png)

**范例**

before：

![](/img/refactor-55.png)

after：

![](/img/refactor-56.png)

![](/img/refactor-57.png)

**范例：搬移字段到共享对象**

before：

![](/img/refactor-58.png)

after：

![](/img/refactor-59.png)

![](/img/refactor-60.png)

**搬移语句到函数（Move Statements into Function）**

![](/img/refactor-21.png)

**"消除重复"**：如果发现调用某个函数时，总有一些相同的代码也需要每次执行，则考虑将此段代码合并到函数里头。

如果某些语句与一个函数放在一起更像一个整体，并且更**有助于理解**，则将语句搬移到函数里去。如果它们与函数不像一个整体，但仍应与函数一起执行，可以用提炼函数将语句和函数一并提炼出去。

**范例**

before：

![](/img/refactor-61.png)

after：

![](/img/refactor-62.png)

**搬移语句到调用者（Move Statements to Callers）**

![](/img/refactor-63.png)

随着系统能力发生演进，原先设定的抽象边界总会悄无声息地发生偏移。对于函数来说，这样的边界偏移意味着曾经视为一个整体、一个单元的行为，如今可能已经分化出两个甚至是多个不同的关注点。

**范例**

before：

![](/img/refactor-64.png)

after：

![](/img/refactor-65.png)

**以函数调用取代内联代码（Replace Inline Code with Function Call）**

![](/img/refactor-66.png)

**移动语句（Slide Statements）**

![](/img/refactor-67.png)

让存在关联的东西一起出现，可以使代码更容易理解。

**命令查询分离原则**（Command-Query Separation,CQS原则）：

**查询：**方法返回结果，但不改变任何系统状态(无副作用)。

**命令：**方法没有结果，但会改变系统状态。

优点如下

查询类型的方法，对于调用者来讲不用在顾虑各个查询方法的调用顺序和次数(忽略性能的因素)。

命令类型的方法，从语义上来讲更准确。

**范例**

![](/img/refactor-68.png)

思考：哪些语句可以移动？

**范例：包含条件逻辑的移动**

before：

![](/img/refactor-69.png)

after：

![](/img/refactor-70.png)

**拆分循环（Split Loop）**

![](/img/refactor-71.png)

**范例**

before：

![](/img/refactor-72.png)

after：

![](/img/refactor-73.png)

**以管道取代循环（Replace Loop with Pipeline）**

![](/img/refactor-74.png)

map运算是指用一个函数作用于输入集合的每一个元素上，将集合变换成另外一个集合的过程；filter运算是指用一个函数从输入集合中筛选出符合条件的元素子集的过程。运算得到的集合可以供管道的后续流程使用。

**范例**

before：

![](/img/refactor-75.png)

![](/img/refactor-76.png)

after：

![](/img/refactor-77.png)

**移除死代码（Remove Dead Code）**

![](/img/refactor-78.png)

**第9章　重新组织数据**

**拆分变量（Split Variable）**

![](/img/refactor-22.png)

除"循环变量"和"结果收集变量"外，还有很多变量用于保存一段冗长代码的运算结果，以便稍后使用。这种**变量应该只被赋值一次。**如果它们被赋值超过一次，就意味它们在函数中承担了一个以上的责任。如果变量承担多个责任，它就应该被替换（分解）为多个变量，**保持职责单一**。

**范例：对输入参数赋值**

before：

![](/img/refactor-23.png)

after：

![](/img/refactor-24.png)

**字段改名（Rename Field）**

![](/img/refactor-79.png)

**范例：给字段改名**

before：

![](/img/refactor-80.png)

after：

![](/img/refactor-81.png)

**以查询取代派生变量（Replace Derived Variable with Query）**

![](/img/refactor-82.png)

**范例**

即时计算，不必每次更新。

before：

![](/img/refactor-83.png)

after：

![](/img/refactor-84.png)

![](/img/refactor-85.png)

**范例：不止一个数据来源**

before：

![](/img/refactor-86.png)

after：

![](/img/refactor-87.png)

引入断言：

![](/img/refactor-88.png)

**将引用对象改为值对象（Change Reference to Value）**

不需要共享一个对象。

![](/img/refactor-89.png)

**范例**

before：

![](/img/refactor-90.png)

after：

![](/img/refactor-91.png)

**将值对象改为引用对象（Change Value to Reference）**

共享一个对象。

![](/img/refactor-92.png)

**范例**

before：

![](/img/refactor-93.png)

after：

![](/img/refactor-94.png)

![](/img/refactor-95.png)

存在的问题：构造函数与一个全局的仓库对象**耦合**。

改进的办法：**将仓库对象作为参数传递给构造函数**。

**第10章　简化条件逻辑**

**分解条件表达式（Decompose Conditional）**

![](/img/refactor-25.png)

程序之中，复杂的条件逻辑是最常导致复杂度上升的因素之一。

对于条件逻辑，**将每个分支条件分解成新函数**还可以带来更多好处：可以突出条件逻辑，更清楚地表明每个分支的作用，并且突出每个分支的原因。

注：实际上为提炼函数的一个应用场景。

**范例**

before：

![](/img/refactor-96.png)

after：

![](/img/refactor-97.png)

**合并条件表达式（Consolidate Conditional Expression）**

![](/img/refactor-26.png)

**以卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard
Clauses）**

![](/img/refactor-27.png)

如果两条分支都是正常行为，就应该使用形如if\...else\...的条件表达式；如果某个条件极其罕见，就应该单独检查该条件，并在该条件为真时立刻从函数中返回。这样的单独检查常常被称为"卫语句"（guard
clauses）。

**如果使用if-then-else结构，则对if分支和else分支的重视是同等的；以卫语句取代嵌套条件表达式的精髓就是：给某一条分支以特别的重视。**

"每个函数只能有一个入口和一个出口"的观念未必有用，保持代码清晰才是最关键的。

**范例**

before

![](/img/refactor-28.png)

after

![](/img/refactor-29.png)

**范例：将条件反转**

初始

![](/img/refactor-30.png)

反转

![](/img/refactor-31.png)

合并条件表达式

![](/img/refactor-32.png)

删除可变变量

![](/img/refactor-33.png)

**以多态取代条件表达式（Replace Conditional with Polymorphism）**

![](/img/refactor-34.png)

**引入特例（Introduce Special Case）**

![](/img/refactor-98.png)

"特例"（Special
Case）模式：创建一个特例元素，用以表达对这种特例的共用行为的处理，**从而用一个函数调用取代大部分特例检查逻辑**。

**引入断言（Introduce Assertion）**

![](/img/refactor-99.png)

**第11章 重构API**

**将查询函数和修改函数分离（Separate Query from Modifier）**

![](/img/refactor-100.png)

**范例**

before

![](/img/refactor-101.png)

After

![](/img/refactor-102.png)

![](/img/refactor-103.png)

**函数参数化（Parameterize Function）**

![](/img/refactor-104.png)

范例

before

![](/img/refactor-105.png)

After

![](/img/refactor-106.png)

![](/img/refactor-107.png)

**移除标记参数（Remove Flag Argument）**

![](/img/refactor-108.png)

**"标记参数"是这样的一种参数：调用者用它来指示被调函数应该执行哪一部分逻辑。**

**范例**

Before

![](/img/refactor-109.png)

After

![](/img/refactor-110.png)

**保持对象完整（Preserve Whole Object）**

![](/img/refactor-111.png)

减少函数参数长度，方便后续拓展。

**以查询取代参数（Replace Parameter with Query）**

![](/img/refactor-35.png)

**函数的参数列表应该总结该函数的可变性**，标示出函数可能体现出行为差异的主要方式。和任何代码中的语句一样，**参数列表应该尽量避免重复**，并且参数列表越短就越容易理解。

使用场景：调用函数时传入了一个值，而这个值由函数自己来获得也是同样容易

什么是"同样容易"：函数可以承担这份原本由调用方所承担的"获得正确的参数值"的责任。

什么时候不适用：移除参数可能会给函数体增加不必要的依赖关系。

留意：如果在处理的函数具有**引用透明性**（referential
transparency，即，不论任何时候，只要传入相同的参数值，该函数的行为永远一致），这样的函数既容易理解又容易测试，不会去除参数，让它访问一个可变的全部变量。

**以参数取代查询（Replace Query with Parameter）**

![](/img/refactor-36.png)

好处：改变依赖关系，去掉令人不快的引用。

注意：要考虑责任分配问题，会增加函数调用者的复杂度，而设计接口时又需要考虑易用性。

**移除设值函数（Remove Setting Method）**

![](/img/refactor-112.png)

去除不必要的设值函数。

**以工厂函数取代构造函数（Replace Constructor with Factory Function）**

![](/img/refactor-113.png)

工厂函数的实现更为灵活。

**以命令取代函数（Replace Function with Command）**

![](/img/refactor-114.png)

**以函数取代命令（Replace Command with Function）**

![](/img/refactor-115.png)

处理的逻辑不是特别复杂，则命令对象可能显得费而不惠。

**第12章　处理继承关系**

**函数上移（Pull Up Method）**

![](/img/refactor-116.png)

消除重复代码。

**字段上移（Pull Up Field）**

![](/img/refactor-117.png)

同样也是消除重复代码。

**构造函数本体上移（Pull Up Constructor Body）**

![](/img/refactor-118.png)

提炼各个子类函数中的重复部分至父类中，同样也是消除重复代码。

**函数下移（Push Down Method）**

![](/img/refactor-119.png)

如果超类中的某个函数只与一个（或少数几个）子类有关，那么最好将其从父类中挪走，放到真正关心它的子类中去。

**字段下移（Push Down Field）**

![](/img/refactor-120.png)

如果某个字段只被一个子类（或者一小部分子类）用到，就将其搬移到需要该字段的子类中。

**以子类取代类型码（Replace Type Code with Subclasses）**

![](/img/refactor-121.png)

可以用多态来处理条件逻辑，而不是根据不同的类型码采取不同的行为。

有些字段或函数只对特定的类型码取值才有意义，子类的形式能更明确地表达数据与类型之间的关系。

**移除子类（Remove Subclass）**

![](/img/refactor-122.png)

如果子类的用处太少，可以移除子类，将替换为父类的一个字段。

**提炼超类（Extract Superclass）**

![](/img/refactor-123.png)

目的在于把重复的行为收拢一处。

**折叠继承体系（Collapse Hierarchy）**

![](/img/refactor-124.png)

随着继承体系的演化，有时会发现一个类与其父类差别不大，此时可以把父类和子类合并起来。

**以委托取代子类（Replace Subclass with Delegate）**

![](/img/refactor-125.png)

![](/img/refactor-126.png)

与继承关系相比，使用委托（即组合）关系时接口更清晰、耦合更少。

**以委托取代超类（Replace Superclass with Delegate）**

![](/img/refactor-37.png)

以组合取代继承。

一个经典的误用继承的例子：让栈（stack）继承列表（list）。这个想法的出发点是想复用列表类的数据存储和操作能力。虽说复用是一件好事，但这个继承关系有问题：列表类的所有操作都会出现在栈类的接口上，然而其中大部分操作对一个栈来说并不适用。更好的做法应该是把列表作为栈的字段，把必要的操作委派给列表就行了。

**所以，如果超类的一些函数对子类并不适用，就说明我不应该通过继承来获得超类的功能。**

同时也要避免走弯路：完全避免使用继承，如果符合继承关系的语义条件（超类的所有方法都适用于子类，子类的所有实例都是超类的实例），那么继承是一种简洁又高效的复用机制。

建议：首先（尽量）使用继承，如果发现继承有问题，再使用以委托取代超类。
