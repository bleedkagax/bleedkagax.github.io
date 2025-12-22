---
title: 0_refactor (EN)
name: 0_refactor_en
date: 2024-09-05
draft: false
tags:
  - Snippet
share: "true"
---
Essentially, **refactoring is improving the design of code after it's been written**.

If you want to add a feature to a program, but find that the code isn't easy to change due to a lack of good structure, refactor that program first so that it's easier to add the feature, and then add the feature.

It is the change in **requirements** that makes refactoring necessary.

The refactoring technique is to **modify the program at a tiny pace**. If you make a mistake, it's easy to spot it.

The test of good code is how easily one can modify it.

To summarize:

The key takeaways for efficient and organized refactoring are: **Smaller steps lead to faster progress**, keep your code in a working state forever, and small changes add up to a much better system design. Refactoring is not a “silver bullet”, but it can be considered a “silver tongs”, which can help you always have good control over your code. Refactoring is a tool.

# **1. Bad taste in code**

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

![](/img/0_refactor.png)

![](/img/0_refactor-1.png)

**Separate Intent from Implementation**: If you need to spend time browsing through a piece of code to figure out what it's actually doing, then you should distill it down to a function and name it according to what it does. Because most of the time you don't need to care about how the function accomplishes its purpose (that's what the function does inside)

Good names: in a big function, a piece of code puts a comment that distills it into a function, and the comment often suggests a good name.

**Practice***

**Create a new function: name it after “what it does”, not “how it does it”**.

Without local variables, refine directly into a function;

with local variables but read-only, passed as arguments to the target function

Local variables are assigned values: declared directly in the refining function if they are used only within the refining function; used outside the refining function as the return value of the refining function; multiple variables are modified by considering returning an object or using other refactoring techniques (querying instead of temporary variables, splitting variables)

## 2\. **Inline Function**

![](/img/0_refactor-2.png)

![](/img/0_refactor-3.png)

![](/img/0_refactor-4.png)

**Indirectness may help, but non-essential indirectness is always uncomfortable.**

Some functions have their contents and names clear and easy to read

A group of functions is not well organized, inline to one big function first, then refine.

## 3\. **Extract Variable**

![](/img/0_refactor-5.png)

![](/img/0_refactor-6.png)

**Variables provide the right context**: they help us break up expressions into more manageable forms, and also make it easier to understand what a portion of the code is doing.

According to The Tao of Tidy Code, “**Use explanatory variables to break up the computation into a series of well-named intermediate values**”.

## 4\. **Inline Variable**

![](/img/0_refactor-7.png)

![](/img/0_refactor-8.png)

Sometimes, **variable names are no more expressive** than the expression itself. There are also times when variables may get in the way of refactoring nearby code.

## 5\. **Rename Variable**

![](/img/0_refactor-9.png)

Explain what a piece of program is doing, **and be more careful naming fields whose scope extends beyond a single function call.**

## 6\. **Change Function Declaration**

![](/img/0_refactor-10.png)

A good name gives an immediate indication of what the **function is used for**;

The argument list of a **function** describes how the function coexists with the outside world, and modifying the argument list not only increases the scope of the function's application, but also removes unnecessary coupling by changing the conditions required to connect a module.

**"A good way to improve the name of a function: write a comment describing what the function is used for, then turn that comment into the name of the function.”**

## 7\. **Introduce Parameter Object**

![](/img/0_refactor-11.png)

Organize data into structures that make the **relationships** between data items clearer;

**shorter parameter list**;

**Code consistency**: all functions that use this data structure can access elements of it by the same name.

Changing the conceptual picture of the code elevates these data structures to new abstractions

## 8\. **Combine Functions into Class**

![](/img/0_refactor-12.png)

**If you find a group of functions that manipulate the same piece of data (usually by passing that piece of data as a parameter to the function), it's time to form a class**. Classes explicitly provide a common environment for these functions, and calling them from within an object simplifies function calls by passing many fewer arguments.

## 9\. **Split Phase**

![](/img/0_refactor-13.png)

A piece of code that handles two different things at **simultaneously** can be considered to be **split into its own separate modules**, because then each topic can be handled separately when it comes time to make changes.

# **3. Encapsulate**

## 1\. **Encapsulate Record**

![](/img/0_refactor-14.png)

Objects can hide details of the structure, **help with renaming of fields**, and are easy to expand to cope with changes.

## 2\. **Encapsulate Variable**

![](/img/0_refactor-15.png)

For all mutable data, as long as its scope extends beyond a single function, I encapsulate it and only allow access through the function. The larger the scope of the data, the more important encapsulation becomes.

## 3\. **Encapsulate Collection**

![](/img/0_refactor-16.png)

One mistake people often make when encapsulating collections is that ** only encapsulates access to the collection variables, but still lets the fetch function return the collection itself. This allows the collection's member variables to be modified directly, while the class encapsulating it is completely unaware and unable to intervene**.

Practice:

Provide methods to modify the collection on the class ------**Usually “add” and “remove” methods to unify the management**.

## 4\. **Substitute Algorithm**

![](/img/0_refactor-17.png)

# **3. Move Characteristics**

Another type of refactoring that is also important is **moving elements between contexts**.

Thinking...
We just translate "搬移函数（Move Function）" to English. Keep the heading. So output:

## 1. **Move Function (Move Function?)** Actually the translation likely is "Move Function (Move Function)"? Wait Chinese: "搬移函数（Move Function）". The parenthesis is English already "Move Function". So translation: "Move Function". Probably keep the same. So final: 

## 1. **Move Function** 

Yes.
...done thinking.

## 1. **Move Function**

![](/img/0_refactor-18.png)

Thinking...
We need to translate: "**任何函数都需要具备上下文环境才能存活**。" into English. Preserve markdown structure. So we translate inside the bold. The text is Chinese: "任何函数都需要具备上下文环境才能存活". Means "Any function needs a contextual environment to survive." Let's produce that.

We output only the markdown.
...done thinking.

**Any function needs a contextual environment to survive.**

Thinking...
We need to translate into English. Keep Markdown. The text has Chinese. Let's translate.

Original:

搬移函数最直接的一个动因是，**它频繁引用其他上下文中的元素，而对自身上下文中的元素却关心甚少**，将函数移动到联系更紧密的上下文那么系统别处就可以减少对当前模块的依赖，**获得更好的封装效果。**

We need to preserve **bold** formatting. Also keep line breaks. There is a period. Let's produce English.

Possible translation: "One of the most direct reasons for moving a function is that **it frequently references elements from other contexts while paying little attention to elements within its own context**. By moving the function to a more tightly coupled context, other parts of the system can reduce their dependence on the current module, thereby **achieving better encapsulation**."

We need preserve line breaks: The original text seems one paragraph with two bold segments. In Markdown, line break may be before '将函数移动到联系更紧密的上下文那么系统别处就可以减少对当前模块的依赖，**获得更好的封装效果。**' There is maybe a line break after '少' but not sure. They inserted a line break? The snippet: 
```
搬移函数最直接的一个动因是，**它频繁引用其他上下文中的元素，而对自身上下文中的元素却关心甚少**，将函数移动到联系更紧密的上下文那么系统别处就可以减少对当前模块的依赖，**获得更好的封装效果。**
```
No line break inside. So we produce single line.

Let's produce the translated Markdown.
...done thinking.

One of the most direct reasons for moving a function is that **it frequently references elements from other contexts while paying little attention to elements within its own context**. By moving the function to a more tightly coupled context, other parts of the system can reduce their dependency on the current module, thereby **achieving better encapsulation**.

Thinking...
We need to translate Chinese Markdown into English, preserving structure, ordering, code blocks, etc. The Markdown given: "整理代码时，发现需要**频繁调用一个别处的函数**；或者函数内部定义了一个帮助函数，而该帮助函数可能**在别的地方也有用处**，此时就可以将它搬移到某些更通用的地方。"

We need to translate to English. It's a paragraph with emphasis (**). So translate accordingly. Let's produce:

"When refactoring code, you may find that you need to **frequently call a function defined elsewhere**; or a function defines a helper function, which may also be **useful in other contexts**; in that case, you can move it to a more generic location."

We must preserve Markdown. So keep **bold** markers. Also line breaks as possible. The original had line break at end of sentence? It ends with a period. So we produce a single paragraph.

Thus output:

When refactoring code, you may find that you need to **frequently call a function defined elsewhere**; or a function defines a helper function, which may also be **useful in other contexts**; in that case, you can move it to a more generic location.

Let's ensure formatting: it's plain paragraph, no code block. So fine.
...done thinking.

When refactoring code, you may find that you need to **frequently call a function defined elsewhere**; or a function defines a helper function, which may also be **useful in other contexts**; in that case, you can move it to a more generic location.

Thinking...
We need translate to English, preserve structure. The text: "**是否需要搬移函数常常不易抉择，但决定越难做，通常说明"搬移这个函数与否"的重要性也越低。**" Means: "**Whether to move a function is often a difficult decision, but the more difficult the decision, usually indicates that the importance of whether to move the function is lower.**"

We should keep the Markdown formatting: bold (**). So final output: **Whether to move a function is often a difficult decision, but the harder the decision, the more it usually indicates that the importance of whether to move the function is lower.** Let's be precise: "whether to move the function" might be "moving the function". The original uses Chinese. The translation: "**Whether to move a function is often hard to decide; the more difficult the decision, the more it usually indicates that the importance of moving or not moving that function is lower.**"

Make it natural: "**Whether to move a function is often hard to decide, but the harder the decision, the more it usually indicates that the importance of moving (or not moving) that function is lower.**"

Better: "**Whether to move a function is often hard to decide, but the harder the decision, the more it typically indicates that the importance of moving or not moving that function is lower.**"

Let's produce.
...done thinking.

**Whether to move a function is often hard to decide, but the harder the decision, the more it typically indicates that the importance of moving (or not moving) that function is lower.**

Thinking...
We need to translate to English, preserve Markdown. The phrase is Chinese: "**范例：搬移内嵌函数至顶层**". Translation: "**Example: Move nested functions to top level**" or "Example: Moving nested functions to the top level". Keep bold. So output:

**Example: Move nested functions to top level**. No code blocks. Just that line.
...done thinking.

**Example: Move nested functions to top level**

before：

Thinking...
We need to translate to English. The content: "计算两点之间距离的函数在别处也有调用". That translates to "The function that calculates the distance between two points is also called elsewhere." So final Markdown: same. Let's produce.
...done thinking.

The function that calculates the distance between two points is also called elsewhere.

![](/img/0_refactor-19.png)

after：

![](/img/0_refactor-20.png)

Thinking...
We just translate "搬移语句到函数" to English. Also the parentheses: "Move Statements into Function". It's already provided. We need to translate entire Markdown: the header "## 2. **搬移语句到函数（Move Statements into Function）**". So the translation: "## 2. **Move Statements into Function**". But we need to preserve the Chinese phrase? The instruction says translate into English. So we replace the Chinese text with English. Keep the parentheses part maybe. But we should produce: "## 2. **Move Statements into Function**". Also maintain the numbering. Probably remove parentheses part. It's already the translation. So final: "## 2. **Move Statements into Function**".
...done thinking.

## 2. **Move Statements into Function**

![](/img/0_refactor-21.png)

Thinking...
We need to translate into English. The content: **"消除重复"**：如果发现调用某个函数时，总有一些相同的代码也需要每次执行，则考虑将此段代码合并到函数里头。

So translation: **"Eliminate duplication"**: If you find that when calling a function, there's some identical code that also needs to be executed each time, consider merging that code into the function.

Preserve markdown. So:

**"Eliminate duplication"**: If you find that when calling a function, there's some identical code that also needs to be executed each time, consider merging that code into the function.

We need to keep line breaks. There's one line. Should we preserve the backticks? There's none. So just translate.

Return ONLY translated Markdown.
...done thinking.

**"Eliminate duplication"**: If you find that when calling a function, there is some identical code that also needs to be executed each time, consider merging that code into the function.

Thinking...
We need to translate into English. Preserve Markdown. It's Chinese with emphasis. So translation:

**If certain statements are more like a whole when placed together with a function and are more helpful for understanding, move the statements into the function.** If they don't seem to form a whole with the function but should still execute together, you can use **refactor function to extract the statements and function together.**

But need proper phrasing. Also maintain bold formatting. Also keep line breaks.

Original:

**如果某些语句与一个函数放在一起更像一个整体**，并且更**有助于理解**，则将语句搬移到函数里去。**如果它们与函数不像一个整体**，但仍应与函数一起执行，可以用**提炼函数将语句和函数一并提炼出去**。

So translation:

**If certain statements are more like a whole when placed together with a function and are more helpful for understanding, move those statements into the function.** **If they don't form a whole with the function, but still should be executed together, you can use a refactoring function to extract both the statements and the function.**

But keep bold around each clause? In original, each part is bold separately. So in translation, we need to preserve same bold segments.

Thus we need to produce:

**If certain statements together with a function are more like a whole, and more helpful for understanding, then move the statements into the function.** **If they are not like a whole with the function, but still should be executed together, you can use a refactoring function to extract both the statements and the function together.**

Also keep line breaks: maybe single line? They originally had line break after first sentence. Actually original has a period then a new line. So keep same.

Thus:

**If certain statements together with a function are more like a whole and more helpful for understanding, then move the statements into the function.** **If they are not like a whole with the function, but should still be executed together, you can use a refactoring function to extract both the statements and the function together.**

Ok.
...done thinking.

**If certain statements together with a function are more like a whole and more helpful for understanding, then move the statements into the function.** **If they are not like a whole with the function, but should still be executed together, you can use a refactoring function to extract both the statements and the function together.**

Thinking...
We need to translate into English. The content: "**五. 重新组织数据**" The numbering: "五" is "5" or "V"? Usually Chinese numbering for sections: "五" is "5". So translation: "**5. Reorganize Data**" Might be "Reorganize Data". We'll produce "**5. Reorganize Data**".

We must keep Markdown structure. So output: "**5. Reorganize Data**"

Check no code blocks. So just output that line.
...done thinking.

**5. Reorganize Data**

Thinking...
The user wants translation into English. The content: "1. **拆分变量（Split Variable）**". Translate to "1. **Split Variable**". Keep numbering. Should preserve Markdown structure. Output only the translated Markdown. No additional explanation. Should keep line break.

So output: "1. **Split Variable**".
...done thinking.

1. **Split Variable**

![](/img/0_refactor-22.png)

Thinking...
We need to translate Chinese markdown to English. Preserve structure. The text:

除"循环变量"和"结果收集变量"外，还有很多变量用于保存一段冗长代码的运算结果，以便稍后使用。这种**变量应该只被赋值一次。**如果它们被赋值超过一次，就意味它们在函数中承担了一个以上的责任。如果变量承担多个责任，它就应该被替换（分解）为多个变量，**保持职责单一**。

We need to keep bold formatting. The Chinese "除" etc. translation: "Apart from loop variables and result collection variables, there are many other variables used to store the results of a lengthy code block for later use. These variables should only be assigned once. If they are assigned more than once, it means they carry more than one responsibility in the function. If a variable has multiple responsibilities, it should be replaced (decomposed) into multiple variables, keeping responsibilities single."

Need to preserve Markdown: The bold parts use **. The Chinese punctuation. Keep line breaks. So we output:

Apart from "loop variables" and "result collection variables", there are many other variables used to store the results of a lengthy block of code for later use. These **variables should only be assigned once**. If they are assigned more than once, it means they carry more than one responsibility in the function. If a variable has multiple responsibilities, it should be replaced (decomposed) into multiple variables, keeping **single responsibility**.

But we need to keep the structure: it's one paragraph. The original had two line breaks? Actually the original had: "除...。**变量应该只被赋值一次。**如果...". So it's one paragraph. We'll output same.

Make sure to not translate URLs or code, but none here.

Let's produce final answer.
...done thinking.

Apart from “loop variables” and “result collection variables”, there are many other variables used to store the results of a lengthy block of code for later use. These **variables should only be assigned once**. If they are assigned more than once, it means they carry more than one responsibility in the function. If a variable has multiple responsibilities, it should be replaced (decomposed) into multiple variables, keeping **single responsibility**.

Thinking...
We need to translate the given Markdown into English. The original is Chinese: "**范例：对输入参数赋值**". That translates to "**Example: Assigning values to input parameters**" or "Example: Assigning values to input parameters". Probably maintain capitalization. Use same Markdown bold formatting. So output:

**Example: Assigning values to input parameters**.
...done thinking.

**Example: Assigning values to input parameters**

before：

![](/img/0_refactor-23.png)

after：

![](/img/0_refactor-24.png)

Thinking...
We need translate Markdown. The input is:

**六. 简化条件逻辑**

We need to translate to English: "**Six. Simplifying Conditional Logic**". But need to preserve Markdown. The title "六" meaning "Six" (the number six). "简化条件逻辑" meaning "Simplify Conditional Logic" or "Simplifying Conditional Logic". Probably "Simplifying Conditional Logic".

Thus:

**Six. Simplifying Conditional Logic**

Return that.
...done thinking.

**Six. Simplifying Conditional Logic**

Thinking...
We need to translate the markdown. Original text: "1\. **分解条件表达式（Decompose Conditional）**". That is "1. **Decompose Conditional Expression (Decompose Conditional)**" but maybe the original is "分解条件表达式（Decompose Conditional）". So translation: "1. **Decompose Conditional Expression (Decompose Conditional)**". But they might want the translation of Chinese to English. The phrase "分解条件表达式" is "Decompose Conditional Expression". The parentheses already contain English "Decompose Conditional". So we can translate the Chinese part. So the line becomes: "1. **Decompose Conditional Expression (Decompose Conditional)**". Should we preserve the dot after 1? Yes. So "1\. **Decompose Conditional Expression (Decompose Conditional)**". Let's produce exactly that.

We must not change code blocks or inline code, but no code here.

Thus final answer: "1. **Decompose Conditional Expression (Decompose Conditional)**".

Check formatting: "1\. **...**". In markdown, escaping dot not necessary but it's fine.

Thus output.
...done thinking.

1\. **Decompose Conditional Expression (Decompose Conditional)**

![](/img/0_refactor-25.png)

Thinking...
We need to translate the Markdown to English, preserving structure. The original is just a single sentence in Chinese: "程序之中，复杂的条件逻辑是最常导致复杂度上升的因素之一。"

We translate: "In programs, complex conditional logic is one of the most common factors that increase complexity." Ensure punctuation. The structure: It's just text, not heading or list. So return that line.
...done thinking.

In programs, complex conditional logic is one of the most common factors that increase complexity.

Thinking...
We need to translate the Chinese text into English, preserving Markdown. The text is:

"对于条件逻辑，**将每个分支条件分解成新函数**还可以带来更多好处：可以突出条件逻辑，更清楚地表明每个分支的作用，并且突出每个分支的原因。"

We translate:

"For conditional logic, **breaking down each branch condition into a new function** can also bring more benefits: it can highlight the conditional logic, more clearly indicate the purpose of each branch, and emphasize the reasons for each branch."

We need to preserve Markdown formatting: the bold around "将每个分支条件分解成新函数" should become bold around "breaking down each branch condition into a new function". The colon remains.

So the translation:

"For conditional logic, **breaking down each branch condition into a new function** can also bring more benefits: it can highlight the conditional logic, more clearly indicate the purpose of each branch, and emphasize the reasons for each branch."

Make sure to keep line breaks; the text is one paragraph. So the final output: the Markdown text exactly.

Thus output only the translated markdown.
...done thinking.

For conditional logic, **breaking down each branch condition into a new function** can also bring more benefits: it can highlight the conditional logic, more clearly indicate the purpose of each branch, and emphasize the reasons for each branch.

Thinking...
We need to translate: "注：实际上为**提炼函数**的一个应用场景。" into English. The text: "Note: this is actually an application scenario of **refactoring into functions**." Probably "Note: This is actually an application scenario for **extract function**." "提炼函数" is "extract function" or "refactor into function". In Chinese, "提炼函数" refers to "extract function" refactoring. So translation: "Note: This is actually an application scenario for **extract function**." The phrase is a single line. Keep Markdown. The bold text remains. So output:

Note: This is actually an application scenario for **提炼函数**? But we must translate. Should we translate the bold content? It says not to translate code blocks or inline code. But bold text is not code. We should translate bold content too? The rule says do NOT translate code blocks or inline code. Bold is not code. So we should translate. "提炼函数" should become "extract function" or "function extraction". So bold becomes **extract function**. So the line: "Note: This is actually an application scenario for **extract function**." But we should preserve Chinese? The instruction: "Translate the following Markdown into English." So everything should be English. Yes.

So final Markdown: "Note: This is actually an application scenario for **extract function**." Ensure Markdown line. Probably add an asterisk? Use same bullet? The original had no bullet. So just a line.

Return only translated Markdown.
...done thinking.

Note: This is actually an application scenario for **extract function**.

Thinking...
We just need to translate the Markdown text. The content: "2\. **合并条件表达式（Consolidate Conditional Expression）**". We need to translate Chinese "合并条件表达式" to English "Consolidate Conditional Expression"? Actually the parenthetical already shows English. We should translate the whole heading. The heading has number 2. So output:

"2. **Consolidate Conditional Expression**" or "2. **Consolidate Conditional Expression (Consolidate Conditional Expression)**"? The original includes the Chinese text and the English translation in parentheses. We probably translate to English: "2. **Consolidate Conditional Expression**". Remove the Chinese part. The parentheses likely optional? The rule: translate the Markdown into English. So we replace Chinese with English, but the English is already there. So final: "2. **Consolidate Conditional Expression**". Keep the parentheses removed. Let's output that.
...done thinking.

2. **Consolidate Conditional Expression**

![](/img/0_refactor-26.png)

Thinking...
We need to translate given Markdown into English. The Markdown: "3\. **以卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard Clauses）**"

We need to preserve Markdown structure. It's a heading number 3, with bold. The Chinese part: "以卫语句取代嵌套条件表达式". It says "Replace Nested Conditional with Guard Clauses" (English translation given). So we should produce the translated Markdown: "3. **Replace Nested Conditional with Guard Clauses**". The Chinese phrase should be replaced with translation, but the part in parentheses is already translation? The original includes Chinese phrase then parentheses of English translation. We need to translate the entire line into English. So we likely output: "3. **Replace Nested Conditional with Guard Clauses**". That would match the rules. So output that line. No extra formatting. Ensure it's exactly as Markdown. So final answer is:

```
3. **Replace Nested Conditional with Guard Clauses**
```

But we don't need triple backticks, just the line. The instruction: "Return ONLY translated Markdown." So just the line. Should we preserve the number 3? Yes. So output: `3. **Replace Nested Conditional with Guard Clauses**`. Good.
...done thinking.

3. **Replace Nested Conditional with Guard Clauses**

![](/img/0_refactor-27.png)

Thinking...
We need to translate the Chinese markdown into English while preserving structure. There's only a single paragraph.

Original: "如果两条分支都是正常行为，就应该使用形如if\...else\...的条件表达式；如果某个条件极其罕见，就应该单独检查该条件，并在该条件为真时立刻从函数中返回。**这样的单独检查常常被称为"卫语句"（guard
clauses）**。"

We must not translate code blocks or inline code. There is inline code "if\...else\...". That is inside backslashes? It's `if\...else\...` inside the sentence, not code block. They used backslashes maybe to escape ellipsis. It's not code block. It's inline code? It is inside backticks? The given: "形如if\...else\...的条件表达式". There are no backticks. So no inline code.

Thus we can translate normally.

English translation: "If both branches represent normal behavior, a conditional expression of the form if … else … should be used; if a condition is extremely rare, it should be checked separately, and the function should return immediately when that condition is true. **Such separate checks are often referred to as "guard clauses" (guard clauses).**" Wait double. We can translate properly.

"Such separate checks are often referred to as 'guard clauses' (guard clauses)." Might keep original Chinese phrase? The phrase "卫语句" is the Chinese term. The translation: "guard clauses".

We need to preserve formatting: ** ... ** for bold. Also link? None.

The Chinese text includes a line break before "clauses" in "guard\nclauses". That is just a line break inside the sentence. We keep that as a line break. In markdown, we might need to preserve line breaks. So we should maintain the same line break.

So output:

If both branches represent normal behavior, a conditional expression of the form if … else … should be used; if a condition is extremely rare, it should be checked separately, and the function should return immediately when that condition is true. **Such separate checks are often referred to as "guard clauses" (guard\nclauses).**

We need to preserve the line break before "clauses"? In original, "guard\nclauses" within parentheses. The newline may be intentional. We keep it.

Thus final markdown: (just one paragraph)

Let's produce.

...done thinking.

If both branches represent normal behavior, a conditional expression of the form `if … else …` should be used; if a condition is extremely rare, it should be checked separately, and the function should return immediately when that condition is true. **Such separate checks are often referred to as "guard clauses" (guard\nclauses).**

Thinking...
We need to translate to English. The text: "**如果使用if-then-else结构，则对if分支和else分支的重视是同等的；以卫语句取代...**" So the translation: "**If you use an if-then-else structure, then the importance of the if branch and the else branch is equal; the essence of replacing a nested conditional expression with a guard statement is to give a particular branch special attention.**"

But we must preserve markdown bold. So output same: **...**.

Let's produce translation.
...done thinking.

**If you use an if‑then‑else structure, the importance given to the if branch and the else branch is equal; the essence of replacing a nested conditional expression with a guard statement is to give a particular branch special emphasis.**

Thinking...
The user wants to translate the given Markdown into English, following rules: preserve structure, no translation of code blocks or inline code. Here the content is just a sentence, no code. The Chinese text: "每个函数只能有一个入口和一个出口"的观念未必有用，**保持代码清晰才是最关键的**。

Translate: The notion that "each function can have only one entry and one exit" may not be useful; **keeping the code clear is the most critical**.

Need preserve Markdown. The bold part is **保持代码清晰才是最关键的**; we translate and keep bold. So final: "The notion that 'each function can have only one entry and one exit' may not be useful; **keeping the code clear is the most important**." or "the most critical." I'll choose "most important" or "most critical". Keep structure: line break? The original has quotes inside sentence. We'll translate. The output must be just the translated markdown. So:

The notion that “each function can have only one entry and one exit” may not be useful; **keeping the code clear is the most critical**.

Add a line break? The original has no extra line breaks except maybe space. We'll just keep a single line.

Return ONLY translated Markdown.

Let's produce.
...done thinking.

The notion that “each function can have only one entry and one exit” may not be useful; **keeping the code clear is the most critical**.

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: - Preserve Markdown structure and ordering. - Do NOT translate code blocks (` ```...```) or inline code in backticks. - Do NOT alter URLs, links, or image paths. - Keep line breaks as much as possible. Return ONLY translated Markdown.

Markdown:
**范例**

So the original Markdown is: "**范例**". This is bold "范例" meaning "Example". So translate into English. Keep Markdown. So "**Example**". Should be bold. Return only that. Ensure no extra. So answer: **Example**.
...done thinking.

**Example**

before

![](img/0_refactor-28.png)

after

![](img/0_refactor-29.png)

Thinking...
We need to translate the given markdown into English. The text is Chinese: "**范例：将条件反转**". That means "**Example: Reverse the Condition**". We need to keep Markdown. So output: **Example: Reverse the Condition**. Should preserve bold. That is it.
...done thinking.

**Example: Reverse the Condition**

Thinking...
We need to translate the given markdown into English. The markdown contains "初始" which means "initial" or "start". Probably we translate "初始" to "Initial" or "Start". The title may be "Initial". But we need to preserve Markdown structure and ordering. The markdown given is just "初始". That's presumably a header? But there's no header marker (#). It's just a line. So we translate that line to "Initial". So the output should be "Initial". That is it. No code blocks. So final answer: just the translated markdown.

...done thinking.

Initial

![](img/0_refactor-30.png)

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: - Preserve Markdown structure and ordering. - Do NOT translate code blocks (```) or inline code in backticks. - Do NOT alter URLs, links, or image paths. - Keep line breaks as much as possible. Return ONLY translated Markdown. Markdown: 反转". The content is just "反转". That's Chinese for "reverse" or "invert" maybe. In context, maybe "Reverse" or "Invert". The translation should be "Reverse". So output just "Reverse". Keep no other formatting. Ensure it's a Markdown but just a line. So final answer: Reverse.
...done thinking.

Reverse

![](/img/0_refactor-31.png)

Thinking...
We need to translate the Markdown into English. The content: "合并条件表达式" which means "Merge Conditional Expressions". Likely heading. But we don't see heading marker (#). The markdown snippet is just a line. Probably it's a heading. Without context, translate as "Merge Conditional Expressions". Should preserve markdown. But original had no markdown syntax. We keep as is: "Merge Conditional Expressions". No code blocks. Just output.
...done thinking.

Merge Conditional Expressions

![](/img/0_refactor-32.png)

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: ... Return ONLY translated Markdown." The Markdown content is:

删除可变变量

So just "删除可变变量" -> "Delete mutable variable" or "Remove mutable variable". In Chinese "删除可变变量" likely means "Delete mutable variable". So output: Delete mutable variable

But need preserve markdown structure: it's a header? No markdown heading marker. Just a line. So output exactly "Delete mutable variable". Probably just the translated text.
...done thinking.

Delete mutable variable

![](/img/0_refactor-33.png)

Thinking...
The task: translate the Markdown into English. It's short. The original:

"4\. **以多态取代条件表达式（Replace Conditional with Polymorphism）**"

We need to preserve Markdown. So output:

"4. **Replace Conditional with Polymorphism**"

The Chinese part within parentheses already has English translation. But maybe we should translate the Chinese as well. It says "以多态取代条件表达式" which means "Replace Conditional with Polymorphism". The parentheses already have the translation. So we could keep that, but we could also translate entire phrase. They want translation of Markdown into English. So likely they want the whole heading translated: "4. **Replace Conditional with Polymorphism**". The parentheses translation already there.

Thus output that. Ensure not to alter code blocks etc. No code. So just that line.

Return ONLY translated Markdown.

Thus: 4. **Replace Conditional with Polymorphism**.
...done thinking.

4. **Replace Conditional with Polymorphism**

![](/img/0_refactor-34.png)

Thinking...
The user wants translation of Markdown into English. The content is just "**七. 重构API**". That's Chinese "Seven. Refactor API". So translation: "**Seven. Refactor API**". They want preserve Markdown structure and ordering, don't translate code blocks or inline code. There are no code blocks. Just the heading. So output: "**Seven. Refactor API**". They said "Return ONLY translated Markdown." So final answer is that line.
...done thinking.

**Seven. Refactor API**

Thinking...
We need to translate given Markdown into English, preserving structure. The markdown is just "**以查询取代参数（Replace Parameter with Query）**". That means it's bold text: "以查询取代参数（Replace Parameter with Query）". So we translate to English: "**Replace Parameter with Query**". Should we keep parentheses? The original has Chinese then parentheses with English translation. We want to translate the whole line: so it might be "**Replace Parameter with Query**". But maybe keep the Chinese? The instruction: translate the following Markdown into English. So we replace the Chinese text with English. So final output: "**Replace Parameter with Query**". Let's output that.
...done thinking.

**Replace Parameter with Query**

![](/img/0_refactor-35.png)

Thinking...
We need to translate to English. Preserve Markdown structure. The input:

**函数的参数列表应该总结该函数的可变性**，标示出函数可能体现出行为差异的主要方式。和任何代码中的语句一样，**参数列表应该尽量避免重复**，并且参数列表越短就越容易理解。

We need to translate Chinese to English. Preserve ** bold. So:

**The function's parameter list should summarize the function's variability**, indicating the main ways the function might exhibit behavioral differences. As with any statement in code, **the parameter list should avoid repetition as much as possible**, and the shorter the parameter list, the easier it is to understand.

We need to maintain line breaks. Input has a single line? There's a Chinese sentence. There's no line break in original except at end? Actually input: "**函数的参数列表应该总结该函数的可变性**，标示出函数可能体现出行为差异的主要方式。和任何代码中的语句一样，**参数列表应该尽量避免重复**，并且参数列表越短就越容易理解。"

We preserve line breaks as much as possible. But original has no line breaks except maybe line breaks at the end? We'll produce a single paragraph.

Return ONLY translated Markdown. Let's produce:

**The function's parameter list should summarize the function's variability**, indicating the main ways the function might exhibit behavioral differences. As with any statement in code, **the parameter list should avoid repetition as much as possible**, and the shorter the parameter list, the easier it is to understand.

That's it.
...done thinking.

**The function's parameter list should summarize the function's variability**, indicating the main ways the function might exhibit behavioral differences. As with any statement in code, **the parameter list should avoid repetition as much as possible**, and the shorter the parameter list, the easier it is to understand.

Thinking...
We need to translate the Chinese text into English. The markdown has a heading? Actually it's just a paragraph: "使用场景：调用函数时传入了一个值，而这个值由函数自己来获得也是同样容易". We translate to: "Use case: Passing a value to a function during a call, and having the function obtain that value itself is equally easy." Or more natural: "Use case: When a value is passed into a function call, and that value is also obtained by the function itself, it is just as easy." Let's produce the markdown unchanged. So output the translated paragraph.

Return only the translated markdown.
...done thinking.

Use case: When a value is passed into a function call, and that value is also obtained by the function itself, it is just as easy.

Thinking...
We need to translate the given Chinese Markdown into English. The content is: "什么是"同样容易"：函数可以承担这份原本由调用方所承担的"获得正确的参数值"的责任。"

We must preserve Markdown structure: it has a header maybe? Let's see: It's a sentence, no explicit heading syntax (#). It's plain text.

We need to translate to English: "What is '同样容易'?: The function can take on the responsibility of 'obtaining the correct parameter values' which was originally borne by the caller."

But "同样容易" maybe "similarly easy" or "equally easy"? The translation: "What is '同样容易': The function can take on the responsibility of 'obtaining the correct parameter value' that was originally borne by the caller."

Better: "What is '同样容易': A function can assume the responsibility of 'obtaining the correct parameter values', which was originally borne by the caller."

We keep no code blocks. No special formatting. So final output is just that sentence.

Let's produce.
...done thinking.

What is “同样容易”: a function can assume the responsibility of “obtaining the correct parameter values,” which was originally borne by the caller.

Thinking...
We need to translate the provided Markdown into English. The original is Chinese: "什么时候不适用：移除参数可能会给函数体增加不必要的依赖关系。"

We preserve Markdown structure; there's a header or maybe a bullet? The original has "什么时候不适用：移除参数可能会给函数体增加不必要的依赖关系。" That looks like a list item or a heading? It's "什么时候不适用：" then sentence. This could be a subheading. But no markup before it. The text is plain. We translate: "When not applicable: Removing a parameter might add unnecessary dependencies to the function body." Or "When it doesn't apply: Removing parameters may add unnecessary dependencies to the function body." The phrase "什么时候不适用" literally "When not applicable". The colon indicates it's a heading. We'll translate: "When it's not applicable:" etc.

The rest: "移除参数可能会给函数体增加不必要的依赖关系。" -> "Removing a parameter may introduce unnecessary dependencies into the function body."

So the final output: "When not applicable: Removing a parameter may introduce unnecessary dependencies into the function body." That is the translation. We should preserve the line breaks.

Thus output:

When not applicable: Removing a parameter may introduce unnecessary dependencies into the function body.

But keep the same line break? The original had a single line. So we output one line.
...done thinking.

When not applicable: Removing a parameter may introduce unnecessary dependencies into the function body.

Thinking...
We need to translate the markdown into English. Title: "以参数取代查询（Replace Query with Parameter）". In English: "Replace Query with Parameter". The Chinese title "以参数取代查询". Then parentheses include "Replace Query with Parameter". Maybe they want to translate entire string. So output: **Replace Query with Parameter**. Let's preserve markdown. So output exactly that.
...done thinking.

**Replace Query with Parameter**

![](/img/0_refactor-36.png)

Thinking...
We need to translate Chinese to English. The Markdown says: 好处：**改变依赖关系**，去掉令人不快的引用。 So translation: "Benefits: **Change the dependency**, remove unpleasant references." Might want better phrasing: "Benefits: **Change dependencies**, get rid of unpleasant references." Probably keep Markdown bold. So:

Benefits: **Change the dependency**, remove unpleasant references.

Make sure line breaks: It's a single line. So output:

Benefits: **Change the dependency**, remove unpleasant references.

Return only translated Markdown.
...done thinking.

Benefits: **Change the dependency**, remove unpleasant references.

Thinking...
We have to translate from Chinese to English the given Markdown. The text: "注意：**要考虑责任分配问题，会增加函数调用者的复杂度，而设计接口时又需要考虑易用性**。"

We need to preserve Markdown structure. The original includes Chinese characters. We need to translate: "注意：**要考虑责任分配问题，会增加函数调用者的复杂度，而设计接口时又需要考虑易用性**。" The translation: "Note: **You need to consider the issue of responsibility allocation, which increases the complexity for the function caller, while designing an interface also requires consideration of usability**." Or similar.

We need to keep the emphasis (**bold**). Also preserve the colon and the period.

The line break? There's only one line. Keep line breaks. So output:

Note: **You need to consider the issue of responsibility allocation, which increases the complexity for the function caller, while designing an interface also requires consideration of usability**.

Return ONLY translated Markdown.
...done thinking.

Note: **You need to consider the issue of responsibility allocation, which increases the complexity for the function caller, while designing an interface also requires consideration of usability**.

Thinking...
We need to translate to English. The Markdown heading: "**八. 处理继承关系**" means "**Eight. Handling inheritance relationships**". So final output: "**Eight. Handling inheritance relationships**". We keep Markdown.
...done thinking.

**Eight. Handling inheritance relationships**

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: ... Return ONLY translated Markdown." The given Markdown is just a header line: "**以委托取代超类（Replace Superclass with Delegate）**". So we need to translate it to English while preserving the Markdown. The translation is "Replace Superclass with Delegate". The Chinese part in parentheses is the English translation. But maybe we need to keep the original? They want to translate the markdown into English. So the Chinese title should be replaced with the English translation: "**Replace Superclass with Delegate**". Or maybe include both? The original contains the English in parentheses. But it's probably intended to produce an English version. So we output:

**Replace Superclass with Delegate**

Yes.
...done thinking.

**Replace Superclass with Delegate**

![](/img/0_refactor-37.png)

Thinking...
We need to translate the Markdown into English. The Markdown content is: "继承：子类继承父类的特征和行为 （车-交通工具）". It's probably a heading? No heading markers, just text. It's Chinese. Translate: "Inheritance: subclasses inherit the characteristics and behaviors of the superclass (car - vehicle)". Keep Markdown structure. There's no code blocks. Just plain text.

Thus output the translation. Should we keep the parentheses? Yes. So:

"Inheritance: subclasses inherit the characteristics and behaviors of the superclass (car - vehicle)"

Return only the translated Markdown.
...done thinking.

Inheritance: subclasses inherit the characteristics and behaviors of the superclass (car - vehicle)

Thinking...
We need translate Chinese to English. The text: "组合：通过对现有对象进行拼装即组合产生新的具有更复杂的功能 （车-轮胎）". Probably: "Composition: By assembling existing objects into a composition, new objects with more complex functionality are produced (car - tire)."

Let's preserve Markdown: There's no heading marker? It says "组合：" maybe a header? Not indicated but could be plain text. Keep same line break. Provide translation. Ensure no code blocks. Provide only translated Markdown.
...done thinking.

Composition: By assembling existing objects into a composition, new entities with more complex functionality are produced (car - tire).

Thinking...
The user wants a translation from Chinese to English. The text is a heading? "以组合取代继承。" Means "Replace inheritance with composition." The markdown likely just a line. We must preserve Markdown structure: likely no heading marker. So output: "Replace inheritance with composition." That's it. Return only translated markdown.
...done thinking.

Replace inheritance with composition.

Thinking...
We need to translate to English. The Markdown content is:

**一个经典的误用继承的例子：**

So translate: "**A classic example of misuse of inheritance:**" But keep Markdown bold formatting. So output:

**A classic example of misuse of inheritance:** Probably. Also preserve line breaks. The input has a line break after the colon? The line ends with colon and newline. We'll preserve.

Thus output:

**A classic example of misuse of inheritance:**
...done thinking.

**A classic example of misuse of inheritance:**

Thinking...
We need to translate the given Markdown into English. The content is Chinese. Let's translate.

Original:

**让栈（stack）继承列表（list）**。这个想法的出发点是想复用列表类的数据存储和操作能力。虽说复用是一件好事，但这个继承关系有问题：列表类的所有操作都会出现在栈类的接口上，然而其中大部分操作对一个栈来说并不适用。**更好的做法应该是把列表作为栈的字段，把必要的操作委派给列表就行了**。

So translate:

**Let stack (stack) inherit list (list)**. The idea is to reuse the data storage and operations of the list class. While reuse is a good thing, this inheritance relationship has issues: all operations of the list class will appear on the stack class's interface, but most of those operations are not applicable to a stack. **A better approach should be to use a list as a field of the stack, and delegate necessary operations to the list**.

But we keep Markdown formatting: **bold** etc.

Also preserve line breaks as much as possible. The input has one paragraph but separate bold parts. There's also a Chinese period, but we replace punctuation. The first part: "**让栈（stack）继承列表（list）**。". We'll translate as "**Let stack (stack) inherit list (list)**." but that seems repetitive. Maybe "Let the stack (stack) inherit the list (list)" but it's weird. We'll just translate literally.

We must not alter URLs, but none.

Return ONLY translated Markdown.

Thus:

**Let stack (stack) inherit list (list)**. The idea behind this is to reuse the data storage and operation capabilities of the list class. While reuse is a good thing, this inheritance relationship has problems: all operations of the list class will appear in the stack class's interface, yet most of those operations are not suitable for a stack. **A better approach should be to treat the list as a field of the stack and delegate the necessary operations to the list**.

We keep bold formatting.

Let's output.
...done thinking.

**Let stack (stack) inherit list (list)**. The idea behind this is to reuse the data storage and operation capabilities of the list class. While reuse is a good thing, this inheritance relationship has problems: all operations of the list class will appear in the stack class's interface, yet most of those operations are not suitable for a stack. **A better approach should be to treat the list as a field of the stack and delegate the necessary operations to the list**.

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

Thinking...
We need to translate the markdown into English. The input is:

```
Stack真正需要的只有四个方法，push/pop/size/isEmpty， Stack只用到了
Vector的两个方法 isEmpty 和 size，而 push 和 pop 是 Stack 自有的实现，
Vector 有大量的方法， 不适用于stack。
```

This is Chinese. Translate: "Stack truly only needs four methods: push/pop/size/isEmpty. Stack only uses Vector's two methods isEmpty and size, while push and pop are Stack's own implementation. Vector has a lot of methods, not suitable for stack."

We need to preserve Markdown structure. The content seems plain text with line breaks. There's no code blocks or inline code. Just plain text. So we output translated markdown. Let's keep the same line breaks.

The text: "Stack truly only needs four methods: push/pop/size/isEmpty. Stack only uses Vector's two methods isEmpty and size, while push and pop are Stack's own implementation. Vector has many methods, not suitable for stack."

But maintain line breaks: original had line break after "Stack只用到了" and after "push 和 pop 是 Stack 自有的实现，". So we can preserve those line breaks.

So output:

Stack truly only needs four methods: push/pop/size/isEmpty. Stack only uses Vector's two methods isEmpty and size, while push and pop are Stack's own implementation.
Vector has many methods, not suitable for stack.

Need to keep line breaks as close to original. The original:

"Stack真正需要的只有四个方法，push/pop/size/isEmpty， Stack只用到了
Vector的两个方法 isEmpty 和 size，而 push 和 pop 是 Stack 自有的实现，
Vector 有大量的方法， 不适用于stack。"

So line break after "Stack只用到了". Another line break after "实现，". So we produce:

Stack truly only needs four methods: push/pop/size/isEmpty, Stack only uses
Vector's two methods isEmpty and size, while push and pop are Stack's own implementation,
Vector has many methods, not suitable for stack.

But we need to preserve the comma after isEmpty? In original: "push/pop/size/isEmpty， Stack只用到了". That's a Chinese comma. We can translate to English comma. So produce: "push/pop/size/isEmpty, Stack only uses". So line break after uses? Actually original break after "Stack只用到了". So we put line break after "uses". So line break after "uses". Next line: "Vector's two methods isEmpty and size, while push and pop are Stack's own implementation,". There's comma at end. Then line break after that. Then "Vector has many methods, not suitable for stack.".

Thus final markdown:

Stack truly only needs four methods: push/pop/size/isEmpty, Stack only uses
Vector's two methods isEmpty and size, while push and pop are Stack's own implementation,
Vector has many methods, not suitable for stack.

Check punctuation: Should we keep period at end? The last sentence ends with a period. So keep period.

Return only this.
...done thinking.

Stack truly only needs four methods: push/pop/size/isEmpty, Stack only uses
Vector's two methods isEmpty and size, while push and pop are Stack's own implementation,
Vector has many methods, not suitable for stack.

Thinking...
We need to translate the Chinese text: "**所以，如果父类的一些函数对子类并不适用，就说明我不应该通过继承来获得超类的功能。**"

English: "**Therefore, if some functions of the parent class are not applicable to the subclass, it indicates that I should not acquire the superclass's functionality via inheritance.**"

We should preserve the Markdown: bold text. So output: **Therefore, if some functions of the parent class are not applicable to the subclass, it indicates that I should not acquire the superclass's functionality via inheritance.**
...done thinking.

**Therefore, if some functions of the parent class are not applicable to the subclass, it indicates that I should not acquire the superclass's functionality via inheritance.**

Thinking...
We need to translate the provided Markdown into English, preserve structure and ordering. There's a single paragraph. It's in Chinese. We must not translate code blocks or inline code, but there is none. No URLs. So we just translate the sentence.

Original: "同时也要避免走弯路：完全避免使用继承，如果符合继承关系的语义条件（超类的所有方法都适用于子类，子类的所有实例都是超类的实例），那么继承是一种简洁又高效的复用机制。"

Translation: "Also avoid taking a detour: entirely avoid using inheritance; if the semantic conditions of an inheritance relationship are met (all methods of the superclass apply to the subclass, all instances of the subclass are instances of the superclass), then inheritance is a concise and efficient mechanism for reuse."

We must preserve punctuation etc.

Return only translated Markdown. So final answer: same line breaks, but we can keep as single line.

Let's produce: "Also avoid taking a detour: completely avoid using inheritance; if the semantic conditions of an inheritance relationship are satisfied (all methods of the superclass apply to the subclass, all instances of the subclass are instances of the superclass), then inheritance is a concise and efficient mechanism for reuse."

Make sure to keep colon, semicolon. Probably correct.

Return.
...done thinking.

Also avoid taking a detour: completely avoid using inheritance; if the semantic conditions of an inheritance relationship are satisfied (all methods of the superclass apply to the subclass, all instances of the subclass are instances of the superclass), then inheritance is a concise and efficient mechanism for reuse.

Thinking...
We need to translate the Chinese markdown into English. Preserve structure. The content: "建议：**首先（尽量）使用继承，如果发现继承有问题，再使用以委托取代超类。**". So we translate to English: "Suggestion: **First (as much as possible) use inheritance; if inheritance has issues, then use delegation to replace the superclass.**". Ensure formatting: Suggestion: **First (as much as possible) use inheritance; if inheritance has issues, then use delegation to replace the superclass.**.

Return only translated Markdown.
...done thinking.

Suggestion: **First (as much as possible) use inheritance; if inheritance has issues, then use delegation to replace the superclass.**

Thinking...
We need to translate the Markdown into English. The content: "**范例**". That's Chinese for "**Example**" (or "范例" meaning "example"). So we need to translate it to English, preserving Markdown. The bold markup is already there. So output: "**Example**". Also keep line breaks. There's just that line. So final output: **Example**.
...done thinking.

**Example**

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: Preserve Markdown structure and ordering. Do NOT translate code blocks (` ```...``` `) or inline code in backticks. Do NOT alter URLs, links, or image paths. Keep line breaks as much as possible. Return ONLY translated Markdown."

The provided Markdown is:

```
背景：

```

So it's just "背景：" which is Chinese meaning "Background:".

We must translate to English: "Background:".

No code blocks present. Just a single line. We output the translated markdown.

Thus output:

```
Background:
```

But do we need code fences? The original was just a heading? It's a single line "背景：" with a colon. No markdown syntax? It's just plain text. So translation should be "Background:" on its own line.

Thus final answer: "Background:".

But keep line breaks. There's only one line.

Thus final.
...done thinking.

Background:

Thinking...
We need to translate the provided markdown into English. The markdown is a paragraph in Chinese. We must preserve Markdown structure: it's a single paragraph. There's no code block or inline code. So just translate. Let's produce an English paragraph: "I provided consulting for a library in an ancient city that houses ancient scrolls (scroll). They compiled a catalog (catalog) of the scroll information; each scroll has an ID number and records the scroll's title (title) and a series of tags (tag). These ancient scrolls need daily cleaning, so the Scroll class that represents a scroll inherits from the CatalogItem class that represents a catalog entry, and extends data related to 'needs cleaning'."

Make sure we keep the inline code markers around "catalog", "title", "tag", "Scroll", "CatalogItem" etc? In original they used backticks around catalog, title, tag, Scroll class, CatalogItem class. The rule: Do NOT translate code blocks or inline code in backticks. So we must keep those backticks and leave them unchanged. But we translate the rest. So we should keep `catalog`, `title`, `tag`, `Scroll`, `CatalogItem` etc. Also the parentheses for scroll? They used "scroll" inside parentheses, but that is not in backticks. The word "scroll" in parentheses is likely plain text; we may translate? The rule says do not translate code blocks or inline code in backticks, but plain text inside parentheses can be translated. They didn't put backticks there. So we should translate "scroll" to "scroll". That is already English. But Chinese "卷轴" translated to "scroll". But they had "上古卷轴（scroll）". The "scroll" in parentheses is already English, but it's a translation of the Chinese word. So we keep as is. So we preserve that. Also "CatalogItem类" and "Scroll类" should keep code formatting: `Scroll` and `CatalogItem`. They used backticks around those class names. So keep them. The Chinese text: "给一个古城里存放上古卷轴（scroll）的图书馆做了咨询。他们给卷轴的信息编制了一份目录（catalog），每份卷轴都有一个ID号，并记录了卷轴的标题（title）和一系列标签（tag），这些古老的卷轴需要日常清扫，因此代表卷轴的Scroll类继承了代表目录项的CatalogItem类，并扩展出与'需要清扫'相关的数据。"

We translate: "Provided consulting to a library in an ancient city that stores ancient scrolls (scroll). They compiled a catalog (catalog) of the scroll information; each scroll has an ID and records the scroll's title (title) and a series of tags (tag). These ancient scrolls require daily cleaning, so the Scroll class representing the scroll inherits from the CatalogItem class representing the catalog entry, and extends data related to 'needs cleaning'."

Keep punctuation. Use English. We should preserve line breaks: It's one paragraph. So we produce a single paragraph.

We need to keep backticks around catalog, title, tag, Scroll, CatalogItem. Also "需要清扫" translation: we could keep Chinese or translate? The instruction says we translate entire paragraph; but we keep code elements unchanged. So we can translate the phrase: "需要清扫" -> "needs cleaning". But do we keep backticks? It's not code. So just translate. So the phrase: "扩展出与'需要清扫'相关的数据" -> "extends data related to 'needs cleaning'". Keep quotes? The original had single quotes around Chinese phrase. We can keep them. Or we can put double quotes? But translation: "related data for 'needs cleaning'." That is okay.

We need to preserve the backticks around the class names. So we will output:

"Provided consulting to a library in an ancient city that stores ancient scrolls (scroll). They compiled a catalog (catalog) of the scroll information; each scroll has an ID and records the scroll's title (title) and a series of tags (tag). These ancient scrolls require daily cleaning, so the `Scroll` class representing the scroll inherits from the `CatalogItem` class representing the catalog entry, and extends data related to 'needs cleaning'."

Yes. Ensure no code blocks. Provide exactly that.
...done thinking.

Provided consulting to a library in an ancient city that stores ancient scrolls (scroll). They compiled a catalog (catalog) of the scroll information; each scroll has an ID and records the scroll's title (title) and a series of tags (tag). These ancient scrolls require daily cleaning, so the `Scroll` class representing the scroll inherits from the `CatalogItem` class representing the catalog entry, and extends data related to 'needs cleaning'.

![](img/0_refactor-38.png)

![](img/0_refactor-39.png)

Thinking...
We need translate to English. Preserve Markdown structure and ordering. There's no special markdown beyond the paragraph. Just translate Chinese to English. Must keep line breaks as much as possible. There's a paragraph. So we produce translated text. Ensure no code blocks. Just normal paragraph.

Let's produce:

"This is a common modeling mistake. The scrolls that actually exist and the catalog entries that exist only on paper are completely different kinds of things. For example, there may be several scrolls on 'how to treat gray scaly disease', but the catalog records only one entry. Such modeling mistakes can often be ignored. Data such as 'title' and 'tags' can be considered copies of the data in the catalog. If this data never changes, such representation is acceptable. However, if some part of it needs to be updated, you must be very careful to ensure that all copies of the data corresponding to the same catalog entry are correctly updated."

Make sure line breaks: we can keep one paragraph line. But maybe preserve line break before "If". So:

This is a common modeling mistake. The scrolls that actually exist and the catalog entries that exist only on paper are completely different kinds of things. For example, there may be several scrolls on “how to treat gray scaly disease”, but the catalog records only one entry. Such modeling mistakes can often be ignored. Data such as “title” and “tags” can be considered copies of the data in the catalog. If this data never changes, such representation is acceptable. However, if some part of it needs to be updated, you must be very careful to ensure that all copies of the data corresponding to the same catalog entry are correctly updated.

Okay.
...done thinking.

This is a common modeling mistake. The scrolls that actually exist and the catalog entries that exist only on paper are completely different kinds of things. For example, there may be several scrolls on “how to treat gray scaly disease”, but the catalog records only one entry. Such modeling mistakes can often be ignored. Data such as “title” and “tags” can be considered copies of the data in the catalog. If this data never changes, such representation is acceptable. However, if some part of it needs to be updated, you must be very careful to ensure that all copies of the data corresponding to the same catalog entry are correctly updated.

Thinking...
We need translate to English. It's a short sentence. "就算没有数据更新的问题，把目录类作为卷轴类的父类，依然会让后来的开发者感到迷惑。" Means: Even if there is no issue with data updates, making the directory class the parent class of the scroll class will still confuse future developers. So output markdown as same, just translated. Probably no markdown markup except the text itself. Just the sentence.
...done thinking.

Even if there is no issue with data updates, making the directory class the parent of the scroll class will still confuse future developers.

Thinking...
We need to translate to English. Keep markdown. The text: "首先在Scroll类中创建一个属性，令其指向一个新建的CatalogItem实例。"

Translate: "First, create a property in the Scroll class that points to a newly created CatalogItem instance."

Return only translated Markdown. Ensure no code blocks. The original didn't have any code blocks. So just output the translated sentence. Use same punctuation.

Let's provide: "First, create a property in the Scroll class that points to a newly created CatalogItem instance."

That's it.
...done thinking.

First, create a property in the `Scroll` class that points to a newly created `CatalogItem` instance.

![](img/0_refactor-40.png)

Thinking...
We need to translate the given Chinese text to English, preserving Markdown. The text is:

"然后对于子类中用到所有属于超类的函数，我要逐一为它们创建转发函数。"

Translate: "Then, for every function belonging to the superclass that is used in the subclass, I need to create forwarding functions for them one by one."

We should keep the same line breaks. No code block. Just this sentence.

Return only the translated Markdown. Let's produce:

"Then, for every function belonging to the superclass that is used in the subclass, I need to create forwarding functions for them one by one."

That's the answer.
...done thinking.

Then, for every function belonging to the superclass that is used in the subclass, I need to create forwarding functions for them one by one.

![](img/0_refactor-41.png)

Thinking...
We need to translate the Markdown into English. The original only has "**详细笔记**" which is bold "Detailed Notes". So output should be `**Detailed Notes**`. Ensure no changes else. Return only translated Markdown.
...done thinking.

**Detailed Notes**

Thinking...
We need translate Chinese to English, preserving markdown. The text: "**第1章 重构，第一个示例**". This is a heading (maybe bold). It says "**Chapter 1 Refactoring, the first example**". The translation could be "**Chapter 1 Refactoring: The First Example**". Keep bold formatting. Also preserve line breaks. The original had no line break after. We'll just produce the translated markdown: "**Chapter 1 Refactoring: The First Example**". Probably okay.
...done thinking.

**Chapter 1 Refactoring: The First Example**

Thinking...
We need to translate the given Markdown: It's Chinese text. The text: "本质上说，重构就是在代码写好之后改进它的设计。" In English: "Essentially, refactoring is improving the design of the code after it has been written." Or "Basically, refactoring is improving the design of code after it has been written." We should preserve Markdown structure. There's no formatting, just a paragraph. So output:

"Essentially, refactoring is improving its design after the code has been written." Or "Essentially, refactoring is improving the design of code after it has been written."

Return only translated Markdown. No explanation.
...done thinking.

Essentially, refactoring is improving the design of code after it has been written.

Thinking...
We need to translate to English. Keep structure. The markdown just has one paragraph. No code blocks. So translate. Let's produce English.
...done thinking.

If you want to add a feature to a program but find that the code is difficult to modify due to poor structure, first refactor the program to make it easier to add the feature, and then add the feature.

Thinking...
The user: "You are a professional technical translator. Translate the following Markdown into English. Rules: - Preserve Markdown structure and ordering. - Do NOT translate code blocks (` ```...``` `) or inline code in backticks. - Do NOT alter URLs, links, or image paths. - Keep line breaks as much as possible. Return ONLY translated Markdown."

Markdown: 
是需求的变化使重构变得必要。

We need to translate this Chinese sentence into English. It says: "It is the change of requirements that makes refactoring necessary." Could also be: "The changes in requirements make refactoring necessary." The original: "是需求的变化使重构变得必要。" The subject is omitted; the verb is "使". A natural translation: "It is the change of requirements that makes refactoring necessary." But maybe they want "It is the change in requirements that makes refactoring necessary." That is more natural. Or "The change in requirements makes refactoring necessary."

Given instructions: keep Markdown structure. The original markdown has no special formatting, just the Chinese sentence. We just translate.

Thus output: "The change in requirements makes refactoring necessary."

Should I include punctuation? The original had Chinese full stop "。". We should add a period. So "The change in requirements makes refactoring necessary."

Ok.
...done thinking.

The change in requirements makes refactoring necessary.

Thinking...
We need to translate the Markdown. It's Chinese: "重构前，先检查自己是否有一套可靠的测试集。这些测试必须有自我检验能力。" Means "Before refactoring, first check whether you have a reliable test suite. These tests must be self-asserting / have self-checking capability."

So the translation: "Before refactoring, first check whether you have a reliable test suite. These tests must be able to self-validate." We'll preserve Markdown: it's plain text, no special formatting. So output the translation.
...done thinking.

Before refactoring, first check whether you have a reliable test suite. These tests must be able to self-validate.

Thinking...
We need translate the given Markdown into English. The original:

"每次想将一块代码抽取成一个函数时，遵循一个标准流程：最大程度减少犯错的可能。------**提炼函数**"

We need to preserve Markdown structure, ordering. It's a single sentence followed by a separator of dashes and bold "**提炼函数**". "提炼函数" means "Refining function" or "Extract function". The dash line is "------" and then bold "**提炼函数**". The translation: "Whenever you want to extract a piece of code into a function, follow a standard process to minimize the likelihood of errors. ------ **Extract Function**"

Make sure not to translate code blocks; there is no code block. Just plain text. So final output should be the translated markdown. Let's ensure line breaks: The original has a space after the sentence? Let's look: "每次想将一块代码抽取成一个函数时，遵循一个标准流程：最大程度减少犯错的可能。------**提炼函数**". There's no line break before the dashes? It might be just a continuous line. But we preserve as is. So output should be:

"Whenever you want to extract a piece of code into a function, follow a standard process to minimize the likelihood of mistakes. ------ **Extract Function**"

However the translation of "犯错的可能" might be "chance of making mistakes". "最大程度减少犯错的可能" is "to reduce the possibility of making mistakes as much as possible." So maybe:

"Whenever you want to extract a block of code into a function, follow a standard process to minimize the chance of making mistakes. ------ **Extract Function**"

Also "提炼函数" is "Extract Function". So translation done. Return only the markdown. Let's output.

...done thinking.

Whenever you want to extract a block of code into a function, follow a standard process to minimize the chance of making mistakes. ------ **Extract Function**

Thinking...
We need translate Chinese to English. The markdown is simple. The rule: preserve Markdown structure. There's bold **. The text: "重构技术就是**以微小的步伐修改程序**。如果你犯下错误，很容易便可发现它。"

We translate to: "Refactoring is about **making small changes to the code**. If you make a mistake, it's easy to spot it." But need preserve punctuation. The Chinese uses full-width period "。". We can use English period. The translation could be: "Refactoring technology is **making small changes to the program**. If you make a mistake, it's easy to spot it."

Let's produce markdown: same structure.

Return only the translated Markdown.
...done thinking.

Refactoring technology is **making small changes to the program**. If you make a mistake, it's easy to spot it.

Thinking...
We need to translate to English while preserving markdown. The original Chinese text: "**营地法则**：保证离开时的代码库一定比你来时更加健康。完美的境界很难达到，但应该时时都**勤加拂拂**。"

We need to translate: "**Camp Rule**: Ensure that when you leave, the codebase is healthier than when you arrived. The perfect state is hard to achieve, but you should always **work diligently**."

We keep bold tags.

Thus output: **Camp Rule**: Make sure that the codebase is healthier when you leave than when you arrived. Achieving a perfect state is difficult, but you should always **work diligently**.

But keep Markdown.

Return only translated Markdown.
...done thinking.

**Camp Rule**: Make sure that the codebase is healthier when you leave than when you arrived. Achieving a perfect state is difficult, but you should always **work diligently**.

Thinking...
We need to translate the given Chinese markdown into English. The markdown: "以实例展开如何重构：包括提炼函数、内联变量、搬移函数和以多态取代条件表达式等，". It is a sentence. Translate to English: "Elaborate on how to refactor using examples: including extracting functions, inlining variables, moving functions, and replacing conditional expressions with polymorphism, etc." Must preserve markdown structure. The input doesn't have markdown structure except a sentence. So output the translated markdown: that sentence in English. No code blocks. Ensure no change to URLs or images, but none. So output: "Elaborate on how to refactor using examples: including extracting functions, inlining variables, moving functions, and replacing conditional expressions with polymorphism, etc." Should keep line breaks? There's just one line. So final.
...done thinking.

Elaborate on how to refactor using examples: including extracting functions, inlining variables, moving functions, and replacing conditional expressions with polymorphism, etc.

Thinking...
We need to translate to English. The provided Markdown includes Chinese paragraph. No code blocks. Should preserve Markdown structure: There's no headings, just a paragraph. We need to preserve line breaks; there is single paragraph with spaces maybe line breaks? The input shows: "几个重要的阶段：将原函数分解成一组嵌套的函数、应用拆分阶段分离计算逻辑与输出格式化逻辑，以及为计算器引入多态性来处理计算逻辑。每一步都给代码添加了更多的结构，以便更好地表达代码的意图。" That is a single paragraph. So translate to English.

Possible translation: "Several important stages: decomposing the original function into a set of nested functions, applying a split phase that separates calculation logic from output formatting logic, and introducing polymorphism to the calculator to handle calculation logic. Each step adds more structure to the code, better expressing its intent." Ensure preserve line breaks: keep as single paragraph.

Return only translated Markdown: So just the paragraph in English.

Let's produce.
...done thinking.

Several important stages: decomposing the original function into a set of nested functions, applying a split phase that separates calculation logic from output‑formatting logic, and introducing polymorphism to the calculator to handle calculation logic. Each step adds more structure to the code, better expressing its intent.

Thinking...
We just need to translate into English: "The criterion for good code is whether people can easily modify it." Keep Markdown, but no code. So plain text. Provide translation.
...done thinking.

The standard for good code is whether people can easily modify it.

Thinking...
The task: Translate the provided Markdown into English. The Markdown content is:

```
总结：
```

We need to preserve Markdown structure. It's just a line: "总结：". We translate to "Summary:" or "Conclusion:"? In English translation, "总结" usually "Summary". The colon indicates heading? It's not a heading; it's just text. Probably "Summary:".

Return only translated Markdown. So output:

Summary:

We keep line break.
...done thinking.

Summary:

Thinking...
We need to translate into English. Keep markdown structure. The text: "开展高效有序的重构，关键的心得是：**小的步子可以更快前进**，请保持代码永远处于可工作状态，小步修改累积起来也能大大改善系统的设计。"

Translate: "Carry out efficient and orderly refactoring; the key insight is: **small steps can move forward faster**. Keep the code always in a working state; incremental changes can greatly improve the system's design."

We must preserve markdown: a paragraph. The bold text is already bold. Use same markdown formatting. So final output:

"Carry out efficient and orderly refactoring. The key insight is: **small steps can move forward faster**. Keep the code always in a working state; incremental changes can greatly improve the system's design."

Return only markdown.
...done thinking.

Carry out efficient and orderly refactoring. The key insight is: **small steps can move forward faster**. Keep the code always in a working state; incremental changes can greatly improve the system's design.

Thinking...
We need to translate the given Markdown into English. The content: "**第2章　重构的原则**". That's "**Chapter 2: Principles of Refactoring**" presumably. Keep bold formatting. So output: **Chapter 2: Principles of Refactoring**. Ensure no extra changes. Return only translated Markdown.
...done thinking.

**Chapter 2: Principles of Refactoring**

Thinking...
The user wants to translate the given Markdown into English. The markdown contains just "**为何重构**". That is bold text: "为何重构". That translates to "Why refactor" or "Why refactor?" Perhaps "Why Refactor". Let's keep the same markdown syntax, so **Why Refactor**. Ensure no code blocks. No URLs. So output: **Why Refactor**. Probably no question mark? But original is "为何重构" - no punctuation. So output "**Why Refactor**". That's it.
...done thinking.

**Why Refactor**

Thinking...
We need to translate Chinese markdown to English. Keep structure, preserve code blocks etc. The markdown content is:

```
它不是一颗"银弹"，却可以算是一把"银钳子"，可以帮你始终良好地控制自己的代码。重构是一个工具
```

Actually not code block, just plain text. We need to translate into English:

"It is not a 'silver bullet', but can be considered a 'silver pliers', which can help you always keep good control over your code. Refactoring is a tool"

But need to preserve the quote marks maybe. The Chinese uses double quotes inside. Should use English quotes? Keep same? Should we translate quotes? The rule: preserve Markdown structure. There's no special Markdown formatting here. We just translate the text. We can keep double quotes.

Thus final output:

```
It is not a "silver bullet," but it can be considered a "silver pliers," which can help you keep good control over your code. Refactoring is a tool.
```

We might adjust punctuation. Keep period. Good. Return only translated markdown.
...done thinking.

It is not a “silver bullet,” but it can be considered a “silver pliers,” which can help you keep good control over your code. Refactoring is a tool.

Thinking...
We just need translate "重构改进软件的设计" into English: "Refactoring and Improving Software Design". Keep markdown formatting. So output:

**Refactoring and Improving Software Design**
...done thinking.

**Refactoring and Improving Software Design**

Thinking...
We need to translate the provided markdown. The original text is Chinese. The translation should be into English, preserving markdown structure. The markdown is just a paragraph: "代码结构的流失有累积效应。经常性的重构有助于代码维持自己该有的形态。消除重复代码，以确定所有事物和行为在代码中只表述一次，这正是优秀设计的根本。" So we translate into English. The rule: don't translate code blocks or inline code. There are none. So just translate. Keep line breaks. There's one paragraph. So output: "The loss of code structure has a cumulative effect. Frequent refactoring helps the code maintain its proper form. Eliminating duplicate code ensures that all things and behaviors are expressed only once in the code, which is exactly the foundation of excellent design." Something like that.

We need to preserve punctuation. Also maybe keep Chinese punctuation replaced with English punctuation. The original uses Chinese punctuation like "。" So we replace with ".".

Thus final: "The loss of code structure has a cumulative effect. Frequent refactoring helps the code maintain its proper form. Eliminating duplicate code ensures that all things and behaviors are expressed only once in the code, which is exactly the foundation of excellent design."

Make sure no code blocks. Good.
...done thinking.

The loss of code structure has a cumulative effect. Frequent refactoring helps the code maintain its proper form. Eliminating duplicate code ensures that all things and behaviors are expressed only once in the code, which is exactly the foundation of excellent design.

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: - Preserve Markdown structure and ordering. - Do NOT translate code blocks or inline code. - Do NOT alter URLs, links, or image paths. - Keep line breaks as much as possible. Return ONLY translated Markdown.

Markdown:

**重构使软件更容易理解**

We need to translate that into English, preserving markdown. So "**重构使软件更容易理解**" in English would be "**Refactoring makes software easier to understand**" or "Refactoring makes software more comprehensible". Use double asterisks to keep bold.

Thus the output: "**Refactoring makes software easier to understand**". Ensure no trailing spaces. Return only that.
...done thinking.

**Refactoring makes software easier to understand**

Thinking...
We need to translate the provided Markdown into English. It's a single paragraph: "在重构上花一点点时间，就可以让代码更好地表达自己的意图------更清晰地说出我想要做的。"

We should preserve markdown structure. The text is not code or links, so we translate. There's a line: "------" that's an em dash? Actually "------" maybe used as separator. It's part of the sentence. So translation: "By spending a little time on refactoring, you can make the code better express its intentions------more clearly state what I want to do." The punctuation: maybe keep same dash: "------". The Chinese is like: "在重构上花一点点时间，就可以让代码更好地表达自己的意图------更清晰地说出我想要做的。" So translation: "By spending a little time on refactoring, you can make the code better express its intentions------clearly state what I want to do." The punctuation: maybe "------" keep. Might use same. So final.

We need to output only translated markdown, so just the paragraph.

Let's produce:

"By spending a little time on refactoring, you can make the code better express its intentions------clearly state what I want to do."

Ensure no extra formatting. That's it.
...done thinking.

By spending a little time on refactoring, you can make the code better express its intentions------clearly state what I want to do.

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: - Preserve Markdown structure and ordering. - Do NOT translate code blocks (```) or inline code in backticks. - Do NOT alter URLs, links, or image paths. - Keep line breaks as much as possible. Return ONLY translated Markdown."

The markdown: "**重构帮助找到bug**"

We need to translate that into English. The phrase "重构帮助找到bug" means "Refactoring helps find bugs". So in English: "**Refactoring helps find bugs**". That's all. The output should be just that.
...done thinking.

**Refactoring helps find bugs**

Thinking...
We need to translate the markdown into English. The markdown includes "Kent" header? It's just "Kent" line? Then a quote: "Beck经常形容自己的一句话："我不是一个特别好的程序员，我只是一个有着一些特别好的习惯的还不错的程序员。"" The Chinese: Beck often describes himself: "I am not a particularly good programmer, I am just a fairly good programmer with some particularly good habits." Need to preserve markdown. The text seems plain, no markdown syntax like headings? "Kent" maybe heading or title. Probably "Kent" as heading? But no special formatting. Keep as is. Just translate the quote.

Thus produce:

Kent

Beck often describes himself with the following sentence: "I am not a particularly good programmer; I am just a fairly good programmer with some especially good habits."

Ensure punctuation. Use double quotes around quote. No code blocks. Just plain text.

Return only translated markdown.
...done thinking.

Kent

Beck often describes himself with the following sentence: "I am not a particularly good programmer; I am just a fairly good programmer with some especially good habits."

Thinking...
We need to translate the Markdown into English. The markdown is:

**重构提高编程速度**

That means **Refactoring Improves Programming Speed** or "Refactoring Boosts Programming Speed" or "Refactoring Improves Programming Speed". Probably "Refactoring Improves Programming Speed". It's bold. Should preserve markup.

We must not alter code blocks or inline code, but there's none. So we output:

**Refactoring Improves Programming Speed**

That's it.
...done thinking.

**Refactoring Improves Programming Speed**

![](/img/0_refactor-42.png)

Thinking...
We need to translate the Chinese text to English. The Markdown is just a paragraph. Must preserve structure. The text: "需要添加新功能时，内部质量良好的软件让我可以很容易找到在哪里修改、如何修改。良好的模块划分使我只需要理解代码库的一小部分，就可以做出修改。如果代码很清晰，引入bug的可能性就会变小。"

Translate: "When I need to add new features, high-quality internal software allows me to easily find where to modify and how to modify. Good modularization means I only need to understand a small part of the codebase to make changes. If the code is clear, the likelihood of introducing bugs is reduced." Ensure punctuation. Provide as Markdown. No code blocks.

Return ONLY translated Markdown. Let's craft.
...done thinking.

When I need to add new features, well‑designed software lets me easily find where to make changes and how to do it. Good modularization means I only need to understand a small portion of the codebase to make modifications. If the code is clear, the likelihood of introducing bugs decreases.

Thinking...
We need to translate into English, preserving Markdown structure and ordering. The input is:

```
"设计耐久性假说"：通过投入精力改善内部设计，我们增加了软件的耐久性，从而可以更长时间地保持开发的快速。
```

So just a sentence with quotes. We should translate: "Design Durability Hypothesis": By investing effort to improve internal design, we increased the software's durability, thereby maintaining rapid development for longer periods.

We must preserve the quotes? The original uses double quotes. In English we might use double quotes too. Also preserve the colon. So produce:

"Design Durability Hypothesis": By investing effort to improve internal design, we increased the software's durability, thereby maintaining rapid development for longer periods.

Yes. Also keep line break? It's just one line. No code blocks. Return only translated Markdown.
...done thinking.

"Design Durability Hypothesis": By investing effort to improve internal design, we increased the software's durability, thereby maintaining rapid development for longer periods.

Thinking...
We need to translate the markdown. Original is Chinese: "**何时重构**". So it's bold text "何时重构" meaning "When to refactor". So output should be "**When to refactor**". We should preserve markdown structure. So just the line.

Return ONLY translated Markdown.

Thus output:

**When to refactor**

No extra explanation.
...done thinking.

**When to refactor**

Thinking...
The user wants to translate the markdown into English. The original markdown has: **预备性重构：让添加新功能更容易**. They want preserve markdown. So we translate the text. It should be bold with double asterisks. The translation: "**Preemptive Refactoring: Making it Easier to Add New Features**". That's the only content. They want only translated Markdown. Should not translate code blocks or inline code. There is no code block. Just return the translated markdown. Ensure not to alter formatting. So output: **Preemptive Refactoring: Making it Easier to Add New Features**.
...done thinking.

**Preemptive Refactoring: Making it Easier to Add New Features**

Thinking...
We need translate into English: "The best time for refactoring is just before adding new features." The rule: preserve markdown structure and ordering. The markdown text is: "重构的最佳时机就在添加新功能之前。"

This is a single paragraph. So translation: "The best time to refactor is just before adding new features." Probably "The best time for refactoring is right before adding new features." The punctuation: period. We should output exactly the translated markdown.

Thus final.
...done thinking.

The best time to refactor is just before adding new features.

Thinking...
We need to translate the given Chinese Markdown into English. Keep Markdown structure and ordering. The text is:

"如果把某些更新数据的逻辑与查询逻辑分开，会更容易避免造成错误的逻辑纠缠。用重构改善这些情况，在同样场合再次出现同样bug的概率也会降低。"

So translation: "Separating certain update logic from query logic makes it easier to avoid entangling erroneous logic. Refactoring to improve these situations also reduces the likelihood of the same bug reappearing in the same context."

We need to preserve line breaks as much as possible. The original had two sentences separated by a line break? Let's check: The original has a line break between the two sentences? The text as provided: "如果把某些更新数据的逻辑与查询逻辑分开，会更容易避免造成错误的逻辑纠缠。用重构改善这些情况，在同样场合再次出现同样bug的概率也会降低。"

There's a newline after the first sentence? The original snippet shows a line break before the second sentence? It's a single paragraph, but in the input there may be a line break. The Markdown block includes:

```
如果把某些更新数据的逻辑与查询逻辑分开，会更容易避免造成错误的逻辑纠缠。用重构改善这些情况，在同样场合再次出现同样bug的概率也会降低。
```

Actually it's within code fences? The Markdown content provided is:

Markdown:
如果把某些更新数据的逻辑与查询逻辑分开，会更容易避免造成错误的逻辑纠缠。用重构改善这些情况，在同样场合再次出现同样bug的概率也会降低。

So there's no code fences. So we just translate that paragraph.

Thus output:

If you separate certain update logic from query logic, it becomes easier to avoid tangled erroneous logic. Refactoring to improve these situations also reduces the probability of the same bug reoccurring in the same context.

We need to keep line breaks as much as possible. The original maybe had a line break between the two sentences? In the snippet, they are in the same line separated by a period. But we could maintain the same single line.

But we can preserve line breaks: if the original had a line break, we maintain it. The original is a single paragraph. So we produce a single paragraph.

Thus final output:

If you separate certain update logic from query logic, it becomes easier to avoid tangled erroneous logic. Refactoring to improve these situations also reduces the probability of the same bug reoccurring in the same context.

Let's output exactly that.
...done thinking.

If you separate certain update logic from query logic, it becomes easier to avoid tangled erroneous logic. Refactoring to improve these situations also reduces the probability of the same bug reoccurring in the same context.

Thinking...
We need to translate the given Markdown into English. The original is Chinese: "**帮助理解的重构：使代码更易懂**". The translation: "**Refactoring for Understanding: Making Code Easier to Understand**". Should preserve markdown. So output: "**Refactoring for Understanding: Making Code Easier to Understand**".
...done thinking.

**Refactoring for Understanding: Making Code Easier to Understand**

Thinking...
The input is a Markdown text: "**捡垃圾式重构**" which is Chinese meaning "Garbage Picking Style Refactoring" or "Refactoring like picking up trash". The instruction: translate into English. Preserve Markdown structure. So output: "**Refactoring by Picking Up Trash**" or something like that. Might be more natural: "**Trash-Picking Refactoring**". I'd choose "Refactoring by Picking Up Trash" with the same bold formatting. So output:

**Refactoring by Picking Up Trash**

That's it.
...done thinking.

**Refactoring by Picking Up Trash**

Thinking...
We need to translate the given Markdown into English. The content is "**有计划的重构和见机行事的重构**". It's a heading or bold text? It's surrounded by **, so bold text. The translation: "Planned refactoring and opportunistic refactoring" or "Refactoring planned vs. refactoring on the spot". Probably "Planned refactoring and opportunistic refactoring". Keep the formatting.

So output: **Planned refactoring and opportunistic refactoring**.

That's it.
...done thinking.

**Planned refactoring and opportunistic refactoring**

Thinking...
We need translate to English. The markdown includes Chinese: "预备性重构、帮助理解的重构、捡垃圾式重构------都是见机行事的". Should keep punctuation. So translation: "Preemptive refactoring, refactoring that aids understanding, and garbage‑pickup refactoring—all are situational." Or maybe "Preemptive refactoring, refactoring that helps understand, and garbage‑pickup refactoring—all are done as the situation calls for it." Let's produce a concise translation: "Preemptive refactoring, refactoring that aids understanding, and garbage‑pickup refactoring—all are opportunistic." Let's produce that.

Return only translated markdown. No code. There's no markdown formatting besides plain text. So just output the translated line.
...done thinking.

Preemptive refactoring, refactoring that aids understanding, and garbage‑pickup refactoring—all are opportunistic.

Thinking...
We need to translate the Markdown into English, preserving structure. It's just a heading: **长期重构**. That means "**Long-Term Refactoring**" or "**Continuous Refactoring**". Chinese: "长期重构" literally "Long-Term Refactoring". So translate to "**Long-Term Refactoring**". Ensure formatting. No code blocks. Just return that.

Return only the translated Markdown. So output: **Long-Term Refactoring**.
...done thinking.

**Long-Term Refactoring**

Thinking...
The task: translate the Markdown into English. The Markdown text is in Chinese. We need to preserve Markdown structure. The content: "如果想替换掉一个正在使用的库，可以先如果想替换掉一个正在使用的库，可以先引入一层新的抽象，使其兼容新旧两个库的接口。一旦调用方已经完全改为使用这层抽象，替换下面的库就会容易得多。"

It seems there's repetition: "如果想替换掉一个正在使用的库，可以先如果想替换掉一个正在使用的库，可以先引入一层新的抽象，使其兼容新旧两个库的接口。一旦调用方已经完全改为使用这层抽象，替换下面的库就会容易得多。"

So translation: "If you want to replace a library that is currently in use, you can first introduce a new abstraction layer that is compatible with both the new and old library interfaces. Once the caller has completely switched to using this abstraction layer, replacing the underlying library will be much easier."

We need to preserve line breaks. The original has one paragraph with repetition maybe a typo. We keep the same structure: one paragraph. No Markdown formatting. Just plain text. So output:

"If you want to replace a library that is currently in use, you can first ..."

Thus final output.
...done thinking.

If you want to replace a library that is currently in use, you can first introduce a new abstraction layer that is compatible with both the new and old library interfaces. Once the caller has completely switched to using this abstraction layer, replacing the underlying library will be much easier.

Thinking...
We need to translate the Chinese text: "复审代码时重构". Means "Refactoring during code review" or "Refactor while reviewing code". We need to keep markdown: **...** is bold.

Thus output: **Refactor during code review**. Ensure not altering. That's it.
...done thinking.

**Refactor during code review**

Thinking...
We need to translate the given Markdown into English. It's a paragraph in Chinese: "与原作者肩并肩坐在一起，一边浏览代码一边重构，体验是最佳的。这种工作方式很自然地导向结对编程：在编程的过程中持续不断地进行代码复审。"

Translate: "Sitting side by side with the original author, browsing code while refactoring, the experience is best. This way of working naturally leads to pair programming: continuously reviewing code throughout the programming process."

We need to preserve Markdown structure and ordering. It's a single paragraph. No code blocks. So we output the translated paragraph.

Check no line breaks? In original, there's a line break after first sentence? Actually text: "与原作者肩并肩坐在一起，一边浏览代码一边重构，体验是最佳的。这种工作方式很自然地导向结对编程：在编程的过程中持续不断地进行代码复审。"

The original has a line break after "最佳的." There's a full stop, then new line: "这种工作方式..." So we keep that break. So output:

"Sitting side by side with the original author, browsing code while refactoring, the experience is best. This way of working naturally leads to pair programming: continuously reviewing code throughout the programming process."

We preserve line break. The output: lines separated.

Thus final answer.
...done thinking.

Sitting side by side with the original author, browsing code while refactoring, the experience is best.  
This way of working naturally leads to pair programming: continuously reviewing code throughout the programming process.

Thinking...
We need to translate Chinese title "**重构的挑战**" into English. Keep markdown. Should be "**Refactoring Challenges**" or "**The Challenges of Refactoring**". The original is bold. So output "**Refactoring Challenges**". Let's produce only that.
...done thinking.

**Refactoring Challenges**

Thinking...
We need to translate the provided markdown: "**延缓新功能开发**" into English, preserving markdown. That phrase means "Delay new feature development". Likely translation: "**Delay New Feature Development**". The instructions: preserve markdown structure, ordering, don't translate code blocks or inline code. Here it's a bold line. So output "**Delay New Feature Development**".

Thus answer: **Delay New Feature Development**.
...done thinking.

**Delay New Feature Development**

Thinking...
We need translate the given markdown into English, preserving structure, but here it's a simple sentence. The content: "重构的唯一目的就是让我们开发更快，用更少的工作量创造更大的价值。" Translate: "The sole purpose of refactoring is to let us develop faster, creating greater value with less effort." Or "Refactoring's sole purpose is to let us develop faster and create greater value with less work." Keep line breaks; it's one line. The markdown doesn't have any formatting beyond plain text. So output that line.

We should ensure no backticks. There's no code. Just plain. So output: "The sole purpose of refactoring is to allow us to develop faster, creating greater value with less effort." That is okay.

Return only the translated markdown.
...done thinking.

The sole purpose of refactoring is to let us develop faster, creating greater value with less effort.

Thinking...
The user wants translation into English. The markdown is:

有时会看到一个（大规模的）重构很有必要进行，而马上要添加的功能非常小，这时应先把新功能加上，然后再做这次大规模重构。

We need to preserve markdown. It's just a sentence. So translation: "Sometimes, it may seem necessary to perform a (large-scale) refactor, while the new feature to be added is very small; in that case, one should first add the new feature, then proceed with the large-scale refactor."

Return only translated markdown. No code blocks.

Ensure no backticks. The sentence no markdown. So just the English sentence. Should keep line breaks as much as possible. There's just one line. So output that line.
...done thinking.

Sometimes, it may seem necessary to perform a (large-scale) refactor, while the new feature to be added is very small; in that case, one should first add the new feature, then proceed with the large-scale refactor.

Thinking...
We need to translate to English. Keep Markdown. The content: "重构不足的情况远多于重构过度的情况。换句话说，绝大多数人应该尝试多做重构。"

Translate: "The cases of insufficient refactoring are far more common than cases of over-refactoring. In other words, the vast majority of people should try to do more refactoring."

Return only the translated markdown. So:

The markdown is just plain text (no markdown formatting?). The original had no markdown structure? Just a paragraph. So output that paragraph. Ensure no code blocks.

Return that.
...done thinking.

The cases of insufficient refactoring are far more common than cases of over‑refactoring. In other words, the vast majority of people should try to do more refactoring.

Thinking...
We need to translate to English, preserving Markdown structure. The text: "重构的意义不在于把代码库打磨得闪闪发光，而是纯粹经济角度出发的考量。我们之所以重构，因为它能让我们更快------添加功能更快，修复bug更快。"

We need to keep line breaks. The original has a line break before "添加功能更快". Actually the original: "我们之所以重构，因为它能让我们更快------添加功能更快，修复bug更快。" That is one line but includes a long dash. Let's preserve.

We will translate:

"The purpose of refactoring is not to polish the codebase until it shines, but rather a purely economic consideration. We refactor because it allows us to do things faster—adding features faster, fixing bugs faster."

Need to preserve the dash line: "------" maybe they used six dashes. We'll keep "------". Then phrase after.

The dash is "------" before "添加功能更快". So we produce "------" in English? We'll preserve the same. They want to keep formatting. So we produce same dashes, but maybe we translate after.

Line break: original had line break after first sentence? Let's check original:

"重构的意义不在于把代码库打磨得闪闪发光，而是纯粹经济角度出发的考量。我们之所以重构，因为它能让我们更快------添加功能更快，修复bug更快。"

It is one paragraph. So we produce a single paragraph. We can preserve line break after first sentence? They said keep line breaks as much as possible. There is a line break? The original shows no line break. So produce same line break pattern: just single line.

Let's produce:

"The meaning of refactoring is not to polish the codebase until it shines, but rather a purely economic consideration. The reason we refactor is that it allows us to be faster—adding features faster, fixing bugs faster."

But we need to keep dashes "------" before "adding features faster". We'll keep them.

Thus:

"The meaning of refactoring is not to polish the codebase until it shines, but purely from an economic perspective. We refactor because it lets us be faster------adding features faster, fixing bugs faster."

Let's output.

...done thinking.

The meaning of refactoring is not to polish the codebase until it shines, but purely from an economic perspective. We refactor because it lets us be faster------adding features faster, fixing bugs faster.

Thinking...
We need to translate the markdown: "**代码所有权**". That means "**Code Ownership**" likely. So output "**Code Ownership**". Should preserve markdown bold. So just that line.
...done thinking.

**Code Ownership**

Thinking...
We need to translate into English. The text: "旧的接口标记为"不推荐使用"（deprecated）。" That means: "The old interface is marked as 'not recommended to use' (deprecated)." So translation: "The old interface is marked as 'deprecated'." or "The old interface is marked as 'not recommended for use' (deprecated)." We preserve markdown: it's just a sentence. No code. Just plain text. So output:

The old interface is marked as "not recommended for use" (deprecated). Or "deprecated".

Let's do: "The old interface is marked as 'deprecated'." That matches.

We keep punctuation. The original had parentheses with Chinese quotes. Let's translate accordingly.

So final answer: "The old interface is marked as 'deprecated'."
...done thinking.

The old interface is marked as "deprecated".

Thinking...
We need to translate the markdown into English. The original markdown: "**分支**" which is bold "分支". "Branch" is the English translation. So output: "**Branch**". Ensure preserve markdown. So output that.
...done thinking.

**Branch**

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: ... Return ONLY translated Markdown." The original Markdown is:

```
持续集成（Continuous Integration，CI），也叫"基于主干开发"（Trunk-Based
Development）。
```

Note there's a line break in the middle. Should preserve structure. The text is Chinese: "持续集成（Continuous Integration，CI），也叫"基于主干开发"（Trunk-Based Development）。"

We need to translate to English. The translation: "Continuous Integration (CI), also known as 'Trunk-Based Development'." The Chinese has Chinese parentheses but includes English. We keep the English inside. So: "Continuous Integration (CI), also known as 'Trunk-Based Development'." There's a period. There's no code block. So just output that line. No need to preserve line breaks? The original had a line break between Development and closing Chinese period. The original is "持续集成（Continuous Integration，CI），也叫"基于主干开发"（Trunk-Based Development）。" So the Chinese quotes around the English? Actually Chinese punctuation: Chinese quotes are "..." around the English phrase. The English phrase is "Trunk-Based Development". So translation: "Continuous Integration (CI), also called 'Trunk-Based Development'." or "also known as 'Trunk-Based Development'." It's "also called".

We might preserve the Chinese comma, but it's a comma. So "Continuous Integration (CI), also called 'Trunk-Based Development'." Yes.

Thus output: Continuous Integration (CI), also called "Trunk-Based Development". Wait, original uses Chinese quotes: "基于主干开发". That is "Trunk-Based Development" in Chinese. The English phrase inside quotes. So keep double quotes around "Trunk-Based Development"? But the rule says do NOT translate code blocks or inline code. The quotes are not code. So we can translate the Chinese portion. So output: Continuous Integration (CI), also called "Trunk-Based Development". Or "also known as 'Trunk-Based Development'". But the original uses Chinese quotes. We could keep double quotes. The translation could preserve them. So final line: Continuous Integration (CI), also called "Trunk-Based Development". Note there's a period.

Let's provide that.
...done thinking.

Continuous Integration (CI), also called "Trunk-Based Development".

Thinking...
We need to translate the provided Markdown into English. The content: "**重构、架构和YAGNI**" The translation: "**Refactoring, Architecture, and YAGNI**". It is a header (bold). So output: "**Refactoring, Architecture, and YAGNI**". Ensure we preserve Markdown. Done.
...done thinking.

**Refactoring, Architecture, and YAGNI**

Thinking...
We need to translate to English. Preserve Markdown structure. The original is plain text. No code blocks. So just translate.

Original text: 
"重构对架构最大的影响在于，通过重构，我们能得到一个设计良好的代码库，使其能够优雅地应对不断变化的需求。"在编码之前先完成架构"这种做法最大的问题在于，它假设了软件的需求可以预先充分理解。"

So translation: "The biggest impact of refactoring on architecture is that, through refactoring, we can obtain a well-designed codebase that can gracefully handle evolving requirements. The major flaw of the approach 'complete architecture before coding' is that it assumes that the software requirements can be fully understood in advance."

Need to keep punctuation. Probably preserve quotation marks? It's Chinese double quotes “ and “”. We can translate them to English quotes. The sentence inside quotes: “在编码之前先完成架构” -> "Complete the architecture before coding" or "Finish the architecture before coding." But the English translation might keep the original phrase: "Finish the architecture before coding." Keep in English quotes.

Thus final output:

"The biggest impact of refactoring on architecture is that, through refactoring, we can obtain a well-designed codebase that can gracefully handle evolving requirements. The biggest problem with the practice of 'finish the architecture before coding' is that it assumes the software requirements can be fully understood in advance."

Let's ensure no code block. Keep line breaks. Provide as single paragraph maybe. It's okay.
...done thinking.

The biggest impact of refactoring on architecture is that, through refactoring, we can obtain a well‑designed codebase that can gracefully handle evolving requirements. The main problem with the practice of **“finish the architecture before coding”** is that it assumes the software requirements can be fully understood in advance.

Thinking...
The user wants to translate the provided Markdown into English. The Markdown is: **重构与软件开发过程**. That's Chinese: "Refactoring and Software Development Process". They want to preserve markdown structure. So the output should be **Refactoring and Software Development Process**. That's all. Ensure we don't translate code blocks or inline code, but there is none. Just output the translated Markdown.
...done thinking.

**Refactoring and Software Development Process**

Thinking...
We need to translate the given markdown into English, preserving structure. The markdown text: "既牢固可靠又能快速响应变化的需求。". It's Chinese: "既牢固可靠又能快速响应变化的需求。" Means "It is both sturdy and reliable and can quickly respond to changing demands." Or "It is both strong and reliable, and can quickly respond to changing demands." It's probably a sentence, maybe a title. We just translate to English. The requirement: preserve markdown structure. The text is plain text with a period. No code blocks. So just output the translated sentence.

Thus output: "It is both sturdy and reliable, and can quickly respond to changing demands." But maybe better: "It is both robust and reliable, and can quickly respond to changing needs." We'll keep literal translation: "It is both solid and reliable, and can quickly respond to changing demands." Use "solid" for "牢固". Could be "robust". Provide English.

Return only the translated Markdown. So just the line.

Thus answer.
...done thinking.

It is both solid and reliable, and can quickly respond to changing demands.

Thinking...
We have a short Markdown: "**自动化重构**". That means "**Automated Refactoring**" presumably. So output: "**Automated Refactoring**". No code blocks. Just the translation. Should preserve the bold markup. So final.
...done thinking.

**Automated Refactoring**

Thinking...
We need to translate into English. Preserve Markdown. The given text is:

"不仅能处理文本，还能处理语法树，这是IDE相比于文本编辑器更先进的地方。重构工具不仅需要理解和修改语法树，还要知道如何把修改后的代码写回编辑器视图。如果我给一个变量改名，工具会提醒我修改使用了旧名字的注释。能借助语法树来分析和重构程序代码，这是IDE与普通文本编辑器相比具有的一大优势。"

We translate: "Not only can it handle text, but it can also handle syntax trees, which is what makes an IDE more advanced compared to a text editor. Refactoring tools not only need to understand and modify the syntax tree, but also know how to write the modified code back to the editor view. If I rename a variable, the tool will prompt me to change comments that used the old name. Using the syntax tree to analyze and refactor program code is a major advantage of IDEs over ordinary text editors."

We should keep line breaks? The original had line breaks? It's a single paragraph. Might preserve line breaks: The prompt: "Preserve Markdown structure and ordering." So we keep same lines. It's one paragraph. So we output same paragraph. Return only translated Markdown.
...done thinking.

Not only can it handle text, but it can also manipulate syntax trees—this is what makes an IDE more advanced than a plain text editor. Refactoring tools must not only understand and modify the syntax tree, but also know how to write the altered code back to the editor view. If I rename a variable, the tool will prompt me to update comments that use the old name. Using the syntax tree to analyze and refactor program code is a major advantage of IDEs over ordinary text editors.

Thinking...
We need to translate into English. The content: "**第3章　代码的坏味道**". That translates to "**Chapter 3: Bad Code Smells**" or "Chapter 3: Code Bad Smells". But preserve Markdown. Should be bold same. So output: **Chapter 3: Code Bad Smells**. Maybe "Bad Code Smells". Let's choose "Bad Code Smells". So final.
...done thinking.

**Chapter 3: Bad Code Smells**

Thinking...
We just translate the heading. It's a heading bold. So we keep same markdown, only translate text. "**神秘命名（Mysterious Name）**" -> "**Mysterious Naming (Mysterious Name)**"? Wait "神秘命名" means "Mysterious Naming". They added parentheses with English translation. So we translate the Chinese part to English: "Mysterious Naming". Keep parentheses maybe keep original? The original is "**神秘命名（Mysterious Name）**". We replace Chinese with English, keep English in parentheses unchanged? Or maybe we can translate parentheses too? The original parentheses hold English translation. So we should preserve it? The instruction: "Translate the following Markdown into English." The original already has English translation. We need to translate entire text into English. So Chinese part should be translated, parentheses part maybe redundant. But we keep both? Could produce "**Mysterious Naming (Mysterious Name)**". But maybe they expect just "Mysterious Naming" without parentheses? But rule: Preserve Markdown structure. So just replace Chinese with English. We'll keep parentheses part unchanged. So final: "**Mysterious Naming (Mysterious Name)**".
...done thinking.

**Mysterious Naming (Mysterious Name)**

Thinking...
We need to translate the given markdown into English, preserving structure. The content is:

命名是编程中最难的两件事之一\[mf-2h\]。正因为如此，改名可能是最常用的重构手法，包括改变函数声明（用于给函数改名）、变量改名、字段改名。

We need to keep markdown structure: there is no headings or bullet lists, just a paragraph. There is a reference [mf-2h] in brackets.

We should translate: "Naming is one of the hardest things in programming\[mf-2h\]. Because of this, renaming may be the most commonly used refactoring technique, including changing function declarations (to rename functions), variable renaming, and field renaming."

Make sure to keep the reference [mf-2h] unchanged. No code blocks. So final:

Naming is one of the hardest things in programming\[mf-2h\]. Because of this, renaming may be the most common refactoring technique, including changing function declarations (used for renaming functions), variable renaming, and field renaming.

Check punctuation. Keep line break: single line. Maybe keep as one line or two? The original had a line break? The original text is:

命名是编程中最难的两件事之一\[mf-2h\]。正因为如此，改名可能是最常用的重构手法，包括改变函数声明（用于给函数改名）、变量改名、字段改名。

It might be one paragraph. So output that.

Ensure no stray translation of code. There is none.

Thus output:

Naming is one of the hardest things in programming\[mf-2h\]. Because of this, renaming may be the most common refactoring technique, including changing function declarations (used for renaming functions), variable renaming, and field renaming.
...done thinking.

Naming is one of the hardest things in programming\[mf-2h\]. Because of this, renaming may be the most common refactoring technique, including changing function declarations (used for renaming functions), variable renaming, and field renaming.

Thinking...
We just translate the heading: "**重复代码（Duplicated Code）**" to English: "**Duplicated Code**" maybe include Chinese? They say translate to English. Should remove Chinese inside parentheses. The heading is **重复代码（Duplicated Code）**. Should translate to "**Duplicated Code**". Probably just that. So output: **Duplicated Code**.
...done thinking.

**Duplicated Code**

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: preserve structure and ordering, don't translate code blocks, etc. Return ONLY translated Markdown." The markdown only contains "**过长函数（Long Function）**". So we translate to English: "**Long Function**" but preserve bold. They also might want parentheses? The Chinese part "过长函数" means "Long Function". The part in parentheses is already "Long Function". The original is "**过长函数（Long Function）**". We need to translate the Chinese part, but keep the English? The rule: translate Markdown. The Chinese part needs translation, but keep parentheses? Probably we should translate to "**Long Function (Long Function)**"? But that duplicates. Maybe we should translate to "**Long Function (Long Function)**" but that seems odd. Actually the Chinese part is translated, the English inside parentheses remains. We might keep the parentheses and English inside. So result: "**Long Function (Long Function)**". But maybe better: "**Long Function (Long Function)**" or just "**Long Function**"? But the rule: preserve structure. The phrase includes Chinese and English. We need to translate Chinese to English. So it becomes "**Long Function (Long Function)**". That seems weird but it's a translation of the entire phrase. Might be acceptable. Probably just translate the Chinese part, keep parentheses and English unchanged. So final.
...done thinking.

**Long Function (Long Function)**

Thinking...
We need to translate Chinese into English. The Markdown: "积极地分解函数." which means "Actively decompose functions." But maybe "Actively decompose function." But the Chinese phrase: "积极地分解函数." Could also be "Actively decompose functions." It's a single sentence. We'll translate as "Actively decompose functions." Provide in Markdown. There's no code blocks. So output only the translated Markdown.
...done thinking.

Actively decompose functions.

Thinking...
We need translate to English. The content is Chinese. Markdown just has a paragraph. We preserve structure. No code. So output English paragraph.

Original: "原则：每当感觉需要以注释来说明点什么的时候，我们就把需要说明的东西写进一个独立函数中，并以其用途（而非实现手法）命名。关键不在于函数的长度，而在于函数"做什么"和"如何做"之间的语义距离。"

Translate: "Principle: Whenever you feel the need to explain something with a comment, write what needs to be explained into a separate function and name it by its purpose (not its implementation). The key is not the length of the function, but the semantic distance between what the function 'does' and 'how it does it'."

Need preserve line breaks. There's only one paragraph. So just output translated paragraph.

Ensure not to add any extra.
...done thinking.

Principle: Whenever you feel the need to explain something with a comment, we write what needs to be explained into a separate function and name it by its purpose (not its implementation). The key is not the length of the function, but the semantic distance between what the function “does” and how it does it.

Thinking...
We need to translate the provided Markdown into English. The text is Chinese: "如何确定该提炼哪一段代码呢？一个很好的技巧是：寻找注释。它们通常能指出代码用途和实现手法之间的语义距离。"

We keep Markdown structure. There's no headings etc. Just a paragraph. We need to translate to English. Also no code blocks. So just output:

"How can you determine which section of code to extract? A great trick is: look for comments. They usually indicate the semantic distance between the code's purpose and the implementation approach."

We should preserve punctuation, line breaks as much as possible. The original has line breaks? It's one line with Chinese punctuation. We'll produce one paragraph in English.

Thus the output should be:

How can you determine which section of code to extract? A great trick is: look for comments. They usually indicate the semantic distance between the code's purpose and the implementation approach.

Let's output that.
...done thinking.

How can you determine which section of code to extract? A great trick is: look for comments. They usually indicate the semantic distance between the code's purpose and the implementation approach.

Thinking...
We need to translate to English. The original text: "条件表达式和循环常常也是提炼的信号。你可以使用分解条件表达式处理条件表达式。"

It is a single paragraph. Translate: "Conditional expressions and loops are often also signals of refinement. You can use decomposition of conditional expressions to handle conditional expressions." Might be better: "Conditional expressions and loops often serve as signals of refinement. You can use decomposition of conditional expressions to handle conditional expressions."

We must preserve Markdown structure. It's just plain text, no special formatting. So output translated Markdown.

Let's produce the translation.
...done thinking.

Conditional expressions and loops often serve as signals of refinement. You can handle conditional expressions by decomposing them.

Thinking...
We need to translate to English. The original is Chinese. Let's translate:

Original text: "对于庞大的switch语句，其中的每个分支都应该通过提炼函数变成独立的函数调用。如果有多个switch语句基于同一个条件进行分支选择，就应该使用以多态取代条件表达式。"

Translate: "For large switch statements, each branch should be extracted into a separate function call. If there are multiple switch statements branching based on the same condition, polymorphism should be used to replace the conditional expression."

Need to preserve Markdown: it's just a paragraph. So output that paragraph in English.

Return only translated Markdown.
...done thinking.

For large switch statements, each branch should be extracted into a separate function call. If there are multiple switch statements branching based on the same condition, polymorphism should be used to replace the conditional expression.

Thinking...
We need translate the markdown. It's Chinese text. The markdown is just plain text, no code blocks, no inline code. So translation to English. Preserve structure and ordering. The given text: "应该将循环和循环内的代码提炼到一个独立的函数中。如果你发现提炼出的循环很难命名，可能是因为其中做了几件不同的事。如果是这种情况，请勇敢地使用拆分循环将其拆分成各自独立的任务。"

So English: "You should extract the loop and the code inside it into a separate function. If you find the extracted loop difficult to name, it may be because it does several different things. In that case, bravely use loop splitting to separate them into independent tasks." Let's produce exactly. Probably preserve punctuation. So:

"You should extract the loop and the code inside the loop into a separate function. If you find the extracted loop hard to name, it may be because it performs several different tasks. In that case, boldly use loop splitting to divide it into separate independent tasks."

Let's output that as markdown. It's just text. We'll keep line breaks? The original had no line breaks. The text is one paragraph. The translation can be one paragraph. Provide same structure. No code blocks. Return only translated markdown.
...done thinking.

You should extract the loop and the code inside it into a separate function. If you find the extracted loop difficult to name, it may be because it performs several different tasks. In that case, bravely use loop splitting to divide it into independent tasks.

Thinking...
We need to translate Markdown into English. The content: "**过长参数列表（Long Parameter List）**". We need to keep Markdown structure. The phrase in Chinese is "过长参数列表", then in parentheses "Long Parameter List". So we need to translate into English: "**Long Parameter List (Long Parameter List)**"? But that's redundant. Probably translation: "**Long Parameter List**". The parentheses part is original translation. Wait the original had both Chinese and English? The title includes both Chinese and English: "过长参数列表（Long Parameter List）". The instruction: translate into English. Should we translate the Chinese part and keep the English part? The instruction: "Translate the following Markdown into English." So the Chinese part "过长参数列表" needs translation. But the part inside parentheses is already English: "Long Parameter List". So we could produce "**Long Parameter List (Long Parameter List)**"? That duplicates. Better: Just keep the parentheses part and replace Chinese with its translation, but maybe we keep parentheses? The original had Chinese then parentheses with English. So the translation could be "**Long Parameter List**". The parentheses maybe not needed. But maybe keep parentheses because the original had them. The instruction says "Translate the following Markdown into English." That implies we convert Chinese to English. So the result: "**Long Parameter List (Long Parameter List)**" is weird. The better is "**Long Parameter List**" or maybe "**Long Parameter List (Long Parameter List)**"? But that duplicates. The original had "过长参数列表（Long Parameter List）" meaning Chinese name with English translation. If we translate into English, we might produce "Long Parameter List" as the title. So we can just output that. The parentheses not needed. But maybe to preserve structure, we keep bold: **Long Parameter List**. That seems correct.

Thus output: **Long Parameter List**.
...done thinking.

**Long Parameter List**

Thinking...
The task: translate the given Markdown into English. The original is Chinese. The Markdown: "如果可以向某个参数发起查询而获得另一个参数的值，那么就可以使用以查询取代参数去掉这第二个参数。"

We should translate that. It's a single sentence. It says: "If you can query one parameter to obtain the value of another parameter, then you can use the query to replace the parameter and remove the second parameter." Maybe "If you can initiate a query against one parameter to obtain the value of another parameter, then you can replace the second parameter with a query and drop it." The original says: "使用以查询取代参数去掉这第二个参数" maybe "using a query instead of the parameter to remove the second parameter."

Let's produce the translation:

"If you can query one parameter to obtain the value of another parameter, then you can use a query to replace the second parameter and remove it." Or "If you can query one parameter to get the value of another parameter, then you can use that query in place of the parameter, thus eliminating the second parameter."

We need to preserve Markdown structure. There's no special structure: just a paragraph. So just provide translated paragraph.

Return only the translated Markdown.

Thus:

If you can query one parameter to obtain the value of another parameter, then you can replace that second parameter with a query and omit it.

Let's produce: "If you can query one parameter to get the value of another parameter, you can replace that second parameter with a query and drop it."

Make it grammatical: "If you can query one parameter to obtain the value of another parameter, then you can use the query to replace the second parameter and omit it."

That's good.
...done thinking.

If you can query one parameter to obtain the value of another parameter, then you can use the query to replace the second parameter and omit it.

Thinking...
We need to translate into English. It's simple Chinese: "If you find yourself extracting many data items from an existing data structure, you might consider using a technique that preserves the object intact, passing the original data structure directly. If several parameters always appear together, you can introduce a parameter object and merge them into a single object."

We need to preserve Markdown structure and ordering: It's plain paragraph. No special formatting. Just translate. Ensure not to translate code blocks. There's none. Keep line breaks. So final output is the translated paragraph.

Thus answer: "If you find yourself extracting many data items from an existing data structure, you can consider using the technique of preserving the object intact, passing the original data structure directly. If several parameters always appear together, you can introduce a parameter object and merge them into one object."

Check no code block. Just one paragraph. Return that.
...done thinking.

If you find yourself extracting many data items from an existing data structure, you can consider using the technique of preserving the object intact, passing the original data structure directly. If several parameters always appear together, you can introduce a parameter object and merge them into a single object.

Thinking...
We need to translate the given Markdown from Chinese to English. The text is: "如果某个参数被用作区分函数行为的标记（flag），可以使用移除标记参数。"

We need to preserve Markdown structure and ordering, but there is no Markdown formatting here except the parentheses and maybe bullet. The instruction says to preserve Markdown structure and ordering. It's a single sentence. We should translate to English: "If a parameter is used as a flag to distinguish function behavior, a remove flag parameter can be used." But maybe "remove flag parameter" is a concept. The original: "可以使用移除标记参数" meaning "can use a 'remove flag' parameter". Could be "you can use a removal flag parameter." Let's do: "If a parameter is used as a flag to distinguish function behavior, you can use a removal flag parameter." Keep the parentheses: (flag). So: "If a parameter is used as a flag to distinguish function behavior (flag), you can use a removal flag parameter." Wait duplication. Better: "If a parameter is used as a flag to distinguish function behavior, a removal flag parameter can be used." That's fine.

Return only translated Markdown. So output that sentence.

...done thinking.

If a parameter is used as a flag to distinguish function behavior, a removal flag parameter can be used.

Thinking...
We need to translate the given Chinese Markdown into English. The instructions: preserve Markdown structure and ordering. No code blocks here, so no need to skip. There's no inline code or URLs. Just a short paragraph. Translate:

"使用类可以有效地缩短参数列表。如果多个函数有同样的几个参数，引入一个类就尤为有意义。你可以使用函数组合成类，将这些共同的参数变成这个类的字段。"

English translation: "Using a class can effectively shorten parameter lists. If multiple functions share the same set of parameters, introducing a class becomes especially meaningful. You can combine functions into a class, turning these common parameters into fields of that class."

But keep the structure: just a single paragraph. So output:

Using a class can effectively shorten parameter lists. If multiple functions share the same set of parameters, introducing a class is particularly meaningful. You can combine functions into a class, turning these common parameters into fields of that class.

Need to keep line breaks as much as possible. The original had line breaks maybe after each sentence? It shows in the prompt as one paragraph with line breaks? Let's see: The Markdown block shows three sentences separated by Chinese punctuation. There is no explicit line break after each sentence. The user didn't provide explicit line breaks except maybe at the end of the paragraph. So we can keep as a single paragraph. It's fine.

Return only the translated Markdown.
...done thinking.

Using a class can effectively shorten parameter lists. If multiple functions share the same set of parameters, introducing a class becomes especially meaningful. You can combine functions into a class, turning these common parameters into fields of that class.

Thinking...
We need to translate Markdown to English. The given is "**全局数据（Global Data）**". The translation: "**Global Data**" presumably. The parentheses show the original Chinese. Should we keep the parentheses? The instruction: translate into English, preserve Markdown structure and ordering. So the text inside the Markdown, but we can choose to translate Chinese. The example has both Chinese and English: "全局数据（Global Data）". So we might keep as is but translate Chinese portion: "**Global Data**". But the original had the English already. Maybe we keep the same structure: "**Global Data**". They might want to preserve the English in parentheses? They want translation into English, so we should produce "**Global Data**". We should preserve any parentheses? If Chinese is removed, we don't need parentheses. So answer: **Global Data**. Ensure it's markdown.
...done thinking.

**Global Data**

Thinking...
The user wants translation into English. The markdown content is simple: "封装变量。有少量的全局数据或许无妨，但数量越多，处理的难度就会指数上升。"

We need to preserve markdown structure. There's no code blocks. Just plain text. So translation: "Encapsulate variables. Having a small amount of global data might be fine, but as the amount increases, the difficulty of handling it rises exponentially." Or "Encapsulate variables. Having a small amount of global data may be fine, but the more you have, the more difficult it becomes to handle, rising exponentially." The translation must be in markdown. No code blocks. So final.
...done thinking.

Encapsulate variables. A small amount of global data may be fine, but as the quantity increases, the difficulty of handling it rises exponentially.

Thinking...
We need to translate given markdown into English. The original text: "**可变数据（Mutable Data）**". Translate to "**Mutable Data**" likely. It says rules: preserve markdown structure. It's a bold heading. So output "**Mutable Data**". Ensure line breaks. There's no extra content. So return only that.
...done thinking.

**Mutable Data**

Thinking...
We need to translate the provided markdown into English. The text: "可以用封装变量来确保所有数据更新操作都通过很少几个函数来进行，使其更容易监控和演进。" Translate to: "You can encapsulate variables to ensure that all data update operations are performed through a few functions, making it easier to monitor and evolve." Or similar. Preserve markdown structure: The original has no headings etc. Just one paragraph. So we output the translation. Ensure we keep same line break, no code. So just the translated sentence. Use plain English. Return only translated markdown.
...done thinking.

You can encapsulate variables to ensure that all data update operations are performed through a few functions, making it easier to monitor and evolve.

Thinking...
We need to translate Chinese Markdown to English. The rules: preserve Markdown structure, no code block translation, but there's no code block. Keep line breaks. Just translate the paragraph.

Original:

如果一个变量在不同时候被用于存储不同的东西，可以使用拆分变量将其拆分为各自不同用途的变量，从而避免危险的更新操作。使用移动语句和提炼函数尽量把逻辑从处理更新操作的代码中搬移出来，将没有副作用的代码与执行数据更新操作的代码分开。设计API时，可以使用将查询函数和修改函数分离。

We translate:

"If a variable is used to store different things at different times, you can split the variable into separate variables for each distinct purpose, thereby avoiding dangerous update operations. Use statement movement and function extraction to move logic out of code that handles updates, separating code without side effects from code that performs data updates. When designing an API, you can separate query functions from modification functions."

We keep line breaks. Possibly preserve the paragraph as one block? The original has line breaks between sentences? It appears it's one paragraph. So output as one paragraph. Ensure no code formatting. Return only translated Markdown.

Let's produce.
...done thinking.

If a variable is used to store different things at different times, you can split it into separate variables for each distinct purpose, thereby avoiding dangerous update operations. Use statement movement and function extraction to move logic out of the code that handles updates, separating code without side effects from code that performs data updates. When designing an API, you can separate query functions from modification functions.

Thinking...
We need to translate the given Markdown into English, preserving structure. The content: "尽早使用移除设值函数，缩小变量作用域。" That is a Chinese sentence: "Use the remove set function as early as possible to narrow the variable scope." The original is a simple sentence. In Markdown, it's just plain text, no code, no lists. So translation: "Use the removal set function as early as possible to narrow the variable scope." Maybe "Use the unset function early to reduce variable scope." But "移除设值函数" literal translation: "remove set function"? Might be "unset function" in programming context. So translation: "Use the unset/set function early to narrow the variable scope." But "set" not needed. I'd translate: "Use the unset function early to reduce the scope of variables." That seems appropriate.

Thus output Markdown: just that line. No bullet. Keep line breaks. It's just one line. So return that.
...done thinking.

Use the unset function as early as possible to narrow the variable scope.

Thinking...
We need to translate the markdown text. The original is Chinese: "**发散式变化（Divergent Change）**". We should translate to English: "**Divergent Change**". But also keep parentheses? The parentheses show original term and translation? The original already includes the translation in parentheses. Actually it's "发散式变化（Divergent Change）". So maybe we keep the same but translate to English: "**Divergent Change**". But we might need to keep the Chinese? The instruction: "Translate the following Markdown into English." So we should translate the content into English. So we replace Chinese with English. The parentheses contain the translation, we can keep that or maybe we need to translate only Chinese part. But the instruction says translate the Markdown into English. So entire text: "**Divergent Change**". If we keep the original parentheses maybe redundant. So I'd output "**Divergent Change**". Let's output that.
...done thinking.

**Divergent Change**

Thinking...
The user wants translation of the markdown. The content is Chinese. Let's translate: "如果某个模块经常因为不同的原因在不同的方向上发生变化，发散式变化就出现了。"

Translate to English: "If a module frequently changes in different directions for various reasons, divergent changes occur."

We should preserve markdown structure. It's a simple sentence, no markdown formatting? The original content is just a paragraph. We output the translation. Let's output the translated markdown: "If a module frequently changes in different directions for various reasons, divergent changes occur."
...done thinking.

If a module frequently changes in different directions for various reasons, divergent changes occur.

Thinking...
We need to translate from Chinese to English. The Markdown is just a single line: "提炼拆分。". That means "Refine and split." or "Extract and split." Could be context. Likely "Refinement and split." Or "Extract and split." We must preserve Markdown structure and ordering. The text is just a line. So output "Extract and split." or "Refine and split." Which is better? "提炼拆分" literally means "Refine and split." But maybe it's a title. We'll translate as "Refine and Split." Use capitalized? The original didn't have capitalization. Probably just "Refine and split." So final output: "Refine and split."
...done thinking.

Refine and split.

Thinking...
We need to translate to English. Title "霰弹式修改（Shotgun Surgery）" translates to "Shotgun Surgery (Shotgun Modification)". Likely "Shotgun Surgery" is the term, so maybe "Shotgun Surgery (Shotgun Modification)". Preserve formatting: **...** So **Shotgun Surgery (Shotgun Modification)**.
...done thinking.

**Shotgun Surgery (Shotgun Modification)**

Thinking...
We need to translate Chinese to English, preserving Markdown. The text: "如果每遇到某种变化，你都必须在许多不同的类内做出许多小修改，你所面临的坏味道就是霰弹式修改。"

This is a sentence. In English: "If every time you encounter a change, you have to make many small modifications across many different classes, the bad smell you are facing is shotgun modification."

Or "shotgun change"? The phrase likely is "shotgun modification" which is a code smell. So translate as: "If every time you encounter a change, you have to make many small modifications across many different classes, the bad smell you are facing is shotgun modification." Or "shotgun refactoring" but I think "shotgun modification" is fine.

We preserve markdown: It's a single paragraph, no markdown markup. So just the sentence.

Return only translated Markdown.

Let's output: If every time you encounter a change, you have to make many small modifications across many different classes, the bad smell you are facing is shotgun modification.

Make sure line breaks preserved; there's just one line.

Let's do it.
...done thinking.

If every time you encounter a change, you have to make many small modifications across many different classes, the bad smell you are facing is shotgun modification.

Thinking...
We need to translate the provided Chinese Markdown into English, preserving structure. The text:

搬移函数和搬移字段把所有需要修改的代码放进同一个模块里。如果有很多函数都在操作相似的数据，可以使用函数组合成类。如果有些函数的功能是转化或者充实数据结构，可以使用函数组合成变换。如果一些函数的输出可以组合后提供给一段专门使用这些计算结果的逻辑，这种时候常常用得上拆分阶段。

This is a paragraph. No code blocks, so translation straightforward.

We need to preserve Markdown structure. It's just a paragraph. So output will be the English translation.

Translate:

"搬移函数和搬移字段把所有需要修改的代码放进同一个模块里。" -> "Move functions and move fields: put all the code that needs to be modified into the same module."

But context: "搬移函数和搬移字段" maybe "Migrating functions and fields" or "Moving functions and fields". The phrase likely is a heading but it's not marked. The translation:

"Move functions and fields: put all the code that needs modification into the same module."

Next sentence: "如果有很多函数都在操作相似的数据，可以使用函数组合成类。" -> "If many functions operate on similar data, you can compose them into a class."

"If some functions' purpose is to transform or enrich data structures, you can compose them into transformations." -> "If some functions serve to transform or enrich data structures, you can combine them into transformations."

"If some functions' output can be combined to provide a segment of logic that specifically uses these computed results, this is often where splitting stages is useful." -> "If the outputs of some functions can be combined and fed to a piece of logic that specifically uses those computed results, it's often helpful to split into stages."

So final paragraph:

"Move functions and fields: put all the code that needs modification into the same module. If many functions operate on similar data, you can compose them into a class. If some functions serve to transform or enrich data structures, you can compose them into transformations. If the outputs of some functions can be combined and fed to a segment of logic that specifically uses those results, this is often where splitting into stages is useful."

Make sure line breaks preserved as possible. Could keep single paragraph. Let's output.

...done thinking.

Move functions and move fields: put all the code that needs to be modified into the same module.  
If many functions operate on similar data, you can compose them into a class.  
If some functions serve to transform or enrich data structures, you can compose them into transformations.  
If the outputs of some functions can be combined and fed to a segment of logic that specifically uses those computed results, this is often where splitting into stages is useful.

Thinking...
We need to translate to English while preserving markdown. There's no markdown formatting except a paragraph. The text: "一个常用的策略就是使用与内联（inline）相关的重构------如内联函数（1或是内联类------把本不该分散的逻辑拽回一处。完成内联之后，你可能会闻到过长函数或者过大的类的味道，再用与提炼相关的重构手法将其拆解成更合理的小块。"

We translate: "A common strategy is to use refactorings related to inlining—such as inlining a function (or an inline class)—to pull logic that shouldn't be scattered back into one place. After completing the inlining, you might notice the smell of a too-long function or an overly large class; then use refactorings related to extraction to break it into more reasonable small pieces."

Ensure we keep line breaks: The original had a single paragraph. So we produce same.

Return only translated Markdown. No code. Ok.
...done thinking.

A common strategy is to use refactorings related to inlining—such as inlining a function (or an inline class)—to pull logic that shouldn’t be scattered back into one place. After completing the inlining, you might notice the smell of a too‑long function or an overly large class; then use refactorings related to extraction to break it into more reasonable small pieces.

Thinking...
We need translate Chinese into English. "依恋情结（Feature Envy）" means "Attachment complex (Feature Envy)"? Actually "依恋情结" likely means "Attachment complex" or "Envy"? Feature Envy is a known code smell. In Chinese, it's "依赖情结" maybe? But translation "Attachment complex (Feature Envy)" is fine. However need to preserve the header. It's bold. So we output "**Attachment complex (Feature Envy)**". Should we keep parentheses. Yes.

Return only the translated Markdown.

Let's produce:

**Attachment complex (Feature Envy)**

That's it.
...done thinking.

**Attachment complex (Feature Envy)**

Thinking...
The user: "You are a professional technical translator. Translate the following Markdown into English. Rules: preserve Markdown structure, do not translate code blocks or inline code, do not alter URLs, keep line breaks. Return only translated Markdown." The provided Markdown is Chinese: "模块化，就是力求将代码分出区域，最大化区域内部的交互、最小化跨区域的交互。"

We need to translate into English, keep structure. The markdown is just a paragraph. No code block. So translation: "Modularization means striving to partition code into regions, maximizing interaction within a region and minimizing cross-region interaction." Ensure punctuation. Use maybe "Modularization aims to partition code into distinct areas, maximizing intra-region interaction while minimizing inter-region interaction." Provide as markdown. That line.

Return only translated markdown.
...done thinking.

Modularization means striving to partition code into distinct regions, maximizing interaction within a region while minimizing interaction across regions.

Thinking...
We need translate to English. It's a short paragraph. The text: "一个函数跟另一个模块中的函数或者数据交流格外频繁，远胜于在自己所处模块内部的交流，这就是依恋情结的典型情况。"

Translate: "A function communicates with functions or data in another module much more frequently than it does with those within its own module; this is a typical case of attachment syndrome." Or "A function interacting with functions or data in another module is especially frequent, far exceeding communication within its own module; this is a classic example of an attachment complex."

We need to preserve Markdown structure. There is no formatting except maybe the sentence. It's a paragraph. So output just translated paragraph.

Let's output: "A function interacts with functions or data in another module far more often than it interacts within its own module; this is a classic example of an attachment complex."
...done thinking.

A function interacts with functions or data in another module far more often than it interacts within its own module; this is a classic example of an attachment complex.

Thinking...
We need to translate the markdown text into English, preserving structure. The only content is:

**数据泥团（Data Clumps）**

We need to translate "数据泥团" and keep "(Data Clumps)". Probably the translation is "**Data Clumps**" but we need to keep parentheses? The original is "**数据泥团（Data Clumps）**". This is Chinese title with parentheses containing English translation. In English we might remove Chinese and keep only the English. But the instruction: "Translate the following Markdown into English." So we translate the content: Chinese text into English. The parentheses part already English: Data Clumps. So we should translate the Chinese "数据泥团" into "Data Clumps" or "Data Clumps" but there is already English. But maybe they want the translation as "**Data Clumps**" because the parentheses part is already English. But we must preserve parentheses? The Chinese text within parentheses is already English. So we can keep it. But translation could be:

**Data Clumps (Data Clumps)**? That seems redundant. Perhaps they want "**Data Clumps**" alone. But rule: Preserve Markdown structure. So we keep the same markdown: **...**. The content is Chinese with parentheses. Should we translate the Chinese inside parentheses? There is Chinese "数据泥团" inside the bold. The parentheses part "Data Clumps" is English. We should translate the Chinese to English, resulting in "**Data Clumps (Data Clumps)**". That would be odd but consistent. But maybe we remove Chinese entirely and keep parentheses? We can translate as **Data Clumps (Data Clumps)**. Or just **Data Clumps**? The instruction says "Translate the following Markdown into English." So the whole text should be English. The parentheses part is already English. So the translation is "**Data Clumps**". That seems most natural.

Thus the final answer: **Data Clumps**.
...done thinking.

**Data Clumps**

Thinking...
The user is a professional technical translator. They want translation of Markdown: "总是绑在一起出现的数据真应该拥有属于它们自己的对象。"

We need to translate into English, preserve structure and ordering. The line is just a sentence. So the output will be the translated sentence: "Data that always appears bound together really should have its own object."

But let's keep proper translation: "Data that always appears bound together truly deserves its own object." Or "Data that always appear together bound should really have its own object." Let's decide: "Data that always appears bound together should truly have its own object." That matches the nuance: "应该拥有属于它们自己的对象" - "should have their own object." So final output: "Data that always appears bound together should truly have its own object."

Ensure no code block translation.

Thus final output: the sentence in English.
...done thinking.

Data that always appears bound together should truly have its own object.

Thinking...
The user provides a short markdown: "**基本类型偏执（Primitive Obsession）**". The instruction: "You are a professional technical translator. Translate the following Markdown into English. Rules: ...". The content to translate: "**基本类型偏执（Primitive Obsession）**".

So we need to translate that into English while preserving Markdown structure. The phrase "基本类型偏执" is "Primitive Obsession" which is already given in parentheses. We need to translate into English. The English translation is probably "Primitive Obsession". But we need to preserve the structure: bold markup "**...**" remains.

So output: "**Primitive Obsession**". But we might keep the original text? The original is "基本类型偏执（Primitive Obsession）". We translate the Chinese part. So the output should be "**Primitive Obsession (Primitive Obsession)**"? That would be redundant. Probably we just output "**Primitive Obsession**". But maybe they want the original title: "Basic Type Obsession" or "Primitive Obsession". Usually "Primitive Obsession" is the name. So output "**Primitive Obsession**". 

Thus answer: 

**Primitive Obsession**.
...done thinking.

**Primitive Obsession**

Thinking...
We need to translate to English. It's a paragraph in Chinese: "把钱当作普通数字来计算的情况、计算物理量时无视单位（如把英寸与毫米相加）的情况以及大量类似if (a < upper && a > lower)这样的代码。" The translation: "Situations where money is treated as an ordinary number, situations where physical quantities are computed ignoring units (e.g., adding inches and millimeters), and a large number of similar code like if (a < upper && a > lower)."

We need to preserve markdown, but there is no markdown structure except the paragraph. So just return that paragraph translated. Keep line breaks. So output:

"Situations where money is treated as an ordinary number, cases where physical quantities are calculated ignoring units (e.g., adding inches and millimeters), and a large number of code fragments like if (a < upper && a > lower)." Let's ensure proper punctuation. Should we use colon after "Situations"? The original: "把钱当作普通数字来计算的情况、计算物理量时无视单位（如把英寸与毫米相加）的情况以及大量类似if(a \< upper && a \> lower)这样的代码。" So translation: "Situations where money is treated as a regular number, situations where physical quantities are calculated without regard to units (such as adding inches and millimeters), and a large number of code snippets like if (a < upper && a > lower)." That seems fine.

We preserve backticks: there are no code blocks or inline code? The snippet (a < upper && a > lower) is code but not wrapped in backticks. The instruction says "Do NOT translate code blocks (```...```) or inline code in backticks." This snippet isn't inline code in backticks; it's part of the sentence. Should we keep it as is? Yes, keep as is.

Thus final output.
...done thinking.

Situations where money is treated as a regular number, situations where physical quantities are calculated without regard to units (such as adding inches and millimeters), and a large number of code fragments like `if (a < upper && a > lower)`.

Thinking...
We need to translate the Markdown into English. The original: "运用以对象取代基本类型。" This is Chinese. It translates to "Use objects to replace primitive types." Or "Apply objects instead of primitive types." But we need to preserve Markdown structure; there's only a paragraph. So output: "Use objects instead of primitive types." Maybe a short sentence. The instruction: preserve Markdown structure and ordering. No code blocks. So output is that sentence. Possibly we add period at end. Ensure it's plain text. So output: "Use objects to replace primitive types." That is good.

Let's do.
...done thinking.

Use objects to replace primitive types.

Thinking...
The user wants translation from the given Markdown into English. The snippet shows Chinese title with English translation in parentheses. Actually the content: "**重复的switch （Repeated Switches）**" is bold. They want to translate the entire Markdown into English. The current content is the title. It has Chinese characters and English translation in parentheses. But the instruction says to translate. The translation would likely keep the English translation? The title already includes both. But the user likely wants to translate the Chinese into English. The title is "**重复的switch （Repeated Switches）**" meaning "**Repeated switch (Repeated Switches)**" But there's already parentheses. Might keep as is? The rule: preserve Markdown structure and ordering. So we should keep the bold formatting. The content is Chinese and English. The translation might be just the same but with the English phrase? Let's produce "**Repeated switch (Repeated Switches)**" However we need to translate the Chinese part "重复的switch" to "Repeated switch". The parentheses remain same. So final: "**Repeated switch (Repeated Switches)**" with no changes to code blocks or links. No code blocks present.

Return only translated Markdown. Ensure line breaks preserved: there is only one line. Provide that line.
...done thinking.

**Repeated switch (Repeated Switches)**

Thinking...
We need to translate the markdown: "多态。". That is Chinese for "Polymorphism." with a period. The original has no code blocks, no backticks. Just one line: "多态。". Translate to English: "Polymorphism." Probably preserve punctuation: the Chinese period "。" is replaced with "."? The instruction: preserve markdown structure. There's no markdown beyond plain text. So output: "Polymorphism.".

Return ONLY translated Markdown. So output exactly that line.
...done thinking.

Polymorphism.

Thinking...
We need to translate Markdown into English, preserving structure, ordering. The original markdown: "**循环语句（Loops）**". That's Chinese heading? It's just bold text "循环语句（Loops）". They want translation into English. We keep markdown. So output: "**Loop Statements (Loops)**" maybe keep parentheses? The original has parentheses with Loops in English. So we can translate to "**Loop Statements (Loops)**". Keep bold. That is the translation.
...done thinking.

**Loop Statements (Loops)**

Thinking...
The original Markdown is:

```
？管道操作（如filter和map）
```

We need translate into English. The title: "? Pipeline operations (such as filter and map)". Probably "? pipeline operations (e.g., filter and map)". The question mark? Might be a heading? It has a question mark at the start: "？管道操作（如filter和map）". So in English: "？Pipeline operations (such as filter and map)". But the question mark maybe indicates a placeholder or missing? Let's preserve the same punctuation. We'll just translate the Chinese part.

"？管道操作（如filter和map）" => "？Pipeline operations (such as filter and map)".

But maybe better: "? Pipeline operations (e.g., filter and map)". But keep the original punctuation? We'll produce:

```
？Pipeline operations (e.g., filter and map)
```

Yes. That should be it.
...done thinking.

？Pipeline operations (e.g., filter and map)

Thinking...
We need to translate the given Markdown into English. The content: "**冗赘的元素（Lazy Element）**". So we translate to "**Redundant Element (Lazy Element)**" maybe. Chinese "冗赘的元素" means "redundant element". So output: **Redundant Element (Lazy Element)**. Should preserve markdown structure and ordering. There's no code blocks, no inline code. Just a header. Keep line breaks. So final: **Redundant Element (Lazy Element)**.
...done thinking.

**Redundant Element (Lazy Element)**

Thinking...
We need to translate the given Chinese Markdown into English. The text is:

"随着重构的进行越变越小，类最后只剩了一个函数。及时删除这个类，使用内联函数或是内联类。"

We need to preserve Markdown structure and ordering. There's no code or links, just a paragraph. So just translate.

English translation: "As the refactoring progresses, it becomes smaller and smaller; eventually the class only contains a single function. Remove this class promptly, using an inline function or an inline class."

But maybe more natural: "As refactoring continues, the changes shrink, and the class ends up with only one function. Remove the class promptly, using an inline function or inline class." But they might want "as refactoring goes on, the changes get smaller, and the class finally has only one function. Delete the class promptly, using an inline function or inline class."

I think the best translation: "As refactoring progresses, the changes get smaller and smaller, and the class ultimately contains only one function. Remove the class promptly, using an inline function or an inline class."

Check for formatting: It's just a paragraph. So output the translated paragraph.

Return only translated Markdown.
...done thinking.

As refactoring progresses, the changes become smaller and smaller, and the class ultimately contains only a single function. Remove the class promptly, using an inline function or an inline class.

Thinking...
We need to translate that Chinese heading. The heading says "夸夸其谈通用性（Speculative Generality）". Likely means "Speculative Generality" is already in English in parentheses. The Chinese part "夸夸其谈通用性" probably means "Speculative Generality". So translation would keep "Speculative Generality" as in parentheses. But we should translate the Chinese part. Possibly "Speculative Generality (夸夸其谈通用性)". But we need to preserve the structure: it's a heading with ** bold.

We need to translate Chinese to English. So the phrase "夸夸其谈通用性" could be translated as "Speculative Generality". But they already gave that in parentheses. The instruction says to translate the Markdown into English. So we should translate the Chinese to English. So the heading becomes "**Speculative Generality (Speculative Generality)**"? That seems odd. Wait: The original had Chinese with parentheses containing English. So probably the intended translation is "**Speculative Generality (Speculative Generality)**"? But that duplicates. Maybe the parentheses contain a translation of the Chinese. The original has "夸夸其谈通用性（Speculative Generality）". The Chinese part "夸夸其谈通用性" is the term in Chinese, and the parentheses provide the English term "Speculative Generality". So we need to translate the Chinese part to English. So we can output "**Speculative Generality (Speculative Generality)**"? That would not make sense. Better to output "**Speculative Generality (Speculative Generality)**" but it's repeating.

Alternatively we might output "**Speculative Generality**" alone, ignoring parentheses? But the rule: "Return ONLY translated Markdown." It doesn't say we must keep the parentheses. We could translate the entire heading: "Speculative Generality (Speculative Generality)" but that seems redundant. But maybe the original had Chinese and English; translation may be "Speculative Generality (Speculative Generality)". Might just keep the English version: "**Speculative Generality**".

Let's think: The heading was "**夸夸其谈通用性（Speculative Generality）**". If we translate, we might write "**Speculative Generality (Speculative Generality)**" but that's weird. Maybe the translation should be "**Speculative Generality (Speculative Generality)**"? The parentheses may be removed. The instruction didn't mention preserving parentheses. But "Preserve Markdown structure and ordering." So we should preserve the parentheses. So we keep them. So we translate the Chinese inside to its English meaning, but the parentheses already contain English. So we could just replace the Chinese with English, leaving the parentheses unchanged. So the result: "**Speculative Generality (Speculative Generality)**". That's repetitive but follows instructions. But maybe we should drop the parentheses? Hmm.

Given guidelines, I'd output "**Speculative Generality (Speculative Generality)**". But maybe we can output "**Speculative Generality (Speculative Generality)**"? Let's check. The heading has ** around entire string. So we keep ** at start and end. Inside we have Chinese and parentheses. We'll replace Chinese with English "Speculative Generality". So final: **Speculative Generality (Speculative Generality)**.

But that seems redundant. But it's what the rule says. Probably fine. I'll output that.
...done thinking.

**Speculative Generality (Speculative Generality)**

Thinking...
We need to translate the given Chinese markdown into English. The markdown text: "用不上的装置只会挡你的路，所以，把它搬开吧。"

That's the entire content. We preserve markdown structure. There is no code block, no links, no images. Just a sentence. Translate to English: "Devices you don't use only block your way, so move them aside."

Better: "Unneeded devices only obstruct your path, so move them aside."

Let's produce that.
...done thinking.

Devices you don’t use only block your path, so move them aside.

Thinking...
We need to translate the given Markdown into English, preserving structure. The given content is:

```
**临时字段（Temporary Field）**
```

The English translation: "**Temporary Field**" The parentheses "（Temporary Field）" is Chinese then parentheses. The requirement: "Translate the following Markdown into English." So likely we translate the Chinese term inside parentheses? Actually the phrase: "**临时字段（Temporary Field）**". The parentheses already contain English translation. But maybe the original Chinese term is "临时字段" meaning "Temporary Field". The English translation could be "**Temporary Field**". But the parentheses might be unnecessary. They might keep it as is? The instruction says to translate. The Chinese part "临时字段" should be translated. So we output "**Temporary Field**". That likely is the correct. But maybe keep parentheses? The original had both Chinese and English. But we only need English. So we remove Chinese and keep parentheses? I'd just output "**Temporary Field**". No code blocks. It's simple.

Return only translated Markdown.

Thus final answer: **Temporary Field**
...done thinking.

**Temporary Field**

Thinking...
We need to translate Chinese to English: "其内部某个字段仅为某种特定情况而设。" Means "One of its internal fields is only set for a specific situation." Or "Its internal field is only intended for a specific case." We keep markdown structure: there's just a single line of text.

We need to preserve markdown: plain text line. No code. So output should be the English translation.

Let's translate: "Its internal field is only set for a specific situation." That seems correct.

Return only translated markdown.

Thus: "Its internal field is only set for a specific situation."

Check formatting: No changes. Provide that line.
...done thinking.

Its internal field is only set for a specific situation.

Thinking...
The task: "You are a professional technical translator. Translate the following Markdown into English. Rules: Preserve Markdown structure and ordering. Do NOT translate code blocks or inline code in backticks. Do NOT alter URLs, links, or image paths. Keep line breaks as much as possible. Return ONLY translated Markdown."

The Markdown given:

**过长的消息链（Message Chains）**

It appears to be a header or title in bold. They want translation into English. The bold formatting remains.

So translate "过长的消息链" into English: "Too Long Message Chains" or "Overly long message chains" or "Long Message Chains".

The parenthetical (Message Chains) is in English already. So we keep that.

Thus the translation: **Long Message Chains (Message Chains)** or **Excessively Long Message Chains (Message Chains)**.

Probably "Long Message Chains (Message Chains)". Keep bold.

So final output: **Long Message Chains (Message Chains)**

That's it.
...done thinking.

**Long Message Chains (Message Chains)**

Thinking...
We need to translate the given markdown. It's Chinese: "先观察消息链最终得到的对象是用来干什么的，看看能否以提炼函数把使用该对象的代码提炼到一个独立的函数中，再运用搬移函数把这个函数推入消息链。"

We need to preserve markdown structure. There's no code or special formatting. So translation: "First observe what the object obtained from the message chain is used for, see if you can extract the code that uses this object into an independent function using function extraction, then use a move function to push this function into the message chain."

We need to keep line breaks. There's one line, but we can keep it as a paragraph.

Thus output is:

"First observe what the object obtained from the message chain is used for, see if you can extract the code that uses this object into an independent function using function extraction, then use a move function to push this function into the message chain."

No markdown special. Just plain text. But maybe we should keep same line breaks. There's only one line. We'll output exactly that.

Ensure no code blocks. Good.

Return only translated markdown.
...done thinking.

First observe what the object obtained from the message chain is used for, see if you can extract the code that uses this object into an independent function using function extraction, then use a move function to push this function into the message chain.

Thinking...
We need to translate the markdown. The original is Chinese title "**中间人（Middle Man）**". The translation: "**Middle Man**". The parenthetical English is already given, but the Chinese part should be translated: "中间人" -> "Middle Man". So result: "**Middle Man**". However, maybe the translation should be "**Middle Man (Middle Man)**"? Wait, the original text has "中间人（Middle Man）". It's Chinese with English translation in parentheses. So in English, we might want to keep just the English translation. The instructions: translate the following Markdown into English. So we need to translate Chinese words. So "中间人" -> "Middle Man". But there is already "Middle Man" inside parentheses. So the result might be "**Middle Man (Middle Man)**"? But that seems redundant. We should probably keep the parentheses? The instruction: "Preserve Markdown structure and ordering." So the Markdown heading had the parentheses. But if we translate, we might want to keep the parentheses. The original text: **中间人（Middle Man）**. In English, maybe we want **Middle Man (Middle Man)**? But that is odd. However, the translation would be: **Middle Man (Middle Man)**. But we might also consider that the parentheses contain the English translation, so maybe we want to preserve the translation and drop the Chinese. But the parentheses are part of the structure, but the content inside parentheses would be replaced with the translation? If we drop the Chinese and keep parentheses with the English translation, it's the same. So we would output **Middle Man (Middle Man)**. But that duplicates. The instruction doesn't say to remove duplicates. But maybe we want to preserve structure, but we might want to keep both Chinese and English? But the task is to translate into English. So the Chinese should be replaced with English. So we might want to output **Middle Man (Middle Man)**. But maybe we might want to keep parentheses empty? Actually no.

Consider an example: Suppose we have **中间人（Middle Man）**. We want to translate into English: The Chinese "中间人" translates to "Middle Man". So the string would be "**Middle Man（Middle Man）**"? The parentheses contain "Middle Man". So we end up with duplicate. But maybe we want to keep it as is: **Middle Man**. Because the English translation is already there.

However, the instruction: "Translate the following Markdown into English." So presumably we need to provide an English version of the text. So we could output "**Middle Man**" as the translated heading. That seems reasonable. I'd lean to output just "**Middle Man**". That would preserve structure: bold heading. The parentheses part is removed. So final answer: **Middle Man**.
...done thinking.

**Middle Man**

Thinking...
We need to translate the Markdown into English, preserving structure and ordering. There's only one paragraph, no code. So translation: "Some class interface delegates half of its functions to other classes, which is overuse. In this case, you should use the 'remove middleman' pattern." But "移除中间人" likely "remove the intermediary" or "use the remove mediator". Let's produce: "If an interface of a class delegates half its functions to other classes, that's overuse. In this case, you should use the 'remove middleman'." Probably the phrase "remove the middleman" is correct. Let's produce final output.
...done thinking.

If an interface of a class delegates half of its functions to other classes, that’s an over‑use. In such a situation you should apply the **remove middleman** pattern.

Thinking...
The user says: "Translate the following Markdown into English. Rules: ... Keep line breaks as possible. Return ONLY translated Markdown." The original markdown: "**内幕交易（Insider Trading）**". That already contains English words "Insider Trading". It has Chinese "内幕交易". So translation should be "Insider Trading" or "Inside trading"? The original is "**内幕交易（Insider Trading）**" maybe we translate Chinese part: "内幕交易" to "Insider Trading" but inside parentheses already. Actually the title is in Chinese with parentheses. We want translation to English: "**Insider Trading**"? But maybe keep the original parentheses? But it's already "Insider Trading" inside parentheses. Maybe we keep Chinese part? The instruction says translate the Markdown into English. So we should translate Chinese to English. That yields "**Insider Trading (Insider Trading)**"? That is odd. Perhaps just remove Chinese part: "**Insider Trading**". But parentheses are redundant. Maybe keep parentheses and the translation? "Insider Trading (Insider Trading)" is redundant but still acceptable? The instruction: preserve structure and ordering, do not translate code. So we can replace "内幕交易" with "Insider Trading". So result: "**Insider Trading（Insider Trading）**". But the parentheses are Chinese. We could keep parentheses but inside still English. The content inside parentheses originally is English. So maybe we produce "**Insider Trading (Insider Trading)**". That would be double. The original had Chinese parentheses (Japanese). Actually parentheses were Chinese parentheses? In original: "内幕交易（Insider Trading）". Chinese parentheses type. So translation: keep parentheses, but the Chinese part replaced. So "**Insider Trading (Insider Trading)**". That seems okay. Provide only the markdown.

Thus output: "**Insider Trading (Insider Trading)**".

Check if need any line breaks. The content is just a single line. So output that.
...done thinking.

**Insider Trading (Insider Trading)**

Thinking...
We need to translate Chinese to English. The content: "模块之间大量交换数据，因为这会增加模块间的耦合。" That means "A large amount of data is exchanged between modules, which increases coupling between modules." The markdown is plain text. So translate. Return only translated markdown. No code blocks. Just output: "A large amount of data is exchanged between modules, which increases coupling between modules." Keep line breaks. So output that.
...done thinking.

A large amount of data is exchanged between modules, which increases coupling between modules.

Thinking...
We need translate to English. Preserve markdown. The original is a single paragraph. Translate: "In real life, data exchange of certain types is inevitable, but we must try to reduce such situations and bring all such exchanges to the surface."

We need to keep formatting. The original has no markdown markup except paragraph. So translation is straightforward.

Return only translated Markdown.
...done thinking.

In practice, certain data exchanges are inevitable, but we must strive to minimize them and bring all such exchanges into the open.

Thinking...
We need to translate the markdown into English, preserving structure. The original text: "**过大的类（Large Class）**". So translation: "**Large Class (Too Large Class)**" or "**Large Class**". The parentheses contain "Large Class" but already included. So maybe "**Large Class**" or "**Too large class (Large Class)**". The rule: preserve markdown. So just translate. Probably "**Large Class (Too Large Class)**" but the Chinese text "过大的类" means "overly large class" or "large class". The parenthetical "Large Class" is the English translation. So we can translate the Chinese to English but keep the parenthetical. So maybe "**Large Class (Large Class)**" no sense. So just translate the Chinese part. So "**Large Class (Large Class)**" but redundant. Perhaps they want "**Large Class (Too large class)**"? The rule: Translate the Markdown into English. So the Chinese title "过大的类（Large Class）". The parenthetical "Large Class" is already English. So we can translate Chinese part to English: "Large Class (Large Class)"? But that's redundant. Perhaps the correct translation: "**Large Class (Large Class)**" not helpful. Instead maybe "Large Class (Large Class)" keep original? The request: "Translate the following Markdown into English." So the output should be English. So we could output: "**Large Class (Large Class)**". But that is same as original? The original had Chinese. The translation would be "**Large Class (Large Class)**". But that's okay. Let's output that.
...done thinking.

**Large Class (Large Class)**

Thinking...
We need to translate the markdown into English, preserving structure. The text is "**异曲同工的类（Alternative Classes with Different Interfaces）**". That likely is a header or bold text. We need to translate. The translation would be "**Classes with Similar Purpose but Different Interfaces (Alternative Classes with Different Interfaces)**" or something. The original is a Chinese phrase and a parenthetical translation. The phrase is "异曲同工的类" meaning "classes that are like a similar work" basically "classes that are analogous" or "alternative classes with different interfaces". They gave a translation "Alternative Classes with Different Interfaces". So the best translation: "**Classes with Similar Purpose but Different Interfaces (Alternative Classes with Different Interfaces)**". But we must preserve original? We should translate. It is bold text. Keep the asterisks. We need to produce only the translated markdown. The content: "**异曲同工的类（Alternative Classes with Different Interfaces）**". We translate: "**Classes with a Similar Purpose but Different Interfaces (Alternative Classes with Different Interfaces)**". But maybe simpler: "**Classes with Similar Purpose but Different Interfaces (Alternative Classes with Different Interfaces)**". Let's produce that.
...done thinking.

**Classes with a Similar Purpose but Different Interfaces (Alternative Classes with Different Interfaces)**

Thinking...
We need to translate into English. The given Markdown: "**纯数据类（Data Class）**" which means "**Pure Data Class (Data Class)**" Actually the Chinese phrase is "纯数据类（Data Class）". So we translate to English while preserving markdown. So we output "**Pure Data Class (Data Class)**". That seems correct. Ensure no code blocks or inline code. Just output that line.
...done thinking.

**Pure Data Class (Data Class)**

Thinking...
We need to translate the Chinese to English. Keep Markdown structure: It's a single paragraph. The original: "纯数据类：它们拥有一些字段，以及用于访问（读写）这些字段的函数，除此之外一无长物。"

Translate: "Pure data classes: they have some fields and functions for accessing (reading/writing) these fields, and nothing else." Or "Pure data classes: they contain some fields and functions for accessing (reading/writing) those fields, and nothing else." The term "纯数据类" maybe "pure data classes" or "plain data classes". The phrase "除此之外一无长物" means "nothing else beyond that". So translation: "Pure data classes: they have some fields and functions for accessing (reading/writing) those fields, and nothing else." Good.

Return only translated Markdown. No code blocks. There's no code block. Just plain paragraph. So output: "Pure data classes: they have some fields and functions for accessing (reading/writing) those fields, and nothing else."

Ensure preserve formatting: It's just a single paragraph. We'll output that.
...done thinking.

Pure data classes: they have some fields and functions for accessing (reading/writing) those fields, and nothing else.

Thinking...
We need to translate the Markdown into English. The original is "**被拒绝的遗赠（Refused Bequest）**". That likely is a heading or bold? It's in bold. So we translate. The title is "被拒绝的遗赠（Refused Bequest）". Should keep the parentheses maybe? The parentheses are Chinese characters. The translation likely is "**Refused Bequest (Refused Bequest)**"? Wait the original has Chinese title and parentheses contain English. Actually it reads: **被拒绝的遗赠（Refused Bequest）**. So the Chinese title and the English translation in parentheses. We should translate into English. The English translation is "Refused Bequest". But maybe keep the Chinese? The rule says translate the Markdown into English. So we might remove Chinese and keep English. But perhaps we should translate the heading as "**Refused Bequest**". But the original had parentheses, maybe it's like a title: "Refused Bequest". The parentheses show the translation. We need to translate into English, so we should output just the English. So I'd produce "**Refused Bequest**". Ensure keep the Markdown bold. That’s all.
...done thinking.

**Refused Bequest**

Thinking...
We need to translate the Chinese text to English. It's a single sentence: "子类应该继承超类的函数和数据。". That means: "Subclasses should inherit the methods and data of the superclass." Or "Subclasses should inherit the superclass's functions and data." Keep the period. Just translate. So the Markdown has only that line. Return the translated line. Ensure not to translate code blocks (none). So output: "Subclasses should inherit the superclass's functions and data." We'll keep a period. Also the original had a period. So final: "Subclasses should inherit the superclass's functions and data." That's all.
...done thinking.

Subclasses should inherit the superclass's functions and data.

Thinking...
We need to translate the given markdown into English. The text is Chinese: "不愿意支持超类的接口，就不要虚情假意地糊弄继承体系，应该运用以委托取代子类或者以委托取代超类彻底划清界限。"

We must preserve markdown structure. It's a single sentence. The translation: "If you are unwilling to support the interface of the superclass, do not feign a relationship with the inheritance hierarchy; instead, you should use delegation to replace subclasses or use delegation to replace superclasses, thereby clearly delineating boundaries."

But we must keep structure. There's no code block. So output just the translated line. Let's produce the translation.
...done thinking.

If you are unwilling to support the superclass’s interface, do not feign a relationship with the inheritance hierarchy; instead, use delegation to replace subclasses or use delegation to replace superclasses, thereby clearly delineating boundaries.

Thinking...
We need to translate "注释（Comments）" into English. It's a heading in bold. So "**Comments**" maybe. In English, "注释" means "comments". The parenthetical (Comments) in original suggests maybe translation is Comments (Comments). But they already wrote "Comments" inside parentheses. The title could be "Comments" or "Annotations". Since they provided English in parentheses, we translate that. So output: "**Comments**". Ensure we keep markdown. Return only translated markdown.
...done thinking.

**Comments**

Thinking...
We need to translate the Chinese markdown into English, preserve markdown structure, line breaks. There's only one paragraph. No code. So just translate:

"如果你需要注释来解释一块代码做了什么，试试提炼函数；如果函数已经提炼出来，但还是需要注释来解释其行为，试试用改变函数声明为它改名；如果你需要注释说明某些系统的需求规格，试试引入断言。"

English translation: "If you need comments to explain what a piece of code does, try extracting a function; if the function has already been extracted but still needs comments to explain its behavior, try renaming it by changing its declaration; if you need comments to specify certain system requirements, try introducing assertions."

Make sure punctuation is fine. Probably maintain Chinese punctuation? Use English punctuation. Use semicolons. Let's produce.

...done thinking.

If you need comments to explain what a piece of code does, try extracting a function; if the function has already been extracted but still needs comments to explain its behavior, try renaming it by changing its declaration; if you need comments to specify certain system requirements, try introducing assertions.

Thinking...
We need translate Chinese to English. Keep markdown structure. The title: "**第4章　构筑测试体系**". So "**Chapter 4: Building a Testing Framework**" maybe. Use Chinese translation? The task: translate the Markdown into English. So we output "**Chapter 4: Building a Testing System**" or "**Chapter 4: Building the Test System**". Should preserve bold and maybe formatting. The Chinese title uses double em dash? Actually "第4章　构筑测试体系". Use two spaces? There is a wide space between 章 and 构筑. We can output "**Chapter 4 Building the Test System**"? Might be "Chapter 4: Building a Testing System". Keep bold and spaces. We need preserve line breaks.

Return ONLY translated Markdown. So:

**Chapter 4 Building a Test System**? Let's choose "Chapter 4: Building the Test System".

But original Chinese: "构筑测试体系" means "Constructing the test system". So we translate to "Constructing a Test System". Use "Chapter 4 Constructing a Test System".

Let's output: **Chapter 4 Constructing a Test System**. Use same spacing? The original has a non-breaking space between 章 and 构筑: there is a full-width space? It might be a Chinese space. We can keep a normal space. So "**Chapter 4 Constructing a Test System**". Should be okay.

Ok.
...done thinking.

**Chapter 4 Constructing a Test System**

Thinking...
We need to translate the given markdown to English. The given markdown: "**自测试代码的价值**" This is Chinese, meaning "**The value of self-test code**" or "**The value of test code**". The translation should preserve markdown. So output: "**The value of self-test code**" or "The value of self-test code". Let's translate. "自测试" is "self-test" or "auto test". So I'd translate: "**The value of self-test code**".
...done thinking.

**The value of self-test code**

Thinking...
We need to translate to English. Preserve Markdown. The original: "**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**" Wait actual: "**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**" Wait we need to read original. Let's copy:

**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**

But the given text: "**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**"

Actually the given is:

**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**

Wait the original text: 
**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**

But actual from the question: "**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**" No it's a bit off.

Actually the original: "**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**"

But reading again: The original text given in the question is:

**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**

No I'm misreading. Let's read the given exactly:

"**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**"

Wait maybe the text is: "**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**" But actually I think the original is:

**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…** Wait I'm still stuck.

Let's scroll: The user gave:

**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**

But the actual from the prompt: 
**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**  

Wait I'm repeating.

Actually the user wrote:

**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**  

But reading the initial: "**时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…**"

Anyway translation: "**Time statistics: The time spent writing code accounts for only a small portion of all time. Some time is spent deciding what to do next, some on design, but the time spent debugging is the largest. The most important thing is that more often than not, the debugging effort reveals issues that arise in earlier work.**" But need to keep original sentence structure: "Time statistics: The time spent writing code is only a small part of all time. Some time is used to decide what to do next, some time is spent on design, but the time spent debugging is the most. The most important thing is that ..."

Wait the original: "时间统计：编写代码的时间仅占所有时间中很少的一部分。有些时间用来决定下一步干什么，有些时间花在设计上，但是，花费在调试工作的量，最重要的是在先前的工作中，出现了，更多地，…" The last part "最重要的是在先前的工作中，出现了，更多地" maybe "most importantly, it often arises in earlier work, more often".

Let's translate carefully: "Time statistics: The time spent writing code accounts for only a small portion of all time. Some time is used to decide what to do next, some time is spent on design, but the time spent on debugging is the greatest. Most importantly, it often appears in previous work, more often..."

But we need to keep sentence structure maybe: "**Time statistics: The time spent writing code accounts for only a small part of all time. Some of the time is spent deciding what to do next, some is spent on design, but the time spent debugging is the largest. The most important thing is that, in earlier work, more often the debugging work arises.**"

But maybe simpler: "**Time statistics: The time spent writing code is only a small portion of all time. Some time is used to decide what to do next, some time is spent on design, but the time spent debugging is the largest. The most important thing is that the debugging work often arises from earlier work.**"

We need to preserve markdown. It's all bold.

Thus final output: **Time statistics: The time spent writing code accounts for only a small portion of all time. Some time is used to decide what to do next, some time is spent on design, but the time spent on debugging is the largest. The most important thing is that, in earlier work, debugging work often arises more frequently.**

Better to keep original structure: "Time statistics: Writing code time only accounts for a small portion of all time. Some time is used to decide what to do next, some is spent on design, but debugging takes the most time. The most important thing is that debugging often arises from earlier work, more often."

Let's produce final.
...done thinking.

**Time statistics: The time spent writing code accounts for only a small portion of all time. Some time is used to decide what to do next, some is spent on design, but debugging takes the most time. The most important thing is that debugging often arises from earlier work, more frequently.**

Thinking...
We have to translate Chinese to English. The Markdown: "一套测试就是一个强大的bug侦测器，能够大大缩减查找bug所需的时间。"

Translate: "A set of tests is a powerful bug detector that can greatly reduce the time required to find bugs."

We must preserve markdown structure. There's no special markdown syntax. Just a paragraph. Return only translated markdown.
...done thinking.

A set of tests is a powerful bug detector that can greatly reduce the time required to find bugs.

Thinking...
We need to translate that Chinese sentence into English. The sentence: "撰写测试代码的最好时机是在开始动手编码之前，把注意力集中于接口而非实现。" That translates to: "The best time to write test code is before you start coding, focusing on interfaces rather than implementations." Or "The best time to write test code is before you start coding, focusing on interfaces rather than implementations." So we need to return only translated Markdown. The original has no formatting except a single line. So output that line in English. Ensure no code blocks. So just the sentence.
...done thinking.

The best time to write test code is before you start coding, focusing on interfaces rather than implementations.

Thinking...
We just need translate the markdown text "测试实例" which is Chinese meaning "Test instance" or "Test example". Since it's a heading? The markdown starts with "**测试实例**" which is bold. So translate into English: "**Test Instance**". Ensure preserve markdown. Ok.
...done thinking.

**Test Instance**

Thinking...
We need translate Chinese sentence to English. Preserve markdown. The phrase: "**总是确保测试不该通过时真的会失败：在代码中暂时引入一个错误。**" So translation: "**Always ensure that tests that should not pass do actually fail: temporarily introduce an error in the code.**" Or "Always make sure that failing tests do fail: temporarily add an error in the code." Keep bold. Provide only translated markdown. Let's output.
...done thinking.

**Always ensure that tests that should fail do indeed fail: temporarily introduce an error in the code.**

Thinking...
We need to translate the provided Markdown into English. The markdown content is:

**探测边界条件**

We need to preserve markdown. Just translate the phrase: "探测边界条件" meaning "Detect boundary conditions" or "Explore boundary conditions" or "Probe boundary conditions". Likely "Detect boundary conditions". Could also be "Test boundary conditions" or "Explore boundary conditions". In context, it's about technical translation. I'll translate as "**Detect Boundary Conditions**". Keep bold. Return only the translated markdown.
...done thinking.

**Detect Boundary Conditions**

Thinking...
We need to translate the given markdown: "输入：空集合、0、空字符串\... 预期输出：？". The instruction: preserve markdown structure and ordering, do not translate code blocks or inline code. The content has no code blocks. The Chinese text: "输入：空集合、0、空字符串\... 预期输出：？". We translate to English: "Input: empty set, 0, empty string... Expected output: ?" But we need to preserve punctuation? We can translate accordingly. There's backslash before ellipsis: "\..." maybe for escape? But it's literal. In translation, we should preserve it. Maybe keep as "…"? But we should keep as is. So translation: "Input: empty set, 0, empty string\... Expected output: ?" Use same formatting.

Thus output: "Input: empty set, 0, empty string\... Expected output: ?" No markdown changes. Probably need to keep a newline? The original line breaks? The input is just a line: "输入：空集合、0、空字符串\... 预期输出：？". That is one line. So translation also one line. Provide it.

Return only translated markdown.
...done thinking.

Input: empty set, 0, empty string\... Expected output: ?

Thinking...
We need to translate the given markdown into English. The text is Chinese: "**考虑可能出错的边界条件**，把测试火力集中在那儿。"

We need to preserve markdown structure. It's bold text: **...**. So we will translate that portion into English: "**Consider the boundary conditions that might cause errors**, focus the testing effort there."

Ensure we preserve punctuation. The Chinese phrase: "**考虑可能出错的边界条件**，把测试火力集中在那儿。" So translation: "**Consider the boundary conditions that might cause errors**, focus the testing effort there."

We need to preserve the bold markup. So output: **Consider the boundary conditions that might cause errors**, focus the testing effort there.

Return only the translated markdown.
...done thinking.

**Consider the boundary conditions that might cause errors**, focus the testing effort there.

Thinking...
We need to translate the Chinese to English. The Markdown text is: "不要因为测试无法捕捉所有的bug就不写测试，因为测试的确可以捕捉到大多数bug。"

We preserve markdown structure; no code blocks. So we output: "Do not stop writing tests just because tests cannot catch all bugs, because tests can indeed catch the majority of bugs."

Check punctuation. The original: "不要因为测试无法捕捉所有的bug就不写测试，因为测试的确可以捕捉到大多数bug。"

We translate: "Don’t stop writing tests just because tests can’t catch every bug, because tests can indeed catch the majority of bugs."

We must preserve line breaks. There's only one line. So output exactly that sentence.
...done thinking.

Do not stop writing tests just because tests can’t catch every bug, because tests can indeed catch the majority of bugs.

Thinking...
We need translate to English. The content is "第5章 介绍重构名录". "第5章" is "Chapter 5". "介绍重构名录" could be "Introduction to the Refactor Catalog" or "Introduction to the Refactoring Directory". "重构名录" literally "refactor directory". Let's produce: **Chapter 5: Introduction to the Refactor Directory**.

Ensure no code blocks. Just translate. So output:

**Chapter 5: Introduction to the Refactor Directory**

Yes.
...done thinking.

**Chapter 5: Introduction to the Refactor Directory**

Thinking...
We need to translate the provided Markdown into English. The Markdown is minimal: "本章主要作用是承上启下，略。" That's a Chinese sentence. Translation: "The main purpose of this chapter is to bridge the previous and subsequent sections, briefly." Or "This chapter mainly serves to connect the previous and the following parts, briefly." We need to preserve Markdown structure. The input has no special Markdown syntax except the text. We should output the English translation. So: "This chapter mainly serves to bridge the preceding and following sections, briefly." Ensure to keep line breaks. There's just one line. So output that.
...done thinking.

This chapter mainly serves to bridge the preceding and following sections, briefly.

Thinking...
We need to translate. The content: "**第6章 第一组重构**" which is Chinese: "**Chapter 6 First Group Refactoring**" maybe. The rule: preserve Markdown structure and ordering. The content is a header in bold. Should preserve bold tags: **. So translation of text inside: "第6章 第一组重构" to English: "Chapter 6: First Group Refactoring". But preserve the bold: **...**. Should we add colon? It might be "Chapter 6 First Group Refactoring" but maybe "Chapter 6: First Group Refactoring" or "Chapter 6 - First Group Refactoring". I'd use "Chapter 6: First Group Refactoring". So output: **Chapter 6: First Group Refactoring**. Also keep line breaks. So final answer.
...done thinking.

**Chapter 6: First Group Refactoring**

Thinking...
We just need to translate. The original: "**提炼函数（Extract Function）**" means "**Extract Function**" but preserve the Markdown. It might keep the Chinese part? We should translate to English: "**Extract Function**". The parenthesis includes Chinese translation? Actually "提炼函数（Extract Function）" meaning Chinese title with English translation. Should we translate to "Extract Function" or "Refactor Function"? It is already English inside parentheses. So final translation: "**Extract Function**". Provide only the translated markdown.
...done thinking.

**Extract Function**

![](/img/0_refactor.png)

![](/img/0_refactor-1.png)

Thinking...
We need to translate markdown into English. Original markdown is:

**动机**

That is bold "动机" which means "Motivation". So translated: **Motivation**. And preserve markdown. So output: **Motivation**.
...done thinking.

**Motivation**

Thinking...
We need to translate the given Markdown into English, preserving structure. The input is:

**将意图与实现分开**：如果你需要花时间浏览一段代码… etc. So we should translate to English. It has Markdown bold formatting (**...**). The text after the colon is Chinese, to translate.

So output: **Separate Intent from Implementation**: If you need to spend time browsing a block of code to figure out what it's actually doing, then you should extract it into a function, and name it based on what it does. Because most of the time there's no need to worry about how the function achieves its purpose (that's what the function body does).

Make sure to preserve line breaks as possible. The original had a line break? The text is:

**将意图与实现分开**：如果你需要花时间浏览一段代码才能弄清它到底在干什么，那么就应该将其提炼到一个函数中，并根据它所做的事为其命名。因为大多数时候根本不需要关心函数如何达成其用途（这是函数体内干的事）

So we translate as:

**Separate Intent from Implementation**: If you need to spend time browsing a piece of code to understand what it's actually doing, then you should extract it into a function and name it based on what it does. Because most of the time there's no need to worry about how the function achieves its purpose (that's what the function body does).

Yes.

Return only translated markdown.
...done thinking.

**Separate Intent from Implementation**: If you need to spend time browsing a piece of code to understand what it’s actually doing, then you should extract it into a function and name it based on what it does. Because most of the time there’s no need to worry about how the function achieves its purpose (that’s what the function body does).

Thinking...
We need to translate Chinese to English. The markdown is short: "好名字：在一个大函数中，一段代码放着一句注释，提炼成函数，注释往往提示一个好名字。"

We need to preserve markdown structure. It's plain text, but has a colon after "好名字：". So we translate: "Good name: In a large function, a piece of code accompanied by a comment; extracting it into a function, the comment often hints at a good name." We could keep the colon. Should we keep "Good name:"? Maybe "Good name:" or "Good Naming:"? Let's translate exactly: "Good Name: In a big function, a section of code accompanied by a comment; extracting it into a function, the comment often hints at a good name." That is fine.

We should not add extra formatting. So just return:

Good Name: In a large function, a piece of code accompanied by a comment; extracting it into a function, the comment often hints at a good name.

Return only the translated markdown.
...done thinking.

Good Name: In a large function, a piece of code accompanied by a comment; extracting it into a function, the comment often hints at a good name.

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: ...". The markdown: **做法**. This likely means "Method" or "Procedure" in Chinese. So we translate into English. The structure is just bold. So output: **Method** or **Procedure**. Let's choose "Method". Return only the translated markdown. So:

**Method**

That's it.
...done thinking.

**Method**

Thinking...
We need to translate the Markdown. The content: "创造一个新函数：以"做什么"而非"怎么做"来命名。"

English translation: "Create a new function: name it by 'what to do' rather than 'how to do'."

We should preserve Markdown. There's no code blocks. So just return the translated line.

Thus output: "Create a new function: name it by 'what to do' instead of 'how to do'."

We should keep the punctuation. The original has colon after "创造一个新函数：" and Chinese colon. We'll use colon.

Return the translation.

Also line break maybe. So final output:

Create a new function: name it by "what to do" rather than "how to do".
...done thinking.

Create a new function: name it by "what to do" rather than "how to do".

Thinking...
The user provides a short text: "无局部变量，直接提炼成函数；" This is Chinese, meaning "No local variables, directly extract into function;". It's a single sentence, maybe a comment. The instruction: translate the Markdown into English. The Markdown structure is trivial: a single line. There's no code blocks. Just translate that sentence. "No local variables, extract directly into a function;". Or "No local variables; directly extract into a function;". We'll keep punctuation similar. The semicolon might remain. The Chinese uses semicolon and Chinese punctuation. We'll translate accordingly.

We preserve line break. So final output: "No local variables, directly extract into a function;"

Return only the translated Markdown.

Let's produce it.
...done thinking.

No local variables, directly extract into a function;

Thinking...
We need to translate the given Markdown. The text is: "有局部变量但只读，作为参数传递给目标函数". That means "There are local variables that are read-only, passed as arguments to the target function". So translation: "Local variables are read-only and passed as arguments to the target function". We need preserve Markdown structure: It's a single paragraph, no special formatting. Just translate. No code blocks. So final output: that line in English. Also keep line breaks. There's no extra formatting. So produce translated Markdown.
...done thinking.

Local variables are read-only and passed as arguments to the target function

Thinking...
We need to translate Chinese text into English, preserving markdown. The content is a paragraph. There's no markdown formatting besides paragraph. So we translate: "局部变量被赋值：只在提炼函数中被使用则可直接声明在提炼函数中；在提炼函数外也被使用则可作为提炼函数的返回值；多个变量被修改可考虑返回一个对象或者使用其他重构手法（以查询取代临时变量、拆分变量）". Provide translation: "Local variables assigned: If they are only used within the extracted function, they can be declared directly inside the extracted function; if they are also used outside the extracted function, they can be returned as the function's return value; if multiple variables are modified, consider returning an object or using other refactoring techniques (replace temporary variables with queries, split variables)." Use plain paragraph. Should we use line breaks? The original had one paragraph; we keep same. Provide only translated markdown.
...done thinking.

Local variables assigned: If they are used only within the extracted function, they can be declared directly inside the extracted function; if they are also used outside the extracted function, they can be returned as the function’s return value; if multiple variables are modified, consider returning an object or using other refactoring techniques (replace temporary variables with queries, split variables).

Thinking...
We need to translate the given Markdown into English, preserving structure. The markdown: **内联函数（Inline Function）**. That's a bold heading: "Inline Function (Inline Function)". Actually "内联函数（Inline Function）" meaning "Inline Function (Inline Function)". We translate into English: "**Inline Function (Inline Function)**". Or "Inline Function (Inline Function)"? The translation: "Inline Function (Inline Function)" is redundant. Probably "Inline Function (Inline Function)"? The original Chinese includes the English term inside parentheses. The translation likely would be "**Inline Function (Inline Function)**". But maybe the translation expects "**Inline Function (Inline Function)**"? We need to preserve the same content but translate the Chinese part: "内联函数" to "Inline Function". The parentheses content is already English "Inline Function". So final: "**Inline Function (Inline Function)**". But we must preserve formatting: bold. So output the line with ** at beginning and end. So answer: **Inline Function (Inline Function)**. That's it.
...done thinking.

**Inline Function (Inline Function)**

![](/img/0_refactor-2.png)

![](/img/0_refactor-3.png)

![](/img/0_refactor-4.png)

Thinking...
We need to translate the markdown into English. It has a heading in bold: **动机** meaning "Motivation". So output: **Motivation**. No other changes. Preserve markdown. Ensure line breaks. Return only translated Markdown.
...done thinking.

**Motivation**

Thinking...
We need to translate the given markdown into English. The content: "**间接性可能带来帮助，但非必要的间接性总是让人不舒服。**" That's a bolded sentence: "Indirectness may bring help, but unnecessary indirectness always makes people uncomfortable." So translation: "**Indirectness can be helpful, but unnecessary indirectness always makes people uncomfortable.**" Keep markdown formatting, bold. So output that.
...done thinking.

**Indirectness can be helpful, but unnecessary indirectness always makes people uncomfortable.**

Thinking...
We need to translate the markdown into English. The content: "某些函数其内容和名称清晰易读". That is Chinese: "Certain functions have clear and readable content and names." So translation: "Some functions have clear and readable content and names." Maybe "Certain functions are clear and easy to read in terms of content and name." Let's keep simple: "Some functions have clear content and naming." The title? The Markdown is just one line. So produce that line in English. Ensure not to alter code blocks. No code. Just output the translation. So: "Certain functions have clear and readable content and names."
...done thinking.

Certain functions have clear and readable content and names.

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: Preserve Markdown structure and ordering. Do NOT translate code blocks (` ```...``` `) or inline code in backticks. Do NOT alter URLs, links, or image paths. Keep line breaks as much as possible. Return ONLY translated Markdown."

The markdown text is:

```
一群函数的组织不甚合理，先内联到一个大函数，再提炼。
```

This is Chinese. We need to translate it into English. It says: "The organization of a group of functions is not very reasonable; first inline them into a large function, then refine."

We need to preserve markdown structure. There's no code block or inline code. So we just produce the translated text.

Return ONLY translated Markdown. So we just output the translated string.

Thus: "The organization of a group of functions is not very reasonable; first inline them into a single large function, then refine." Should be simple. Ensure keep line breaks as much as possible; there's just one line.

So output:

"The organization of a group of functions is not very reasonable; first inline them into a single large function, then refine."

Yes.
...done thinking.

The organization of a group of functions is not very reasonable; first inline them into a single large function, then refine.

Thinking...
We need to translate the markdown content from Chinese to English. The content is only "**做法**". That's "Method" or "Procedure" maybe. In Markdown, bold text: **做法**. So we translate to "**Method**" or "**Procedure**". I think "Method" is concise. Keep the formatting: **Method**. No code blocks. Just output the translated markdown. So final answer: **Method**.
...done thinking.

**Method**

Thinking...
We need to translate the markdown content. The markdown just says: "确定函数不具多态性". That's Chinese, meaning "Confirm that the function has no polymorphism" or "Determine that the function is not polymorphic". The phrase "确定函数不具多态性" is likely a section title. In English, "Confirm that the function is not polymorphic". So translation: "Confirm that the function is not polymorphic". Keep markdown structure: no bullet, no header, but might be heading? It's just a line.

Given the markdown structure: there's no heading syntax (#). It's just plain text. So output is just the translated text.

Let's produce: "Confirm that the function is not polymorphic". That's the translation.
...done thinking.

Confirm that the function is not polymorphic

Thinking...
The task: The input is a markdown: "找到所有调用点执行替换（重点在于始终小步前进）"

We need to translate into English. Preserve Markdown structure and ordering. There is no code block. So just translate. The phrase: "Find all call points to execute replacement (the key is always to move forward in small steps)". We should keep parentheses, perhaps. Let's produce: "Find all call sites and perform replacements (the focus is on always moving forward in small steps)".

Return ONLY translated Markdown. So output that line.
...done thinking.

Find all call sites and perform replacements (the focus is on always moving forward in small steps)

Thinking...
We need translate: "**提炼变量（Extract Variable）**" into English, preserving markdown. Should be "**Extract Variable**". The Chinese part inside parentheses: (提炼变量) maybe translation: "Extract Variable". Actually we need translate entire line: "**提炼变量（Extract Variable）**". So we produce "**Extract Variable**" or maybe keep original? The rule: translate markdown into English. So we need translate the whole content. The entire phrase is "**提炼变量（Extract Variable）**". The translation likely: "**Extract Variable**". The parentheses contain the English version. But we can just produce "**Extract Variable**". Let's produce that.

Check rules: preserve markdown structure and ordering. So output "**Extract Variable**".

Return ONLY translated Markdown.

Done.
...done thinking.

**Extract Variable**

![](img/0_refactor-5.png)

![](img/0_refactor-6.png)

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: ..."

We have Markdown: **动机**

We translate to English. "Motivation" is the translation. We need to preserve formatting. So **Motivation**. So output: **Motivation**. Only that.
...done thinking.

**Motivation**

Thinking...
We need to translate the markdown: "**提供了合适的上下文**：帮助我们将表达式分解为比较容易管理的形式，也便于…". Should preserve bold, colon, etc. Translate to English: "**Provided suitable context**: helps us break down the expression into a more manageable form, and makes it easier to understand what part of the code does."

Ensure preserve punctuation and formatting. So output:

**Provided suitable context**: helps us break down the expression into a more manageable form, and makes it easier to understand what part of the code does.

Make sure no changes to code blocks - none present. Just this line.

Return only translated markdown.
...done thinking.

**Provided suitable context**: helps us break down the expression into a more manageable form, and makes it easier to understand what part of the code does.

Thinking...
We just translate the heading. "内联变量（Inline Variable）" to English. The asterisks for bold. So "**Inline Variable (Inline Variable)**"? Wait we need keep structure: It's bold. So "**Inline Variable (Inline Variable)**"? Probably better: "**Inline Variable (Inline Variable)**" but the parenthesis already says "Inline Variable". The Chinese title "内联变量（Inline Variable）". In English we can just keep "Inline Variable (Inline Variable)". But it's redundant. Could translate to "**Inline Variable (Inline Variable)**". But perhaps just keep original Chinese? We should translate. So "**Inline Variable (Inline Variable)**" is okay. Alternatively, maybe use "**Inline Variable (Inline Variable)**". Provide final output.

But maybe we want to keep Chinese inside? But rule: translate. So we remove Chinese. So produce: **Inline Variable (Inline Variable)**

Let's produce that.
...done thinking.

**Inline Variable (Inline Variable)**

![](img/0_refactor-7.png)

![](img/0_refactor-8.png)

Thinking...
We need to translate Chinese to English. The markdown: "**动机**" meaning "**Motivation**". So translate to "**Motivation**". Keep markdown. Ensure no extra spaces. Output only the translated markdown.
...done thinking.

**Motivation**

Thinking...
We need translate into English. The markdown is simple: two sentences in Chinese. Must preserve markdown. The text: "有时候，变量名字并不比表达式本身更具表现力。还有些时候，变量可能会妨碍重构附近的句子。" Actually the last word: "附近的代码" maybe "代码" not "句子". The original says "附近的代码". So translation: "Sometimes, a variable name is no more expressive than the expression itself. Other times, the variable may hinder refactoring of nearby code." Need to keep line breaks. So output:

Sometimes, a variable name is no more expressive than the expression itself. Other times, the variable may hinder refactoring of nearby code.

But preserve markdown structure: the original had two sentences separated by line break? It shows two sentences separated by a space? The markdown shows:

有时候，变量名字并不比表达式本身更具表现力。还有些时候，变量可能会妨碍重构附近的代码。

So it's one paragraph? Might be two sentences separated by newline? It shows them separated by a newline in the markdown. The content shows a line break between the two sentences? There's no blank line. It's just newline after the first sentence? In the markdown snippet: after Chinese punctuation? Actually it's a single line? It shows a newline after the first sentence? The snippet:

有时候，变量名字并不比表达式本身更具表现力。还有些时候，变量可能会妨碍重构附近的代码。

It seems one line? But we can't guarantee. We can preserve the line break. So output:

Sometimes, a variable name is no more expressive than the expression itself. Other times, the variable may hinder refactoring of nearby code.

Thus just that.
...done thinking.

Sometimes, a variable name is no more expressive than the expression itself. Other times, the variable may hinder refactoring of nearby code.

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: ... Return ONLY translated Markdown." The markdown contains "**改变函数声明（Change Function Declaration）**". So translate to English: "**Change Function Declaration**". Keep formatting. Provide only the translated markdown. No code blocks. Just the header. Probably keep the bold. So output: **Change Function Declaration**.
...done thinking.

**Change Function Declaration**

![](img/0_refactor-10.png)

Thinking...
We need to translate into English: "**动机**" => "**Motivation**". Keep markdown. Return only translated markdown. So output "**Motivation**".
...done thinking.

**Motivation**

Thinking...
We need to translate into English. The sentence: "一个好名字能让人一眼看出函数的用途；". Should be "A good name lets you see the purpose of the function at a glance;" or "A good name makes the function's purpose obvious at a glance;". Keep the punctuation. Let's keep the semicolon? It ends with ;. Should we keep? In English it's fine.

Return only translated markdown. So just that line.

Note: It's a Markdown paragraph. So just output the translated sentence.
...done thinking.

A good name lets you see a function’s purpose at a glance;

Thinking...
We need translate Chinese text to English. The Markdown includes just a paragraph. Should preserve formatting. No code. Just translation. Let's produce English.
...done thinking.

The function's parameter list describes how the function interacts with the external world. Modifying the parameter list not only expands the function's applicability but also changes the conditions required to connect a module, thereby eliminating unnecessary coupling.

Thinking...
We need to translate the markdown into English. The heading is **封装变量（Encapsulate Variable）**. In English: **Encapsulate Variable**. Possibly the Chinese is for clarity; we can preserve the translation. So final output:

**Encapsulate Variable**

But we have to preserve the original markup. The original is "**封装变量（Encapsulate Variable）**". In translation, we might replace the entire text? They say translate into English. So presumably we replace the Chinese part. We might keep the parentheses and English inside. The best is "**Encapsulate Variable**". But we might also translate the Chinese part but keep the English part in parentheses? The original had Chinese then English. So we might translate it to just English. So final: **Encapsulate Variable**.

Thus output: **Encapsulate Variable**.

Let's do that.
...done thinking.

**Encapsulate Variable**

![](img/0_refactor-15.png)

Thinking...
We need to translate the Markdown into English. The content: **动机**. That's a heading or bold: "Motivation". In Markdown, **word** is bold. The translation would be **Motivation**. Keep the Markdown structure. So output: **Motivation**. Ensure no changes.
...done thinking.

**Motivation**

Thinking...
We need to translate Chinese to English. Let's do it.

Original: "对于所有可变的数据，只要它的作用域超出单个函数，我就会将其封装起来，只允许通过函数访问。数据的作用域越大，封装就越重要。"

Translation: "For all mutable data, as long as its scope extends beyond a single function, I will encapsulate it, allowing access only through functions. The larger the data's scope, the more important encapsulation becomes."

We preserve Markdown structure. There's no markdown formatting beyond plain text. So we just provide the translated paragraph.

Thus output: 
For all mutable data, as long as its scope extends beyond a single function, I will encapsulate it, allowing access only through functions. The larger the data's scope, the more important encapsulation becomes.

Return ONLY translated Markdown.
...done thinking.

For all mutable data, as long as its scope extends beyond a single function, I will encapsulate it, allowing access only through functions. The larger the data’s scope, the more important encapsulation becomes.

Thinking...
We just need to translate the text into English. The only text is "**变量改名（Rename Variable）**". Should preserve markdown: bold. So "**Variable Rename (Rename Variable)**"? They want translate into English. The original Chinese inside parentheses is "Rename Variable". The phrase outside is "变量改名". The English translation: "Variable Renaming (Rename Variable)". Should keep markdown bold: **Variable Renaming (Rename Variable)**. That matches. Ensure no extra. Let's provide.
...done thinking.

**Variable Renaming (Rename Variable)**

![](img/0_refactor-9.png)

Thinking...
We need to translate the given Markdown into English. The content: "**动机**". This is bold Chinese: "Motivation". So translation: "**Motivation**". Keep same Markdown formatting. Return only translated Markdown. Let's do that.
...done thinking.

**Motivation**

Thinking...
We need to translate Chinese text into English. The Markdown: "解释一段程序在干什么，**对于作用域超出一次函数调用的字段，则需要更用心命名。**" We preserve formatting. So translate: "Explain what a piece of program is doing, **for fields whose scope extends beyond a single function call, you need to be more careful with naming.**" The first part: "解释一段程序在干什么" could be "Explain what a section of code is doing". The second part: "**对于作用域超出一次函数调用的字段，则需要更用心命名。**" could be "**For fields whose scope extends beyond a single function call, you need to name them more carefully.**" The original uses Chinese punctuation: "解释一段程序在干什么，**对于作用域超出一次函数调用的字段，则需要更用心命名。**". There is a comma before the bold. So the translation: "Explain what a section of code is doing, **for fields whose scope extends beyond a single function call, you need to name them more carefully.**" That's correct. No code blocks. So just output the translated Markdown.
...done thinking.

Explain what a section of code is doing, **for fields whose scope extends beyond a single function call, you need to name them more carefully.**

Thinking...
We need to translate the markdown text into English. There's a heading: **引入参数对象（Introduce Parameter Object）**. So we translate "Introduce Parameter Object" but also keep the original Chinese? The rule says to translate into English, preserve markdown structure. The heading is bold. The Chinese text inside parentheses is a translation. The Chinese text "引入参数对象" is the original title; "Introduce Parameter Object" is the English translation. But they want us to translate into English, so we should produce something like **Introduce Parameter Object (引入参数对象)**? Actually the current is "**引入参数对象（Introduce Parameter Object）**". That is Chinese first then parentheses with English. We need to translate the whole markdown into English. So we replace Chinese with English. So we would output "**Introduce Parameter Object**"? But maybe include parentheses? The rule: translate the following Markdown into English. So we can translate the text inside. That text includes Chinese characters and English inside parentheses. We should translate the Chinese into English, leaving the English translation maybe? But there is already English translation inside parentheses. Might keep it? But it's redundant. The instruction: preserve markdown structure and ordering. Do not alter URLs, etc. So we can transform the heading to "**Introduce Parameter Object**". The parentheses can be removed or maybe we keep the English translation? But it's already English. It might be originally Chinese title with English translation inside parentheses. We are asked to translate into English. So we might produce "**Introduce Parameter Object**". That seems correct.

Let's output that.
...done thinking.

**Introduce Parameter Object**

![](img/0_refactor-11.png)

Thinking...
We need to translate "动机" into English. The markdown just contains a heading in bold: **动机**. So translation: "**Motivation**". We preserve Markdown structure: it's bold text. So output: **Motivation**.
...done thinking.

**Motivation**

Thinking...
We need to translate the given Chinese markdown into English, preserving structure, no code. The text: "将数据组织成结构，使数据项之间的**关系更清晰**；". That means: "Organize data into structures to make the relationships between data items clearer;". Ensure preserve bold formatting (**). So produce: "Organize data into structures to make the **relationships between data items clearer**;" but maintain semicolon? The Chinese ends with a semicolon. We can keep semicolon at end. So final translation: "Organize data into structures to make the **relationships between data items clearer**;" . That's all.
...done thinking.

Organize data into structures to make the **relationships between data items clearer**;

Thinking...
We need to translate Chinese to English. The markdown: "**缩短参数列表**；". That's a heading? Actually bold. It's "缩短参数列表" meaning "Shorten parameter list". There's a Chinese semicolon at end "；". Should preserve. So translation: "**Shorten parameter list**；" Probably keep semicolon.

Also preserve markdown. So output:

**Shorten parameter list**；

Ensure no trailing spaces. So final.
...done thinking.

**Shorten parameter list**；

Thinking...
We need to translate to English. The text: "**代码一致性**：所有使用该数据结构的函数都可以通过相同的名字来访问其中元素。"

So "Code consistency: All functions that use this data structure can access its elements through the same name." The markdown: bold text "**Code Consistency**". Keep structure.

Thus output:

**Code Consistency**: All functions that use this data structure can access its elements through the same name.
...done thinking.

**Code Consistency**: All functions that use this data structure can access its elements through the same name.

Thinking...
The user wants translation to English. The markdown is:

"改变代码的概念图景，将这些数据结构提升为新的抽象概念"

We need to translate that. It means "Change the conceptual landscape of code, elevating these data structures to new abstract concepts." Let's produce that. It's a single line. We need to preserve markdown structure; it's a single line text, not a header. So just translate. Probably keep the same spacing. So final output:

"Change the conceptual landscape of code, elevating these data structures to new abstract concepts"

That is likely the translation. Ensure no code block. Just plain text.
...done thinking.

Change the conceptual landscape of code, elevating these data structures to new abstract concepts

Thinking...
We need to translate the given Markdown into English. The content is a heading. The original is "**函数组合成类（Combine Functions into Class）**". This is already partially English: Combine Functions into Class. The Chinese part "函数组合成类" translates to "Combining Functions into a Class" or "Function combination into class". The parentheses already provide the English. So maybe we translate the Chinese part into English while keeping the parentheses? But we need to preserve Markdown structure. The original is "**函数组合成类（Combine Functions into Class）**". The heading is bold text. Should we translate the Chinese part? Probably yes: "**Combining Functions into Class (Combine Functions into Class)**"? But the English phrase inside parentheses is already the translation. Usually we would replace Chinese with English and keep parentheses? But maybe the instruction says translate the following Markdown into English. So we need to translate entire thing. That means we should produce "**Combining Functions into Class (Combine Functions into Class)**". But that duplicates. Maybe we could just use the English translation: "**Combining Functions into Class**". But the parentheses likely are there to indicate translation; maybe we can just translate the Chinese part and keep the English part as is? But the instruction says translate into English. So we should produce just the English translation. So we could produce "**Combining Functions into Class (Combine Functions into Class)**" or "**Combining Functions into Class (Combine Functions into Class)**". Wait duplication? Let's think: The original Chinese plus English in parentheses. The English translation is already in parentheses. So we might just remove Chinese. That yields "**(Combine Functions into Class)**" but that seems odd. Usually one would keep heading "Combine Functions into Class". So maybe the best is to produce "**Combine Functions into Class**". But the requirement says "translate the following Markdown into English." So yes. Provide the translation: "**Combine Functions into Class**". We could keep parentheses? but it's redundant. The instruction: "Preserve Markdown structure and ordering. Do NOT translate code blocks ... Keep line breaks as much as possible." So only one line. So final answer: "**Combine Functions into Class**". That seems right.
...done thinking.

**Combine Functions into Class**

![](img/0_refactor-12.png)

Thinking...
We have a simple Markdown with Chinese title. Must translate to English. Must preserve structure. The content only: "**动机**". In English: "**Motivation**". Return only translated Markdown.
...done thinking.

**Motivation**

Thinking...
We need to translate the Chinese into English while preserving Markdown. The original is just a paragraph, no code blocks. We translate. Let's produce final.
...done thinking.

If you notice a set of functions that always operate on the same piece of data (typically passing that data as an argument to each function), it’s time to create a class. A class can provide a shared environment for these functions, allowing them to be invoked within an object with fewer arguments, thereby simplifying the function calls.

Thinking...
We need to translate the markdown. The title is Chinese: "函数组合成变换（Combine Functions into Transform）". It says we need to translate to English. Should preserve markdown: **...**. So translation: "**Combine Functions into a Transform**" or "**Combine Functions into Transform**"? The part in parentheses already gives translation. The original: "**函数组合成变换（Combine Functions into Transform）**". So likely translation: "**Combine Functions into Transform**". Or "Combine Functions into a Transform". In markdown we keep bold.

Also we might consider if parentheses remain: The original had both Chinese and translation. We need to translate to English. So remove Chinese part? The rule: "Translate the following Markdown into English." So the Chinese text should be replaced with English translation. The parentheses already contain English translation. So maybe we keep only that? The translation of the entire title could be "Combine Functions into Transform". The parentheses is the translation. We can simply output "**Combine Functions into Transform**".

Thus final answer: **Combine Functions into Transform**.
...done thinking.

**Combine Functions into Transform**

![](img/0_refactor-43.png)

Thinking...
We have a prompt: "You are a professional technical translator. Translate the following Markdown into English. Rules: ... Markdown: **动机**". So we translate "**动机**" into English. "动机" means "Motivation". So the translated markdown should be "**Motivation**". We must preserve markdown structure. So output: **Motivation**. Also keep line breaks. There is only one line. So final.
...done thinking.

**Motivation**

Thinking...
We need to translate the Markdown text into English while preserving structure and ordering. The text is in Chinese. There's no code block. So we translate. The Chinese says: "In software, it's often necessary to feed data to a program, so that it **computes various derived information**. These derived values might be used in several different places, so **the calculation logic often repeats where the derived data is used**. By consolidating all the logic that calculates derived data in one place, you can always find and update these logic in a fixed location, avoiding duplication across the code."

We need to keep the bold formatting. The original has Chinese characters and bold tags. We'll produce English.

Make sure we keep the Markdown bold syntax (** ... **). We should keep line breaks. There's only one paragraph? The original has line breaks? It seems it's a single paragraph but broken lines maybe. It is:

在软件中，经常需要把数据"喂"给一个程序，让它**再计算出各种派生信息**。这些派生数值可能会在几个不同地方用到，因此**这些计算逻辑也常会在用到派生数据的地方重复**。把所有计算派生数据的逻辑收拢到一处，这样始终可以在固定的地方找到和更新这些逻辑，避免到处重复。

So we will produce English:

"In software, it is often necessary to feed data to a program, so that it **computes various derived information**. These derived values may be used in several different places, so **the calculation logic often repeats wherever the derived data is used**. Consolidating all the logic that calculates derived data into a single place ensures that you can always find and update these logic at a fixed location, avoiding duplication everywhere."

Check the translation: "避免到处重复" -> "avoiding duplication everywhere" or "avoiding duplication across the code". I think "avoiding duplication everywhere" is fine.

Make sure we keep the bold. And we preserve line breaks: the paragraph breaks as original.

Thus produce:

In software, it is often necessary to feed data to a program, so that it **computes various derived information**. These derived values may be used in several different places, so **the calculation logic often repeats wherever the derived data is used**. Consolidating all the logic that calculates derived data into a single place ensures that you can always find and update this logic in a fixed location, avoiding duplication everywhere.

Yes.

Return only the translated Markdown.
...done thinking.

In software, it is often necessary to feed data to a program, so that it **computes various derived information**. These derived values may be used in several different places, so **the calculation logic often repeats wherever the derived data is used**. Consolidating all the logic that calculates derived data into a single place ensures that you can always find and update this logic in a fixed location, avoiding duplication everywhere.

Thinking...
We need to translate to English. The Markdown says "**函数组合成变换**与**函数组合成类**区别：". In English: "**Difference between composing functions into transformations** and **composing functions into classes**:" or "Difference between Function Composition as Transformation and Function Composition as Class". Let's keep bold formatting. So output: "**Difference between composing functions into transformations** and **composing functions into classes**:".

Make sure not to change anything else. Return only that line.
...done thinking.

**Difference between composing functions into transformations** and **composing functions into classes**:

Thinking...
We need to translate the Chinese Markdown into English. Preserve structure. The text is:

"如果代码中会对源数据做更新，那么使用类要好得多；如果使用变换，派生数据会被存储在新生成的记录中，一旦源数据被修改，我就会遭遇数据不一致。"

We need to translate. There's no code block. So output should be the translated line.

English: "If the code updates the source data, using classes is much better; if you use transformations, the derived data will be stored in newly created records, and once the source data is modified, I will encounter data inconsistency."

Check punctuation: Chinese uses semicolon and comma. We'll keep semicolon. So final:

"If the code updates the source data, using classes is far better; if you use transformations, the derived data will be stored in newly generated records, and once the source data is modified, I will run into data inconsistency."

Could use "far better" or "much better". We'll choose "much better". Or "far better". Both fine. Provide final.
...done thinking.

If the code updates the source data, using classes is much better; if you use transformations, the derived data will be stored in newly generated records, and once the source data is modified, I will run into data inconsistency.

Thinking...
We need to translate into English. Keep markdown. The text: "**拆分阶段（Split Phase）**". Likely title. Should translate: "**Split Phase**". Should we keep parentheses? The original has both Chinese and English. It says "拆分阶段（Split Phase）". We translate that into English. The markdown: "**拆分阶段（Split Phase）**". We need to preserve markdown structure. Should we translate the Chinese part to English while leaving the parentheses? According to instruction: Translate the Markdown into English. So the entire phrase should be in English. So "**Split Phase**". Keep bold. So final output: "**Split Phase**".
...done thinking.

**Split Phase**

![](img/0_refactor-13.png)

Thinking...
We need translate the markdown into English. The markdown content: "**动机**" means "**Motivation**". That's it. The output: just the markdown with English translation, preserve structure. So output "**Motivation**".
...done thinking.

**Motivation**

Thinking...
We need to translate into English. The Markdown is simple: paragraph with bold formatting. Must preserve structure. The translation: "A piece of code that **handles two different things at the same time** can consider splitting it into separate modules for each function, because then when modifications are needed, each topic can be handled separately." But we need to keep bold tags. The original: "一段代码在**同时处理两件不同的事**，可以考虑把它**拆分成各自独立的模块**，因为这样到了需要修改的时候，可以单独处理每个主题。"

Translate: "A piece of code that **handles two different tasks simultaneously** can consider splitting it into **separate independent modules**, because this way, when modifications are needed, each topic can be handled separately."

We preserve bold tags. Keep line breaks: the paragraph is a single line. Just translate. Return only the translated Markdown.
...done thinking.

A piece of code that **handles two different tasks simultaneously** can consider splitting it into **separate independent modules**, because this way, when modifications are needed, each topic can be handled separately.

Thinking...
We need translate the markdown. It's just "**例子**". That means "**Example**". Should keep Markdown structure. So output "**Example**".
...done thinking.

**Example**

Thinking...
We need to translate the markdown: "重构前：" into English. It's a heading? There's no heading marker. Just text "重构前：". We should keep markdown structure and ordering. This is just a line. Translate: "Before refactoring:" Probably. So output that. Ensure no extra. Return only translated Markdown. So just "Before refactoring:"
...done thinking.

Before refactoring:

![](img/0_refactor-44.png)

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: Preserve Markdown structure and ordering. Do NOT translate code blocks (```) or inline code in backticks. Do NOT alter URLs, links, or image paths. Keep line breaks as much as possible. Return ONLY translated Markdown."

Markdown: 
重构后：

That's Chinese: "After refactoring:" The output should be English: "After refactoring:".

Return only the translated Markdown.

Thus output:

After refactoring:

Probably just that. Ensure no extra whitespace.
...done thinking.

After refactoring:

Thinking...
We need to translate the provided Markdown into English, preserving structure. The text is:

"提炼函数、引入中转数据结构："

We need to translate that phrase. It is in Chinese: "提炼函数、引入中转数据结构：". That means "Refine functions, introduce intermediary data structures:" or "Extract functions, introduce intermediate data structures:".

Since it's a heading or a bullet maybe. There's no explicit markdown structure except the colon. So the translation: "Refine functions, introduce intermediary data structures:".

Return only the translated markdown. Probably just that line. Ensure no code blocks, no changes.

So final answer:

"Refine functions, introduce intermediary data structures:"
...done thinking.

Refine functions, introduce intermediary data structures:

![](/img/0_refactor-45.png)

Thinking...
We need to translate the Markdown into English, preserving structure. The text is "**第七章 封装**". In English: "**Chapter Seven: Encapsulation**" or "Chapter 7 Encapsulation". We need to preserve formatting: ** ... **.

So output: **Chapter Seven: Encapsulation**. Probably that. Ensure not adding new lines. It's just one line. No code blocks. So final answer is that.
...done thinking.

**Chapter Seven: Encapsulation**

Thinking...
We need to translate given Markdown into English. It's just one line with bold text: **封装记录（Encapsulate Record）**. Should translate to **Encapsulate Record** maybe keep parentheses? The original includes both Chinese and English. The instruction: translate the following Markdown into English. So we translate the Chinese part into English. The bold text currently: "**封装记录（Encapsulate Record）**". Already has English inside parentheses. Probably we keep the English inside parentheses but replace Chinese with English? Might produce: **Encapsulate Record (Encapsulate Record)**? That duplicates. But maybe just translate to "**Encapsulate Record**"? But parentheses likely indicate note. The original Chinese "封装记录" means "Encapsulate Record". The parentheses contain the translation. So maybe we keep that same. But the instruction: translate into English. We could replace Chinese with English and keep translation: **Encapsulate Record (Encapsulate Record)**? That seems redundant. But maybe we could remove Chinese part, leaving only the English inside parentheses. But the parentheses is translation; maybe we don't need parentheses? I'd do "**Encapsulate Record**". That preserves structure.

Thus output: **Encapsulate Record**.
...done thinking.

**Encapsulate Record**

![](/img/0_refactor-14.png)

Thinking...
We need to translate into English. The content: "**动机**" which is bold "Motivation". Should preserve Markdown. So output: "**Motivation**". That's all.
...done thinking.

**Motivation**

Thinking...
We need translate to English. The Markdown is just a sentence: "对象可以隐藏结构的细节，有助于字段的改名，方便拓展以应对变化。" Means "Objects can hide the details of the structure, which helps with renaming fields, and facilitates extension to cope with changes." Return only translated markdown. Let's output: "Objects can hide the details of the structure, helping with field renaming and making it easier to extend to handle changes." Ensure no code blocks. Let's produce.
...done thinking.

Objects can hide the details of the structure, helping with field renaming and making it easier to extend to handle changes.

Thinking...
The original Markdown: **封装集合（Encapsulate Collection）**

We need to translate to English. The translation likely: **Encapsulate Collection**? The part in parentheses already says Encapsulate Collection. But we might translate the Chinese part to English, while preserving the English inside parentheses? The rule: preserve Markdown structure. We can translate the Chinese to English, but keep the English in parentheses. So **Encapsulate Collection (Encapsulate Collection)**? That seems redundant. Maybe they want just "Encapsulate Collection" with English only, but we should translate the Chinese portion. The Chinese part is the title. The English part is already a translation. Might want: **Encapsulate Collection**.

But the instruction: translate the following Markdown into English. So the Chinese text "封装集合" should be translated. The parentheses contain "Encapsulate Collection" which is already translation. So we might keep it as is. So output: **Encapsulate Collection (Encapsulate Collection)**? That seems odd. I'd output: **Encapsulate Collection (Encapsulate Collection)** but that duplicates. Maybe better to translate the Chinese and remove duplicate: **Encapsulate Collection**. The parentheses maybe optional. I'd produce: **Encapsulate Collection**. I think that's the best.

Return only translated Markdown.
...done thinking.

**Encapsulate Collection**

![](/img/0_refactor-16.png)

Thinking...
We need to translate to English. "动机" means "Motivation". So the heading is bold. Output should be "**Motivation**". Keep Markdown.
...done thinking.

**Motivation**

Thinking...
We need to translate the given Markdown into English, preserve structure. The Markdown is just a paragraph:

"封装集合时人们常常犯一个错误：只对集合变量的访问进行了封装，但依然让取值函数返回集合本身。这使得集合的成员变量可以直接被修改，而封装它的类则全然不知，无法介入。"

We translate to English:

"When encapsulating collections, people often make a mistake: they only encapsulate access to the collection variable, but still let the getter return the collection itself. This allows the collection's member variables to be modified directly, while the class that encapsulates it remains unaware and cannot intervene."

We need to keep Markdown. It's just a paragraph. So output that paragraph.

Check for line breaks: original has no line breaks inside, just a single paragraph.

Return only translated Markdown.
...done thinking.

When encapsulating collections, people often make a mistake: they only encapsulate access to the collection variable, but still let the getter return the collection itself. This allows the collection's member variables to be modified directly, while the class that encapsulates it remains unaware and cannot intervene.

Thinking...
The input: "Markdown: 做法：" Means Chinese text: "做法：" means "Method:" or "Procedure:".

We need to translate to English. Preserve Markdown structure. There's a heading? It just says "做法：" followed by maybe no further content? The instruction: Return only translated Markdown. So output should be "Method:" or "Procedure:"? "做法：" is like "Method:".

Better to translate as "Method:".

Thus output: "Method:".

Also preserve that it's a heading? Actually no markdown heading symbol (#). The original text "做法：" is just text. So translation "Method:".

So output: "Method:".

Return only translated Markdown. No extra commentary.
...done thinking.

Method:

Thinking...
We need to translate into English: "在类上提供一些修改集合的方法------通常是"添加"和"移除"方法。"

We need to preserve Markdown. It's a paragraph. So output in English: "Provide some methods for modifying a collection on the class — usually 'add' and 'remove' methods."

But need to keep structure. There's no code. So just translate.

Also preserve dashes? In original: "在类上提供一些修改集合的方法------通常是"添加"和"移除"方法。"

The dashes: "------" maybe just a separator. Should we keep same? Keep it as is? They want preserve structure. So we keep "------". Replace Chinese text.

Thus: "Provide some methods for modifying a collection on the class ------ usually 'add' and 'remove' methods."

Let's preserve punctuation. Use single quotes for English terms. Provide in same line.

Also preserve trailing period? In original: "方法。" Chinese period. In English, maybe a period. So "methods.".

Thus final output.
...done thinking.

Provide some methods for modifying a collection on the class ------ usually 'add' and 'remove' methods.

Thinking...
The user is asking: "You are a professional technical translator. Translate the following Markdown into English. Rules: ...". The Markdown to translate is:

**以对象取代基本类型（Replace Primitive with Object）**

So the translation: **Replace Primitive Types with Objects (Replace Primitive with Object)**. But keep structure: bold. So output: **Replace Primitive with Object**? Wait, the original is "**以对象取代基本类型（Replace Primitive with Object）**". It's bold and includes Chinese and English inside parentheses. We need to translate the Chinese portion to English. But maybe keep the parentheses? The English inside parentheses is already "Replace Primitive with Object". So we can translate the Chinese to "Replace Primitive with Object (Replace Primitive with Object)". But that duplicates. Perhaps we translate just Chinese part: "Replace Primitive with Object" and keep the English inside parentheses? That would be redundant. Probably we keep both: The original has both Chinese and English, but we translate the Chinese to English, and keep the parentheses content. But that yields duplication.

Maybe they want the translation: "**Replace Primitive Types with Objects (Replace Primitive with Object)**". The English inside parentheses is the original English translation of the Chinese phrase. But we are translating the entire markdown, so we may keep the English inside parentheses or remove? The instruction says: "Translate the following Markdown into English." So we want the final output to be in English. The original already has English inside parentheses. The Chinese part "以对象取代基本类型" is the Chinese title. We translate to English, maybe "Replace Primitive Types with Objects". Then we can keep the parenthetical English as maybe a translation note? The original had both Chinese and English; we need to produce a pure English title. So we can output "**Replace Primitive with Object**" or "Replace Primitive Types with Objects". The English inside parentheses may be removed. But instruction says preserve Markdown structure and ordering. So we need a bold line. So output: **Replace Primitive with Object**.

But the original had parentheses containing "Replace Primitive with Object". That might be a translation note. The translation might be the same phrase. If we keep it, we would duplicate. Maybe better: "**Replace Primitive with Object**". So that's our output.

Thus produce: **Replace Primitive with Object**.
...done thinking.

**Replace Primitive with Object**

![](/img/0_refactor-46.png)

Thinking...
The user asks to translate Markdown into English. The input markdown is:

**以查询取代临时变量（Replace Temp with Query）**

Need to preserve structure. The bold formatting remains, but translate the Chinese into English. The parentheses contain the English phrase, so keep it.

Thus output: **Replace Temp with Query** (maybe keep the Chinese? But translation: "Replace Temp with Query" is the English part. The Chinese is description, so translation would be "**Replace Temp with Query**". But we need to preserve structure and ordering. The original had both Chinese and English inside. We can translate Chinese part. So output: **Replace Temp with Query**. Should we keep parentheses? Already inside the bold. So just output that. Probably no other text.

Thus final answer: **Replace Temp with Query**.
...done thinking.

**Replace Temp with Query**

![](/img/0_refactor-47.png)

Thinking...
We need translate. Title: 提炼类 (Extract Class). So "**Extract Class**". Keep bold. So output: **Extract Class**.
...done thinking.

**Extract Class**

![](/img/0_refactor-48.png)

Thinking...
We need to translate the markdown into English. The original is Chinese: "**动机**". That's a heading or bold text: "**动机**" meaning "**Motivation**". Keep the markdown, so "**Motivation**". So output: **Motivation**. Probably that's all.
...done thinking.

**Motivation**

Thinking...
We need to translate to English: "If certain data and certain functions always appear together, certain data frequently change at the same time or even depend on each other, this indicates that you should separate them out." Also preserve Markdown structure: The given text is a paragraph, not a list. So just translate into English, keep line breaks. The original had a line break? The text is just one paragraph. Provide translated markdown.
...done thinking.

If certain data and certain functions always appear together, if certain data frequently change simultaneously or even depend on each other, this indicates that you should separate them out.

Thinking...
We need translate to English. The markdown is a single paragraph. Should preserve structure. So output: "If you find that subclassing only affects certain aspects of the class, or if you find that some features require one way of subclassing while others require a different way, this means you need to decompose the original class." Maybe maintain Chinese? The instruction: translate the following Markdown into English. So output the translated paragraph. Also preserve Markdown structure; it's just a paragraph, no code. So final.
...done thinking.

If you discover that subclassing only affects certain aspects of a class, or if you find that some features require one way to subclass while others require a different approach, this means you need to decompose the original class.

Thinking...
We need translate to English. The heading **Inline Class**. Ensure keep markdown. Return only that.
...done thinking.

**Inline Class**

![](/img/0_refactor-49.png)

Thinking...
We need to translate Chinese to English. Title: **隐藏委托关系（Hide Delegate）**. Probably "**Hide Delegate Relationship**"? But translation should be consistent with provided parentheses? The parentheses contain "Hide Delegate" presumably the English name. The phrase before parentheses is Chinese: 隐藏委托关系. That could be "Hide Delegate Relationship". Should we translate to "**Hide Delegate**"? Actually original: **隐藏委托关系（Hide Delegate）**. Might be that the English name is "Hide Delegate". So translation would be "**Hide Delegate**". Or preserve parentheses? They said preserve Markdown structure. The parentheses part is presumably not to be translated. But we should translate the Chinese part? They didn't specify to translate the parentheses. They say translate the following Markdown into English. So we need to translate the whole content. The parentheses part is already English. So we just translate the Chinese part. So output: **Hide Delegate**. But need parentheses maybe? The original had both Chinese and English inside parentheses. We can keep parentheses but the English inside remains same. So new: **Hide Delegate**. Should we keep parentheses? The instruction: "translate the following Markdown into English." So entire content should be English. So we replace Chinese with its English translation. But parentheses part may be redundant. But if we translate entire line, we could produce "**Hide Delegate**" or "**Hide Delegate (Hide Delegate)**" which is odd. Better to just produce "**Hide Delegate**". But to be safe, keep parentheses maybe: "**Hide Delegate (Hide Delegate)**" but that duplicates. I'd output "**Hide Delegate**". No code blocks to preserve. So final.
...done thinking.

**Hide Delegate**

![](/img/0_refactor-50.png)

Thinking...
We just translate "移除中间人（Remove Middle Man）" into English. But the Chinese part says "移除中间人（Remove Middle Man）". They want to translate entire Markdown into English. The only content is the header? It's a heading? It begins with **, which is bold. So translation: "**Remove Middle Man (Remove Middle Man)**"? Wait original includes "Remove Middle Man" in parentheses. It's Chinese title with English translation inside parentheses. The instruction: translate into English, but we cannot translate code blocks. There's no code. So we translate Chinese part to English. But original had Chinese and English: "移除中间人（Remove Middle Man）". If we translate fully to English, we might produce "**Remove Middle Man (Remove Middle Man)**" which duplicates. Maybe the intention is to keep the English translation part unchanged, but we could just remove Chinese. The rule: "Translate the following Markdown into English." So we replace Chinese text with English equivalent. So "**Remove Middle Man (Remove Middle Man)**" seems redundant but could be accepted. Maybe we should just output "**Remove Middle Man**"? But keep parentheses? The original has English inside parentheses, maybe it's part of title. They might want to keep the translation inside parentheses. But if we translate Chinese, we might remove it and keep only the English inside parentheses? However the translation says "Remove Middle Man (Remove Middle Man)" which is weird.

Better: "**Remove Middle Man**" (English only). But that removes parentheses.

But the instruction: preserve Markdown structure and ordering. No instruction to remove parentheses. But we can adjust content. Possibly they'd accept "**Remove Middle Man (Remove Middle Man)**" but it's redundant.

Let's think: The original "移除中间人（Remove Middle Man）". It's a title with Chinese and English. Translating to English: "**Remove Middle Man**". The English version inside parentheses is just a translation. So when translating entire text to English, we don't need both. So we can output "**Remove Middle Man**".

Thus final answer: **Remove Middle Man**.
...done thinking.

**Remove Middle Man**

![](/img/0_refactor-51.png)

Thinking...
We need to translate the provided Markdown into English. The markdown is just a quoted string: "合适的隐藏程度"。 That is Chinese. It means "Suitable level of hiding" or "Appropriate degree of concealment". Likely the phrase "合适的隐藏程度" is the translation of some phrase "appropriate level of hiding". It might be context for UI options like "Hidden depth". The translation is "Appropriate level of concealment" maybe.

We need to preserve Markdown structure: the original markdown is a quoted string: "合适的隐藏程度"。 There's an opening quote and closing Chinese punctuation. In English, we need to translate within quotes. So it would be "Appropriate level of hiding" or "Suitable level of hiding". But what is the correct? I'd choose "Appropriate level of hiding". Let's output that.

Also ensure we keep line breaks. There's just one line. So output exactly:

"Appropriate level of hiding".

Make sure to keep the closing punctuation maybe a period. In Chinese it ends with a Chinese full stop. In English we might keep it as a period. But we need to preserve structure: It's a quoted string. So output: "Appropriate level of hiding". That matches. Let's deliver.
...done thinking.

"Appropriate level of hiding"

Thinking...
The task: Translate the given Markdown into English. The Markdown is:

**替换算法（Substitute Algorithm）**

The rule: preserve Markdown structure and ordering. Only translation.

So we need to output:

**Substitute Algorithm (Substitute Algorithm)**? Wait the Chinese: 替换算法 (Substitute Algorithm). The parentheses contain the translation maybe? The original: 替换算法（Substitute Algorithm）. So translation: **Substitute Algorithm (Substitute Algorithm)** but we need to keep parentheses maybe? The translation might be: **Substitute Algorithm (Substitute Algorithm)** but that is redundant. Perhaps the translation should be: **Substitute Algorithm (Substitute Algorithm)**? But better: **Substitute Algorithm (Substitute Algorithm)**. But we might translate the Chinese portion only: **Substitute Algorithm (Substitute Algorithm)**? Actually we could translate the Chinese into English and keep the English inside parentheses. That might be: **Substitute Algorithm (Substitute Algorithm)**. It's basically same.

But maybe we should translate the Chinese phrase only: 替换算法 = "Substitute Algorithm" or "Replacement Algorithm". The parentheses contain English translation: (Substitute Algorithm). So the Markdown after translation: **Substitute Algorithm (Substitute Algorithm)**. That seems odd but following rule: we should translate. So we keep the parentheses. So final output: **Substitute Algorithm (Substitute Algorithm)**

However we could also translate into: **Substitute Algorithm (Substitute Algorithm)**. That's okay.

Return only translated Markdown.
...done thinking.

**Substitute Algorithm (Substitute Algorithm)**

![](/img/0_refactor-17.png)

Thinking...
We just need to translate the markdown: "**第8章　搬移特性**" into English. That is "**Chapter 8 Migration Characteristics**" or "Chapter 8 Transfer Characteristics" (搬移特性 is usually "Transfer characteristics" in electronics context). So we preserve bold. Return "**Chapter 8 Transfer Characteristics**" .
...done thinking.

**Chapter 8 Transfer Characteristics**

Thinking...
We need to translate the Chinese markdown. The text: "另一种类型的重构也很重要，那就是**在不同的上下文之间搬移元素**。"

Translate to English: "Another type of refactoring is also important, namely **moving elements between different contexts**." Keep markdown. The double asterisks for bold. Also preserve punctuation. Should include the Chinese text replaced by English. Also keep line breaks.

The markdown is just a paragraph. So output:

Another type of refactoring is also important, namely **moving elements between different contexts**.

Check line breaks: The original had a newline after? It shows the paragraph only. We'll output same.

...done thinking.

Another type of refactoring is also important, namely **moving elements between different contexts**.

Thinking...
The user: "You are a professional technical translator. Translate the following Markdown into English. Rules: preserve markdown structure and ordering. Do not translate code blocks or inline code. Do not alter URLs, links, or image paths. Keep line breaks. Return only translated Markdown."

The Markdown given:

**搬移函数（Move Function）**

We need translate into English. Bold text. "搬移函数" means "Move Function" and there is a parenthetical Chinese "Move Function". It seems the original is "搬移函数（Move Function）". So we translate into English: "**Move Function**". The Chinese part removed, we just keep English? Possibly they want to translate the whole phrase, so the English would be "**Move Function**". Or maybe they want to keep the Chinese and translate the English part? The original has both Chinese and English inside parentheses. The instruction says "translate the following Markdown into English." So translate everything. So the Chinese part removed. So final: "**Move Function**". And preserve formatting. So output: **Move Function**.

Let's produce that.
...done thinking.

**Move Function**

![](/img/0_refactor-18.png)

Thinking...
We need to translate the Chinese markdown into English, preserving structure, no changes to code blocks (none present), no altering URLs etc. The text: "**任何函数都需要具备上下文环境才能存活**。". In English: "**Any function needs a context environment to survive**." or "**Any function must have a contextual environment to survive**." The period in Chinese after the punctuation is a Chinese full stop. In English, we can keep the period after the English sentence. The text is inside bold. So translation: **Any function must have a contextual environment to survive**. Or "Any function needs a contextual environment to survive." Let's decide: "Any function needs a contextual environment to survive." Add period at end. Provide only translated Markdown. No extraneous commentary.

Thus answer: **Any function needs a contextual environment to survive**. Ensure the period at end.
...done thinking.

**Any function needs a contextual environment to survive**.

Thinking...
We need translate into English. Provide markdown. Preserve structure. The paragraph is a sentence. Let's translate: "搬移函数最直接的一个动因是，它频繁引用其他上下文中的元素，而对自身上下文中的元素却关心甚少，将函数移动到联系更紧密的上下文那么系统别处就可以减少对当前模块的依赖，**获得更好的封装效果。**"

English: "One of the most direct motivations for moving a function is that it frequently references elements from other contexts while paying little attention to elements within its own context. Moving the function to a more tightly connected context allows other parts of the system to reduce their dependency on the current module, thereby achieving better encapsulation."

We need preserve Markdown structure. This is a single paragraph. Use bold for "**获得更好的封装效果。**" -> "**achieve better encapsulation.**" Or "**obtain better encapsulation.**"

Let's produce.

...done thinking.

One of the most direct motivations for moving a function is that it frequently references elements from other contexts while paying little attention to elements within its own context. Moving the function to a more tightly connected context allows other parts of the system to reduce their dependency on the current module, thereby **achieving better encapsulation.**

Thinking...
We need to translate the given markdown (in Chinese) into English. The markdown only has one paragraph (no code). So translation: "While organizing code, I found that I need to frequently call a function from elsewhere; or a function defines a helper function inside, and that helper may be useful elsewhere, so you can move it to a more general place."

Make sure we preserve markdown structure (there is just a paragraph). No code. So output the translated paragraph. Should we maintain line breaks? The original has one paragraph: "整理代码时，发现需要频繁调用一个别处的函数；或者函数内部定义了一个帮助函数，而该帮助函数可能在别的地方也有用处，此时就可以将它搬移到某些更通用的地方。"

We can produce: "When organizing code, I found that I need to frequently call a function from elsewhere; or a function defines a helper function internally, which might be useful elsewhere. In such cases, you can move it to a more general location."

Return only the translated markdown. No extra commentary.
...done thinking.

When organizing code, I found that I need to frequently call a function from elsewhere; or a function defines a helper function internally, and that helper may be useful elsewhere. In such cases, you can move it to a more general location.

Thinking...
We have to translate the given Markdown text into English. The original is Chinese: "**是否需要搬移函数常常不易抉择，但决定越难做，通常说明"搬移这个函数与否"的...". Let me translate accurately.

Original: **是否需要搬移函数常常不易抉择，但决定越难做，通常说明"搬移这个函数与否"的重要性也越低。**

English translation: **Whether a function needs to be moved is often difficult to decide, but the harder the decision, the more it usually indicates that the importance of moving the function is lower.**

We must preserve the Markdown: bold markup. So we output:

**Whether a function needs to be moved is often difficult to decide, but the harder the decision, the more it usually indicates that the importance of moving the function is lower.**

Return only the translated Markdown. Let's ensure the line break: The original had a line break after the sentence? It's a single line. We'll keep as one line.

Thus output exactly that line.
...done thinking.

**Whether a function needs to be moved is often difficult to decide, but the harder the decision, the more it usually indicates that the importance of moving the function is lower.**

Thinking...
We need to translate the given markdown into English. The original is Chinese: "**范例：搬移内嵌函数至顶层**". This translates to "**Example: Moving nested function to top-level**" or "**Example: Promote nested function to top-level**". We need to preserve markdown. So output: "**Example: Moving nested function to top level**" or maybe "Example: Moving nested function to the top level". Use proper English. Keep the bold tags. So final markdown: **Example: Moving nested function to top-level**. Use same dash? The original had Chinese colon. In English: "Example: Moving nested functions to top level". But singular? The original: "搬移内嵌函数至顶层". So singular. I'd choose "Example: Moving a nested function to the top level". But we want to keep formatting minimal. I'd go with "Example: Moving nested function to top-level". That preserves hyphen. So final.
...done thinking.

**Example: Moving nested function to top-level**

before：

![](/img/0_refactor-19.png)

after：

![](/img/0_refactor-20.png)

Thinking...
We need to translate. The text: "**范例：在类之间搬移函数**" into English. So likely "**Example: Moving functions between classes**" but keep Markdown structure. The heading is a bold text, not a heading. So just translate the bold string. So output: "**Example: Moving functions between classes**".
...done thinking.

**Example: Moving functions between classes**

before：

![](/img/0_refactor-52.png)

after：

![](/img/0_refactor-53.png)

Thinking...
We need to translate the markdown to English. The heading: "**搬移字段（Move Field）**" probably means "**Move Field**". The Chinese "搬移字段" is "Move Field". The parentheses include the English translation. We should preserve markdown, so output "**Move Field**".
...done thinking.

**Move Field**

![](/img/0_refactor-54.png)

Thinking...
We need to translate the given markdown into English, following the rules.

The markdown contains only "**范例**". In English that's "**Example**".

Need to preserve markdown structure. So the output should be:

**Example**

Yes.
...done thinking.

**Example**

before：

![](/img/0_refactor-55.png)

after：

![](/img/0_refactor-56.png)

![](/img/0_refactor-57.png)

Thinking...
We just translate "范例：搬移字段到共享对象" to English. It's in bold. So output: **Example: Moving Fields to Shared Object** or "Example: Moving Fields to a Shared Object". We should preserve markdown. Keep bold formatting. So output "**Example: Moving Fields to a Shared Object**".
...done thinking.

**Example: Moving Fields to a Shared Object**

before：

![](/img/0_refactor-58.png)

after：

![](/img/0_refactor-59.png)

![](/img/0_refactor-60.png)

Thinking...
We just need to translate the heading. The text is "**搬移语句到函数（Move Statements into Function）**". The translation: "**Move Statements into Function**". The part in parentheses already includes English. In Chinese part: "搬移语句到函数". So translation should be "**Move Statements into Function**". Ensure we preserve Markdown structure and ordering. Just that line. Return only translated Markdown. So answer: **Move Statements into Function**.
...done thinking.

**Move Statements into Function**

![](/img/0_refactor-21.png)

Thinking...
The input: 

Markdown: **"消除重复"**：如果发现调用某个函数时，总有一些相同的代码也需要每次执行，则考虑将此段代码合并到函数里头。

We need to translate to English, preserve Markdown structure. The bold text is "**" around Chinese text. So we translate **"消除重复"** to **"Eliminate Redundancy"** perhaps. The colon after: Chinese punctuation. Keep colon? We'll keep punctuation as is? Probably use colon. So:

**"Eliminate Redundancy"**: If you find that when calling a function, there is some code that needs to be executed each time, consider merging that code into the function itself.

We must preserve line breaks: it's a single line. Let's output:

**"Eliminate Redundancy"**: If you find that when calling a function, there is some code that needs to be executed each time, consider merging that code into the function.

Check: we should keep the colon punctuation. Use same punctuation? There's a colon after Chinese quote. We'll use colon. Should we keep the Chinese punctuation after translation? Use English colon. Yes.

So final output: only translated Markdown.
...done thinking.

**"Eliminate Redundancy"**: If you find that when calling a function, there is some code that needs to be executed each time, consider merging that code into the function.

Thinking...
We need to translate the Markdown into English. The Markdown includes Chinese text: "如果某些语句与一个函数放在一起更像一个整体，并且更**有助于理解**，则将语句搬移到函数里去。如果它们与函数不像一个整体，但仍应与函数一起执行，可以用提炼函数将语句和函数一并提炼出去。"

We preserve Markdown structure. There are no code blocks or inline code. Just plain text with bold formatting (**有助于理解**). That should be translated. The bold remains as **...**.

We need to keep line breaks as much as possible. There is just one paragraph. Should we preserve line breaks? There's no explicit line breaks. The text is one paragraph. So output that paragraph in English with same formatting. "If some statements together with a function look more like a whole and are more **helpful to understand**, then move the statements into the function. If they are not like a whole with the function but still should be executed together with the function, you can extract the statements and the function together using a 'refactor function'." The Chinese phrase "提炼函数" means "extract function" or "refactor function". "提炼" means "refine" but in programming context "提炼函数" is "extract function" refactoring. So "use extract function to extract the statements and the function together."

We can translate "提炼函数" as "Extract Function" refactoring. Let's produce:

"If some statements together with a function look more like a whole and are more **helpful to understand**, then move the statements into the function. If they do not form a whole with the function but still should be executed together with the function, you can use an Extract Function refactoring to extract both the statements and the function."

We should preserve the original bold: **有助于理解** => **helpful to understand**. Keep bold.

We need to keep Markdown. There's no formatting beyond bold. The original had bold inside the Chinese: **有助于理解**. So we should produce: **helpful to understand**.

Thus final translation:

"If some statements together with a function look more like a whole and are more **helpful to understand**, then move the statements into the function. If they are not like a whole with the function but still should be executed together with the function, you can use an Extract Function refactoring to extract both the statements and the function."

We need to preserve line breaks as much as possible. The original had two sentences separated by a period. So we produce same. Probably all in one paragraph.

Thus output.
...done thinking.

If some statements together with a function look more like a whole and are more **helpful to understand**, then move the statements into the function. If they are not like a whole with the function but still should be executed together with the function, you can use an Extract Function refactoring to extract both the statements and the function.

Thinking...
We need to translate the markdown into English. The markdown is:

**范例**

So just a bold text "范例" which means "Example" or "Sample". In English, we translate to **Example**. Ensure markdown preserved. Return only translated markdown. So output:

**Example**

Yes.
...done thinking.

**Example**

before：

![](/img/0_refactor-61.png)

after：

![](/img/0_refactor-62.png)

Thinking...
The user wants translation into English. It's a single line Markdown: "**搬移语句到调用者（Move Statements to Callers）**". We need to translate into English while preserving Markdown. Likely "Move Statements to Callers". The Chinese part "搬移语句到调用者" is the same as the English in parentheses. So translate that entire line. Should we translate the Chinese to English? Probably yes: "**Move Statements to Callers (Move Statements to Callers)**" or just "**Move Statements to Callers**". But the instruction says "translate the following Markdown into English". That likely means convert the entire Markdown into English, not just the English part. So the output should be "**Move Statements to Callers (Move Statements to Callers)**". But that duplicates. Usually we just translate Chinese to English. So "**Move Statements to Callers**". The parentheses may be removed. But we need to preserve structure: it's bold. So output: "**Move Statements to Callers**". That's it.
...done thinking.

**Move Statements to Callers**

![](/img/0_refactor-63.png)

Thinking...
We need to translate to English, preserve structure. The text is:

"随着系统能力发生演进，原先设定的抽象边界总会悄无声息地发生偏移。对于函数来说，这样的边界偏移意味着曾经视为一个整体、一个单元的行为，如今可能已经分化出两个甚至是多个不同的关注点。"

We translate: "As system capabilities evolve, the originally set abstract boundaries will inevitably shift silently. For a function, such a boundary shift means that behavior once considered a single whole, a single unit, may now have split into two or even multiple distinct concerns."

We must keep Markdown structure: There are no headings or lists. Just paragraphs. So output that translation.
...done thinking.

As system capabilities evolve, the abstract boundaries originally set will inevitably shift silently. For a function, such a boundary shift means that behavior once regarded as a single whole, a single unit, may now have split into two—or even multiple—distinct concerns.

Thinking...
We need to translate the given Markdown into English. The Markdown contains "**范例**" which is Chinese for "Example" or "Sample". Should translate to "**Example**". Keep bold formatting. The rest of the Markdown: It's a section header maybe? It says "**范例**" which is just bold. There are no code blocks. So we output "**Example**".

Ensure we don't add any extra text. Return only translated Markdown. The line breaks: There's only one line.

Thus output: **Example**.
...done thinking.

**Example**

before：

![](/img/0_refactor-64.png)

after：

![](/img/0_refactor-65.png)

Thinking...
We need to translate the given Markdown into English. The content: "**以函数调用取代内联代码（Replace Inline Code with Function Call）**". It contains Chinese text and English parentheses. The instructions: preserve markdown structure, don't translate code blocks or inline code. There is no code block. Just translate the Chinese phrase. The phrase is "以函数调用取代内联代码" meaning "Replace inline code with function call". But we also have parentheses containing "Replace Inline Code with Function Call". Should we keep that? The instructions say preserve structure, but we are to translate the whole markdown. The given includes parentheses with English text. The Chinese part is inside bold markup: **以函数调用取代内联代码（Replace Inline Code with Function Call）**. The parentheses contain an English phrase. The question: we translate the whole markdown. If we translate Chinese, we might remove the English parentheses? But maybe keep the English phrase because it's already English. The instruction: "Translate the following Markdown into English." The English part is already English. So we translate the Chinese portion to English, while preserving the parentheses. So the output should be "**Replace Inline Code with Function Call**" maybe including parentheses? Wait, the parentheses contain the English phrase. But we want the entire text to be English. So maybe we output "**Replace Inline Code with Function Call**". The parentheses are redundant. So we might drop the parentheses. The instruction says preserve structure and ordering. The bold markup is part of structure. So we keep the bold markup. So output: "**Replace Inline Code with Function Call**". That is correct.
...done thinking.

**Replace Inline Code with Function Call**

![](/img/0_refactor-66.png)

Thinking...
We need to translate Chinese to English. The text: "**移动语句（Slide Statements）**" likely means "**Slide Statements**" with translation. The Chinese inside parentheses: "移动语句" meaning "Slide Statements" or "move statement". So we produce "**Slide Statements**". But must preserve markdown. So just output that line.

The original has "**移动语句（Slide Statements）**". The parentheses contain both Chinese and English. We should keep that? The instruction: translate the following Markdown into English. So we should translate the whole. If we keep the English inside parentheses? Might be optional. But likely we translate "移动语句" to "Slide Statements" and preserve the English "Slide Statements" inside parentheses? That seems duplicate. But maybe keep as is: "**Slide Statements**". But maybe they want to keep the parentheses but inside only English? It says translate into English, so we would remove Chinese. So we output "**Slide Statements**". That is best.

We need to keep the structure. So final answer: **Slide Statements**.
...done thinking.

**Slide Statements**

![](/img/0_refactor-67.png)

Thinking...
We need to translate the given Markdown into English, preserving structure. The content is: "让存在关联的东西一起出现，可以使代码更容易理解。"

That means: "Let related items appear together, which can make code easier to understand."

We need to keep the Markdown; there is no markup aside from the text, maybe a paragraph. The translation: "Making related items appear together can make the code easier to understand." Or "Having related things appear together can make code easier to understand." Or "Let related elements appear together to make the code easier to understand."

We should preserve structure: it's a paragraph. Just output the translated paragraph.

Thus final answer:

"Let related items appear together, which can make code easier to understand."

We might choose: "Having related items appear together can make code easier to understand."

Pick one. I'll produce:

"Having related items appear together can make code easier to understand."

Return only the translated Markdown.
...done thinking.

Having related items appear together can make code easier to understand.

Thinking...
We need translate. Title: "**命令查询分离原则**（Command-Query Separation,CQS原则）：" to English: "**Command-Query Separation Principle** (Command-Query Separation, CQS Principle):". Provide translation. Keep markdown.
...done thinking.

**Command-Query Separation Principle** (Command-Query Separation, CQS Principle):

Thinking...
We need to translate the Markdown content from presumably Chinese to English. The content: "**查询：**方法返回结果，但不改变任何系统状态(无副作用)。"

So translate: "**Query:** method returns a result but does not change any system state (no side effects)."

We must preserve Markdown structure and ordering. So keep the bold and colon. In original: **查询：**. So we will translate that to **Query:**. And the rest: 方法返回结果，但不改变任何系统状态(无副作用)。 So: "The method returns a result, but does not alter any system state (no side effects)."

Thus produce: **Query:** The method returns a result, but does not alter any system state (no side effects). Ensure no extra formatting changes. Also preserve the line break? There's just one line.

Thus final answer.
...done thinking.

**Query:** The method returns a result, but does not alter any system state (no side effects).

Thinking...
We have a short piece: "**命令：**方法没有结果，但会改变系统状态。"

We need to translate into English, preserving Markdown. So "**Command:** The method has no result, but changes system state." But we need to preserve the formatting: bold "Command:" then the text.

So output: "**Command:** The method has no return value, but changes system state." or "The method has no result, but changes system state." Choose translation. I think "has no result" or "does not return a result". In the original Chinese: "方法没有结果，但会改变系统状态。" So "The method has no result, but changes system state." That is fine.

Return only the translated Markdown. No extra.
...done thinking.

**Command:** The method has no result, but changes system state.

Thinking...
We need to translate the markdown: "优点如下" into English. It's just a phrase. So translate: "Advantages are as follows". Or "The advantages are as follows". So the translation: "The advantages are as follows". Return only translated markdown. So output: "The advantages are as follows". Probably keep line break? Just one line. So:

The advantages are as follows

Yes.
...done thinking.

The advantages are as follows

Thinking...
We need to translate the given Chinese Markdown into English, preserving structure. The content: "查询类型的方法，对于调用者来讲不用在顾虑各个查询方法的调用顺序和次数(忽略性能的因素)。"

Translate: "The method of query type, for the caller it is unnecessary to worry about the call order and number of each query method (ignoring performance factors)."

Let's produce Markdown: just the sentence. The sentence is not code, just normal paragraph. Provide translation.

Return only translated markdown. Let's produce:

"The method of query type, for the caller there's no need to worry about the order of invocation and the number of each query method (performance factors are ignored)."

But we need preserve punctuation maybe. Chinese had parentheses. So keep parentheses. Provide English.

Thus final answer.
...done thinking.

The method of query type allows callers to ignore the order and number of calls to each query method (performance factors are ignored).

Thinking...
We have a simple markdown snippet: "命令类型的方法，从语义上来讲更准确。"

Need translate to English: "The method of command type is more accurate from a semantic perspective." Could be: "The method of command type is more accurate in terms of semantics." Let's produce.

Return only translated markdown. Probably just that sentence. Let's output.
...done thinking.

The method of command type is more accurate from a semantic standpoint.

Thinking...
We need to translate the Markdown into English. The Markdown has just "**范例**" which is bold Chinese word meaning "example". So translate to "**Example**". We preserve structure: the line is "**范例**". So output "**Example**". No code blocks. Just that line. Ensure line break after? The original has newline after? The Markdown: "**范例**" (maybe line break after). We return ONLY translated Markdown. So output:

**Example**

That's all.
...done thinking.

**Example**

![](/img/0_refactor-68.png)

Thinking...
The task: We need to translate the given Markdown into English, preserve structure, not translate code blocks or inline code. The Markdown content: "思考：哪些语句可以移动？" which is Chinese. It's likely a heading? Actually it's just a line. It's not indicated as a heading (no #). But maybe it's just a line. The translation: "Thought: Which statements can be moved?" or "Consider: Which statements can be moved?" We need to translate to English.

But we need to preserve structure: There is no code blocks, no inline code. Just plain text. So output: "Thought: Which statements can be moved?" Or "Thinking: Which statements can be moved?" The original Chinese: 思考：哪些语句可以移动？ This literally "Thought: Which statements can be moved?" So I'll output that.

Also the line break: just a single line. So final answer: "Thought: Which statements can be moved?"
...done thinking.

Thought: Which statements can be moved?

Thinking...
We need to translate the Markdown into English. The original is Chinese. It's just one line: "**范例：包含条件逻辑的移动**". That's "**Example: Move with conditional logic**" or "**Sample: Move containing conditional logic**". Likely "Example: Move with conditional logic". Should preserve the bold markdown. So output: **Example: Move with conditional logic**. That should be it.
...done thinking.

**Example: Move with conditional logic**

before：

![](/img/0_refactor-69.png)

after：

![](/img/0_refactor-70.png)

Thinking...
We have a short markdown: "**拆分循环（Split Loop）**". They want translation to English. Preserve markdown. So output: "**Split Loop**". The Chinese part inside parentheses: (Split Loop). But original had Chinese title and English in parentheses. Actually original: "**拆分循环（Split Loop）**". We translate to English: maybe "**Split Loop**"? The parentheses may contain translation, but we can omit Chinese part. Should we keep parentheses? The instruction: Translate the following Markdown into English. So translate the whole text. Should preserve markdown structure. So the translated string: "**Split Loop**". That seems correct.

Return only translated Markdown.
...done thinking.

**Split Loop**

![](/img/0_refactor-71.png)

Thinking...
We need to translate the given Markdown into English. The text is just "**范例**". That is Chinese for "Example" or "范例" means "example" or "sample".

We need to preserve Markdown structure and ordering. There is a line: **范例**. In English, we would write **Example**.

Thus output: **Example**. And nothing else. Ensure no extra content. Return only translated Markdown.
...done thinking.

**Example**

before：

![](/img/0_refactor-72.png)

after：

![](/img/0_refactor-73.png)

Thinking...
We need translate into English. The heading: **Replace Loop with Pipeline** maybe. The original title: "以管道取代循环（Replace Loop with Pipeline）". They want preserve Markdown. So we output **Replace Loop with Pipeline** in English. Probably just that heading. Ensure markdown remains.

Return only translated markdown. So we output:

**Replace Loop with Pipeline**
...done thinking.

**Replace Loop with Pipeline**

![](/img/0_refactor-74.png)

Thinking...
We need to translate into English. Markdown structure: just paragraph. Keep line breaks. So output:

map operation refers to applying a function to each element of the input set, transforming the set into another set; filter operation refers to applying a function to select a subset of elements from the input set that meet the condition. The resulting set can be used by subsequent stages of the pipeline.

Ensure not to alter formatting. Just plain text. Provide exactly that.
...done thinking.

map operation refers to applying a function to each element of the input set, transforming the set into another set; filter operation refers to applying a function to select a subset of elements from the input set that meet the condition. The resulting set can be used by subsequent stages of the pipeline.

Thinking...
The user asks: "You are a professional technical translator. Translate the following Markdown into English. Rules: - Preserve Markdown structure and ordering. - Do NOT translate code blocks (` ``...`` `) or inline code in backticks. - Do NOT alter URLs, links, or image paths. - Keep line breaks as much as possible. Return ONLY translated Markdown. Markdown: **范例**"

So the input Markdown is just "**范例**" which is bold text "范例" meaning "Example". So we translate to English: "**Example**".

Return ONLY the translated Markdown. No explanation. So final answer: **Example**
...done thinking.

**Example**

before：

![](/img/0_refactor-75.png)

![](/img/0_refactor-76.png)

after：

![](/img/0_refactor-77.png)

Thinking...
We just need to translate to English. The title in Chinese: "**移除死代码（Remove Dead Code）**". In English, maybe "**Remove Dead Code**". The parentheses likely keep the English. So translation: "**Remove Dead Code**". But the Chinese also says "移除死代码（Remove Dead Code）". So we can translate to "**Remove Dead Code**". But should we keep both? The rule: preserve Markdown. It seems to include translation. So we produce:

**Remove Dead Code**

Thus output.
...done thinking.

**Remove Dead Code**

![](/img/0_refactor-78.png)

Thinking...
The user wants to translate the markdown into English, preserving structure, not translating code blocks. The markdown is only a heading: **第9章　重新组织数据**. We need to translate that: "**Chapter 9: Reorganizing Data**". Keep bold formatting. Possibly keep line break. So output:

**Chapter 9: Reorganizing Data**.
...done thinking.

**Chapter 9: Reorganizing Data**

Thinking...
We need to translate the markdown into English. The original markdown: "**拆分变量（Split Variable）**". The Chinese part "拆分变量" means "Split Variable". Already provided in parentheses. So translation: "**Split Variable**" or maybe keep the original? But we need to translate. Should keep bold. So final: "**Split Variable**". Also include the parentheses? The original includes "(Split Variable)". We may drop the parentheses? They ask to translate the following Markdown into English. So likely we translate the Chinese into English. We could keep the English translation only: "**Split Variable**". Could also keep the parentheses for explanation: "**Split Variable (Split Variable)**"? But that's redundant. I'll produce "**Split Variable**".
...done thinking.

**Split Variable**

![](/img/0_refactor-22.png)

Thinking...
We need to translate into English, preserving Markdown. The text is in Chinese. So we translate:

Original:

除"循环变量"和"结果收集变量"外，还有很多变量用于保存一段冗长代码的运算结果，以便稍后使用。这种**变量应该只被赋值一次。**如果它们被赋值超过一次，就意味它们在函数中承担了一个以上的责任。如果变量承担多个责任，它就应该被替换（分解）为多个变量，**保持职责单一**。

We must preserve bold formatting. In markdown, **text** remains.

So translation:

Except for "loop variables" and "result collection variables", there are many other variables used to store the results of a lengthy piece of code for later use. Such variables should only be assigned once. If they are assigned more than once, it means they take on more than one responsibility in the function. If a variable bears multiple responsibilities, it should be replaced (decomposed) into multiple variables, keeping responsibilities single.

But we need to preserve Markdown structure: It's just a paragraph.

Let's produce the translated Markdown.
...done thinking.

Except for **loop variables** and **result collection variables**, there are many other variables used to store the results of a lengthy block of code for later use. Such variables should only be assigned once. If they are assigned more than once, it means they are taking on more than one responsibility within the function. If a variable bears multiple responsibilities, it should be replaced (decomposed) into multiple variables, **keeping each responsibility single**.

Thinking...
We need to translate the provided markdown into English. It says:

**范例：对输入参数赋值**

Which in English: "**Example: Assigning values to input parameters**" or something. It wants preserve Markdown. So bold. The Chinese says "范例：对输入参数赋值" meaning "Example: Assigning values to input parameters". So final output:

**Example: Assigning values to input parameters**
...done thinking.

**Example: Assigning values to input parameters**

before：

![](/img/0_refactor-23.png)

after：

![](/img/0_refactor-24.png)

Thinking...
We need to translate given Markdown into English. Provided is:

**字段改名（Rename Field）**

So in English: **Field Rename (Rename Field)**? Actually "字段改名" meaning "Rename Field". So maybe "**Field Rename (Rename Field)**" but original includes "Rename Field" in parentheses. Should be "**Field Rename (Rename Field)**". The second part is English inside parentheses. The original has Chinese and English.

They want translation of Markdown into English. So we translate Chinese part. Keep English parentheses.

Thus: **Field Rename (Rename Field)**

We preserve bold markup.

Return only the translated Markdown.

So answer: **Field Rename (Rename Field)**

...done thinking.

**Field Rename (Rename Field)**

![](/img/0_refactor-79.png)

Thinking...
The user wants translation of Markdown: "**范例：给字段改名**". They want English translation. The rule: preserve markdown. So just translate the text inside the bold tags. That phrase means "Example: Renaming a field". So the translated version would be "**Example: Renaming a field**". No other changes.

Thus output only that.

...done thinking.

**Example: Renaming a field**

before：

![](/img/0_refactor-80.png)

after：

![](/img/0_refactor-81.png)

Thinking...
We need to translate to English. Keep markdown. Title: **以查询取代派生变量（Replace Derived Variable with Query）**. The translation: "**Replace Derived Variables with Queries**" or "Replace Derived Variables by Query". The parentheses part: "Replace Derived Variable with Query". Probably we keep the original Chinese and add translation? But rule says translate the Markdown into English. Should we keep Chinese? Maybe just translate to English. So the output:

**Replace Derived Variable with Query**

But the original had Chinese and English inside parentheses. Could translate both. Let's produce: "**Replace Derived Variable with Query**" but that is redundant. Actually the title maybe: "**Replace Derived Variable with Query**". The parentheses maybe redundant. The original had both Chinese and English. We can translate the whole: "**Replace Derived Variable with Query**". We can include Chinese? No, translation. So final output:

**Replace Derived Variable with Query**.

But also keep original order and structure. So only that line. Let's output.
...done thinking.

**Replace Derived Variable with Query**

![](/img/0_refactor-82.png)

Thinking...
We need to translate into English: The example: "**范例**" is a heading? Bold. Means "Example". The instruction: Preserve Markdown structure, but only translate. So "**范例**" -> "**Example**". That's it.
...done thinking.

**Example**

Thinking...
We need translate Chinese sentence into English. The markdown just has a single line "即时计算，不必每次更新。" That's likely a heading or paragraph? There is no markdown header. It's a simple text. So translation: "Instant calculation, no need to update each time." Or "Real-time calculation, no need to update each time." In English: "Real-time calculation, no need to update each time." or "Instant calculation, no need to update each time." So produce that. Should keep structure. Just a single line. No code blocks. No changes. Provide just the translated Markdown.
...done thinking.

Instant calculation, no need to update each time.

before：

![](/img/0_refactor-83.png)

after：

![](/img/0_refactor-84.png)

![](/img/0_refactor-85.png)

Thinking...
We need to translate Chinese text: "**范例：不止一个数据来源**" to English. Keep the markdown structure: it's bold. So "**Example: More than one data source**" or "**Example: Multiple data sources**" or "Example: Not just one data source". We'll translate as "**Example: Multiple Data Sources**". That preserves structure. Return only the translated markdown.
...done thinking.

**Example: Multiple Data Sources**

before：

![](/img/0_refactor-86.png)

after：

![](/img/0_refactor-87.png)

Thinking...
We need to translate the given Markdown into English. The input:

"引入断言："

It's a heading maybe? The text: "引入断言：" means "Introducing assertions:" or "Introduce assertions:".

We must preserve Markdown structure. There's no markup indicated besides the colon? It might be a heading? It's just plain text. But it's likely a heading level? The original is just a line. Maybe it's a heading like "# 引入断言：" but not given. We need to translate only the content. So output "Introducing assertions:".

Make sure to preserve Markdown structure and ordering. Since there is no Markdown formatting, just plain text, output that line.

Return only the translated Markdown. So output "Introducing assertions:".

Let's do that.
...done thinking.

Introducing assertions:

![](/img/0_refactor-88.png)

Thinking...
We need to translate the Markdown into English. It contains "**将引用对象改为值对象（Change Reference to Value）**". This is a heading? It's bold. The translation should keep markdown structure. Probably we need to translate the Chinese part to English, but keep the parenthetical "Change Reference to Value" which is already English. Should we translate Chinese? The translation likely: "**Change Reference Objects to Value Objects (Change Reference to Value)**" Wait, the original says "将引用对象改为值对象（Change Reference to Value）". So Chinese phrase: "将引用对象改为值对象" meaning "Change reference objects to value objects". So we translate that: "**Change Reference Objects to Value Objects (Change Reference to Value)**". Or maybe we preserve parentheses? But we want to keep the structure: bold. The parenthetical is already in English. But we might keep Chinese? We should translate entire phrase, but keep the parenthetical? The rule: preserve Markdown structure and ordering. Do not alter URLs, links, or image paths. But translation: we should translate. The parenthetical "Change Reference to Value" is probably a note; we might preserve. But maybe we need to translate the Chinese part. So final: "**Change Reference Objects to Value Objects (Change Reference to Value)**".

Thus output: 

**Change Reference Objects to Value Objects (Change Reference to Value)**

We keep line breaks? It's single line. Provide just that.
...done thinking.

**Change Reference Objects to Value Objects (Change Reference to Value)**

Thinking...
The task: Translate the given Markdown into English. The text: "不需要共享一个对象。". That is Chinese. The translation: "You don't need to share an object." Or "No need to share an object." Might choose: "No need to share an object." The output must be only the translated Markdown. So final output: "No need to share an object." Ensure no code blocks. So answer.
...done thinking.

No need to share an object.

![](/img/0_refactor-89.png)

Thinking...
We need to translate the markdown into English. It's a short snippet: "**范例**" which means "**Example**". So the translation would be "**Example**". No code blocks. Keep markdown. So output only "**Example**".
...done thinking.

**Example**

before：

![](/img/0_refactor-90.png)

after：

![](/img/0_refactor-91.png)

Thinking...
We need to translate the given Markdown into English. The heading: "**将值对象改为引用对象（Change Value to Reference）**" should become "**Change Value Objects to Reference Objects**" or similar. The parentheses contain original Chinese phrase: (Change Value to Reference). So translation likely "Change Value to Reference". The whole string: "**将值对象改为引用对象（Change Value to Reference）**". We need preserve formatting: double asterisks, parentheses, etc. Should keep line breaks but only one line. So final: **Change Value Objects to Reference Objects (Change Value to Reference)**? Wait maybe they want to keep Chinese inside? Actually rule says translate the markdown into English. So translate Chinese parts into English. The parentheses already contain English translation. So we could keep that but maybe we can change wording: "Change Value to Reference". But we can also produce "Change Value Objects to Reference Objects (Change Value to Reference)". But the original Chinese says "将值对象改为引用对象" which is "Change Value Objects to Reference Objects". So we need to translate into English, keep parentheses? The parentheses contain English translation "Change Value to Reference". But maybe we need to adjust to "Change Value to Reference". It might be a subtitle? The parentheses might be optional. But we can keep it as is. The translation would be:

**Change Value Objects to Reference Objects (Change Value to Reference)**

But maybe we want "Change Value to Reference". But they already have that inside. I'll output:

**Change Value Objects to Reference Objects (Change Value to Reference)**

We need to preserve markdown structure. That's it. No code. Return only the translated markdown.
...done thinking.

**Change Value Objects to Reference Objects (Change Value to Reference)**

Thinking...
We need to translate the markdown "共享一个对象。" into English. The original is Chinese: "共享一个对象。" means "Share an object." The context: "共享一个对象。" likely refers to "Share an object." Could also be "Share an object." So the translation should be:

Share an object.

So we keep the same structure: maybe just one line. Should preserve punctuation: "Share an object." So output exactly that.

We must preserve Markdown structure. The input had "共享一个对象。". That is a single line. We output the same structure. Ensure we keep the period. So output: "Share an object."
...done thinking.

Share an object.

![](/img/0_refactor-92.png)

Thinking...
The input: "Markdown: **范例**". We need to translate into English. "范例" means "Example" or "sample". The heading is bold. So "**范例**" becomes "**Example**". Keep markdown structure. So output: **Example**.
...done thinking.

**Example**

before：

![](/img/0_refactor-93.png)

after：

![](/img/0_refactor-94.png)

![](/img/0_refactor-95.png)

Thinking...
We need translate to English. The original text: "存在的问题：构造函数与一个全局的仓库对象**耦合**。"

In English: "Existing issue: constructor is coupled with a global repository object."

But need preserve Markdown. The original had line break? It's a single paragraph. The phrase "存在的问题：" becomes "Existing problem:" or "Problem:". They want translation. Use Markdown. So final output:

```
Existing issue: the constructor is coupled with a global repository object.
```

But we should keep bold around "耦合" maybe convert to "**coupled**". So: "Existing issue: constructor is coupled with a global repository object." Bold? "coupled" maybe bold? They wrote **耦合** originally, so we keep bold on 'coupled'. So final: "Existing issue: constructor is coupled with a global repository object."

But need preserve the "**耦合**" as "**coupled**". So:

"Existing issue: constructor is coupled with a global repository object."

Wrap coupled in **. So:

"Existing issue: constructor is coupled with a global repository object."

But maybe add line break? Just one line.

Thus final output: 
Existing issue: constructor is coupled with a global repository object.

Add bold around coupled: "**coupled**".

So:

Existing issue: constructor is **coupled** with a global repository object.

Yes.
...done thinking.

Existing issue: the constructor is **coupled** with a global repository object.

Thinking...
We need to translate the Markdown text from Chinese to English, preserving structure and ordering, not translating code blocks or inline code. There's no code block here, just plain text. The Chinese text: "改进的办法：**将仓库对象作为参数传递给构造函数**。" Means: "Improved approach: **Pass the repository object as a parameter to the constructor**."

We need to preserve Markdown: the text is "改进的办法：**将仓库对象作为参数传递给构造函数**。". There's a colon, bold part. So we translate: "Improved method: **Pass the repository object as a parameter to the constructor**." But we need to keep the period. There's Chinese punctuation. We translate to English punctuation. So output: "Improved approach: **Pass the repository object as a parameter to the constructor**." Use the same formatting. Let's produce that.
...done thinking.

Improved approach: **Pass the repository object as a parameter to the constructor**.

Thinking...
We just translate Chinese title: "第10章 简化条件逻辑" into English. Should preserve markdown. So output: "**Chapter 10: Simplifying Conditional Logic**" with same emphasis. So just that line.
...done thinking.

**Chapter 10: Simplifying Conditional Logic**

Thinking...
We need to translate the Markdown into English. Original text is:

**分解条件表达式（Decompose Conditional）**

We need to preserve markdown. The translation should be: "**Decompose Conditional Expression (Decompose Conditional)**"? But "分解条件表达式" means "Decompose Conditional Expression" or "Decompose Condition". The parentheses already has "Decompose Conditional". The translation should be "Decompose Conditional Expression (Decompose Conditional)" or maybe keep the same? The original has both Chinese and English in parentheses: (Decompose Conditional). So the translation probably just convert Chinese to English: "**Decompose Conditional Expression (Decompose Conditional)**".

But the parentheses might be a translation of "Decompose Conditional"? Actually the original includes both Chinese and English: "分解条件表达式（Decompose Conditional）". The English translation likely is "Decompose Conditional Expression (Decompose Conditional)". But the parentheses might be an optional translation. The instructions: "Translate the following Markdown into English." So we need to translate the Chinese part to English. So we would produce "**Decompose Conditional Expression (Decompose Conditional)**". But we might consider not to translate the English inside parentheses because it's already English. So just change "分解条件表达式" to "Decompose Conditional Expression". Keep parentheses with "Decompose Conditional" unchanged. So final output: **Decompose Conditional Expression (Decompose Conditional)**. Ensure line breaks etc. Just that.

...done thinking.

**Decompose Conditional Expression (Decompose Conditional)**

![](/img/0_refactor-25.png)

Thinking...
We need to translate the provided Markdown into English. The original content is:

"程序之中，复杂的条件逻辑是最常导致复杂度上升的因素之一。"

This is a single sentence. The translation: "In a program, complex conditional logic is one of the most common factors that leads to increased complexity."

Preserve markdown structure: it's just a paragraph. No code. So we return the translated paragraph. Ensure line breaks as possible: it's a single line. So output:

"In a program, complex conditional logic is one of the most common factors that lead to increased complexity."

We can choose "leads" or "lead". The original uses singular? "是最常导致复杂度上升的因素之一" = "is one of the most common factors that cause complexity to rise." So maybe "causes". Let's produce:

"In a program, complex conditional logic is one of the most common factors that cause complexity to increase."

Return only that.

...done thinking.

In a program, complex conditional logic is one of the most common factors that cause complexity to increase.

Thinking...
We need to translate the given Chinese Markdown into English. Preserve structure. The content is: "对于条件逻辑，**将每个分支条件分解成新函数**还可以带来更多好处：可以突出条件逻辑，更清楚地表明每个分支的作用，并且突出每个分支的原因。"

So translation: "For conditional logic, **breaking each branch condition into a new function** can bring even more benefits: it can highlight the conditional logic, more clearly indicate the purpose of each branch, and emphasize the reason for each branch."

We should preserve Markdown: bold formatting with **. No code blocks. So final.
...done thinking.

For conditional logic, **breaking each branch condition into a new function** can bring even more benefits: it can highlight the conditional logic, more clearly indicate the purpose of each branch, and emphasize the reason for each branch.

Thinking...
The user asks to translate the given Markdown into English. The text: "注：实际上为提炼函数的一个应用场景。". It means "Note: Actually, this is a use case for extracting functions." or something similar.

We must preserve Markdown structure and ordering. It's just one line. No code blocks, no URLs. So translation: "Note: Actually, this is a scenario for extracting functions." Could also be "Note: This is actually an application scenario for refactoring functions." We need to keep punctuation. Original: "注：实际上为提炼函数的一个应用场景。" So: "Note: This is actually a scenario for extracting functions." That seems correct.

We must not add extra lines. The output should be the translated Markdown. Just that line.

Return ONLY translated Markdown. So final.
...done thinking.

Note: This is actually a scenario for extracting functions.

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: Preserve Markdown structure and ordering. Do NOT translate code blocks or inline code in backticks. Do NOT alter URLs, links, or image paths. Keep line breaks as much as possible. Return ONLY translated Markdown. Markdown: **范例**"

So the content is just "**范例**". That is "**Example**" in English. So we translate "**范例**" to "**Example**". And we need to preserve Markdown structure and ordering. It's a single bold text. So the output should be: "**Example**". No other content. Return ONLY translated Markdown. So answer: **Example**.
...done thinking.

**Example**

before：

![](/img/0_refactor-96.png)

after：

![](/img/0_refactor-97.png)

Thinking...
We need translate to English. The Markdown has a heading with bold: "**合并条件表达式（Consolidate Conditional Expression）**". In English: "**Consolidate Conditional Expression (Consolidate Conditional Expression)**"? Wait the original Chinese phrase "合并条件表达式" then in parentheses "Consolidate Conditional Expression". So we translate entire string: "**Consolidate Conditional Expression**". But keep the parentheses? The original has Chinese phrase with parentheses containing English translation. We might translate entire line to English, but preserving Markdown structure and ordering. The line is just bold text. We might convert to "**Consolidate Conditional Expression**". That seems correct. Ensure no code block.

Thus output: **Consolidate Conditional Expression**.
...done thinking.

**Consolidate Conditional Expression**

![](/img/0_refactor-26.png)

Thinking...
We need translate Chinese to English. Title: "**以卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard Clauses）**". So output: **Replace Nested Conditional with Guard Clauses** maybe preserve parentheses. The original includes Chinese and English. The translation: "**Replace Nested Conditional with Guard Clauses**". Should we keep Chinese? No. Should translate entire line: "**以卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard Clauses）**". The Chinese part should be translated: "Replace Nested Conditional with Guard Clauses". Maybe include both languages? But rule: translate to English. So remove Chinese. So final: "**Replace Nested Conditional with Guard Clauses**". Keep Markdown structure. No code blocks. So output that line.
...done thinking.

**Replace Nested Conditional with Guard Clauses**

![](/img/0_refactor-27.png)

Thinking...
We need to translate the given Markdown into English, preserving structure. The text: Chinese. It mentions "如果两条分支都是正常行为，就应该使用形如if...else...的条件表达式；如果某个条件极其罕见，就应该单独检查该条件，并在该条件为真时立刻从函数中返回。这样的单独检查常常被称为"卫语句"（guard clauses）。"

We translate: "If both branches represent normal behavior, a conditional expression of the form if...else... should be used; if a certain condition is extremely rare, it should be checked separately, and the function should return immediately when that condition is true. Such separate checks are often called guard clauses."

Make sure not to translate code blocks or inline code. There is no code block or inline code. So just the paragraph. The Markdown might be a paragraph. No special formatting. So final answer: the English translation as a Markdown paragraph.

Return only translated Markdown.

Thus: "If both branches represent normal behavior, one should use a conditional expression of the form `if...else...`; if a certain condition is extremely rare, it should be checked separately, and the function should return immediately when that condition is true. Such separate checks are often called guard clauses."

We need to keep code in backticks if present. There's `if...else...`. So put backticks. Use same formatting: the original had if\...else\... in code formatting maybe backticks? Actually original had if\...else\... with backslashes to escape, but no code formatting. In markdown, it might be just plain text with backslashes. But it's okay. We can preserve with backticks. But guidelines: do not translate code blocks and inline code in backticks. So if we use backticks, we must preserve code. But we could just keep as plain text. It's fine. I'd use backticks around the expression. The original had if\...else\... but we can use `if...else...`.

Thus final.
...done thinking.

If both branches represent normal behavior, a conditional expression of the form `if...else...` should be used; if a certain condition is extremely rare, it should be checked separately, and the function should return immediately when that condition is true. Such separate checks are often called guard clauses.

Thinking...
We need to translate the provided markdown into English, following the rules: preserve structure and ordering, do not translate code blocks or inline code. There's no code blocks or inline code. The text: "**如果使用if-then-else结构，则对if分支和else分支的重视是同等的；以卫语句取代嵌套条件表达式的精髓就是：给某一条分支以特别的重视。**" It's all bolded. So translation: "**If you use an if-then-else structure, then the importance given to the if branch and the else branch is equal; the essence of replacing a nested conditional expression with a guard statement is: give special attention to a particular branch.**"

We need to preserve the bold markdown. So final answer is the translation.
...done thinking.

**If you use an if‑then‑else structure, then the importance given to the if branch and the else branch is equal; the essence of replacing a nested conditional expression with a guard statement is to give special attention to a particular branch.**

Thinking...
We need to translate to English. The text: “每个函数只能有一个入口和一个出口”的观念未必有用，保持代码清晰才是最关键的。 The punctuation: Chinese quotes. We translate: "The idea that each function can have only one entry and one exit may not be useful; keeping the code clear is the most important." Must preserve Markdown. There's no code. Just plain text. So output that line. Keep formatting. So output:

"The idea that each function can have only one entry and one exit may not be useful; keeping the code clear is the most important."

Make sure it's same line breaks. It's a single line. Use English quotes? The original uses Chinese quotation marks. We can keep them or use English. It's part of the text. But translation likely: "The notion that each function can have only one entry and one exit may not be useful; keeping the code clear is the most important." Should we keep the quotation marks? The original: "每个函数只能有一个入口和一个出口"的观念未必有用，保持代码清晰才是最关键的。 We can translate as: "The notion that each function can have only one entry and one exit may not be useful; keeping the code clear is the most important." Might keep quotes around the phrase. Probably keep the quotes but use English quotes. I'll output that.
...done thinking.

The notion that each function can have only one entry and one exit may not be useful; keeping the code clear is the most important.

Thinking...
We need translate given Markdown into English. The given is "**范例**" meaning "**Example**". We must preserve markdown. So output: "**Example**". That's it.
...done thinking.

**Example**

before

![](/img/0_refactor-28.png)

after

![](/img/0_refactor-29.png)

Thinking...
We have a short markdown: "**范例：将条件反转**". Translate to English: "**Example: Invert Condition**" maybe "Example: Reverse Condition". Let's think. "将条件反转" literally means "invert condition" or "reverse condition". So "Example: Invert Condition". We'll preserve bold. So "**Example: Invert Condition**". Ensure line breaks as same. Output only that.
...done thinking.

**Example: Invert Condition**

Thinking...
We need to translate "初始" to English. In Markdown, it's just a heading? The original just shows "初始" alone, likely a heading or a line. The Markdown given:

```
初始
```

No backticks. It could be just a heading or a paragraph. Should preserve structure. So translate "初始" to "Initial". Should we use capital? Probably keep same case. So output:

```
Initial
```

But we must preserve Markdown structure and ordering. Just one line. So output just "Initial". No extra formatting.

Thus final answer: Initial.
...done thinking.

Initial

![](/img/0_refactor-30.png)

Thinking...
The user wants to translate the Markdown into English. The input markdown content: "反转" which likely means "reverse". Just one word. So translation: "Reverse". Preserve Markdown structure. It's just a word. So output: "Reverse".
...done thinking.

Reverse

![](/img/0_refactor-31.png)

Thinking...
The user says: "You are a professional technical translator. Translate the following Markdown into English. Rules: - Preserve Markdown structure and ordering. - Do NOT translate code blocks (```) or inline code in backticks. - Do NOT alter URLs, links, or image paths. - Keep line breaks as much as possible. Return ONLY translated Markdown.

Markdown:
合并条件表达式"

We need to translate "合并条件表达式" into English. The phrase means "Merge conditional expressions". Could also be "Combine conditional expressions" or "Merge condition expressions". Usually, Chinese "合并条件表达式" means "Merge condition expressions". In English, could be "Combine conditional expressions". Let's see context: "合并条件表达式" as a heading perhaps. So translation: "Merge Conditional Expressions" maybe capitalized.

Thus output: "Merge Conditional Expressions". And keep as Markdown? There's no code blocks. Just a single line. So output that.
...done thinking.

Merge Conditional Expressions

![](img/0_refactor-32.png)

Thinking...
We need to translate the given Markdown into English. The text: "删除可变变量" which means "Delete mutable variables". So we produce "Delete mutable variables". But the markdown may have some heading? The original had "删除可变变量" alone. In Markdown, if it's a heading, it may start with #, but not shown. It seems just plain text. But we can translate as plain text. So output: "Delete mutable variables". Keep line breaks as possible. There's just one line. So output that line.
...done thinking.

Delete mutable variables

![](img/0_refactor-33.png)

Thinking...
We need to translate the Markdown into English. The title: "**以多态取代条件表达式（Replace Conditional with Polymorphism）**" The text inside bold includes Chinese phrase "以多态取代条件表达式" and the English translation in parentheses. So we translate. The output should be only translated Markdown. So we write:

**Replace Conditional with Polymorphism**

But we might keep the parentheses? The original includes both Chinese and English. The instruction: translate the following Markdown into English. So likely we should translate Chinese part to English, but keep the English part? Should we keep the parentheses? The original includes Chinese then parentheses with English translation. So translating we could keep the English translation as is. But maybe we should produce only English title: **Replace Conditional with Polymorphism**. The parenthetical could be omitted because it's already translation. But the instruction: "translate the following Markdown into English" means the whole. So we replace Chinese with English, and keep the English part too? Might be redundant. Probably output: **Replace Conditional with Polymorphism**.

Let's output that.
...done thinking.

**Replace Conditional with Polymorphism**

![](img/0_refactor-34.png)

Thinking...
We need to translate the given Markdown into English. The original is:

**引入特例（Introduce Special Case）**

So translation: **Introduce Special Case (Introduce Special Case)**? Wait: "引入特例（Introduce Special Case）" means Chinese part and English part in parentheses. They might want to translate into English. The parentheses already contain "Introduce Special Case". But maybe they want to translate the Chinese part as "Introduce Special Case" and keep the parentheses part unchanged? But rule says: translate Markdown into English. That suggests we should translate the whole content into English. But the original already has English in parentheses. The Chinese phrase means "Introduce Special Case". So translation would be **Introduce Special Case (Introduce Special Case)**? That would be redundant.

Maybe we translate the Chinese part to English but keep the parentheses part as is? Let's think. The original text is "引入特例（Introduce Special Case）". Usually they might write "引入特例（Introduce Special Case）" to show Chinese and English version. For translation into English, we might drop the Chinese part entirely, leaving only the English inside parentheses? But they might want to keep the parentheses as is. The instruction: "Translate the following Markdown into English." So we should produce English only. I'd translate the Chinese to English, maybe produce "Introduce Special Case (Introduce Special Case)"? But the parentheses part already says "Introduce Special Case". Might just keep that.

Alternatively we could produce "**Introduce Special Case**". But the original has parentheses part. The instruction: preserve Markdown structure and ordering, don't translate code blocks. There's only one line of Markdown. It's a heading (bold). So we need to translate that line.

I think the best output: **Introduce Special Case**. That is the English translation of the Chinese phrase, ignoring the redundant English in parentheses.

But maybe they'd expect us to keep the parentheses part unchanged: "**Introduce Special Case (Introduce Special Case)**". However that seems odd.

Given typical practice: if they give Chinese text with English in parentheses, the translator would simply translate the Chinese part and preserve the English translation. But here the English is same as the translation. So we can drop the Chinese part, leaving only the English translation. Or we could keep the parentheses part as is.

I'll choose to output:

**Introduce Special Case (Introduce Special Case)**

But that duplicates. Might be acceptable.

But I think better: **Introduce Special Case**. Because translation of Chinese phrase is "Introduce Special Case". The parentheses might be original translation but we don't need to keep it.

The instruction: "Preserve Markdown structure and ordering." The structure is one bold text. So output the translated bold text. So:

**Introduce Special Case**

Yes.

Let's answer with that.
...done thinking.

**Introduce Special Case**

![](img/0_refactor-98.png)

Thinking...
We need to translate into English. The Markdown includes quotation marks around "特例" and (Special Case). It says: "Create a special case element, to express shared behavior handling for this special case, thereby replacing most of the special case checking logic with a single function call."

We need to preserve Markdown structure. The original is: 

"特例"（Special
Case）模式：创建一个特例元素，用以表达对这种特例的共用行为的处理，**从而用一个函数调用取代大部分特例检查逻辑**。

We need to keep the quotes. Also preserve the line breaks: after "Special" newline "Case" etc. The rule: "Preserve Markdown structure and ordering." So we keep the text, maybe we need to keep the line break in the "Special Case" parentheses.

We should translate Chinese parts into English. Keep the Chinese characters? The translation should replace Chinese with English, but keep the Markdown.

Thus: `"Special Case"（Special Case）模式`? No, they already have Chinese: "特例"（Special Case）模式: That part is bilingual: "特例" (Special Case) pattern: But maybe we translate Chinese part: "Special Case" (Special Case) pattern: but the Chinese part "特例" should be left? They might want to translate the entire phrase: "Special Case (Special Case) pattern"? Actually we should translate Chinese: "特例" means "Special Case". So maybe we just keep the parentheses part unchanged? Let's produce: `"Special Case"（Special Case）pattern: create a special case element to express the shared behavior handling for this special case, **thus replacing most of the special case checking logic with a single function call**.` But keep line breaks? The original had line break after "Special" new line "Case". So we should preserve: "Special\nCase". But it's inside parentheses: （Special\nCase）. We'll keep the newline.

Thus final Markdown:

"Special Case"（Special
Case）pattern: create a special case element, to express the shared behavior handling for this special case, **thus replacing most of the special case checking logic with a single function call**.

But the quotes: "Special Case". The original had quotes around "特例" and then parentheses with "Special Case". We can keep quotes around "Special Case". So:

"Special Case"（Special
Case）pattern: create a special case element, to express the shared behavior handling for this special case, **thus replacing most of the special case checking logic with a single function call**.

Need to keep line break after Special. In Markdown, a line break is a single newline (or double?). We'll keep single newline.

Also maybe we keep the colon after pattern. The original had "模式：". So pattern: after colon.

Thus:

"Special Case"（Special
Case）pattern: create a special case element, to express the shared behavior handling for this special case, **thus replacing most of the special case checking logic with a single function call**.

Let's output that.
...done thinking.

"Special Case"（Special
Case）pattern: create a special case element, to express the shared behavior handling for this special case, **thus replacing most of the special case checking logic with a single function call**.

Thinking...
We need to translate. The markdown header says "**引入断言（Introduce Assertion）**". Should translate to "**Introduce Assertion**". But we might keep original? The instruction: translate. So we translate. Also parentheses? The Chinese title "引入断言（Introduce Assertion）". Probably keep the original and English? But rule: preserve markdown structure. So the entire text is the header. We can translate it as "**Introduce Assertion**". The Chinese part may be removed. Should we keep? It says "translate". So I think we replace with English. So output: **Introduce Assertion**. No other content.
...done thinking.

**Introduce Assertion**

![](img/0_refactor-99.png)

Thinking...
We just need to translate the given markdown text: "**第11章 重构API**". That's Chinese: "Chapter 11 Refactoring API". It wants preserve markdown structure: bold. So output "**Chapter 11 Refactoring API**". Probably no punctuation? Just translate. Return only translated Markdown.
...done thinking.

**Chapter 11 Refactoring API**

Thinking...
We need to translate the Chinese title into English. Keep Markdown structure: ** text. So "**Separate Query from Modifier**" but we might keep translation: "**Separate Query Functions and Modifier Functions**" The Chinese: "将查询函数和修改函数分离（Separate Query from Modifier）". The translation might be "**Separate Query from Modifier**". But also preserve the Chinese parentheses? The rule: "Preserve Markdown structure and ordering." We can translate entire text: "**Separate Query from Modifier**". But maybe keep both Chinese and English? The original has Chinese heading then the English phrase in parentheses. The instruction: "Translate the following Markdown into English." So we translate the entire content. The parentheses already contain English. So we can produce: "**Separate Query from Modifier**". That covers both parts? The parentheses already have "Separate Query from Modifier". But if we translate, we can produce the English translation. However the original includes the English phrase already. So maybe we keep the original Chinese phrase with translation: "**Separate Query from Modifier**". But that would replace the Chinese text. But the instruction: "Translate the following Markdown into English." So we should translate to English: "**Separate Query from Modifier**". This also matches the parentheses. Good. But maybe we need to maintain the Chinese phrase in parentheses? No.

Thus output: **Separate Query from Modifier**.
...done thinking.

**Separate Query from Modifier**

![](img/0_refactor-100.png)

Thinking...
We have input: "**范例**". That's Chinese: "Example". They want translation into English. Preserve Markdown structure: it's bold text. So output "**Example**". Ensure not to change anything else. They want only translated Markdown. So output: "**Example**".
...done thinking.

**Example**

before

![](img/0_refactor-101.png)

After

![](img/0_refactor-102.png)

![](img/0_refactor-103.png)

Thinking...
We need to translate the given markdown into English. The original is:

**函数参数化（Parameterize Function）**

We translate to: **Function Parameterization (Parameterize Function)** maybe. The rule: preserve markdown. So output:

**Function Parameterization (Parameterize Function)**

That's it.
...done thinking.

**Function Parameterization (Parameterize Function)**

![](img/0_refactor-104.png)

Thinking...
We need to translate "范例" to English. In markdown, this is just a heading? The input shows:

Markdown:
范例

So "范例" means "Example" or "Sample". Likely "Example". The output should preserve Markdown structure: a heading? But the original has no heading markup, just text. It's just a paragraph containing "范例". So we translate to "Example". Keep line breaks. So output is:

Example

Just that. Ensure no code blocks. So just "Example".
...done thinking.

Example

before

![](img/0_refactor-105.png)

After

![](img/0_refactor-106.png)![](img/0_refactor-107.png)g)

Thinking...
The input is a Markdown file: 
**移除标记参数（Remove Flag Argument）**

We need to translate to English. The heading text is "移除标记参数（Remove Flag Argument）". The English translation: "**Remove Flag Argument**". But there is a parenthetical Chinese explanation. The original had "移除标记参数（Remove Flag Argument）". That means Chinese title then English in parentheses. The instruction says translate the Markdown into English. Should we translate Chinese parts to English? Likely yes. We should translate the heading to English. The title "Remove Flag Argument". The parentheses contains English already. But we can translate the Chinese part. So result: "**Remove Flag Argument**". But maybe include original English? The requirement: Translate the Markdown into English. So we replace Chinese with English. So final: "**Remove Flag Argument**". The parentheses part might be redundant; we can keep it. But original had Chinese and English. If we translate Chinese, we keep English part? Might not need parentheses. The requirement to preserve structure and ordering. So we can produce "**Remove Flag Argument**". That is the translation.

Thus final.
...done thinking.

**Remove Flag Argument**

![](img/0_refactor-108.png)

Thinking...
We need to translate the given Markdown. It's a Chinese sentence:

**"标记参数"是这样的一种参数：调用者用它来指示被调函数应该执行哪一部分逻辑。**

In English: "**"Tag parameter" is a kind of parameter like this: the caller uses it to indicate which part of the logic the called function should execute.** We need to preserve bold. The quotes around 标记参数 are double quotes. So we can produce: **"Tag parameter" is a kind of parameter like this: the caller uses it to indicate which part of the logic the callee function should execute.** The Chinese "被调函数" means "called function". Also "调用者" is "caller". So the translation: "**"Tag parameter" is a parameter of this kind: the caller uses it to indicate which part of the logic the callee function should execute.** That's fine.

Make sure to preserve line breaks: There is just one line. So output the translated Markdown.

Thus final answer: **"Tag parameter" is a kind of parameter like this: the caller uses it to indicate which part of the logic the called function should execute.**
...done thinking.

**"Tag parameter" is a kind of parameter like this: the caller uses it to indicate which part of the logic the called function should execute.**

Thinking...
The task: translate markdown into English, preserving structure. Input markdown:

**范例**

It means "**Example**" in Chinese. So translate to English: "**Example**" with bold. So output: **Example**.

We need to keep Markdown structure and ordering. There's only one line: **范例**. Should be **Example**. Return only translated Markdown. No extra commentary.

Thus final answer: **Example**.
...done thinking.

**Example**

Before

![](img/0_refactor-109.png)

After

![](img/0_refactor-110.png)

Thinking...
The user wants to translate the Markdown into English, preserving structure, but the content is only a header bold: "**保持对象完整（Preserve Whole Object）**". The English translation: "**Preserve Whole Object**". Since the parentheses show translation of Chinese into English, but maybe they want the whole header in English. So the output should be:

**Preserve Whole Object**

But we need to preserve Markdown. So the output: **Preserve Whole Object**. No code. Just that line.
...done thinking.

**Preserve Whole Object**

![](img/0_refactor-111.png)

Thinking...
We need to translate the given Markdown into English. The original text: "减少函数参数长度，方便后续拓展。"

Translation: "Reduce function parameter length, facilitating subsequent expansion." Might phrase: "Reduce the length of function parameters to facilitate future expansion." Provide translation. Keep structure; there's just a line. So output that line.
...done thinking.

Reduce function parameter length to facilitate future expansion.

Thinking...
We just need to translate the Markdown header. The line "**以查询取代参数（Replace Parameter with Query）**" becomes "**Replace Parameter with Query (Replace Parameter with Query)**"? Wait. The Chinese part says "以查询取代参数" which means "Replace Parameter with Query". In parentheses it shows "Replace Parameter with Query". So translation: "**Replace Parameter with Query**". Probably keep parentheses but maybe not needed? The original: "**以查询取代参数（Replace Parameter with Query）**". In English we would write "**Replace Parameter with Query**". The parentheses is just translation. But maybe they'd want the entire string. So output:

**Replace Parameter with Query**

Thus preserve Markdown. Done.
...done thinking.

**Replace Parameter with Query**

![](img/0_refactor-35.png)

Thinking...
We need to translate the provided markdown into English. The original text: 
**函数的参数列表应该总结该函数的可变性**，标示出函数可能体现出行为差异的主要方式。和任何代码中的语句一样，**参数列表应该尽量避免重复**，并且参数列表越短就越容易理解。

We need to preserve Markdown structure. The bold marks are in **. So we keep ** around the translated phrase. The commas maybe in Chinese punctuation. Should we preserve punctuation? They ask to preserve Markdown structure and ordering, but not to alter punctuation? It's translation. So we translate content. We keep the commas? The original uses Chinese commas and punctuation. But in English we might use commas. It's fine.

Return only translated markdown. So produce:

**The function's parameter list should summarize the function's variability**, indicating the main ways the function may exhibit behavioral differences. As with any statement in code, **the parameter list should avoid repetition as much as possible**, and the shorter the parameter list, the easier it is to understand.

But need to maintain Markdown: The bold parts should remain bold. The punctuation after the phrase should be a comma? We can keep a comma or a period. Let's match original: "**函数的参数列表应该总结该函数的可变性**，标示出函数可能体现出行为差异的主要方式。和任何代码中的语句一样，**参数列表应该尽量避免重复**，并且参数列表越短就越容易理解。"

Original Chinese: Bold phrase, comma, sentence. So we can translate with punctuation: "The function's parameter list should summarize the function's variability," etc. Keep punctuation consistent.

Also note "参数列表" repeated. The second bold phrase "参数列表应该尽量避免重复". So in translation: "**The parameter list should avoid repetition as much as possible**". The earlier bold phrase: "**The function's parameter list should summarize the function's variability**". Good.

Now we produce the final markdown.
...done thinking.

**The function's parameter list should summarize the function's variability**, indicating the main ways the function may exhibit behavioral differences. As with any statement in code, **the parameter list should avoid repetition as much as possible**, and the shorter the parameter list, the easier it is to understand.

Thinking...
We need to translate into English. The text: "使用场景：调用函数时传入了一个值，而这个值由函数自己来获得也是同样容易". Means: "Use case: Passing a value to a function when calling it, and this value is obtained by the function itself is equally easy." So translation: "Use case: When calling a function, a value is passed in, and the value can also be obtained by the function itself, which is equally easy." We need to keep markdown structure. There's no markdown elements? The text seems plain. It could be a heading? It starts with "使用场景：". So we can translate: "Use case: When calling a function, a value is passed in, and the value can also be obtained by the function itself, which is equally easy." But keep the colon and the dash maybe. Let's produce exactly: "Use case: When calling a function, a value is passed in, and the value can also be obtained by the function itself, which is equally easy."

Return only the translated Markdown.
...done thinking.

Use case: When calling a function, a value is passed in, and the value can also be obtained by the function itself, which is equally easy.

Thinking...
We need translate into English. The text is Chinese: "什么是'同样容易'：函数可以承担这份原本由调用方所承担的'获得正确的参数值'的责任。"

We need preserve markdown structure. It's a single line? It's a sentence. We need to translate. So output: "What is 'equally easy': functions can take on the responsibility of 'obtaining the correct parameter values' that was originally borne by the caller."

Need preserve Markdown formatting. No code blocks. The original has no code block. So just output the translated sentence. Keep punctuation. Probably keep the quotes. We translate quotes. The Chinese uses single quotes around words. In English we can keep them. "What is 'equally easy': functions can take on the responsibility of 'obtaining the correct parameter values' that was originally borne by the caller."

That is translation.
...done thinking.

What is “equally easy”: functions can take on the responsibility of “obtaining the correct parameter values” that was originally borne by the caller.

Thinking...
We need to translate into English. Original Chinese: "什么时候不适用：移除参数可能会给函数体增加不必要的依赖关系。"

Translate: "When it is not applicable: removing parameters may add unnecessary dependencies to the function body." Need preserve Markdown. It's a heading? It looks like a line: "什么时候不适用：移除参数可能会给函数体增加不必要的依赖关系。"

Probably it's a heading? No markdown syntax, just plain text. So we translate it as plain text.

Thus output: "When it is not applicable: removing parameters may add unnecessary dependencies to the function body." Use same punctuation. Should keep line breaks. There's only one line.

Return only translated Markdown.

Let's provide.
...done thinking.

When it is not applicable: removing parameters may add unnecessary dependencies to the function body.

Thinking...
We need to translate the given markdown into English. Keep markdown structure. There is only text, no code blocks or inline code. So we translate Chinese to English.

Original:

留意：如果在处理的函数具有**引用透明性**（referential
transparency，即，不论任何时候，只要传入相同的参数值，该函数的行为永远一致），这样的函数既容易理解又容易测试，不会去除参数，让它访问一个可变的全部变量。

We need to preserve markdown structure. There's a bold part **引用透明性**. We keep bold. Also parentheses with referential transparency. There's newline after "referential". But we preserve line breaks as possible. The text is in Chinese. So we translate to English.

We keep bold part: **referential transparency** or keep Chinese? We translate bold text as well: **referential transparency**. But original has bold on Chinese "引用透明性" but we can translate that to bold English. Let's produce:

Note: If the function being processed has **referential transparency** (referential transparency, i.e., regardless of when it is invoked, as long as the same argument values are passed in, the function's behavior is always consistent), such a function is both easy to understand and easy to test, and it will not remove parameters to let it access all mutable variables.

Wait original: "不会去除参数，让它访问一个可变的全部变量。" Actually Chinese: "不会去除参数，让它访问一个可变的全部变量。" Means "It won't remove parameters to let it access all mutable variables." So translation: "such a function is easy to understand and test, and it will not remove parameters in order to access a mutable entire variable." Hmm.

Better translation: "such functions are easy to understand and test, and they don't eliminate parameters to allow access to a mutable global variable." But original says "可变的全部变量" maybe "mutable all variables"? Let's translate: "mutably accessible all variables" but better: "mutable global variables". So:

Note: If the function being processed has **referential transparency** (referential transparency, i.e., no matter when it's called, as long as the same argument values are passed in, the function's behavior is always consistent), such functions are easy to understand and test, and they don't remove parameters to allow access to mutable global variables.

We need to keep line breaks. The original has a line break after "referential". We'll preserve.

So final output:

Note: If the function being processed has **referential transparency** (referential
transparency, i.e., no matter when it is called, as long as the same argument values are passed in, the function's behavior is always consistent), such a function is easy to understand and easy to test, and it will not remove parameters to allow access to mutable global variables.

But we need to keep bold on referential transparency. The text: **引用透明性** => **referential transparency**. So we convert.

Let's produce final.
...done thinking.

Note: If the function being processed has **referential transparency** (referential
transparency, i.e., no matter when it is called, as long as the same argument values are passed in, the function's behavior is always consistent), such a function is easy to understand and easy to test, and it will not remove parameters to allow access to mutable global variables.

Thinking...
We need to translate the given Markdown: "**以参数取代查询（Replace Query with Parameter）**" into English. The rules: preserve Markdown structure. So we translate the Chinese phrase into English, while preserving the Markdown markup. The original is bold (**...). Inside we have "以参数取代查询（Replace Query with Parameter）". The translation should likely be "**Replace Query with Parameter**" maybe with the original Chinese inside parentheses? Actually the original has both Chinese and English. The translation may keep the English phrase and translate Chinese to English, but the English phrase already there. We need to translate the entire phrase: "以参数取代查询（Replace Query with Parameter）". So we need to translate to "Replace Query with Parameter". But we might want to include the Chinese part? The rule: Translate the Markdown into English. So we should translate the Chinese part to English. The parentheses contain the English translation. So maybe we drop the Chinese and keep the English? But we might keep both? But it's "translate the following Markdown into English". The English translation would likely be "**Replace Query with Parameter**". But we might include the English inside parentheses? No. The original already had parentheses with English. But translation would just be that English phrase. So final output: "**Replace Query with Parameter**". Should we keep the parentheses? The original had "Replace Query with Parameter" inside parentheses. In translation, we might just keep that phrase. But no parentheses needed. The entire string inside bold is "Replace Query with Parameter". So we output "**Replace Query with Parameter**". That should satisfy.
...done thinking.

**Replace Query with Parameter**

![](img/0_refactor-36.png)

Thinking...
We need to translate to English. The original is: "好处：改变依赖关系，去掉令人不快的引用。"

We need preserve Markdown. That is a heading? No, it's a line starting with "好处：" which might be a bullet? But it's just a line. We'll translate: "Benefits: change the dependency, remove unpleasant references." But Chinese: "好处：改变依赖关系，去掉令人不快的引用。" Means "Benefits: change the dependency, remove unpleasant references." So translation: "Benefits: change the dependency, remove unpleasant references."

Return only translated Markdown. So we output that line. Ensure no code block. It's just a normal line.

Thus output:

Benefits: change the dependency, remove unpleasant references.

That's it.
...done thinking.

Benefits: change the dependency, remove unpleasant references.

Thinking...
The user wants translation of the given Markdown into English. They provided a single sentence in Chinese: "注意：要考虑责任分配问题，会增加函数调用者的复杂度，而设计接口时又需要考虑易用性。"

We must preserve Markdown structure, ordering. It's a paragraph with "注意：" then the rest. We translate to English: "Note: You need to consider responsibility allocation, which increases the complexity for function callers, and when designing interfaces, usability must also be taken into account." Or something like that.

We should preserve line breaks. There's no code blocks. So just output the translated Markdown. The sentence: "Note: You need to consider the responsibility allocation issue, which will increase the complexity of function callers, while designing interfaces you also need to consider usability." That is good.

Return ONLY translated Markdown.

Let's produce:

Note: When considering responsibility allocation, it will increase the complexity for function callers, and when designing interfaces you must also consider usability.

Make sure to keep "Note:" capitalized. Also the colon after Note.

I'll produce:

Note: When considering responsibility allocation, it will increase the complexity for function callers, and when designing interfaces, you also need to consider usability.
...done thinking.

Note: When considering responsibility allocation, it will increase the complexity for function callers, and when designing interfaces you also need to consider usability.

Thinking...
We need to translate the given Markdown into English. Title "移除设值函数（Remove Setting Method）". The translation likely should be "**Remove Setting Method**" or "**Remove Setting Function**" with parentheses perhaps. The phrase inside parentheses "Remove Setting Method" is already English, so maybe it's the translation: "**Remove Setting Method**" but we keep the Chinese part? The instruction says translate Markdown into English, so we should translate Chinese text to English. The heading has Chinese and English in parentheses. The translation could be "**Remove Setting Method**" and maybe keep parentheses? The parenthetical is already English, but maybe keep it for context. The instruction: preserve Markdown structure and ordering, do not alter URLs, etc. So we just translate the Chinese part. The heading originally is "**移除设值函数（Remove Setting Method）**". The translation likely " **Remove Setting Function (Remove Setting Method)**" but maybe the Chinese meaning "移除设值函数" means "Remove Set Method"? Actually "设值函数" means "set method" (setter). So "移除设值函数" means "Remove Setter Function". So translation: "**Remove Setter Function (Remove Setting Method)**". But the parentheses already have "Remove Setting Method". Could be redundant. Perhaps we keep original parentheses as is. The best translation: "**Remove Setter Function (Remove Setting Method)**". That is the English translation. So produce that.
...done thinking.

**Remove Setter Function (Remove Setting Method)**

![](img/0_refactor-112.png)

Thinking...
The user requests: "You are a professional technical translator. Translate the following Markdown into English." The markdown content: "去除不必要的设值函数。" which is Chinese. It means "Remove unnecessary set functions." or "Remove unnecessary assignment functions." So translation: "Remove unnecessary set functions." We should preserve markdown. There's no code blocks. So just output translated line. No other formatting. Provide only the translated markdown. Let's do that.
...done thinking.

Remove unnecessary set functions.

Thinking...
We need to translate the given markdown to English, preserving markdown structure and ordering. The given markdown is:

**以工厂函数取代构造函数（Replace Constructor with Factory Function）**

We translate that: "**Replace Constructor with Factory Function**". But original contains Chinese and parentheses containing English phrase: (Replace Constructor with Factory Function). Should we keep both Chinese and English? The instruction says "Translate the following Markdown into English." So we need to translate the whole content into English. That includes the Chinese part. But we can keep the parenthetical English phrase? The phrase already is English. But the title is in Chinese. We translate it to English. We might produce "**Replace Constructor with Factory Function**". Or we could keep both: "**Replace Constructor with Factory Function** (Replace Constructor with Factory Function)". But that is redundant. The original has Chinese title with English parenthetical. So translation might drop the Chinese and keep the English title. The parenthetical maybe kept? But we could translate to keep the parenthetical or we can keep it. The instruction: "Translate the following Markdown into English." So we likely replace Chinese with English. The part inside parentheses is already English, so keep it. The title might then be: "**Replace Constructor with Factory Function (Replace Constructor with Factory Function)**" But that is odd. But could be fine.

Maybe better: "**Replace Constructor with Factory Function**". But then we would lose the parenthetical, but it's fine. However, the instruction is to preserve markdown structure and ordering, but not to alter URLs, links, or image paths. There are none. So we can output the translated title. We should preserve markdown structure: it's just a bold text. So output "**Replace Constructor with Factory Function**".

Thus the answer: **Replace Constructor with Factory Function**.

Check if we need to keep parentheses. The original: **以工厂函数取代构造函数（Replace Constructor with Factory Function）**. The parentheses are Chinese parentheses. Inside is English phrase. The translation might keep the English phrase inside parentheses? But the parentheses are just for clarification. In English, we might write: **Replace Constructor with Factory Function (Replace Constructor with Factory Function)**. That's redundant. But maybe they want the translation of the Chinese part, not the English part. So maybe just: **Replace Constructor with Factory Function**. The parentheses would be removed. That seems fine.

Thus answer: **Replace Constructor with Factory Function**.
...done thinking.

**Replace Constructor with Factory Function**

![](img/0_refactor-113.png)

Thinking...
We need to translate the markdown: "工厂函数的实现更为灵活。" into English. It is just a sentence. The rules: preserve markdown structure and ordering, don't translate code blocks, etc. There's no code. Just a sentence. Translate to English: "The implementation of the factory function is more flexible." Or "Factory function implementation is more flexible." Likely: "The implementation of factory functions is more flexible." The phrase "工厂函数的实现更为灵活。" Means "The implementation of factory functions is more flexible." We'll keep as a sentence. Ensure same formatting: just the sentence. Return only translated markdown. So output: "The implementation of factory functions is more flexible."
...done thinking.

The implementation of factory functions is more flexible.

Thinking...
The task: translate the given markdown into English. The content: "**以命令取代函数（Replace Function with Command）**". That is a heading in bold. We need to preserve markdown. So we output: "**Replace Function with Command**". But we need to translate the Chinese phrase. The Chinese phrase in parentheses already includes English translation "Replace Function with Command". So likely we should translate entire phrase: "**Replace Function with Command**". The instruction: preserve markdown structure, ordering, do not alter code blocks or inline code. There is no code. So just output the translation.

Thus output: **Replace Function with Command**.
...done thinking.

**Replace Function with Command**

![](img/0_refactor-114.png)

Thinking...
We need translate. The original: "**以函数取代命令（Replace Command with Function）**". So translate to English: "**Replace Command with Function**". But maybe also keep Chinese? Probably translation only. So just that line. Output only the translated markdown. Let's produce.

...done thinking.

**Replace Command with Function**

![](img/0_refactor-115.png)

Thinking...
We need to translate into English. The Markdown has a line: "处理的逻辑不是特别复杂，则命令对象可能显得费而不惠。". That seems like Chinese. We translate: "The processing logic is not particularly complex, so the command object may seem costly and not beneficial." Or better: "If the processing logic is not particularly complex, the command object may seem cumbersome and not advantageous." Let's produce that. It's one line of markdown. No code blocks. So output that line.
...done thinking.

If the processing logic is not particularly complex, the command object may appear cumbersome and not advantageous.

Thinking...
The task: translate the markdown into English. The given markdown is:

**第12章　处理继承关系**

This is Chinese: "Chapter 12: Handling Inheritance Relationships". But maintain the markdown structure and ordering. It is just a heading in bold. So translate to English: "**Chapter 12: Handling Inheritance Relationships**" Or maybe "Chapter 12: Handling Inheritance". The Chinese "处理继承关系" is "Handling Inheritance Relationships". So the translation: **Chapter 12: Handling Inheritance Relationships**. Keep formatting.

Thus output only that line.
...done thinking.

**Chapter 12: Handling Inheritance Relationships**

Thinking...
We need to translate the given Markdown into English. The content is Chinese. It's a heading: "**函数上移（Pull Up Method）**". The translation: "**Function Pull Up (Pull Up Method)**" maybe. Actually "函数上移" literally "Function Pull Up". The phrase "Pull Up Method" is included as parentheses. So the translation: "**Function Pull Up (Pull Up Method)**". But maybe it's "Function Pull-Up (Pull Up Method)". Might need to preserve the parentheses. So final: "**Function Pull Up (Pull Up Method)**". Should keep the Markdown. Return only the translated Markdown. Let's output: **Function Pull Up (Pull Up Method)**.
...done thinking.

**Function Pull Up (Pull Up Method)**

![](img/0_refactor-116.png)

Thinking...
We need to translate "消除重复代码。" into English. That is "Eliminate duplicate code." Or "Remove duplicate code." The phrase: "消除重复代码" means "Eliminate duplicate code." In technical context: "Remove duplicate code." The rule: preserve Markdown. The Markdown only includes that sentence. No code. So just output "Eliminate duplicate code." Probably as a single line.

Return ONLY translated Markdown. So output:

Eliminate duplicate code.
...done thinking.

Eliminate duplicate code.

Thinking...
We just need to translate the given text. The original is "字段上移（Pull Up Field）" in Chinese. It's a heading? It's in bold. It's probably a title. So we translate "字段上移" to "Move Field Up" or "Pull Up Field". The translation already includes Pull Up Field in parentheses. So maybe we translate to "**Move Field Up (Pull Up Field)**" or keep "Pull Up Field" as translation. We must preserve structure: It's bold, with parentheses. We must keep Markdown formatting. So final should be "**Move Field Up (Pull Up Field)**". No code. Keep line breaks: There's just one line. So answer is that line.
...done thinking.

**Move Field Up (Pull Up Field)**

![](img/0_refactor-117.png)

Thinking...
The user wants to translate the Markdown: "同样也是消除重复代码。" This is a Chinese sentence meaning "It also eliminates duplicate code." So translation: "It also eliminates duplicate code." But maybe the context: "同样也是消除重复代码。" Could be "This also eliminates duplicate code." I'd keep as "It also eliminates duplicate code." Or "This also removes duplicate code." The best is "It also removes duplicate code." They didn't provide code. So just translate that sentence. The markdown is just that line. So output exactly that.
...done thinking.

It also eliminates duplicate code.

Thinking...
We need to translate the markdown text. It is a heading in Chinese: "**构造函数本体上移（Pull Up Constructor Body）**". The translation: "**Constructor Body Pull-Up (Pull Up Constructor Body)**" or "**Move Constructor Body Up (Pull Up Constructor Body)**". Let's see typical naming. The parentheses contain the English name: Pull Up Constructor Body. So we can keep that. The Chinese part "构造函数本体上移" can be translated to "Move Constructor Body Up". So final: "**Move Constructor Body Up (Pull Up Constructor Body)**". Must preserve markdown: double asterisks at beginning and end. So output: **Move Constructor Body Up (Pull Up Constructor Body)**.
...done thinking.

**Move Constructor Body Up (Pull Up Constructor Body)**

![](img/0_refactor-118.png)

Thinking...
We need translate into English. The sentence: "提炼各个子类函数中的重复部分至父类中，同样也是消除重复代码。" Means: "Extract the repeated parts from functions in each subclass into the parent class, also eliminating duplicate code." So translation: "Refactor the repeated sections from each subclass's functions into the parent class, thereby also eliminating duplicate code." Let's produce just Markdown.

No special formatting needed.
...done thinking.

Refactor the repeated parts of each subclass’s functions into the parent class, thereby eliminating duplicate code.

Thinking...
We just translate Chinese title to English. Keep Markdown. The text: "**函数下移（Push Down Method）**". Should be "**Push Down Method (Function Push Down)**" maybe. The phrase "函数下移" means "Method Push Down". Usually English is "Push Down Method". But the original already includes English in parentheses. Maybe translate as "**Push Down Method (Function Push Down)**". But keep parentheses? In original, the Chinese is inside parentheses: "(Push Down Method)". So the English is outside. They want translation of the whole Markdown. So we convert Chinese inside to English. So "**Push Down Method (Push Down Method)**" would duplicate. Might want "**Push Down Method (Method Push Down)**". Actually Chinese meaning: "函数下移" is "Push Down Method" where method means function. So English translation: "**Push Down Method (Method Push Down)**". The original had "函数下移（Push Down Method）" meaning Chinese then English. So we translate to English: maybe "**Push Down Method (Push Down Method)**" but that's redundant. Could be "**Push Down Method (Method Push Down)**" to maintain order. I'll choose "**Push Down Method (Method Push Down)**".

Also preserve formatting. No code blocks. So final answer.
...done thinking.

**Push Down Method (Method Push Down)**

![](img/0_refactor-119.png)

Thinking...
We just translate the Chinese text into English. The markdown has only a paragraph. We keep structure. So produce:

"If a function in the superclass only concerns one (or a few) subclasses, it's best to move it out of the parent class and into the subclass that really cares about it."

Yes. Ensure same line breaks.
...done thinking.

If a function in the superclass only concerns one (or a few) subclasses, it's best to move it out of the parent class and into the subclass that really cares about it.

Thinking...
We need to translate the given Markdown. The text is: "**字段下移（Push Down Field）**". It's bold. So translate to English: "**Push Down Field**". But we should keep the parentheses? The original includes both Chinese and English. Maybe we translate to "**Push Down Field**". But the instruction: "Translate the following Markdown into English." The content includes Chinese with translation. So maybe we should keep both? But the given text is already bilingual: Chinese and English in parentheses. The instruction likely expects translation of Chinese parts, but keep English parts. But if we translate the whole phrase into English, we might just output "**Push Down Field**". That removes Chinese. That seems correct.

Let's output that.
...done thinking.

**Push Down Field**

![](img/0_refactor-120.png)

Thinking...
We need to translate Chinese to English. The markdown content: "如果某个字段只被一个子类（或者一小部分子类）用到，就将其搬移到需要该字段的子类中。"

We must preserve markdown structure. There's no code blocks, no inline code. Just a sentence. We translate: "If a field is only used by one subclass (or a small subset of subclasses), move it to the subclass(es) that need it." Or similar.

We must preserve line breaks. The text is a single line. We can keep it as a single line paragraph.

Thus final output: "If a field is only used by one subclass (or a small number of subclasses), move it to the subclass that needs it." Or "If a field is only used by one subclass (or a small subset of subclasses), move it to the subclass(es) that require it."

We need to output only the translated markdown.
...done thinking.

If a field is only used by one subclass (or a small subset of subclasses), move it to the subclass that needs it.

Thinking...
We need to translate the given markdown into English. The text is:

**以子类取代类型码（Replace Type Code with Subclasses）**

They want translation into English but also include parentheses maybe? The rule: preserve markdown. So translate Chinese into English: "Replace Type Code with Subclasses". They already provided translation in parentheses. But we should produce English only. So we could produce:

**Replace Type Code with Subclasses**

But maybe they want the Chinese part removed. The phrase in parentheses indicates translation already provided. But instruction: Translate the following Markdown into English. So we should translate Chinese to English, while keeping existing English in parentheses. But if the parentheses already contain English translation, we might not need to duplicate. But keep as is? The instruction: "Translate the following Markdown into English." The content: "**以子类取代类型码（Replace Type Code with Subclasses）**". So translation: "**Replace Type Code with Subclasses**". But we could also keep the Chinese? It says translate into English; so remove Chinese. But maybe keep the parentheses translation as provided. But we should not alter the content of parentheses? The parentheses already contain English. The instruction says "Preserve Markdown structure and ordering." So we should keep formatting. So final answer:

**Replace Type Code with Subclasses**

We should not translate code blocks or inline code. Not relevant. Keep line breaks. So final.
...done thinking.

**Replace Type Code with Subclasses**

![](img/0_refactor-121.png)

Thinking...
We need to translate the markdown content from Chinese to English. The markdown: "可以用多态来处理条件逻辑，而不是根据不同的类型码采取不同的行为。"

That is a sentence: "You can use polymorphism to handle conditional logic, rather than taking different actions based on different type codes." Need to preserve markdown structure. There is no headings, no lists, no code. So just plain text. So output: "Polymorphism can be used to handle conditional logic instead of taking different actions based on different type codes." Or something similar. Ensure translation of "多态" to "polymorphism". So the final output.
...done thinking.

Polymorphism can be used to handle conditional logic instead of taking different actions based on different type codes.

Thinking...
We need to translate the markdown into English. The markdown content is: "有些字段或函数只对特定的类型码取值才有意义，子类的形式能更明确地表达数据与类型之间的关系。"

This is a sentence. Translate into English: "Some fields or functions are only meaningful for certain type codes; subclassing can more clearly express the relationship between data and type." Need to preserve markdown structure. The content doesn't have any markdown markup except plain text. So output the translated English sentence.

Return only translated markdown. So output: "Some fields or functions are only meaningful for certain type codes; using subclasses can more clearly express the relationship between data and type." Ensure line breaks same. There's only one line. Provide it.
...done thinking.

Some fields or functions are only meaningful for certain type codes; using subclasses can more clearly express the relationship between data and type.

Thinking...
The task: translate the given Markdown into English. The original has "**移除子类（Remove Subclass）**". So the English version should preserve the Markdown. The translation: "**Remove Subclass (Remove Subclass)**"? Actually the original is Chinese "移除子类" and then in parentheses "Remove Subclass". So maybe keep Chinese title and parentheses? The instruction: Translate into English. So we should translate the Chinese to English. But the original text contains English already inside parentheses. The entire phrase is "**移除子类（Remove Subclass）**". So we could translate to "**Remove Subclass (Remove Subclass)**"? That seems redundant. Maybe we should keep the English translation only: "**Remove Subclass**". But they might want the same style: "**Remove Subclass (Remove Subclass)**" is odd. So likely we keep only the English title: "**Remove Subclass**". But if we want to preserve the structure: "**Remove Subclass**". I'd do that.

Also note that the original has the Chinese title plus English in parentheses. So we translate the Chinese part: "Remove Subclass" in parentheses already. So we can produce "**Remove Subclass**". That meets translation. Or "**Remove Subclass (Remove Subclass)**" would duplicate. I'd choose "**Remove Subclass**".

Thus output:

**Remove Subclass**

No other changes.
...done thinking.

**Remove Subclass**

![](img/0_refactor-122.png)

Thinking...
The input is Chinese: "如果子类的用处太少，可以移除子类，将替换为父类的一个字段。"

We need to translate into English, preserving markdown structure and ordering. There's no markdown structure except the sentence. So output: "If the subclass is rarely used, it can be removed and replaced by a field in the parent class." or "If the subclass has very little use, you can remove it and replace it with a field in the parent class."

Return only translated markdown. So just the sentence in English. Keep line breaks: it's a single line. Return only that line.

Let's produce: "If a subclass has very little use, it can be removed and replaced with a field in the parent class."
...done thinking.

If a subclass has very little use, it can be removed and replaced with a field in the parent class.

Thinking...
The user wants the translation of the Markdown into English. The content is:

```
**提炼超类（Extract Superclass）**
```

We need to translate "提炼超类" into English. "提炼" means "refine" or "extract". The parenthetical "Extract Superclass" is already in English. So we can translate the Chinese part: "提炼超类" probably means "Extract Superclass". The parentheses already have the English. So we might translate to "**Extract Superclass**". But there is already the English inside parentheses: "Extract Superclass". But the translation might be "Refine Superclass (Extract Superclass)". However, the user asked to preserve Markdown. The original has "**提炼超类（Extract Superclass）**". We can translate the Chinese to English, keep the English inside parentheses? Possibly we want "**Extract Superclass (Extract Superclass)**"? That duplicates. Maybe we remove the Chinese part and keep the English inside parentheses. The best translation would be "**Extract Superclass**". But we might keep the parentheses as original: "**提炼超类（Extract Superclass）**" -> "**Extract Superclass (Extract Superclass)**"? That seems redundant. Usually we translate the Chinese part: "提炼超类" -> "Extract Superclass". So the final would be "**Extract Superclass (Extract Superclass)**"? But we can remove parentheses: "**Extract Superclass**". The instructions: "Translate the following Markdown into English." So we need to translate everything into English. So we remove Chinese. The only Chinese is "提炼超类". So we translate to "Extract Superclass". The parentheses already contain English, so we might keep that? But we should keep the parentheses for clarity: "**Extract Superclass (Extract Superclass)**" but that seems odd. Instead we might keep the translation and also keep the original English? But that duplicates.

Better: "**Extract Superclass**". Probably that's what they'd want. But to be safe, we could keep parentheses: "**Extract Superclass (Extract Superclass)**" but that duplicates. The rule: "Do NOT alter URLs, links, or image paths." Not relevant. We need to preserve Markdown structure. The only markup is the bold. So we output "**Extract Superclass**".

Let's produce that.
...done thinking.

**Extract Superclass**

![](img/0_refactor-123.png)

Thinking...
The user: "You are a professional technical translator. Translate the following Markdown into English. Rules: - Preserve Markdown structure and ordering. - Do NOT translate code blocks (```) or inline code in backticks. - Do NOT alter URLs, links, or image paths. - Keep line breaks as much as possible. Return ONLY translated Markdown.

Markdown:
目的在于把重复的行为收拢一处。"

We need to translate that sentence into English. The sentence is Chinese: "目的在于把重复的行为收拢一处。" That means "The purpose is to consolidate repetitive actions into one place." So output: "The purpose is to bring repetitive actions together in one place." Probably keep exactly. It's just one line. So output: The purpose is to bring repetitive actions together in one place. Let's produce that.
...done thinking.

The purpose is to bring repetitive actions together in one place.

Thinking...
We need to translate Chinese to English. Title: "**折叠继承体系（Collapse Hierarchy）**". We translate the Chinese part: "折叠继承体系" to "Collapse Hierarchy". The parenthesis part already says (Collapse Hierarchy). So translation could be "**Collapse Hierarchy (Collapse Hierarchy)**" but that duplicates. The instruction: "Translate the following Markdown into English." So likely we translate Chinese into English but keep parentheses same? In original, parentheses contains the English translation. Actually original contains both Chinese and English? It says "**折叠继承体系（Collapse Hierarchy）**". The English translation is already there. So we need to translate to English, removing Chinese? So output should be "**Collapse Hierarchy**"? But the parentheses with English could be omitted? The instruction: "Translate the following Markdown into English." So we want English only. So we should translate to English only. So we produce "**Collapse Hierarchy**". That is probably the desired output.
...done thinking.

**Collapse Hierarchy**

![](/img/0_refactor-124.png)

Thinking...
We need to translate the given Markdown into English. The markdown is a short Chinese text: "随着继承体系的演化，有时会发现一个类与其父类差别不大，此时可以把父类和子类合并起来。"

Translate: "As the inheritance hierarchy evolves, sometimes you may find that a subclass is not much different from its parent class; at that time you can merge the parent and child classes."

We need to preserve Markdown structure and ordering, but there is no markdown elements besides text. So just output the English translation.

Return ONLY translated Markdown.

Thus final: "As the inheritance hierarchy evolves, sometimes you find that a subclass differs little from its parent class; at that point, you can merge the parent and child classes."
...done thinking.

As the inheritance hierarchy evolves, you may sometimes find that a subclass differs little from its parent class; at that point, you can merge the parent and child classes.

Thinking...
We just translate: "**以委托取代子类（Replace Subclass with Delegate）**" into English. So bold with translation. Keep Markdown structure. It becomes "**Replace Subclass with Delegate**". Or might include the parentheses: "Replace Subclass with Delegate". The Chinese part should be replaced by English. The parentheses part "（Replace Subclass with Delegate）" is originally Chinese with English inside parentheses. The translation could be "**Replace Subclass with Delegate**". Should we translate the Chinese phrase? Yes. So the entire bold phrase should be replaced with the English title. The parentheses part may be removed or just keep "Replace Subclass with Delegate" without parentheses. The instructions: "Translate the following Markdown into English." So we translate all Chinese. So we output:

**Replace Subclass with Delegate**

That's all.
...done thinking.

**Replace Subclass with Delegate**

![](/img/0_refactor-125.png)

![](/img/0_refactor-126.png)

Thinking...
We need to translate Chinese to English. The content: "与继承关系相比，使用委托（即组合）关系时接口更清晰、耦合更少。" Means: "Compared with inheritance, using delegation (i.e., composition) results in a clearer interface and less coupling." Keep Markdown; but it's just a single paragraph. So output translated.
...done thinking.

Compared with inheritance, using delegation (i.e., composition) results in a clearer interface and less coupling.

Thinking...
We need to translate given Markdown: "**以委托取代超类（Replace Superclass with Delegate）**" into English. It likely should be: "**Replace Superclass with Delegate**". The Chinese is "以委托取代超类". So translation: "**Replace Superclass with Delegate**". The parentheses already include the English phrase; but maybe keep that as is? The original has "(Replace Superclass with Delegate)" after the Chinese. But we should translate the whole heading. Probably keep parentheses? The rule: preserve Markdown structure. So heading is bold. We can translate Chinese part to English, leaving parentheses? Might combine: "**Replace Superclass with Delegate**". We can drop Chinese part. But parentheses likely redundant. Could just produce "**Replace Superclass with Delegate**". That is straightforward. Let's produce that.
...done thinking.

**Replace Superclass with Delegate**

![](/img/0_refactor-37.png)

Thinking...
We need to translate "以组合取代继承。" into English. It's a Chinese sentence meaning "Use composition instead of inheritance." Should keep Markdown structure. The text is just a line. Should return the English translation. Ensure not to alter URLs or code. There's none. Just a single sentence. So final output: "Use composition instead of inheritance."
...done thinking.

Use composition instead of inheritance.

Thinking...
We need to translate the provided Markdown into English, preserving structure, not translating code blocks or inline code, but there are no code blocks. The text: Chinese paragraphs. We need to produce English translation.

Original:

一个经典的误用继承的例子：让栈（stack）继承列表（list）。这个想法的出发点是想复用列表类的数据存储和操作能力。虽说复用是一件好事，但这个继承关系有问题：列表类的所有操作都会出现在栈类的接口上，然而其中大部分操作对一个栈来说并不适用。更好的做法应该是把列表作为栈的字段，把必要的操作委派给列表就行了。

Translate to English:

A classic example of misusing inheritance: letting a stack inherit from a list. The idea behind this is to reuse the data storage and operation capabilities of the list class. While reuse is a good thing, this inheritance relationship has problems: all operations of the list class will appear in the stack class's interface, yet most of those operations are not applicable to a stack. A better approach would be to make the list a field of the stack and delegate only the necessary operations to it.

We should keep Markdown structure: just paragraph. So we output the translated text.

Ensure no code. Good.

Return only translated Markdown.
...done thinking.

A classic example of misusing inheritance: letting a stack inherit from a list. The idea behind this is to reuse the data storage and operational capabilities of the list class. While reuse is a good thing, this inheritance relationship has problems: all operations of the list class will appear in the stack class's interface, yet most of those operations are not applicable to a stack. A better approach would be to make the list a field of the stack and delegate only the necessary operations to it.

Thinking...
The user provides a markdown snippet with Chinese text. They want it translated to English. Rules: preserve markdown, no code blocks. The snippet: **所以，如果超类的一些函数对子类并不适用，就说明我不应该通过继承来获得超类的功能。** So translate: "**So, if some functions of the superclass are not applicable to the subclass, it means I should not obtain the superclass's functionality through inheritance.**" Ensure bold formatting. So output: **So, if some functions of the superclass are not applicable to the subclass, it means I should not obtain the superclass's functionality through inheritance.** No extra. Return only that.
...done thinking.

**So, if some functions of the superclass are not applicable to the subclass, it means I should not obtain the superclass's functionality through inheritance.**

Thinking...
We need to translate the given Markdown. The text is Chinese. It says:

"同时也要避免走弯路：完全避免使用继承，如果符合继承关系的语义条件（超类的所有方法都适用于子类，子类的所有实例都是超类的实例），那么继承是一种简洁又高效的复用机制。"

We need to preserve Markdown structure and ordering. There's no special markdown elements except maybe a line. The text might be within a paragraph. The original is a single paragraph. So we produce the same structure but translated into English:

"Also, avoid taking a detour: completely avoid using inheritance. If the semantic conditions of an inheritance relationship are met (all methods of the superclass apply to the subclass, all instances of the subclass are instances of the superclass), then inheritance is a concise and efficient reuse mechanism."

We need to keep line breaks. There's no code. So just translate the paragraph.

Return only translated markdown. Let's preserve line breaks. The original had maybe a line break? It might be a single paragraph. We'll output same.

Let's produce:

"At the same time, avoid taking a detour: completely avoid using inheritance. If the semantic conditions of an inheritance relationship are met (all methods of the superclass apply to the subclass, and all instances of the subclass are instances of the superclass), then inheritance is a concise and efficient reuse mechanism."

Ok.
...done thinking.

Also, avoid taking a detour: completely avoid using inheritance. If the semantic conditions of an inheritance relationship are met (all methods of the superclass apply to the subclass, and all instances of the subclass are instances of the superclass), then inheritance is a concise and efficient reuse mechanism.

Thinking...
We need to translate Chinese to English, preserve Markdown structure. The text is:

"建议：首先（尽量）使用继承，如果发现继承有问题，再使用以委托取代超类。"

It is a suggestion. The translation: "Recommendation: First (as much as possible) use inheritance; if inheritance causes problems, then replace the superclass with delegation." The Chinese includes parentheses: "(尽量)" meaning "as much as possible." Also "以委托取代超类" means "use delegation to replace the superclass." So translation: "Suggestion: First (as much as possible) use inheritance; if inheritance has problems, then use delegation to replace the superclass." We might phrase: "Suggestion: First (as much as possible) use inheritance; if inheritance proves problematic, then replace the superclass with delegation."

Let's produce Markdown: the original text is not a code block, just a paragraph. So we output:

Suggestion: First (as much as possible) use inheritance; if inheritance has problems, then use delegation to replace the superclass. (We can keep the colon after Suggestion.)

We preserve line breaks: There is one line. So final output.

...done thinking.

Suggestion: First (as much as possible) use inheritance; if inheritance has problems, then replace the superclass with delegation.

