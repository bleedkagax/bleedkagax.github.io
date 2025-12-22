---
title: 重构（中文）
name: 0_refactor_zh
date: 2024-09-05
draft: false
tags:
  - Snippet
share: "true"
---
Thinking...
We just translate sentence. Keep markdown bold. Should be Chinese: "基本上，**重构就是在代码已写完后改进其设计**。" Ensure preserve markdown.
...done thinking.

基本上，**重构就是在代码已写完后改进其设计**。

Thinking...
We just translate text to Simplified Chinese. Keep Markdown. There's only a paragraph. No code fences or inline code. So translate: "If you want to add a feature to a program, but find that the code isn't easy to change due to a lack of good structure, refactor that program first so that it's easier to add the feature, and then add the feature."

Translate: "如果你想给程序添加一个功能，但由于缺乏良好的结构，代码不易修改，先对程序进行重构，使其更易于添加功能，然后再添加该功能。"

We must keep punctuation. Let's output in markdown. Probably just the paragraph.
...done thinking.

如果你想给程序添加一个功能，但由于缺乏良好的结构，代码不易修改，先对程序进行重构，使其更易于添加功能，然后再添加该功能。

Thinking...
We need to translate the given Markdown to Simplified Chinese, preserving structure. The content: "It is the change in **requirements** that makes refactoring necessary." So we translate to Chinese. Use bold for requirements remains **. So result: "正是 **requirements** 的变化使得重构变得必要。" But we must preserve code fences? Not needed. No code fences. So output that line. We keep markdown: maybe same paragraph. So output:

"It is the change in **requirements** that makes refactoring necessary." -> "正是 **requirements** 的变化使得重构变得必要。"

Return only the translated Markdown.
...done thinking.

正是 **requirements** 的变化使得重构变得必要。

Thinking...
We need to translate to Simplified Chinese, preserving markdown. The content: "The refactoring technique is to **modify the program at a tiny pace**. If you make a mistake, it's easy to spot it."

So translation: "重构技术是 **以微小的步伐修改程序**。如果犯错，很容易发现。"

Ensure bold remains same. So final markdown:

"The refactoring technique is to **modify the program at a tiny pace**. If you make a mistake, it's easy to spot it."

Translation:

"重构技术是 **以微小的步伐修改程序**。如果犯错，很容易发现。"

Return only that.
...done thinking.

重构技术是 **以微小的步伐修改程序**。如果犯错，很容易发现。

Thinking...
We need translate the given Markdown to Simplified Chinese. The text is:

"The test of good code is how easily one can modify it."

We need preserve Markdown structure exactly. There's no heading or list. It's just a sentence. We should translate to Chinese: "好代码的考验在于它能被多容易地修改。" That is correct.

We need to keep punctuation same? The original has period. Keep period.

Return only the translated Markdown.

Let's output: "好代码的考验在于它能被多容易地修改。"

But original had no special formatting. So just this line.

We need preserve line breaks. So output that sentence.

...done thinking.

好代码的考验在于它能被多容易地修改。

Thinking...
We need translate into Simplified Chinese. The content is just "To summarize:" presumably heading? Actually the markdown snippet shows: "To summarize:" maybe a bullet? It says "Markdown to translate:" then a line. The snippet is:

```
To summarize:
```

This is plain text. We need translate to Simplified Chinese, preserving markdown. So "To summarize:" -> "总结一下:" or "简而言之:".

Probably "To summarize:" => "总结一下:".

Return only that.
...done thinking.

总结一下:

Thinking...
We need to translate the Markdown to Simplified Chinese, preserving Markdown structure. The content is just a paragraph. We should translate the sentence but keep Markdown emphasis like **...** around "Smaller steps lead to faster progress" etc. Actually the original: "The key takeaways for efficient and organized refactoring are: **Smaller steps lead to faster progress**, keep your code in a working state forever, and small changes add up to a much better system design. Refactoring is not a “silver bullet”, but it can be considered a “silver tongs”, which can help you always have good control over your code. Refactoring is a tool."

We need to translate but keep **. The phrase inside ** is "Smaller steps lead to faster progress" should be translated? The instruction: preserve Markdown, but we translate the text. Should we translate inside emphasis? Yes. So we translate that phrase as well.

Also the quote marks are curly quotes. In Chinese translation, we can keep the same style or use “”. Probably keep same.

Thus output:

"高效有序重构的关键要点是：**更小的步骤会带来更快的进展**，始终保持代码处于可工作状态，并且小改动会累计成更好的系统设计。重构不是“银弹”，但它可以被视为“银镊子”，它能帮助你始终对代码保持良好控制。重构是一种工具。"

Make sure ** around the phrase.

Thus final.
...done thinking.

高效有序重构的关键要点是：**更小的步骤会带来更快的进展**，始终保持代码处于可工作状态，并且小改动会累计成更好的系统设计。重构不是“银弹”，但它可以被视为“银镊子”，它能帮助你始终对代码保持良好控制。重构是一种工具。

Thinking...
We have to translate only the markdown into Simplified Chinese, preserve markdown structure exactly. Title: "# **1. Bad taste in code**". So we need to translate "Bad taste in code" into Chinese: "代码中的不良风格" maybe "代码中的不良品味" or "代码中的糟糕味道". But the context: "Bad taste in code" might be "代码中的不良品味". We'll choose "代码中的不良品味". The Markdown: "# **1. Bad taste in code**" remains heading level 1 with bold. So translation: "# **1. 代码中的不良品味**". That should be it.

Return only the translated markdown.
...done thinking.

# **1. 代码中的不良品味**

Thinking...
We need translate the heading and bold text. Keep markdown. Output:

## 1\. **神秘名字**

Check Chinese: "Mysterious Name" => "神秘名字" or "神秘的名字". Keep same structure.

We must keep backslashes? It's "## 1\. **Mysterious Name**" The backslash before period is part of Markdown? It's an escape for period? Usually "## 1. **Mysterious Name**". But in original: "## 1\. **Mysterious Name**". The backslash escapes the period. Keep same.

We translate inside bold: "Mysterious Name". So "**神秘名字**".

Thus output: "## 1\. **神秘名字**".
...done thinking.

## 1\. **神秘名字**

Thinking...
We need translate into Simplified Chinese, preserve Markdown, but original text is plain text: "There are only two hard things in Computer Science: cache invalidation and naming things— Phil Karlt". We need to translate. Keep punctuation. Should we translate as "在计算机科学中只有两件难事：缓存失效和命名事物——菲尔·卡尔特" but proper noun "Phil Karlt" maybe keep as is. The rule: Keep proper nouns/product names when appropriate. So maybe keep "Phil Karlt" unchanged. The dash: "—". So translation: "在计算机科学中只有两件难事：缓存失效和命名事物——Phil Karlt". Let's keep punctuation. Also "cache invalidation" is "缓存失效". "naming things" is "命名事物". It's correct. Ensure spacing: After colon maybe space. The original: "There are only two hard things in Computer Science: cache invalidation and naming things— Phil Karlt". Note a space before Phil? It shows "— Phil Karlt". So after dash there's space. So translation: "在计算机科学中只有两件难事：缓存失效和命名事物—— Phil Karlt". Keep space after dash. So final.
...done thinking.

在计算机科学中只有两件难事：缓存失效和命名事物—— Phil Karlt

Thinking...
We need to translate to Simplified Chinese, preserve markdown structure. It's just a paragraph with no code. So translate.

"Naming is one of the two hardest things in programming. Because of this, renaming is probably the most commonly used refactoring technique, including changing function declarations (for renaming functions), variable renaming, and field renaming."

Translate: "命名是编程中两件最难的事之一。由于此，重命名可能是最常用的重构技术之一，包括更改函数声明（用于重命名函数）、变量重命名以及字段重命名。"

Ensure punctuation. That's it.
...done thinking.

命名是编程中两件最难的事之一。由于此，重命名可能是最常用的重构技术之一，包括更改函数声明（用于重命名函数）、变量重命名以及字段重命名。

Thinking...
We need to translate Markdown into Simplified Chinese, preserving structure. The heading "## 2\. **Global Data**" should become "## 2\. **全球数据**" presumably. We need to keep emphasis and bold. So translation: "全球数据". So final markdown: "## 2\. **全球数据**". Ensure same backslash escaping? The original had "## 2\. **Global Data**". The backslash before dot ensures formatting? In Markdown, "## 2. **Global Data**" works. The backslash escapes the dot? Not necessary. But keep as original: "## 2\. **Global Data**". So we should produce: "## 2\. **全球数据**". That is it.
...done thinking.

## 2\. **全球数据**

Thinking...
We just translate: "**Wrapped Variables**. It may not hurt to have a small amount…". Keep markdown bold. Ensure Chinese translation. Probably "**Wrapped Variables**" remains same? Maybe keep as is, but we could translate heading? The text is a sentence. So translation: "**Wrapped Variables**。拥有少量全局数据并不会有害，但数量越大，处理起来就越困难（指数级）。" Use Chinese punctuation. Ensure we keep bold. Keep period. The text: "It may not hurt to have a small amount of global data, but the larger the number, the exponentially more difficult it is to deal with." So translation: "拥有少量全局数据并不会有害，但数量越大，处理起来就越困难（指数级）." Use same formatting. So final markdown: **Wrapped Variables**。拥有少量全局数据并不会有害，但数量越大，处理起来就越困难（指数级）。 Use Chinese punctuation. Ensure no extra spaces. Let's output.
...done thinking.

**Wrapped Variables**。拥有少量全局数据并不会有害，但数量越大，处理起来就越困难（指数级）。

Thinking...
We need to translate the markdown heading "## 3. **Mutable Data**" to Simplified Chinese. Need to preserve Markdown structure. The heading is "## 3. **Mutable Data**". So we need to translate "Mutable Data" to Simplified Chinese. Likely "可变数据" or "可变数据" is correct. "Mutable Data" as a phrase can be "可变数据". So the result: "## 3. **可变数据**". Keep numbering "3." unchanged. So final answer: "## 3. **可变数据**". Ensure no extra commentary.
...done thinking.

## 3. **可变数据**

Thinking...
We need to translate to Simplified Chinese, preserving Markdown. The text: "Encapsulated variables can be **used to ensure that all data update operations are performed through very few functions**, making them easier to monitor and evolve."

We must preserve bold. So we translate the sentence but keep "**" around the bold part. The phrase "Encapsulated variables" maybe translate as "封装变量". "can be used to ensure that all data update operations are performed through very few functions" -> "可以用于确保所有数据更新操作都通过极少数函数完成". "making them easier to monitor and evolve" -> "从而更容易监控和演进". Need to preserve punctuation. The entire sentence: "封装变量可以用于确保所有数据更新操作都通过极少数函数完成，从而更容易监控和演进。"

But must keep "**" around the bold part. So we need to put "**" around the part "用于确保所有数据更新操作都通过极少数函数完成". Actually original bold part: "**used to ensure that all data update operations are performed through very few functions**". So we need to keep "**" around translated equivalent: "**用于确保所有数据更新操作都通过极少数函数完成**". Then the rest sentence: "封装变量可以**用于确保所有数据更新操作都通过极少数函数完成**，从而更容易监控和演进。"

We should keep the same punctuation: original had comma after bold? Actually original: "Encapsulated variables can be **used to ensure that all data update operations are performed through very few functions**, making them easier to monitor and evolve." There's a comma after bold part. So we replicate: "封装变量可以**用于确保所有数据更新操作都通过极少数函数完成**，从而更容易监控和演进。"

Thus final output: "封装变量可以**用于确保所有数据更新操作都通过极少数函数完成**，从而更容易监控和演进。"

Return only that.
...done thinking.

封装变量可以**用于确保所有数据更新操作都通过极少数函数完成**，从而更容易监控和演进。

Thinking...
We need to translate the given Markdown to Simplified Chinese, preserving formatting, no extra commentary.

The content: "**If a variable is used to store different things at different times, split variables can be used to split it into variables for their own…**" So we translate into Chinese. Bold markers remain. So:

**如果一个变量在不同时间用于存储不同的内容，可以使用拆分变量，将其拆分成各自不同用途的变量，从而避免危险的更新操作**.

But we must preserve Markdown: **...**. So final output:

**如果一个变量在不同时间用于存储不同的内容，可以使用拆分变量将其拆分成各自不同用途的变量，从而避免危险的更新操作**.

Ensure punctuation: maybe add comma after 变量? The original: "split variables can be used to split it into variables for their own different purposes". Chinese translation: "拆分变量可以将其拆分成各自不同用途的变量". Good.

We keep bold. So final answer.
...done thinking.

**如果一个变量在不同时间用于存储不同的内容，可以使用拆分变量将其拆分成各自不同用途的变量，从而避免危险的更新操作**

Thinking...
We need to translate the given Markdown text into Simplified Chinese. The text: "Use move statements and refine functions to try to move logic out of the code that handles update operations, separating code that has no side effects from code that performs data update operations."

We need preserve Markdown structure. There is just a single sentence. No headings or lists. It's plain text. So we just translate. "Use move statements and refine functions to try to move logic out of the code that handles update operations, separating code that has no side effects from code that performs data update operations."

In Chinese: "使用 move 语句和 refine 函数尝试将逻辑移出处理更新操作的代码，将无副作用的代码与执行数据更新操作的代码分离。"

We need keep code fences or inline code? There are no code fences. But there are words 'move', 'refine', but they might be function names? The instruction says: Do NOT translate code fences or inline code spans wrapped in backticks. There's no backticks. But "move statements" might refer to a function. We might keep 'move' and 'refine' as is? The instruction says: "Keep proper nouns/product names when appropriate." They might be function names, so maybe we keep them as is. So "move 语句" might be "move 语句" or maybe "move 语句" in Chinese. Usually we'd keep "move" as is if it's a function. Let's keep "move" and "refine" as is. So "使用 move 语句和 refine 函数尝试将逻辑移出处理更新操作的代码，将无副作用的代码与执行数据更新操作的代码分离。"

Yes. That's the translation. No formatting needed. Just the translated line.
...done thinking.

使用 **move** 语句和 **refine** 函数尝试将逻辑移出处理更新操作的代码，将无副作用的代码与执行数据更新操作的代码分离。

Thinking...
We need to translate: "When designing APIs, you can use ** to separate query functions from modification functions**."

We must keep Markdown structure. The "**" are bold markup. In the original: "When designing APIs, you can use ** to separate query functions from modification functions**." Wait there is a missing content between the asterisks? It appears they intend to bold something but it's empty? Actually the original says: "you can use ** to separate query functions from modification functions**." So inside the asterisks is blank. Might be a mistake. Should we translate entire sentence preserving bold? But content inside bold is empty. We could preserve as is. So translation: "在设计 API 时，你可以使用 ** 来将查询函数与修改函数分离**." But inside bold is empty again. So maybe the translator will keep empty bold. That is okay. So produce Chinese. Provide only translated Markdown. Ensure bold markers stay. So final.
...done thinking.

在设计 API 时，你可以使用 ** 来将查询函数与修改函数分离。

Thinking...
We need to translate to Simplified Chinese. The instruction: preserve markdown structure. The sentence: "Use **Remove set-value functions** as early as possible to narrow the variable scope." Should translate to Chinese: "尽可能早地使用 **Remove set-value functions** 来缩小变量作用域。" But need to keep the bold formatting. The bold is **...**. Keep that. So final: "尽可能早地使用 **Remove set-value functions** 来缩小变量作用域。"

Thus output: that sentence.
...done thinking.

尽可能早地使用 **Remove set-value functions** 来缩小变量作用域。

Thinking...
We need to translate the given Markdown to Simplified Chinese, preserving structure. The content is:

```
## 4\. **Long Functions**
```

We must translate. "Long Functions" becomes "长函数" maybe. Also keep the heading and markdown.

So output:

```
## 4\. **长函数**
```

That's it.
...done thinking.

## 4\. **长函数**

Thinking...
We need to translate the given Markdown to Simplified Chinese. The Markdown is:

**Actively Decompose Functions.**

We need to preserve Markdown structure exactly, headings, lists, emphasis. There is bold emphasis around the sentence. So the output should be:

**积极拆解函数。**

We must keep the bold markers **. The Chinese translation: "积极拆解函数。" (Functions in Chinese: 函数). Also the phrase "Actively Decompose Functions." is imperative. "积极拆解函数" works.

Return only translated Markdown. So answer: **积极拆解函数。**
...done thinking.

**积极拆解函数。**

Thinking...
We need to translate the given Markdown to Simplified Chinese. The given content:

"Principle: **Whenever we feel that we need to explain something in a comment, we write what we need to explain in a separate function and name it after its purpose (not how it was implemented)**."

We need to preserve Markdown structure. The structure: "Principle:" is plain text. Then bold text: "**Whenever we feel that we need to explain something in a comment, we write what we need to explain in a separate function and name it after its purpose (not how it was implemented)**."

So we translate the whole sentence inside bold. The translation in Simplified Chinese:

"原则：**每当我们觉得需要在注释中解释某些内容时，我们就把需要解释的内容写在单独的函数中，并根据其用途命名，而不是根据实现方式**。"

But must preserve the bold markup: "**...**". So we produce:

"Principle: **...**" but "Principle:" can be translated too? The guidelines: translate the Markdown. We need to translate the entire content. So "Principle:" becomes "原则：". The colon maybe same. Then bold part translated.

Thus final Markdown:

原则：**每当我们觉得需要在注释中解释某些内容时，我们就把需要解释的内容写在单独的函数中，并根据其用途命名，而不是根据实现方式**。 Ensure the punctuation. The original had no period at end, but we can include. The original bold ends with "**". No period inside the bold. The text inside: "Whenever we feel that we need to explain something in a comment, we write what we need to explain in a separate function and name it after its purpose (not how it was implemented)". So translation inside bold ends with no period. We may add period after closing bold? The original didn't have period after closing bold. So keep consistent: after closing bold, we can optionally add a period. But guidelines: preserve structure exactly, not alter content. We can add a period or not? The original didn't have period. So we might not add a period. But the translation might naturally end with a period. We need to keep it as close to original. The original had no period after closing bold. So we keep no period after closing bold. But we may add a Chinese punctuation at the end? In Chinese, a period would be "。". If we don't add, the sentence ends abruptly. It's okay? The original may end at the closing bold. We might preserve that. Let's produce:

原则：**每当我们觉得需要在注释中解释某些内容时，我们就把需要解释的内容写在单独的函数中，并根据其用途命名，而不是根据实现方式**。

Note the period after closing bold. In the original there was none. But the entire line ends after closing bold. In our translation we put a period after closing bold, but it's extra punctuation. The guidelines: preserve Markdown structure exactly. We didn't alter the structure. We changed content but not the structure. The period is content. But does it alter meaning? It's minor. We could omit the period to be consistent. But Chinese often ends with a period. But to preserve original exactly, maybe we should not add. Let's omit.

Thus final:

原则：**每当我们觉得需要在注释中解释某些内容时，我们就把需要解释的内容写在单独的函数中，并根据其用途命名，而不是根据实现方式**。 Actually there's still a period after closing bold, but the original didn't. Let's remove the period:

原则：**每当我们觉得需要在注释中解释某些内容时，我们就把需要解释的内容写在单独的函数中，并根据其用途命名，而不是根据实现方式**. Wait we can't have a period after closing bold? In English they'd have no period. So to preserve, we don't add period. But maybe we should preserve Chinese punctuation. But guidelines: preserve Markdown structure, but not necessarily punctuation. But they didn't mention punctuation. The original didn't have a period; we should keep it. So final:

原则：**每当我们觉得需要在注释中解释某些内容时，我们就把需要解释的内容写在单独的函数中，并根据其用途命名，而不是根据实现方式**.

Yes. Done.
...done thinking.

原则：**每当我们觉得需要在注释中解释某些内容时，我们就把需要解释的内容写在单独的函数中，并根据其用途命名，而不是根据实现方式**.

Thinking...
We need to translate the given markdown into Simplified Chinese. It says "What kind of function is too long? More than 50 lines? More than 70 lines? It's not the length of the function that matters, it's the semantic distance between the “what” and “how” of the function."

We must preserve markdown structure exactly, but there's no headings or lists. Just paragraph(s). The content must be translated. Use Simplified Chinese. The quotation marks around "what" and "how" should remain. It's a paragraph. We can produce the Chinese translation.

"什么样的函数太长？超过50行？超过70行？重要的不是函数的长度，而是函数“what”和“how”之间的语义距离。"

But must preserve quotes: “what” and “how” should be preserved. We can use Chinese punctuation. They used curly quotes “ and ”. We'll keep them. So "函数“what”和“how”之间的语义距离". Keep that.

Thus final output: Chinese paragraph.

Let's output:

什么样的函数太长？超过50行？超过70行？重要的不是函数的长度，而是函数“what”和“how”之间的语义距离。
...done thinking.

什么样的函数太长？超过50行？超过70行？重要的不是函数的长度，而是函数“what”和“how”之间的语义距离。

Thinking...
We need translate into Simplified Chinese. Preserve markdown. So translation: "How do you determine which piece of code to refine? A good tip is to **look for comments. They usually indicate the semantic distance between what the code does and how it does it.**"

Simplified Chinese: "你怎么决定要优化哪一段代码？一个好建议是 **查看注释。它们通常会指出代码所做的事情与实现方式之间的语义距离。**"

Preserve bold. Markdown: **text** remains. Should we keep quotes? No. Just translate. The line break? The original had a question then a new line. We'll preserve same.

Return only translated markdown.
...done thinking.

How do you determine which piece of code to refine? A good tip is to **look for comments. They usually indicate the semantic distance between what the code does and how it does it.**

Thinking...
We need translate given markdown to Simplified Chinese. Preserve structure: **bold** etc. Should not translate code fences or inline code, but there is none. So just translate the sentence: "**Conditional expressions and loops often signal refinement as well**. Conditional expressions can be handled using decomposition conditional expressions."

So translation: "**条件表达式和循环通常也表明精炼**。条件表达式可以使用分解条件表达式来处理。"

Check Chinese grammar: "条件表达式和循环通常也表明精炼" maybe "条件表达式和循环往往也表示细致" but use "表明" is okay. "使用分解条件表达式来处理" maybe "使用分解的条件表达式来处理" but okay.

Thus produce: **条件表达式和循环通常也表明精炼**。条件表达式可以使用分解条件表达式来处理。

Return only translated markdown.
...done thinking.

**条件表达式和循环通常也表明精炼**。条件表达式可以使用分解条件表达式来处理。

Thinking...
We need translate into Simplified Chinese, preserving markdown. The text is bold: "**For huge switch statements, each branch should be turned into a separate function call by refining the function. If there are multiple...**". We translate the sentence: "For huge switch statements, each branch should be turned into a separate function call by refining the function. If there are multiple switch statements that branch selection based on the same condition, you should use replace conditional expressions with polymorphism." Into Chinese: "对于大型 switch 语句，每个分支应通过细化函数转换为单独的函数调用。如果有多个 switch 语句根据相同条件进行分支选择，应使用多态来替代条件表达式。" Ensure preserve markdown bold. So final: **对于大型 switch 语句，每个分支应通过细化函数转换为单独的函数调用。如果有多个 switch 语句根据相同条件进行分支选择，应使用多态来替代条件表达式。** Ensure no extra commentary.
...done thinking.

**对于大型 switch 语句，每个分支应通过细化函数转换为单独的函数调用。如果有多个 switch 语句根据相同条件进行分支选择，应使用多态来替代条件表达式。**

Thinking...
We need translate into Simplified Chinese, preserving markdown. So translate "**Loops and code within loops should be refined into a separate function**." -> "**循环和循环内部的代码应该提炼成单独的函数**." Next sentence: "If you find the distilled loop hard to name, it may be because it does several different things in it." -> "如果你发现提炼后的循环难以命名，可能是因为它在内部执行了几件不同的事情。" Next: "If this is the case, be brave and use a split loop to break it up into its own separate tasks." -> "如果是这种情况，请大胆使用拆分循环，将其拆分成独立的任务。"

We need preserve bold formatting. So all sentences with **. Each sentence maybe on separate line. The original had each sentence separated by a period; we can preserve each as separate line. The Markdown didn't have any heading etc. So produce the translated markdown. Let's do that.

...done thinking.

**循环和循环内部的代码应该提炼成单独的函数**。如果你发现提炼后的循环难以命名，可能是因为它在内部执行了几件不同的事情。若是这种情况，请大胆使用拆分循环，将其拆分成独立的任务。

Thinking...
We need to translate title and heading into Simplified Chinese. Keep Markdown structure. The heading: "## 5. **Long Parameter List**"

We translate "Long Parameter List" to "长参数列表" maybe. The numbering: "5." remains. Keep bold formatting. So: "## 5. **长参数列表**". That's it.
...done thinking.

## 5. **长参数列表**

Thinking...
We need translate into Simplified Chinese, preserving markdown. The given text: **If it is possible to launch a query on one parameter to get the value of another parameter, then this second parameter can be removed by replacing the parameter with a query.**

So bold text. Translate: "如果可以通过对一个参数发起查询来获取另一个参数的值，那么可以通过用查询替换该参数来移除第二个参数。"

Ensure bold markers preserved: ** ... **. No code. So final output is the translated Markdown.
...done thinking.

**如果可以通过对一个参数发起查询来获取另一个参数的值，那么可以通过用查询替换该参数来移除第二个参数。**

Thinking...
We need to translate the given Markdown into Simplified Chinese while preserving structure. The text:

"If you find yourself pulling a lot of data items out of an existing data structure, consider **Using the Keep Objects Intact technique to pass directly into the original data structure**. **If there are several parameters that always appear at the same time, you can combine them into a single object** by introducing a parameter object."

We need to keep bold formatting (double asterisks). We cannot translate code fences or inline code spans. There are no code fences or inline code. Just plain text with bold.

So translation: "如果你发现自己正在从现有的数据结构中提取大量数据项，请考虑 **使用保持对象完整技术（Keep Objects Intact）直接传递到原始数据结构**。 **如果有多个参数总是一起出现，你可以通过引入一个参数对象将它们合并为一个对象**。"

Need to preserve the exact same punctuation? The original has "Consider **Using the Keep Objects Intact technique to pass directly into the original data structure**." The Chinese translation may use same punctuation. Ensure double asterisks remain. The sentence "If there are several parameters that always appear at the same time, you can combine them into a single object by introducing a parameter object." becomes Chinese.

Thus final output.
...done thinking.

如果你发现自己正在从现有的数据结构中提取大量数据项，请考虑 **使用保持对象完整技术（Keep Objects Intact）直接传递到原始数据结构**。 **如果有多个参数总是一起出现，你可以通过引入一个参数对象将它们合并为一个对象**。

Thinking...
We need to translate the given Markdown text into Simplified Chinese, preserving structure. The text: "If a parameter is used as a flag to distinguish the behavior of a function, remove the flag parameter."

No markdown syntax. Just a sentence. Translate to Simplified Chinese: "如果一个参数被用作标志来区分函数的行为，则移除该标志参数。"

Need to keep punctuation as Chinese. Use period.

Return only the translated Markdown. No other commentary.
...done thinking.

如果一个参数被用作标志来区分函数的行为，则移除该标志参数。

Thinking...
We need to translate to Simplified Chinese. Preserve Markdown structure: heading? It's bold text. So "**Using classes can effectively shorten the argument list**." => "**使用类可以有效缩短参数列表**". Next sentence: "Introducing a class makes particular sense if multiple functions have the same few parameters." => "如果多个函数拥有相同的少量参数，引入一个类就特别有意义。" Next: "You can use functions combined into classes to make these common parameters into fields of this class." => "你可以将这些函数组合到类中，将这些公共参数变为该类的字段。" Ensure no code fences or inline code spans. None. Return only the translated Markdown. Ensure proper punctuation. Let's craft.

...done thinking.

**使用类可以有效缩短参数列表**。如果多个函数拥有相同的少量参数，引入一个类就特别有意义。你可以将这些函数组合到类中，将这些公共参数变为该类的字段。

Thinking...
We just translate heading: "## 6. **Shotgun Surgery**" to Simplified Chinese. Must preserve Markdown structure, so keep "## 6. **Shotgun Surgery**" but translate the content inside the heading. The asterisks denote emphasis. So we keep "## 6. **Shot枪手手术**"? Wait translation: "Shotgun Surgery" in software engineering context refers to "散弹式手术" or "枪炮式手术"? In Chinese, "Shotgun Surgery" is usually translated as "枪管手术" no, it's a software design smell: "散弹式修改" maybe? Actually the term "Shotgun Surgery" is often translated as "枪口手术" or "散弹式手术". Let me check typical Chinese translation: In D. Thomas and A. L. Brown's book? It's a software design smell: "散弹式修改". Quick memory: In Chinese, "Shotgun Surgery" is "散弹式修改" or "散弹手术". Many Chinese references use "散弹式修改". The heading uses "Shotgun Surgery" as a term. We need to translate that to Chinese. Let's choose "散弹式手术" or "散弹式修改". Since heading is a technical term, maybe "散弹式手术" because "Surgery" is used. But many resources call it "散弹式修改" or "枪管手术" but the term "Shotgun Surgery" is a design smell. I'll use "散弹式修改" maybe. But heading has "Shotgun Surgery" which literally translates to "散弹式手术". I think "散弹式手术" is correct. So translation: "## 6. **散弹式手术**".

Need to keep heading number and formatting. So final: "## 6. **散弹式手术**".
...done thinking.

## 6. **散弹式手术**

Thinking...
We need to translate the given Markdown. The text is "**If you have to make many small modifications within many different classes every time...**"

We must keep the Markdown bold markers. The translation into Simplified Chinese should preserve formatting. So we keep "**" around the sentence.

Let's translate: "If you have to make many small modifications within many different classes every time you encounter some kind of change, the bad taste you're facing is Shotgun Surgery."

Simplified Chinese: "如果每次遇到某种更改时，你必须在许多不同的类中进行许多小的修改，那么你所面临的难点就是“枪炮式手术”(Shotgun Surgery)。"

We need to keep the code fences or inline code? Not applicable. No code fences. Keep bold. No links.

Thus output:

**如果每次遇到某种更改时，你必须在许多不同的类中进行许多小的修改，那么你所面临的难点就是“枪炮式手术”(Shotgun Surgery)。**

But the original had no quotes or parentheses; but we can incorporate them. Should we preserve the parentheses? It says keep links or image paths. There's no link. We can just translate the sentence. Should we keep parentheses? It's part of sentence. The phrase "Shotgun Surgery" is a term; maybe keep it as is. The translation could be: "**如果每次遇到某种更改时，你必须在许多不同的类中做许多小的修改，那么你所面临的难点就是 Shotgun Surgery。**"

We can choose to keep the English term as is. Let's do that.

Thus final:

**如果每次遇到某种更改时，你必须在许多不同的类中做许多小的修改，那么你所面临的难点就是 Shotgun Surgery。**
...done thinking.

**如果每次遇到某种更改时，你必须在许多不同的类中做许多小的修改，那么你所面临的难点就是 Shotgun Surgery。**

Thinking...
We need to translate to Simplified Chinese, preserving Markdown. We must not translate code fences or inline code spans. There's no code fences. The text: "**Moving functions and moving fields puts all the code that needs to be modified into the same module**. If **there are a lot of functions that operate on similar data, you can use a combination of functions into a class**. If some functions function to transform or enrich data structures, you can use functions to combine into transformations. If the output of some functions can be combined and made available to a piece of logic that specializes in using the results of those computations, this is often useful **Split Stage (e.g., parsing an order before calculating the price of an order**)**."

We need to preserve bold markers. So the entire sentence in Chinese. Also note the parentheses part: "(e.g., parsing an order before calculating the price of an order" - there's missing closing parenthesis? The original text: "**Split Stage (e.g., parsing an order before calculating the price of an order**)**." There might be a formatting issue. But we must preserve. So we keep same formatting. So Chinese translation:

**移动函数和移动字段将所有需要修改的代码集中在同一模块**。如果 **有很多函数作用于相似的数据，你可以把这些函数组合成一个类**。如果有些函数用于转换或丰富数据结构，你可以将函数组合成转换。若某些函数的输出可以合并并提供给专门使用这些计算结果的逻辑，这通常很有用 **Split Stage (例如，先解析订单再计算订单价格**)**。

But need to keep bold for "Split Stage". The bold part includes the parentheses. So keep bold markers: **Split Stage (例如，先解析订单再计算订单价格**)**. But the original had "**Split Stage (e.g., parsing an order before calculating the price of an order**)**." So keep bold for the whole phrase including parentheses. We'll translate inside parentheses: "(e.g., parsing an order before calculating the price of an order" to "(例如，先解析订单再计算订单价格". Need closing parenthesis? The original didn't have closing ), but we can keep same structure. But we can add closing parenthesis inside translation? We should preserve original structure: The original had open parenthesis after Split Stage and then bold continues until closing ** before closing **? Wait: "**Split Stage (e.g., parsing an order before calculating the price of an order**)**." So there is "**Split Stage (e.g., parsing an order before calculating the price of an order**)**." There are two asterisks before "Split Stage" and two after "order**)**." Actually it is "**Split Stage (e.g., parsing an order before calculating the price of an order**)**." So it opens bold before Split Stage, includes everything until the first ** before the closing parentheses? Let's parse: The first "**" before Split Stage starts bold. Then "Split Stage (e.g., parsing an order before calculating the price of an order" then "**)**." Wait: after "order" there's **)**. So two asterisks then close parenthesis then period. That seems wrong because bold should close before parenthesis. But the markdown may be miswritten. For safety, we should keep the same exact punctuation: "**Split Stage (e.g., parsing an order before calculating the price of an order**)**." So we keep exactly that. We will translate inside but preserve same markers.

Thus translation: "**Split Stage (例如，先解析订单再计算订单价格**)**."

Yes.

Also earlier translation of "moving functions and moving fields puts all the code that needs to be modified into the same module". Should keep bold markers exactly: **...**. So translation inside that must be bold. So we will put Chinese inside bold markers: **移动函数和移动字段将所有需要修改的代码集中到同一模块**.

Next sentence: If **there are a lot of functions that operate on similar data, you can use a combination of functions into a class**. So bold: **有许多函数作用于相似的数据时，你可以将这些函数组合成一个类**.

Next: If some functions function to transform or enrich data structures, you can use functions to combine into transformations. That is not bold. Translate to Chinese: 如果有些函数用于转换或丰富数据结构，你可以将它们组合成转换。 Keep same structure.

Next: If the output of some functions can be combined and made available to a piece of logic that specializes in using the results of those computations, this is often useful Split Stage (e.g., parsing an order before calculating the price of an order). We translate: 如果某些函数的输出可以合并并提供给专门使用这些计算结果的逻辑，这通常很有用 **Split Stage (例如，先解析订单再计算订单价格**)**. But ensure we keep the period after the last **)**. So we will put period after that.

Thus final translated markdown.
...done thinking.

**移动函数和移动字段将所有需要修改的代码集中到同一模块**。如果 **有许多函数作用于相似的数据时，你可以将这些函数组合成一个类**。如果有些函数用于转换或丰富数据结构，你可以将它们组合成转换。若某些函数的输出可以合并并提供给专门使用这些计算结果的逻辑，这通常很有用 **Split Stage (例如，先解析订单再计算订单价格**)**。

Thinking...
We need to translate into Simplified Chinese, preserving markdown structure. The text is:

"A common strategy is to use refactoring related to inlining ------ such as **inline functions** (or inline classes) ------ to yank logic that shouldn't be scattered back into one place**. After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks."

We need to keep headings, lists, emphasis. There are no headings or lists. The text contains **inline functions**. That must remain **inline functions**? Should we keep the asterisks? We keep them because they are part of markdown emphasis. We shouldn't translate them. So we keep the asterisks but the content inside we translate? Wait the phrase inside the asterisks is "inline functions". Should we translate the words inside? They said: "Keep proper nouns/product names when appropriate." "inline functions" is not a proper noun, it's a concept. So we should translate inside? But the rule: Do NOT translate code fences or inline code spans wrapped in backticks. But this is emphasis, not inline code. The asterisks are markdown emphasis, not backticks. So we can translate the words inside the emphasis. So we translate "inline functions" to "内联函数". The same for "inline classes" to "内联类". We need to preserve emphasis, so we write **内联函数** and (or **内联类**) but maintain parentheses? The original: **inline functions** (or inline classes). Should translate to **内联函数** (or 内联类). Wait we might keep parentheses and the word 'or' translated? "or" is just English; we translate to "或". So we should translate "or" to "或". So the part becomes **内联函数** (或内联类). But we might want to keep the parentheses around? Yes keep parentheses. The translation: **内联函数** (或内联类).

Also the phrase "yank logic that shouldn't be scattered back into one place" we need to translate.

The text: "yank logic that shouldn't be scattered back into one place". Maybe "提取不应该被散布的逻辑并集中到一个位置". "yank" is slang for "pull out". So we can translate as "提取不应被散布的逻辑并集中回一个位置".

The rest: "After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks." Translate: "完成内联后，你可能会注意到一个过长的函数或过大的类，然后使用与精炼相关的重构技术将其拆分成更合理的块。"

Now, we also need to keep the dashes? The original uses "------" to separate parts. This might be used as a visual separator. We need to preserve them exactly. So we keep "------" exactly as is. Also there is "------" again. We need to keep them. So the text will look like:

"A common strategy is to use refactoring related to inlining ------ such as **inline functions** (or inline classes) ------ to yank logic that shouldn't be scattered back into one place**."

Wait there's an extra "**" at the end after place**. In original: "place**." Actually original has "**" after place, then period. That is an error: maybe they intended to emphasize "place" but forgot closing. The "**" appears after place. It's like "**place**." but they had an unmatched "**"? The original: "... into one place**." Actually they had one opening ** before inline functions, closed after inline functions, then after "place**." there's one opening **? Actually it's "**place**." They open with ** at inline functions, close after. Then they open again at place and close? Wait they didn't close. Let's examine: "... back into one place**." There's only "**" after place but not before. So it appears they intended to open emphasis at inline functions but closed after, then at place they had an opening ** but didn't close? Let's parse: "such as **inline functions** (or inline classes) ------ to yank logic that shouldn't be scattered back into one place**." So after place** we see a ** but no closing. So maybe a typo. We need to preserve the markdown exactly? The instruction: "Preserve Markdown structure exactly". So we should keep the unmatched ** as is. That is part of the input. So we keep the unmatched **. When we translate inside the emphasis, we preserve the asterisks but we must keep the unmatched one. So we will have "**内联函数** (或内联类) ------ to yank logic that shouldn't be scattered back into one place**." Wait we still have the unmatched ** after place. So we need to produce that. Good.

Also there is no heading or list.

Now we need to ensure we don't translate code fences or inline code. There is no code fences. Inline code spans would be wrapped in backticks; none present.

Thus the final translation:

"A common strategy is to use refactoring related to inlining ------ such as **内联函数** (或内联类) ------ to yank logic that shouldn't be scattered back into one place**. After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks."

But we need to translate the rest. The rest is not inside asterisks. We translate it into Chinese.

So final:

"A common strategy is to use refactoring related to inlining ------ such as **内联函数** (或内联类) ------ to yank logic that shouldn't be scattered back into one place**. After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks."

Translates:

"A common strategy is to use refactoring related to inlining ------ such as **内联函数** (或内联类) ------ to yank logic that shouldn't be scattered back into one place**. After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks."

We should produce Chinese. So:

"A common strategy is to use refactoring related to inlining ------ such as **内联函数** (或内联类) ------ to yank logic that shouldn't be scattered back into one place**. After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks."

Translate:

"A common strategy is to use refactoring related to inlining ------ such as **内联函数** (或内联类) ------ to yank logic that shouldn't be scattered back into one place**. After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks."

Wait I'm repeating. I need to produce final Chinese. Let's write the entire paragraph:

"A common strategy is to use refactoring related to inlining ------ such as **inline functions** (or inline classes) ------ to yank logic that shouldn't be scattered back into one place**. After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks."

Translate:

"A common strategy is to use refactoring related to inlining ------ such as **内联函数** (或内联类) ------ to yank logic that shouldn't be scattered back into one place**. After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks."

We still haven't translated the second part. Let's translate fully:

"After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks."

=> "完成内联后，你可能会发现一个过长的函数或过大的类，然后使用与精炼相关的重构技术将其拆分成更合理的块。"

Now combine with the first sentence:

"A common strategy is to use refactoring related to inlining ------ such as **inline functions** (or inline classes) ------ to yank logic that shouldn't be scattered back into one place**. After you've finished inlining, you may smell an overly long function or overly large class, and then use refactoring techniques related to refinement to break it up into more sensible chunks."

So final Chinese:

"A common strategy is to use refactoring related to inlining ------ such as **内联函数** (或内联类) ------ to yank logic that shouldn't be scattered back into one place**. 完成内联后，你可能会发现一个过长的函数或过大的类，然后使用与精炼相关的重构技术将其拆分成更合理的块。"

We should keep the dashes and asterisks as is. Also we need to keep the original punctuation. So:

"A common strategy is to use refactoring related to inlining ------ such as **内联函数** (或内联类) ------ to yank logic that shouldn't be scattered back into one place**. 完成内联后，你可能会发现一个过长的函数或过大的类，然后使用与精炼相关的重构技术将其拆分成更合理的块。"

Wait the first part remains in English? The first sentence "A common strategy is to use refactoring related to inlining" etc. We translate entire first sentence into Chinese. So we need to translate the first sentence too. We currently have translated only part of it. Let's translate full first sentence.

"A common strategy is to use refactoring related to inlining ------ such as **inline functions** (or inline classes) ------ to yank logic that shouldn't be scattered back into one place**."

Translate:

"A common strategy is to use refactoring related to inlining ------ such as **inline functions** (or inline classes) ------ to yank logic that shouldn't be scattered back into one place**."

-> "一个常见的策略是使用与内联相关的重构 ------ 例如 **内联函数**（或内联类）------ 将不应被散布的逻辑提取并集中回一个位置**。"

But note we have to keep the unmatched ** after place. So we should end with "位置**。"

Thus final Chinese paragraph:

"一个常见的策略是使用与内联相关的重构 ------ 例如 **内联函数**（或内联类）------ 将不应被散布的逻辑提取并集中回一个位置**。完成内联后，你可能会发现一个过长的函数或过大的类，然后使用与精炼相关的重构技术将其拆分成更合理的块。"

Check punctuation: we replaced English punctuation with Chinese punctuation? But we keep original dashes etc. Use Chinese full-width punctuation for Chinese. We keep the dashes and asterisks. The period after Chinese punctuation should be a full-width period? We might keep as "." to preserve original? But it's okay. We need to preserve markdown structure; punctuation not part of markdown. We can convert to Chinese. It's fine.

But the asterisks around **inline functions** are markdown emphasis. In Chinese we should keep the asterisks. So **内联函数**.

The parentheses: (or inline classes) we translate to （或内联类）. That's fine.

Now ensure that we keep dashes "------". So:

"一个常见的策略是使用与内联相关的重构 ------ 例如 **内联函数**（或内联类）------ 将不应被散布的逻辑提取并集中回一个位置**。完成内联后，你可能会发现一个过长的函数或过大的类，然后使用与精炼相关的重构技术将其拆分成更合理的块。"

Also note that the second sentence starts with "完成内联后". Good.

We need to preserve the unmatched "**" after "位置". That is included.

Thus final answer.
...done thinking.

一个常见的策略是使用与内联相关的重构 ------ 例如 **内联函数**（或内联类）------ 将不应被散布的逻辑提取并集中回一个位置**。完成内联后，你可能会发现一个过长的函数或过大的类，然后使用与精炼相关的重构技术将其拆分成更合理的块。

Thinking...
We just translate heading: "## 7. **Comments**." into Chinese: "## 7. **评论**." Probably. Ensure preserve formatting: "## 7\. **Comments**." The dot after 7 maybe. In Chinese we could keep "## 7. **Comments**." But translate Comments to 评论. So "## 7. **评论**." The backslash before dot: "## 7\. **Comments**." In markdown, dot can be escaped. So we maintain same: "## 7\. **评论**." Let's output that.
...done thinking.

## 7\. **评论**.

Thinking...
We need to translate the given markdown into Simplified Chinese, preserving markdown structure. The text includes bold emphasis. The text:

**If you need comments to explain what a piece of code does, try refining the function**; **If the function has been refined but still needs ...**; **If you need comments to explain the specification ...**

We need to translate each bold phrase. The semicolons separate them. Ensure we preserve the bold markup. The translation in Chinese: "如果你需要注释来解释代码片段的作用，请尝试细化函数"; "如果函数已经被细化，但仍然需要注释来解释其行为，请尝试用对函数声明的更改来重命名它"; "如果你需要注释来解释某些系统需求的规范，请尝试引入断言。"

We must keep the punctuation exactly? The original had semicolons; we can keep them.

Also need to preserve the emphasis: ** ... **. In Chinese, we keep the same.

Return only the translated markdown.

Let's produce:

**如果你需要注释来解释代码片段的作用，请尝试细化函数**; **如果函数已经被细化，但仍然需要注释来解释其行为，请尝试用对函数声明的更改来重命名它**; **如果你需要注释来解释某些系统需求的规范，请尝试引入断言。**

Yes.
...done thinking.

**如果你需要注释来解释代码片段的作用，请尝试细化函数**; **如果函数已经被细化，但仍然需要注释来解释其行为，请尝试用对函数声明的更改来重命名它**; **如果你需要注释来解释某些系统需求的规范，请尝试引入断言。**

Thinking...
We just need translate that sentence into Simplified Chinese, preserving Markdown. The sentence is **When you feel the need...**. So output with bold markup preserved. So "**当你觉得有必要写注释时，先尝试重构并尽量让所有注释变得多余。**"

Yes. Ensure Markdown bold remains.
...done thinking.

**当你觉得有必要写注释时，先尝试重构并尽量让所有注释变得多余。**

Thinking...
We need to translate heading and text to Simplified Chinese. The original has a number 8. **Data Clumps**. So "## 8. **Data Clumps**." Translate to "## 8. **数据聚集**." or "数据块"? The term "Data Clumps" in software design refers to "数据聚集" or "数据块". In Chinese translation, often "数据聚集" or "数据块" or "数据团". I'd translate as "数据聚集". Keep emphasis and bold. So final output: "## 8. **数据聚集**." That's all.
...done thinking.

## 8. **数据聚集**.

Thinking...
We need to translate the sentence: "Data that always appears tied together really should have objects of their own." into Simplified Chinese, preserving markdown structure. The given text has no markdown headings or lists, just a sentence. So we output the translation as a sentence. Must not translate code fences, but none present. So just translate. "Data that always appears tied together really should have objects of their own." could be: "总是出现成组的数据真的应该有自己的对象。" or "经常一起出现的数据真的应该各自拥有自己的对象。" Let's produce a concise translation. We'll output exactly that sentence.
...done thinking.

总是一起出现的数据真的应该各自拥有自己的对象。

Thinking...
We just need to translate the heading. "## 9. Repeated Switches" -> "## 9\. 反复切换" maybe. Keep numbering and period. "Repeated Switches" could be "反复切换" or "重复切换". Use Simplified Chinese. The dot after 9 is part of Markdown heading. Should we escape the dot? In the source it's "## 9\. Repeated Switches". The backslash before dot escapes the dot? But we should preserve structure exactly. So we keep "## 9\. Repeated Switches" but translate "Repeated Switches" to Chinese. So "## 9\. 反复切换". Or "## 9\. 反复切换" maybe use "重复切换" but "反复" more natural. Let's use "## 9\. 反复切换". Ensure not to translate code fences; none present. So final answer.
...done thinking.

## 9\. 反复切换

Thinking...
We need to translate the given markdown to Simplified Chinese, preserving markdown structure. The given markdown is just a heading? The text is:

Polymorphism.

There's a period. It's a single line: "Polymorphism." Possibly considered a heading? It could be a paragraph. The instruction: preserve markdown structure exactly. So we have a paragraph "Polymorphism." We translate to Chinese: "多态性。" That is the translation.

Thus final output should be:

多态性。

But must preserve markdown: just a paragraph. So the output: "多态性。" with a newline? Probably exactly the translated line.
...done thinking.

多态性。

Thinking...
We need to translate "## 10. **Lazy Element" into Simplified Chinese, preserving markdown. So "## 10. **Lazy Element" -> "## 10. **Lazy Element" but Lazy Element maybe translated as "懒惰元素" or "懒元素". The original text: "## 10\. **Lazy Element". So we translate "Lazy Element" to Chinese, preserving emphasis. The asterisks around Lazy Element? Actually "**Lazy Element" indicates bold. So keep the asterisks. So translation: "## 10. **懒惰元素". But maybe "懒惰元素" is direct translation. Or "懒元素". Use "懒惰元素". So final: "## 10. **懒惰元素". No code fences, just translation. Let's output that.
...done thinking.

## 10. **懒惰元素

Thinking...
We need to translate to Simplified Chinese. Preserve markdown structure. The original is just a paragraph. No code fences. The paragraph: "As the refactoring progresses it gets smaller and smaller and the class ends up with only one function. Remove this class in time to use inline functions or inline classes."

Translate: "随着重构的进行，代码会变得越来越小，最终类只剩下一个函数。及时删除这个类，改用内联函数或内联类。" Use Chinese punctuation. Let's produce exactly same formatting: just the paragraph. No other changes.
...done thinking.

随着重构的进行，它会变得越来越小，最终类只剩下一个函数。及时删除这个类，改用内联函数或内联类。

Thinking...
We need to translate: "## 11\. **Refused Bequest**." into Simplified Chinese, preserving Markdown.

So "Refused Bequest" -> "拒绝的遗产" or "被拒绝的遗赠". Let's choose "拒绝的遗赠" maybe. Also include the numbering. The Markdown uses "## 11\. **Refused Bequest**." The period after 11. Keep the backticks? There's no code fences. Just a heading. So final output: "## 11\. **拒绝的遗赠**."

Yes.
...done thinking.

## 11\. **拒绝的遗赠**.

Thinking...
We need to translate the given Markdown to Simplified Chinese. The text: "Subclasses should inherit functions and data from the superclass."

We must preserve Markdown structure exactly. There's no headings or lists. Just a single sentence. So we just translate.

"Subclasses" -> "子类"

"should inherit functions and data" -> "应继承方法和数据"

"from the superclass." -> "来自超类。"

Thus translation: "子类应继承方法和数据来自超类。" But more natural: "子类应从超类继承方法和数据。" Let's keep simple.

We should preserve punctuation. So: "子类应从超类继承方法和数据。"

Return only the translated Markdown.

...done thinking.

子类应从超类继承方法和数据。

Thinking...
We need to translate to Simplified Chinese. Keep markdown. The content: "If you do not want to support the interface of the superclass, you should not be false to the inheritance system, and you should use delegates (using combinations instead of inheritance) instead of subclasses or delegates instead of superclasses to draw a line in the sand."

We need translate while preserving punctuation and meaning. "interface" probably means "接口". "inheritance system" -> "继承系统". "delegates" -> "委托" or "代理". "subclasses" -> "子类". "superclasses" -> "父类". "draw a line in the sand" -> "划定界限" or "划清界线". Also "using combinations instead of inheritance" -> "使用组合而非继承". The sentence is a bit odd; we keep meaning: "如果你不想支持超类的接口，你不应该违背继承系统，你应该使用委托（使用组合而不是继承）来代替子类，或者使用委托代替超类，以划定界限." Or: "你不应违背继承系统，而是应使用委托（即使用组合而非继承）来代替子类或用委托代替超类，划定界限。"

Let's craft translation:

如果你不想支持超类的接口，你不应该违背继承系统，而应该使用委托（即用组合代替继承）来代替子类，或者使用委托代替超类，以划定界限。

We need preserve Markdown. There's no markdown structure. It's a paragraph. So just translate.

Let's output.
...done thinking.

如果你不想支持超类的接口，你不应该违背继承系统，而应该使用委托（即用组合代替继承）来代替子类，或者使用委托代替超类，以划定界限。

Thinking...
We need to translate into Simplified Chinese. Keep Markdown structure. So heading # **2. First set of reconstructions**.

In Chinese, maybe "**2. 第一组重建**" but "First set of reconstructions" translation. So keep the asterisks as bold. Keep heading level.

So result: "# **2. 第一组重建**"

That's all.
...done thinking.

# **2. 第一组重建**

Thinking...
We need to translate to Simplified Chinese. Heading: "## 1. **Extract Function**". Keep markdown structure, so headings remain. We translate "Extract Function" to Chinese: "提取功能" or "抽取函数"? Likely "提取功能" as in "function extraction". Might be "提取函数". But "function" in programming context can be "函数". So "提取函数" is better. So heading: "## 1. **提取函数**". Ensure markdown same.

Return only that.
...done thinking.

## 1. **提取函数**

![](/img/0_refactor.png)

![](/img/0_refactor-1.png)

Thinking...
We need to translate the Markdown to Simplified Chinese while preserving structure, headings, lists, emphasis. The Markdown snippet is:

**Separate Intent from Implementation**: If you need to spend time browsing through a piece of code ... etc.

We must translate the text but keep the Markdown formatting: **bold**.

Also we need to keep any links or code fences. There is no code fences or links.

We must not translate code fences or inline code spans wrapped in backticks. None.

So translation:

**Separate Intent from Implementation**: -> **分离意图与实现**

Then the rest: "If you need to spend time browsing through a piece of code to figure out what it's actually doing, then you should distill it down to a function and name it according to what it does. Because most of the time you don't need to care about how the function accomplishes its purpose (that's what the function does inside)"

Translate into Chinese: "如果你需要花时间浏览一段代码来弄清楚它到底在做什么，那么你应该把它提炼成一个函数，并按其功能命名。因为大多数情况下，你不需要关心函数如何实现其目的（那就是函数内部所做的）。"

But ensure punctuation consistent. Also note we keep English phrase "Separate Intent from Implementation" is inside bold. We translated the phrase to Chinese but preserve **. So final:

**分离意图与实现**: 如果你需要花时间浏览一段代码来弄清楚它到底在做什么，那么你应该把它提炼成一个函数，并按其功能命名。因为大多数情况下，你不需要关心函数如何实现其目的（那就是函数内部所做的）。

Make sure the colon remains after bold. In original: **Separate Intent from Implementation**: If you need...

So we translate: **分离意图与实现**: 如果...

Return only translated markdown.

Let's craft final answer.
...done thinking.

**分离意图与实现**: 如果你需要花时间浏览一段代码来弄清楚它到底在做什么，那么你应该把它提炼成一个函数，并按其功能命名。因为大多数情况下，你不需要关心函数如何实现其目的（那就是函数内部所做的）。

Thinking...
We need to translate the text. The Markdown has no headings, just a paragraph. We must preserve structure. No code fences or inline code. So just translate "Good names: in a big function, a piece of code puts a comment that distills it into a function, and the comment often suggest[s] a good name." Ensure we preserve the colon after Good names. In Chinese we can translate as "好名字：在一个大函数里，某段代码会写一个注释，将其浓缩成一个函数，而这个注释往往会建议一个好的名字。" Let's produce that.
...done thinking.

Good names: 在一个大函数里，某段代码会写一个注释，将其浓缩成一个函数，而这个注释往往会建议一个好的名字。

Thinking...
The user wants the given Markdown to be translated into Simplified Chinese. The markdown is: 
```
**Practice***
```
Wait there are two asterisks at the end: "**Practice***". The first two asterisks open bold, then "Practice" then three asterisks close? Actually formatting: "**Practice***" seems like open bold, then "Practice", then "***" maybe italic? It might be a formatting error. But they want to preserve the Markdown structure exactly. So we need to translate "Practice" to Chinese: "练习". But need to preserve the formatting. So the translation should be: "**练习***". But that is ambiguous: do we keep the same number of asterisks? The original is "**Practice***". That is two asterisks at start, one at end? Wait let's count: "**Practice***" = 2 stars, "Practice", then 3 stars. That is odd. It might be a typo. But we should preserve exactly: two asterisks, then "Practice", then three asterisks. So translation: "**练习***". That is 2 asterisks, Chinese, 3 asterisks.

However, if the intention was "**Practice**", they mis-typed. But we must preserve structure exactly. So we will translate "Practice" to "练习". Then the resulting Markdown: "**练习***". That is what I'll output.

We must not add any commentary.
...done thinking.

**练习***

Thinking...
We need to translate the given Markdown into Simplified Chinese. The text: "**Create a new function: name it after “what it does”, not “how it does it”**." We keep the Markdown bold. We need to translate the sentence. So bold text remains. So "**创建一个新函数：以“它的功能”为名，而不是“它如何实现”**" or something. Let's craft: "**创建一个新函数：按其功能命名，而非按实现方式**" That's good. Ensure we preserve the exact Markdown. So final output: **创建一个新函数：按其功能命名，而非按实现方式**. Return only that.
...done thinking.

**创建一个新函数：按其功能命名，而非按实现方式**

Thinking...
We need to translate the markdown to Simplified Chinese, preserving structure. The markdown is simple: "Without local variables, refine directly into a function;" It is a sentence maybe as paragraph. There might be a leading bullet? It's just a line. In the original text, it might be a heading or a paragraph. It's likely a paragraph. We translate: "Without local variables, refine directly into a function;" into Chinese: "不使用局部变量，直接将其精炼为函数；" But punctuation: in Chinese maybe "不使用局部变量，直接改为函数；" but keep the semicolon? It's okay. We'll just translate as "不使用局部变量，直接精炼为函数；". Or "不使用局部变量，直接细化为函数；" We'll keep as "不使用局部变量，直接精炼为函数；". No code fences. So final.
...done thinking.

不使用局部变量，直接精炼为函数；

Thinking...
We need to translate the Markdown text: "with local variables but read-only, passed as arguments to the target function". It's a short phrase. We preserve markdown. There's no headings. It's just plain text. So translate to Simplified Chinese: "带有本地变量但只读，作为参数传递给目标函数". Or maybe "使用本地变量但只读，以参数方式传递给目标函数". Let's keep style: "with local variables but read-only, passed as arguments to the target function". Chinese: "使用本地变量但只读，通过参数传递给目标函数". That's good. Let's output only the translation.
...done thinking.

使用本地变量但只读，通过参数传递给目标函数

Thinking...
We need translate to Simplified Chinese. Keep Markdown structure. The content: "Local variables are assigned values: declared directly in the refining function if they are used only within the refining function; used outside the refining function as the return value of the refining function; multiple variables are modified by considering returning an object or using other refactoring techniques (querying instead of temporary variables, splitting variables)"

It's a sentence. Translate. Let's produce Chinese: "局部变量被赋值：如果仅在 refining 函数内部使用，则直接在该函数中声明；如果在 refining 函数外部使用，则将其作为 refining 函数的返回值；若有多个变量被修改，可考虑返回一个对象或使用其他重构技术（查询代替临时变量、拆分变量）。"

We preserve punctuation. Use proper Chinese punctuation. Also use "refining 函数" maybe keep refining? but better to translate "refining function" to "精炼函数"? The original is "refining function". Could translate to "精炼函数" but might not be known. Keep "refining 函数". The instruction: Keep proper nouns/product names when appropriate. 'refining function' likely a term. So we keep it. Use Chinese. Also maybe "return value" translate to "返回值". "querying instead of temporary variables" -> "查询代替临时变量". "splitting variables" -> "拆分变量".

Return Markdown only. There's no Markdown structure except paragraph. So output paragraph.
...done thinking.

局部变量被赋值：如果仅在 refining 函数内部使用，则直接在该函数中声明；如果在 refining 函数外部使用，则将其作为 refining 函数的返回值；若有多个变量被修改，可考虑返回一个对象或使用其他重构技术（查询代替临时变量、拆分变量）。

Thinking...
We need translate the heading line "## 2\. **Inline Function**" to Simplified Chinese while preserving formatting: the numbering, the markdown heading, the asterisks. The translation: "## 2\. **内联函数**" likely. We need preserve the period and backticks? There are no code fences. So just output "## 2\. **内联函数**". Ensure the escape dot is correct. Also need to preserve the asterisks.

Return only translated markdown.
...done thinking.

## 2\. **内联函数**

![](/img/0_refactor-2.png)

![](/img/0_refactor-3.png)

![](/img/0_refactor-4.png)

Thinking...
We need to translate to Simplified Chinese. Keep markdown: **bold** remains. Only translation of text inside. The text: "**Indirectness may help, but non-essential indirectness is always uncomfortable.**"

Translate: "间接性可能有帮助，但非必要的间接性总是让人不舒服。" Ensure punctuation. In Chinese, the sentence inside bold: "间接性可能有帮助，但非必要的间接性总是让人不舒服。"

Return exactly with ** around. So final.
...done thinking.

**间接性可能有帮助，但非必要的间接性总是让人不舒服。**

Thinking...
We need to translate the given Markdown to Simplified Chinese, preserving structure. The content is:

"Some functions have their contents and names clear and easy to read"

We need to translate that into Chinese. So:

"有些函数的内容和名称清晰易读"

But we must keep the same formatting. There's no headings or lists, just a paragraph. So output the translated Markdown.

Thus:

"有些函数的内容和名称清晰易读"

Ensure no trailing spaces. That's it.
...done thinking.

有些函数的内容和名称清晰易读

Thinking...
We need to translate into Simplified Chinese, preserving Markdown structure. The content is simple: "A group of functions is not well organized, inline to one big function first, then refine."

Need to translate to Chinese: "一组函数没有很好地组织，先将它们内联到一个大函数，然后再细化。" Possibly "一组函数未被很好地组织，先把它们内联成一个大函数，然后再进行细化。"

But maintain Markdown. There's no headings. It's just a single sentence.

So output the translated markdown: "一组函数未被很好地组织，先将它们内联到一个大函数，然后再进行细化。" Ensure not to translate code fences but there are none.

Return only the translated Markdown.

Let's produce.
...done thinking.

一组函数未被很好地组织，先将它们内联到一个大函数，然后再进行细化。

Thinking...
We need to translate the markdown to Simplified Chinese. The text is: "## 3\. **Extract Variable**"

We need to keep markdown structure exactly. So output: "## 3\. **Extract Variable**" but in Chinese: "## 3\. **提取变量**". The numbering 3. remains same. So output: "## 3\. **提取变量**".

Make sure the backticks remain? There's none. So just output that line.
...done thinking.

## 3\. **提取变量**

![](/img/0_refactor-5.png)

![](/img/0_refactor-6.png)

Thinking...
We need to translate to Simplified Chinese. Keep Markdown structure. The given text: "**Variables provide the right context**: they help us break up ...". So we need to translate. Bold text: "**Variables provide the right context**". That part is a heading or bold? It's bold. So we need to keep bold, but translate content: "**变量提供正确的上下文**". Then colon and rest. So final: "**变量提供正确的上下文**: 它们帮助我们将表达式拆分为更易管理的形式，也更容易理解代码的某个部分在做什么。"

Need to ensure Chinese punctuation. Also we might keep colon after bold. The rest: "they help us break up expressions into more manageable forms, and also make it easier to understand what a portion of the code is doing." Translate accordingly. Use "它们帮助我们将表达式拆分为更易管理的形式，也更容易理解代码的某个部分在做什么。"

Return just translated markdown.
...done thinking.

**变量提供正确的上下文**: 它们帮助我们将表达式拆分为更易管理的形式，也更容易理解代码的某个部分在做什么。

Thinking...
We need to translate the provided Markdown into Simplified Chinese, preserving structure. The text: "According to The Tao of Tidy Code, “**Use explanatory variables to break up the computation into a series of well-named intermediate values**”." That is a heading? Actually it's a paragraph. The phrase inside quotes is in bold. Should keep it as is: "**Use explanatory variables to break up the computation into a series of well-named intermediate values**". That remains same because we are not translating code or text inside backticks? It's not inside backticks, it's normal text but bold. Should we translate the bold text? According to instruction: "Translate the given Markdown to Simplified Chinese." So we should translate the content. But we need to keep the Markdown structure, but we can translate inside. The text inside quotes is not code fences or backticks, so we should translate it. However the bold part is not inside backticks. So we translate the bold text. But we must preserve the double asterisks. So the translation of that phrase: "使用解释性变量将计算分解为一系列命名良好的中间值". But we need to keep emphasis: **使用解释性变量将计算分解为一系列命名良好的中间值**. The quotes remain. The quote marks: “ and ” are Chinese quotation marks. Should we preserve them? Yes, preserve punctuation. So final translation:

"According to The Tao of Tidy Code, “**使用解释性变量将计算分解为一系列命名良好的中间值**”."

The preceding "According to The Tao of Tidy Code," remains. Should we translate that part? Yes. "根据《Tidy Code 的道》,"? Wait the book is "The Tao of Tidy Code". In Chinese we might translate as "《整洁代码的道》". But maybe keep proper names. "The Tao of Tidy Code" is a proper noun, we might keep it. But we could translate as "《整洁代码的道》". But instruction says keep proper nouns/product names when appropriate. "The Tao of Tidy Code" is a title; we can translate. Usually we translate book titles? The instruction says keep proper nouns/product names when appropriate. That might mean we keep them untranslated if they are product names. But "The Tao of Tidy Code" is a book title. We can translate or keep. The guidelines not explicit. But we can keep it as is to avoid confusion. But translation would be "《整洁代码的道》". The phrase "According to The Tao of Tidy Code," might become "根据《整洁代码的道》,". But we can keep as is: "根据 The Tao of Tidy Code,"? That mixes English title. But that's okay. Let's keep it as "根据《整洁代码的道》,". I think it's fine.

Thus final output:

"根据《整洁代码的道》，“**使用解释性变量将计算分解为一系列命名良好的中间值**”。"

Check punctuation: Chinese quotes: “ and ”. Good.

Return only that.
...done thinking.

根据《整洁代码的道》，“**使用解释性变量将计算分解为一系列命名良好的中间值**”。

Thinking...
We need to translate the Markdown text: "## 4. **Inline Variable**" to Simplified Chinese. Keep Markdown structure. So heading level 2, number 4, bold Inline Variable.

In Chinese: "内联变量" maybe. So "## 4. **内联变量**". Ensure we keep the Markdown formatting. So final output: the translated markdown.
...done thinking.

## 4\. **内联变量**

![](/img/0_refactor-7.png)

![](/img/0_refactor-8.png)

Thinking...
We need to translate the markdown text to Simplified Chinese, preserving markdown. The text: "Sometimes, **variable names are no more expressive** than the expression itself. There are also times when variables may get in the way of refactoring nearby code." Should translate to Chinese: "有时，**变量名并不比表达式本身更具表达性**。也有时候变量可能会妨碍附近代码的重构。"

Check for proper formatting: headings? There's no heading. Just a paragraph. Bold is **. Keep bold. Keep punctuation.

We produce final.
...done thinking.

Sometimes, **variable names are no more expressive** than the expression itself. There are also times when variables may get in the way of refactoring nearby code.

Thinking...
We need to translate to Simplified Chinese. The Markdown: "## 5\. **Rename Variable**". We need to preserve formatting. So "## 5. **Rename Variable**" -> "## 5. **重命名变量**". Ensure escape backslashes? In original they had "5\. **Rename Variable**". The backslash before dot is likely to escape dot in markdown? In translation, keep same structure: "## 5\. **重命名变量**". So output that.
...done thinking.

## 5\. **重命名变量**

![](/img/0_refactor-9.png)

Thinking...
We need to translate the given Markdown into Simplified Chinese, preserve formatting, headings, lists, emphasis. The given text: "Explain what a piece of program is doing, **and be more careful naming fields whose scope extends beyond a single function call.**"

No headings or lists. It's a sentence with bold emphasis. So translate into Chinese. Must preserve **. So output: "解释一段程序在做什么，**并且在命名跨越单个函数调用范围的字段时要更加小心。**" Keep the bold formatting. Use same Markdown: bold with **. So produce that line. No extra commentary.
...done thinking.

Explain what a piece of program is doing, **and be more careful naming fields whose scope extends beyond a single function call.**

Thinking...
We need to translate heading "## 6. **Change Function Declaration**" into Simplified Chinese, preserving markdown. So "## 6. **Change Function Declaration**" becomes "## 6. **更改函数声明**" maybe. We need to keep heading, number, and emphasis. So "## 6. **Change Function Declaration**" -> "## 6. **更改函数声明**". Yes. Return only the translated markdown.
...done thinking.

## 6. **更改函数声明**

![](/img/0_refactor-10.png)

Thinking...
We just need to translate the short sentence: "A good name gives an immediate indication of what the **function is used for**;". We must preserve Markdown, so we keep the **bold** formatting. The translation into Simplified Chinese: "一个好的名称能立即表明该**函数的用途**；". Need to keep punctuation. Use Chinese punctuation maybe "；". We can keep the semicolon. The original has a semicolon after the sentence. So we will output the Chinese sentence. Ensure no markdown formatting changes except translation. We'll keep ** around function. So "一个好的名称能立即表明该**函数用途**；"? Wait the phrase "the function is used for" translation: "函数的用途" or "函数所用之处". Usually "函数用途". But we need to preserve bold formatting. The phrase "function is used for" could be "函数的用途". Let's keep "函数的用途". So "一个好的名称能立即表明该**函数的用途**；". That should be correct. The semicolon after? We'll keep Chinese punctuation "；". So output that.
...done thinking.

一个好的名称能立即表明该 **函数的用途**；

Thinking...
We need to translate the given Markdown to Simplified Chinese while preserving Markdown structure exactly. There's only one paragraph, no code fences, no links, no images. The paragraph starts with "The argument list of a **function** describes how the function coexists with the outside world, and modifying the argument list not only increases the scope of the function's application, but also removes unnecessary coupling by changing the conditions required to connect a module."

We need to translate that, keeping **function** bold. We need to keep **function** as bold markup, so preserve "**function**". But "function" is inside bold; we must keep that exact markup. We need to translate the rest into Simplified Chinese. So:

"The argument list of a **function** describes how the function coexists with the outside world, and modifying the argument list not only increases the scope of the function's application, but also removes unnecessary coupling by changing the conditions required to connect a module."

Simplified Chinese translation: "一个 **function** 的参数列表描述了该函数如何与外部世界共存，而修改参数列表不仅扩大了函数应用的范围，还通过改变连接模块所需的条件来消除不必要的耦合。"

We need to preserve **function** markup. But "function" might be left in English because it's a proper noun product name? The rule: keep proper nouns/product names when appropriate. "function" is not a proper noun; it's a generic term. But maybe we should translate "function" to Chinese? The rule says "Keep proper nouns/product names when appropriate." "function" is not a proper noun; we can translate it as "函数". But the text includes **function** in bold. Should we translate "function" as "函数"? That would be a translation, not a proper noun. The rule says we can translate. There's no instruction to keep "function" unchanged. But we must preserve markdown. So we could translate inside bold to Chinese: "**函数**". But the original phrase uses "function" in English; we should translate it to Chinese. But I'm uncertain if we need to keep "function" or translate. The rule: Keep proper nouns/product names when appropriate. Not a product name. So we can translate it. But we might want to preserve the original **function** as bold, but we can replace "function" with "函数". So "**函数**" in bold.

However, the user might expect we translate the term. The question: The paragraph has "function" inside bold. That may be the product name? But "function" is not a product. But the text is about programming, so "function" is a concept. So we translate to Chinese. So "**函数**".

So final translation: "一个 **函数** 的参数列表描述了该函数如何与外部世界共存，而修改参数列表不仅扩大了函数应用的范围，还通过改变连接模块所需的条件来消除不必要的耦合。"

Double-check: The original says "The argument list of a **function** describes how the function coexists with the outside world, and modifying the argument list not only increases the scope of the function's application, but also removes unnecessary coupling by changing the conditions required to connect a module."

We want to preserve meaning. "函数" in Chinese is "function" concept. So "一个 **函数** 的参数列表描述了该函数如何与外部世界共存，且修改参数列表不仅扩展了函数的应用范围，还通过改变连接模块所需的条件来消除不必要的耦合。" That seems fine.

We must preserve heading? There is no heading. Just paragraph. So return the translated paragraph.

Thus output is the translated paragraph with same Markdown.

Let's output only that.

...done thinking.

一个 **函数** 的参数列表描述了该函数如何与外部世界共存，而修改参数列表不仅扩大了函数应用的范围，还通过改变连接模块所需的条件来消除不必要的耦合。

Thinking...
We need to translate to Simplified Chinese. Keep Markdown structure. The content: a bold line: **"A good way to improve the name of a function: write a comment describing what the function is used for, then turn that comment into the name of the function.”**. Translate inside. The whole line is bold. The quotation marks are inside. Should keep them.

Translation: "一种改进函数命名的好方法：编写一段说明函数用途的注释，然后将该注释变成函数名。"

We need to preserve quotes. Use double quotes. So: **"一种改进函数命名的好方法：编写一段说明函数用途的注释，然后将该注释变成函数名。"**

Ensure punctuation Chinese. Ok.

Return only translated markdown.
...done thinking.

**"一种改进函数命名的好方法：编写一段说明函数用途的注释，然后将该注释变成函数名。"**

Thinking...
We just translate the heading line. It says "## 7\. **Introduce Parameter Object**". The backslash escape maybe for the period. We should preserve it. Translate to Simplified Chinese: "介绍参数对象". Keep heading syntax and emphasis. So output:

## 7\. **介绍参数对象**

But ensure the escape is kept. The original had "## 7\. **Introduce Parameter Object**". So we replace text but keep period escape. So produce exactly: "## 7\. **介绍参数对象**". That is final.
...done thinking.

## 7\. **介绍参数对象**

![](/img/0_refactor-11.png)

Thinking...
We need to translate the given Markdown to Simplified Chinese. It's a short phrase: "Organize data into structures that make the **relationships** between data items clearer;"

We must preserve Markdown structure exactly, headings, lists, emphasis. No code fences. There's a bold word **relationships**.

Translate to Chinese: "将数据组织成能使数据项之间的 **关系** 更清晰的结构；"

We need to keep the Markdown bold on "relationships". So we preserve **relationships** as is, but that is in English. The instruction: "Keep proper nouns/product names when appropriate." "relationships" is not a proper noun, so we might translate it. But we need to preserve bold markup. The instruction says: "Do NOT translate code fences or inline code spans wrapped in backticks." Bold is not code. So we can translate the word. But we must keep Markdown emphasis. So we can write **关系** in Chinese. That will preserve bold markup. So final translation: "将数据组织成能使数据项之间的 **关系** 更清晰的结构；"

We need to keep the trailing semicolon. That's part of the original. In Chinese punctuation, we might use Chinese semicolon '；'. They used ; in original. It's a standard semicolon but we can keep it or replace with Chinese punctuation. It's part of the phrase: maybe we keep as ;. However they used ;. The requirement: preserve Markdown structure exactly, but punctuation can be changed. The semicolon is part of the sentence, not Markdown. It's fine to keep ;. We could use Chinese semicolon for naturalness, but not required. The original had ; after the sentence. We'll keep the same punctuation: "；" is Chinese; but we might preserve ; as semicolon. But translation could use Chinese punctuation for better readability. I'll use Chinese semicolon "；" for consistency with Chinese. But the original had ;, not ;. Actually the original used ; at the end. I think it's fine to use Chinese semicolon. It's not a structural element. The instruction about Markdown structure only. So we can use Chinese punctuation. I'll use "；".

Thus final answer:

将数据组织成能使数据项之间的 **关系** 更清晰的结构；
...done thinking.

将数据组织成能使数据项之间的 **关系** 更清晰的结构；

Thinking...
We need to translate the markdown to Simplified Chinese. The text: "**shorter parameter list**;". So we need to preserve bold markup, but translate "shorter parameter list" to Simplified Chinese. "shorter parameter list" -> "更短的参数列表". So we produce "**更短的参数列表**;". Also preserve semicolon. So final output: "**更短的参数列表**;".

Ensure no extra commentary.
...done thinking.

**更短的参数列表**;

Thinking...
We need to translate into Simplified Chinese, preserving Markdown. The text is "**Code consistency**: all functions that use this data structure can access ..."

So "**代码一致性**: 所有使用此数据结构的函数都可以通过相同的名称访问其元素。"

We need to preserve bold formatting. The original uses **Code consistency**. So we need **代码一致性**.

Thus final output: **代码一致性**: 所有使用此数据结构的函数都可以通过相同的名称访问其元素。
...done thinking.

**代码一致性**: 所有使用此数据结构的函数都可以通过相同的名称访问其元素。

Thinking...
We need to translate the given markdown to Simplified Chinese. It's just a sentence: "Changing the conceptual picture of the code elevates these data structures to new abstractions". The translation: "改变代码的概念视角将这些数据结构提升为新的抽象". Need to preserve markdown structure; it's just a paragraph. So output that sentence translated. No extra commentary.
...done thinking.

改变代码的概念视角将这些数据结构提升为新的抽象

Thinking...
We need to translate heading: "## 8. **Combine Functions into Class**" into Simplified Chinese. Heading style preserved: "## 8. **Combine Functions into Class**". We must keep the asterisks. Translate to Chinese: "组合函数为类" maybe. So heading: "## 8. **组合函数为类**" or "## 8. **将函数合并为类**" But need proper translation of phrase. "Combine Functions into Class" meaning merge functions into a class. So Chinese: "将函数合并为类". So with emphasis: "## 8. **将函数合并为类**". Let's deliver.
...done thinking.

## 8. **将函数合并为类**

![](/img/0_refactor-12.png)

Thinking...
We need to translate the provided Markdown text to Simplified Chinese. The text: "**If you find a group of functions that manipulate the same piece of data (usually by passing that piece of data as a parameter to the function), it's time to form a class**. Classes explicitly provide a common environment for these functions, and calling them from within an object simplifies function calls by passing many fewer arguments."

We must preserve Markdown structure: bold text. Keep code fences unchanged? There are no code fences. Just a sentence.

We need to translate to Chinese while preserving formatting: bold via double asterisks.

Translate content: "If you find a group of functions that manipulate the same piece of data (usually by passing that piece of data as a parameter to the function), it's time to form a class." → "如果你发现一组函数在操作同一份数据（通常是通过将该数据作为参数传递给函数），那么是时候创建一个类了。" But we need to keep bold markup: **...**. So the entire sentence inside bold.

Second sentence: "Classes explicitly provide a common environment for these functions, and calling them from within an object simplifies function calls by passing many fewer arguments." → "类显式地为这些函数提供一个公共环境，并且在对象内部调用它们可以通过传递更少的参数来简化函数调用。" Keep the same bold? Wait second sentence is not bold. The original had first sentence bold; second is plain. The text in original: "**If you find ...**. Classes explicitly provide..." So second is not bold. So translation must reflect that.

Let's produce the Markdown:

**如果你发现一组函数在操作同一份数据（通常是通过将该数据作为参数传递给函数），那么是时候创建一个类了。**  
Classes explicitly provide a common environment for these functions, and calling them from within an object simplifies function calls by passing many fewer arguments.

We must translate second sentence too. So:

**如果你发现一组函数在操作同一份数据（通常是通过将该数据作为参数传递给函数），那么是时候创建一个类了。**  
类显式地为这些函数提供一个公共环境，并且在对象内部调用它们可以通过传递更少的参数来简化函数调用。

But must preserve Markdown: The second line is plain paragraph.

Check punctuation: In Chinese, full stop at the end of bold sentence. Also second paragraph.

Thus final answer.
...done thinking.

**如果你发现一组函数在操作同一份数据（通常是通过将该数据作为参数传递给函数），那么是时候创建一个类了。**  
类显式地为这些函数提供一个公共环境，并且在对象内部调用它们可以通过传递更少的参数来简化函数调用。

Thinking...
We need to translate to Simplified Chinese. Preserve Markdown. "## 9\. **Split Phase**" heading level 2. So translation: "## 9\. **分相**" or "分相阶段". Likely "分相". Keep the numbering. So output:

## 9\. **分相**

Return that only.
...done thinking.

## 9\. **分相**

![](/img/0_refactor-13.png)

Thinking...
We need to translate the provided Markdown text into Simplified Chinese, preserving Markdown structure, headings, lists, emphasis. The text is:

"A piece of code that handles two different things at **simultaneously** can be considered to be **split into its own separate modules**, because then each topic can be handled separately when it comes time to make changes."

There are no headings or lists; just a paragraph with emphasis. We must translate the paragraph into Chinese, keep ** bold markers. The emphasis is indicated with **. We must preserve **. So the translation should maintain ** before and after words. The words to be bold are "simultaneously" and "split into its own separate modules". In Chinese we need to keep the same bold formatting. So:

"A piece of code that handles two different things at **simultaneously** can be considered to be **split into its own separate modules**, because then each topic can be handled separately when it comes time to make changes."

Translate: "一段代码同时处理两件不同的事可以被认为是**拆分为各自独立的模块**，因为这样在需要做更改时每个主题都可以单独处理。"

But we need to preserve the bold formatting. The first bold word is "simultaneously". In Chinese we might use "同步" or "同时". So we should keep bold markers around the Chinese translation of that word. For example: **同步**. And the second bold phrase: "split into its own separate modules" should be translated to "拆分为各自独立的模块". So we put **拆分为各自独立的模块**.

Thus final translation:

“一段代码同时处理两件不同的事可以被认为是 **同步**，而且可以被视为 **拆分为各自独立的模块**，因为这样在需要做更改时每个主题都可以单独处理。”

But note the original sentence: "can be considered to be **split into its own separate modules**, because then each topic can be handled separately..." The bold phrase is "split into its own separate modules". So we need to preserve ** before and after. So we keep "**拆分为各自独立的模块**".

Also need to maintain the comma after "simultaneously"? The original: "at **simultaneously** can be considered to be **split into its own separate modules**". Actually the grammar is slightly off: "at simultaneously can be considered to be split into its own separate modules". We can translate accordingly: "同时可以被认为是**拆分为各自独立的模块**" but we need to keep bold.

Better translation: "一段代码同时处理两件不同的事，可以被认为是**同步**，也可以被视为**拆分为各自独立的模块**，因为这样在需要做更改时每个主题都可以单独处理。"

But we need to maintain the original structure: "A piece of code that handles two different things at **simultaneously** can be considered to be **split into its own separate modules**, because then each topic can be handled separately when it comes time to make changes."

We could translate to:

“一段代码同时处理两件不同的事，可以被认为是 **同步**，也可以被视为 **拆分为各自独立的模块**，因为这样在需要更改时每个主题都可以单独处理。”

But we need to preserve ** around both words: **同步** and **拆分为各自独立的模块**.

Let's produce the final Markdown with that sentence in Chinese. No other formatting.
...done thinking.

一段代码同时处理两件不同的事，可以被认为是 **同步**，也可以被视为 **拆分为各自独立的模块**，因为这样在需要更改时每个主题都可以单独处理。

Thinking...
The user wants the translation of the Markdown "# **3. Encapsulate**" into Simplified Chinese, preserving Markdown structure. The heading and bold. So "# **3. Encapsulate**" becomes "# **3. 封装**" presumably. "Encapsulate" in Chinese is "封装". So final output: "# **3. 封装**". Ensure no extra commentary.
...done thinking.

# **3. 封装**

Thinking...
We need to translate the heading and text into Simplified Chinese, preserve markdown. The heading: "## 1\. **Encapsulate Record**". The backslash escapes dot. The translation: "## 1\. **封装记录**" maybe "封装记录" or "封装记录" is fine. Should keep asterisks around text. So we output that line. No extra commentary.
...done thinking.

## 1\. **封装记录**

![](/img/0_refactor-14.png)

Thinking...
We need to translate the markdown to Simplified Chinese. The content: "Objects can hide details of the structure, **help with renaming of fields**, and are easy to expand to cope with changes."

We must preserve markdown structure exactly. There are no headings, just a sentence with emphasis on a phrase: **help with renaming of fields**.

We must not translate code fences or inline code. There's none. No links or images.

We must keep proper nouns/product names when appropriate. No such names.

Thus translation: "对象可以隐藏结构细节，**帮助重命名字段**，并且易于扩展以应对更改。"

Return only that. Ensure punctuation: Chinese punctuation is comma etc. Use "、" for list items maybe? But keep as original: original uses comma. Chinese translation: "对象可以隐藏结构细节，**帮助重命名字段**，并且易于扩展以应对更改。"

Let's produce.
...done thinking.

对象可以隐藏结构细节，**帮助重命名字段**，并且易于扩展以应对更改。

Thinking...
We need to translate the given Markdown to Simplified Chinese. The heading: "## 2. **Encapsulate Variable**"

We need to preserve markdown structure: heading, bold.

So we translate "Encapsulate Variable" to Chinese. In context likely "封装变量" or "封装变量". The "2." remains.

Thus the translated Markdown: "## 2. **封装变量**". Ensure we keep the markdown.

We should not translate code fences or inline code spans; but there are none. So final output: the translated heading.

...done thinking.

## 2. **封装变量**

![](/img/0_refactor-15.png)

Thinking...
We need to translate the given Markdown to Simplified Chinese, preserving structure. The Markdown is:

"For all mutable data, as long as its scope extends beyond a single function, I encapsulate it and only allow access through the function. The larger the scope of the data, the more important encapsulation becomes."

This is just a paragraph. So translation: "对于所有可变数据，只要其作用域超出单个函数，我就对其进行封装，并只允许通过该函数访问。数据作用域越大，封装就越重要。"

We need to preserve Markdown structure exactly. It's a paragraph. So output that paragraph. No extra commentary.

Return ONLY the translated Markdown. Let's produce the paragraph.

...done thinking.

对于所有可变数据，只要其作用域超出单个函数，我就对其进行封装，并只允许通过该函数访问。数据作用域越大，封装就越重要。

Thinking...
We need to translate: "## 3\. **Encapsulate Collection**". So headings: "## 3. **Encapsulate Collection**". Need to translate to simplified Chinese. "Encapsulate Collection" maybe "封装集合". But keep formatting: "## 3. **封装集合**". Also escape the dot? It's "3\. **Encapsulate Collection**" includes backslash before dot. In Markdown the backslash is escape for period? Usually 3\. means 3. But preserve as is. So "## 3\. **封装集合**". The dot after 3 maybe backslash? It's "3\. **Encapsulate Collection**". So maintain same: "## 3\. **封装集合**". No other content. Return only that.
...done thinking.

## 3\. **封装集合**

![](/img/0_refactor-16.png)

Thinking...
We need to translate the paragraph into Simplified Chinese, preserving markdown. There is no code fences. There's a bold (** only encapsulates ...). In Chinese, bold syntax is same. We just translate the text inside.

Original text:

"One mistake people often make when encapsulating collections is that ** only encapsulates access to the collection variables, but still lets the fetch function return the collection itself. This allows the collection's member variables to be modified directly, while the class encapsulating it is completely unaware and unable to intervene**."

We need to translate this into Chinese. Note there is a space after ** before 'only'. It might be a typo: "** only encapsulates ...". Probably they mean "**only encapsulates ...**" but there's a space. We keep the markup as is, but we will translate the text. The markup includes ** at start and end. We should preserve them and translate between them.

So we translate: "人们在封装集合时常犯的一个错误是 **只封装了对集合变量的访问，但仍然允许 fetch 函数返回集合本身。这样会导致集合的成员变量可以被直接修改，而封装该集合的类却完全不知道并且无法干预**。"

But need to keep the structure: the ** encloses the whole phrase. So we put Chinese inside **. But in Markdown, if we put Chinese inside **, it remains bold. That's fine.

Thus final:

"人们在封装集合时常犯的一个错误是 **只封装了对集合变量的访问，但仍然允许 fetch 函数返回集合本身。这样会导致集合的成员变量可以被直接修改，而封装该集合的类却完全不知道并且无法干预**。"

Check: The original had "One mistake people often make when encapsulating collections is that ** only encapsulates access to the collection variables, but still lets the fetch function return the collection itself. This allows the collection's member variables to be modified directly, while the class encapsulating it is completely unaware and unable to intervene**."

So we translate: "人们在封装集合时常犯的一个错误是 **只封装了对集合变量的访问，但仍然允许 fetch 函数返回集合本身。这样会导致集合的成员变量可以被直接修改，而封装该集合的类却完全不知道并且无法干预**。"

Yes.

Return only the translated Markdown.
...done thinking.

人们在封装集合时常犯的一个错误是 **只封装了对集合变量的访问，但仍然允许 fetch 函数返回集合本身。这样会导致集合的成员变量可以被直接修改，而封装该集合的类却完全不知道并且无法干预**。

Thinking...
We need translate "Practice:" only? The given Markdown to translate is:

Practice:

It might be a heading? There's a colon. Possibly a heading "Practice:" maybe level 1? The preceding context? It's just "Practice:" maybe a heading? The rule: preserve markdown structure. There's no backticks or code. Just translate to Simplified Chinese. "Practice:" -> "实践:"? Probably "练习:"? Which one? In context of technical translation, "Practice:" could be "实践:" or "练习:". In English it's ambiguous. Could be heading for a section on practice. I'd choose "实践:" because it's common heading. Provide exactly the translated Markdown: "实践:".

Thus output: "实践:" with no markdown? It is just a line. If it's a heading maybe need to keep same level. But no heading symbol provided. It's just plain "Practice:". So translation: "实践:".

Return only that.
...done thinking.

实践:

Thinking...
We need to translate the given Markdown to Simplified Chinese. The content: "Provide methods to modify the collection on the class ------**Usually “add” and “remove” methods to unify the management**."

The structure: This is a sentence, with a dash line and bold text. The dash line "------" maybe just a horizontal line? In Markdown, "------" is not a horizontal rule unless it's three or more hyphens on a line by themselves. But here it's "------**Usually ..." It's part of the same line? Let's interpret: "Provide methods to modify the collection on the class ------**Usually “add” and “remove” methods to unify the management**."

The dash line might just be a separator. We can preserve as is: "------". Then the bold part: **Usually “add” and “remove” methods to unify the management**. That should be translated to Simplified Chinese: "**通常使用 “add” 和 “remove” 方法统一管理**". Need to preserve the quotes around add and remove. In Chinese, quotes for code should be maybe double quotes but can keep as is.

Also note that we should not translate code fences or inline code spans wrapped in backticks. But here no backticks. So we can translate.

The final result: "Provide methods to modify the collection on the class ------**通常使用 “add” 和 “remove” 方法统一管理**."

But we should preserve the same structure. There's no markdown heading. So output is just the translated line.

Let's produce that.
...done thinking.

Provide methods to modify the collection on the class ------**通常使用 “add” 和 “remove” 方法统一管理**.

Thinking...
We just translate the heading and bold text: "## 4. Substitute Algorithm" into Simplified Chinese. The heading remains same level. Translate "Substitute Algorithm" to "替代算法" or "代替算法"? Usually "替代算法" or "替换算法". "Substitute" could be "替代". Let's choose "替代算法". Keep bold formatting. So output:

## 4. **替代算法**

Check rule: preserve Markdown structure exactly. Good. No other changes.
...done thinking.

## 4. **替代算法**

![](/img/0_refactor-17.png)

Thinking...
The user: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: Preserve Markdown structure exactly (headings, lists, emphasis). Do NOT translate code fences or inline code spans wrapped in backticks. Do NOT alter links or image paths. Keep proper nouns/product names when appropriate. Return ONLY the translated Markdown, no extra commentary."

Markdown to translate:

# **3. Move Characteristics**

So we translate: The heading is # **3. Move Characteristics**. So it's a top-level heading with bold "3. Move Characteristics". The translation: "**3. 移动特性**"? Wait "Move Characteristics" -> Chinese: "移动特性". Or "运动特性"? Since "Move" in context may be "移动". Probably "移动特性".

Thus final Markdown: # **3. 移动特性**. Keep bold and heading. No extra.
...done thinking.

# **3. 移动特性**

Thinking...
We need to translate the given markdown into Simplified Chinese, preserving structure. The content: "Another type of refactoring that is also important is **moving elements between contexts**."

We need to translate to Chinese. So: "另一种同样重要的重构类型是 **在不同上下文之间移动元素**。"

Be careful to preserve bold markup. The output should be just the translated markdown. Let's produce that.
...done thinking.

另一种同样重要的重构类型是 **在不同上下文之间移动元素**。

Thinking...
The user wants a translation of the given Markdown to Simplified Chinese. The markdown includes a heading:

```
## 1\. **搬移函数（Move Function）**
```

We need to preserve Markdown structure exactly, headings, etc. So we translate the content: "搬移函数（Move Function）" is already partially translated: the Chinese term "搬移函数" and the English term "Move Function" in parentheses. It seems the heading is "## 1. **搬移函数（Move Function）**". The dot after 1\. should be preserved. We might want to preserve the backticks? There are none. We can keep the asterisks for bold. So final output is:

```
## 1\. **搬移函数（Move Function）**
```

We must not add any extra commentary. Just that line. That's all.

But the heading is "## 1\. **搬移函数（Move Function）**". That is the translation. There's no other content.

Hence final answer.
...done thinking.

## 1\. **搬移函数（Move Function）**

![](/img/0_refactor-18.png)

**任何函数都需要具备上下文环境才能存活**。

搬移函数最直接的一个动因是，**它频繁引用其他上下文中的元素，而对自身上下文中的元素却关心甚少**，将函数移动到联系更紧密的上下文那么系统别处就可以减少对当前模块的依赖，**获得更好的封装效果。**

整理代码时，发现需要**频繁调用一个别处的函数**；或者函数内部定义了一个帮助函数，而该帮助函数可能**在别的地方也有用处**，此时就可以将它搬移到某些更通用的地方。

**是否需要搬移函数常常不易抉择，但决定越难做，通常说明"搬移这个函数与否"的重要性也越低。**

**范例：搬移内嵌函数至顶层**

Thinking...
We need to translate the given Markdown to Simplified Chinese. The provided content is:

"before：

"

So the original has heading? Actually the content is "before：" and then maybe some content? The Markdown to translate is:

before：

So the original might be a heading? Actually it's "before：" followed by maybe nothing else. It's probably a heading? "before：" maybe it's a section? It's not a heading, it's just plain text. So we need to translate "before：" into Simplified Chinese, preserving punctuation. So "before：" becomes "之前：" maybe.

Thus output:

之前：

But need to preserve exactly same formatting. There is a line "before：" and maybe nothing else. So output "之前：" on its own line. So final.

...done thinking.

之前：

计算两点之间距离的函数在别处也有调用

![](/img/0_refactor-19.png)

Thinking...
The user wants translation of Markdown. The given content: "after：" presumably is a heading? But the Markdown to translate is only "after："? Let's examine: The input:

```
after：
```

That's a line with "after：" plus maybe some colon? The colon is a Chinese colon "：" not standard ascii colon. It's a heading? No heading mark. It's just a line. So we need to translate "after：" into Simplified Chinese. But "after" in English could be translated as "之后" or "后". But the user has already used Chinese colon after "after". The original text is "after：" with a Chinese colon. That likely is a heading or something. But they said preserve Markdown structure exactly. So we need to translate the word "after" into Chinese. In context maybe "after:" meaning as a header for "after" section? So translate "after：" to "之后：". Keep the Chinese colon. So output: "之后：" and nothing else. Let's double-check: The user said "after：" as the only content. So output "之后：" (since "after" as translation). We need to preserve structure. So we just produce that line. Also ensure no other text. Let's produce.
...done thinking.

之后：

![](/img/0_refactor-20.png)

Thinking...
We need to translate the markdown text into Simplified Chinese. The text: 
```
## 2\. **搬移语句到函数（Move Statements into Function）**
```
We preserve markdown structure. The heading is "## 2. **搬移语句到函数（Move Statements into Function）**". The part "搬移语句到函数" is Chinese; we need to translate the English part? Wait the original has both Chinese and English: "**搬移语句到函数（Move Statements into Function）**". The Chinese part is already there. The instruction: "Translate the given Markdown to Simplified Chinese." So we need to translate the English parts to Simplified Chinese. But the Chinese part "搬移语句到函数" is already Chinese. We keep that. But the English part "Move Statements into Function" should be translated to Chinese. Maybe we translate inside the parentheses? The parentheses currently contain English. We need to translate that to Chinese as well. So we would produce:

```
## 2\. **搬移语句到函数（将语句移动到函数中）**
```

But check translation: "Move Statements into Function" => "将语句移动到函数中". So parentheses Chinese: (将语句移动到函数中). But the instruction: "Keep proper nouns/product names when appropriate." Not relevant.

Also preserve markdown. Also preserve backticks etc. There's no code fences. Just heading.

Thus final output: "## 2\. **搬移语句到函数（将语句移动到函数中）**"

But we need to keep the backslash? The original had "## 2\. **搬移语句到函数（Move Statements into Function）**". The backslash before dot escapes? In markdown, "## 2\. ..." The dot after number maybe purposely escaped. Keep same. So we keep "## 2\. **搬移语句到函数（将语句移动到函数中）**".

Return only that.
...done thinking.

## 2\. **搬移语句到函数（将语句移动到函数中）**

![](/img/0_refactor-21.png)

**"消除重复"**：如果发现调用某个函数时，总有一些相同的代码也需要每次执行，则考虑将此段代码合并到函数里头。

**如果某些语句与一个函数放在一起更像一个整体**，并且更**有助于理解**，则将语句搬移到函数里去。**如果它们与函数不像一个整体**，但仍应与函数一起执行，可以用**提炼函数将语句和函数一并提炼出去**。

**五. 重新组织数据**

Thinking...
We need to translate into Simplified Chinese. The Markdown contains numbered list item 1. "**拆分变量（Split Variable）**" Wait, original is "1\. **拆分变量（Split Variable）**". Actually the content is in English? Wait original Markdown: "1\. **拆分变量（Split Variable）**". This appears to be Chinese "拆分变量" with English in parentheses. So translation of heading? But the original already Chinese? The instruction says translate to Simplified Chinese. It's already Chinese. But maybe the original had English heading? The line shows "1. **拆分变量（Split Variable）**". So maybe they want to translate to Simplified Chinese, but content is already Chinese. Could be the "Split Variable" term to translate? But it's already Chinese with English in parentheses. Maybe we need to translate "Split Variable" to Chinese "拆分变量". But that's already there. So no change needed? Perhaps the original had "Split Variable" and Chinese translation is given. But it's the other way. So translation might be unnecessary. But to be safe, maybe we should keep as is.

But rule: Preserve Markdown structure. Do not translate code fences or inline code spans. So the line is plain text. It already Chinese. The part inside parentheses is English, but maybe we should translate that too? The instruction: translate given Markdown to Simplified Chinese. So we need to translate the whole text. The English term "Split Variable" is not translated because it's in parentheses but maybe still need translation. The parenthetical English could be translated to Chinese within parentheses? But original text shows Chinese first then English in parentheses. So maybe we want to keep as is. There's no other content. So final output should be same line. But ensure it's Markdown numbered list. So output:

1. **拆分变量（拆分变量）**? That would duplicate. That seems wrong.

Maybe we should translate to: "1. **拆分变量（拆分变量）**"? But that seems redundant.

Given the ambiguous, best to keep original as is.

Thus output: "1. **拆分变量（Split Variable）**".
...done thinking.

1. **拆分变量（Split Variable）**

![](/img/0_refactor-22.png)

除"循环变量"和"结果收集变量"外，还有很多变量用于保存一段冗长代码的运算结果，以便稍后使用。这种**变量应该只被赋值一次。**如果它们被赋值超过一次，就意味它们在函数中承担了一个以上的责任。如果变量承担多个责任，它就应该被替换（分解）为多个变量，**保持职责单一**。

**范例：对输入参数赋值**

Thinking...
We have a user input: "before：". That seems incomplete. Perhaps the prompt originally includes a Markdown to translate, but here we only see "before：". Maybe there is a formatting issue. Could be that the user wants to translate the Markdown that follows "before：" but it's empty. So we should output nothing? But they say "Translate the given Markdown to Simplified Chinese." The Markdown to translate is:

before：

That is just a heading? Actually "before：" not in Markdown syntax. Could be a line: "before：" which means "before:" in English, maybe a heading? The translator should produce Chinese. But no further content. So we produce the translation: "before：" -> "before："? We should translate "before：" to Chinese: "before:" would be "之前：" or "在此之前：" but they said preserve Markdown exactly. So we just translate the text "before：" to Chinese. We don't modify punctuation. So "before：" -> "之前：" maybe. But the punctuation is colon. Keep that. So final answer: "之前：" maybe with the same colon. The translator should output that line. Let's produce that.
...done thinking.

之前：

![](/img/0_refactor-23.png)

Thinking...
We need to translate the given Markdown to Simplified Chinese. The markdown to translate is:

```
after：
```

Actually just "after：" followed by a space? Let's examine exactly: The user wrote:

```
after：
```

That seems to be a markdown heading? No, it's just "after：" presumably a line. Might be a header? There's no hash marks. It's just plain text "after：".

We need to preserve markdown structure exactly. The input has only "after：" on one line. There's a colon after "after". It might be a Chinese colon "：" (fullwidth colon). So we should translate "after：" to "之后：" maybe? But need to preserve markdown. It's a line of text. The translation would be "之后：". No code fences.

Thus output should be:

```
之后：
```

Return only that.
...done thinking.

之后：

![](/img/0_refactor-24.png)

**六. 简化条件逻辑**

Thinking...
We need to translate to Simplified Chinese, preserving markdown. Title: 1. **分解条件表达式（Decompose Conditional）** Should be: 1\. **分解条件表达式（Decompose Conditional）** But the Chinese translation of the term "Decompose Conditional" maybe keep English? It says keep proper nouns/product names when appropriate. "Decompose Conditional" might be a technical term; we might translate it? The parenthesis includes English. They want translation: "分解条件表达式（Decompose Conditional）". Actually the original has Chinese first then English in parenthesis. In translation we want Chinese first, but likely keep English in parenthesis. But the original is Chinese "分解条件表达式（Decompose Conditional）". They want translate the markdown: "1\. **分解条件表达式（Decompose Conditional）**". It is already Chinese with English in parentheses. So translation maybe same? But maybe they want translate to Simplified Chinese: "1\. **分解条件表达式（Decompose Conditional）**". Already Chinese. Maybe keep same. But maybe need to translate "Decompose Conditional" to Chinese: "分解条件" but that duplicates. Perhaps better: "分解条件表达式（Decompose Conditional）" same as original. Since they said "keep proper nouns/product names when appropriate". "Decompose Conditional" might be a term. We keep as is. So the output is the same markdown line.

Return ONLY the translated Markdown. So just that line. Ensure backslashes escape dot? The original had "1\. **分解条件表达式（Decompose Conditional）**". We keep that.
...done thinking.

1\. **分解条件表达式（Decompose Conditional）**

![](/img/0_refactor-25.png)

程序之中，复杂的条件逻辑是最常导致复杂度上升的因素之一。

对于条件逻辑，**将每个分支条件分解成新函数**还可以带来更多好处：可以突出条件逻辑，更清楚地表明每个分支的作用，并且突出每个分支的原因。

注：实际上为**提炼函数**的一个应用场景。

Thinking...
We need to translate the given Markdown to Simplified Chinese. The content is short: "2\. **合并条件表达式（Consolidate Conditional Expression）**". Wait, it's already partially translated? The heading says "2. **合并条件表达式（Consolidate Conditional Expression）**". Actually it's "2. **Merge Conditional Expression**"? The original maybe in English? The content: "2\. **合并条件表达式（Consolidate Conditional Expression）**". It is partially translated. But we need to translate the Markdown. The rule: preserve Markdown structure exactly. Do not translate code fences or inline code spans. There are no code fences. Also do not alter links or image paths. Keep proper nouns/product names. Return only the translated Markdown.

We need to translate the text to Simplified Chinese. The heading includes both Chinese and English: "合并条件表达式（Consolidate Conditional Expression）". This is already Chinese for "Consolidate Conditional Expression" with English translation. But the rule: translate the given Markdown to Simplified Chinese. The content is partially translated. Should we translate the English words into Chinese? The heading already includes Chinese. But we may need to translate the English part to Chinese: "Consolidate Conditional Expression" maybe "合并条件表达式". That is already present. So maybe we just preserve the heading as is, because it's already Chinese. But maybe the original English heading was "2. Consolidate Conditional Expression". They have inserted the Chinese translation. But the instruction says "Translate the given Markdown to Simplified Chinese." So the translation should be Chinese, but we can keep the Chinese already present. The heading "2. **合并条件表达式（Consolidate Conditional Expression）**" contains Chinese. So maybe we should translate the English in parentheses? They have "Consolidate Conditional Expression". Should we translate that into Chinese? The heading already includes Chinese: "合并条件表达式". So we could keep the English part or we could translate it. But the instruction: preserve Markdown structure. We can change the text. So we could modify the heading to "2. **合并条件表达式**". Or "2. **合并条件表达式（合并条件表达式）**" but that duplicates. So likely we just keep "2. **合并条件表达式**". The parentheses maybe can be removed. But we must preserve the heading formatting. The heading currently uses an asterisk for bold inside Markdown. The bullet: "2\. **合并条件表达式（Consolidate Conditional Expression）**". We might transform to "2. **合并条件表达式**". That would be the translation.

But maybe the original text had "Consolidate Conditional Expression" and the translation inserted Chinese inside parentheses. They want us to produce translation but preserve original Chinese? Actually the prompt might be a snippet from a translation exercise where the English text hasn't been translated fully. The provided snippet contains partially translated Chinese text: "2. **合并条件表达式（Consolidate Conditional Expression）**". It includes the Chinese phrase and the English phrase. We need to translate to Simplified Chinese. So the English phrase "Consolidate Conditional Expression" needs to be translated. We could just replace it with Chinese. So final Markdown: "2. **合并条件表达式（合并条件表达式）**"? But that duplicates. Better to just keep Chinese phrase. The heading would be "2. **合并条件表达式**". That is simplest.

Let's output: "2. **合并条件表达式**". That is the translation. There's no other text.

We need to preserve Markdown. There's no code fences. So just output that line.

Thus final output: 
```
2. **合并条件表达式**
```

But careful: in the original it's "2\. **合并条件表达式（Consolidate Conditional Expression）**". The backslash before dot escapes dot? In Markdown, "2. " is fine. But they wrote "2\. **...**" maybe for Markdown to avoid formatting. But we can keep "2. **...**". It's fine.

Thus final answer.
...done thinking.

2. **合并条件表达式**

![](/img/0_refactor-26.png)

Thinking...
We need to translate the heading: "3. **以卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard Clauses）**"

Simplified Chinese translation: "以卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard Clauses）" is already partially Chinese? The heading is "3. **以卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard Clauses）**". They want to translate to Simplified Chinese. The phrase inside parentheses is English; we can keep it. The Chinese part "以卫语句取代嵌套条件表达式" may be okay. But "卫语句" maybe should be "guard clauses". In Chinese translation, "以 guard 语句取代嵌套条件表达式"? Wait we preserve parentheses. So we translate heading into Chinese only the Chinese part? We need to translate the heading into Simplified Chinese, including Chinese characters. The heading is already partially Chinese: "以卫语句取代嵌套条件表达式". But "卫语句" might be a translation of "guard clauses". But the original is "Replace Nested Conditional with Guard Clauses". The Chinese part "以卫语句取代嵌套条件表达式" is correct? Might be "以 guard 语句取代嵌套条件表达式". But "卫" is likely wrong? It should be "守卫" or "守护"? In Chinese, "guard clauses" is often translated as "守卫语句" or "守护语句". "以守卫语句取代嵌套条件表达式" is correct. But the given text says "以卫语句取代嵌套条件表达式". Maybe a small mistake. But we should translate properly. We preserve Markdown structure. So the translation should be: "3. **以守卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard Clauses）**". We keep the parentheses unchanged. That would be best.

Thus output: 3. **以守卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard Clauses）**
...done thinking.

3. **以守卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard Clauses）**

![](/img/0_refactor-27.png)

Thinking...
We need translate to Simplified Chinese. The given text is already Chinese. The instruction: "Translate the given Markdown to Simplified Chinese." The source text is Chinese. Likely translation to Simplified Chinese? The text already is Simplified Chinese, but maybe some characters are traditional? It says "卫语句" in Chinese. It's fine. The instruction says preserve Markdown. The original has "**" for emphasis. No code fences. So we just output the same content? The translation might be same. Ensure we keep emphasis. So output same.

Thus final: keep the text unchanged.
...done thinking.

如果两条分支都是正常行为，就应该使用形如if\...else\...的条件表达式；如果某个条件极其罕见，就应该单独检查该条件，并在该条件为真时立刻从函数中返回。**这样的单独检查常常被称为"卫语句"（guard clauses）**。

**如果使用if-then-else结构，则对if分支和else分支的重视是同等的；以卫语句取代嵌套条件表达式的精髓就是：给某一条分支以特别的重视。**

"每个函数只能有一个入口和一个出口"的观念未必有用，**保持代码清晰才是最关键的**。

**范例**

Thinking...
We need to translate "before" into Simplified Chinese. The instructions: "Translate the given Markdown to Simplified Chinese. Rules: preserve markdown structure exactly. Do NOT translate code fences or inline code spans wrapped in backticks. Do NOT alter links or image paths. Keep proper nouns/product names when appropriate. Return ONLY the translated Markdown, no extra commentary."

The input is:

```
before
```

That's literally the word "before". It's not a heading, just plain text? It's just "before". It's not a code block; it's just a single line. We need to translate "before" into Simplified Chinese: "之前". So output should be:

```
之前
```

But we need to keep markdown structure exactly. Since it's just text, output is "之前". No code fences. Just the text.

Thus final answer: "之前".
...done thinking.

之前

![](/img/0_refactor-28.png)

Thinking...
We have a prompt: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: Preserve Markdown structure exactly (headings, lists, emphasis). Do NOT translate code fences or inline code spans wrapped in backticks. Do NOT alter links or image paths. Keep proper nouns/product names when appropriate. Return ONLY the translated Markdown, no extra commentary."

The markdown to translate: 
```
after
```

That's a single word "after". We need to translate to Simplified Chinese: "之后". But the markdown includes the word after alone. It's just a word. It may not have any markdown syntax. So output "之后" alone. Ensure no extra commentary. No trailing spaces. That is the answer.
...done thinking.

之后

![](/img/0_refactor-29.png)

**范例：将条件反转**

初始

![](/img/0_refactor-30.png)

反转

![](/img/0_refactor-31.png)

合并条件表达式

![](/img/0_refactor-32.png)

删除可变变量

![](/img/0_refactor-33.png)

Thinking...
We need to translate the Markdown content. The content: "4\. **以多态取代条件表达式（Replace Conditional with Polymorphism）**". Actually it's "4. **以多态取代条件表达式（Replace Conditional with Polymorphism）**". The translation should keep the structure. We preserve the numbering, heading maybe? It's just a line: "4. **以多态取代条件表达式（Replace Conditional with Polymorphism）**". Should we keep the "4."? Yes. We need to translate the Chinese part? Wait the content is already partly Chinese: "以多态取代条件表达式". But we need to translate to Simplified Chinese. But it's already Chinese. However the English phrase "Replace Conditional with Polymorphism" is inside parentheses. We might translate that part too? The instruction: "Translate the given Markdown to Simplified Chinese." So everything should be in Simplified Chinese. The line currently is "4. **以多态取代条件表达式（Replace Conditional with Polymorphism）**". The Chinese part is already Chinese. The English part should be translated to Chinese. So we translate "Replace Conditional with Polymorphism" into Chinese: "用多态取代条件表达式". So the full line becomes: "4. **以多态取代条件表达式（用多态取代条件表达式）**". But we should be careful not to double repeat. Actually the Chinese part is "以多态取代条件表达式", the English translation is "Replace Conditional with Polymorphism". We might translate the English into Chinese as "用多态取代条件表达式" or "用多态替代条件判断". Keep consistency. So inside parentheses, we translate.

Thus final output: "4. **以多态取代条件表达式（用多态取代条件表达式）**". But maybe we need to preserve the original meaning? The original title is "Replace Conditional with Polymorphism". So Chinese translation: "用多态取代条件表达式". But we also have "以多态取代条件表达式" as heading. That duplicates. But okay.

Thus final answer.
...done thinking.

4. **以多态取代条件表达式（用多态取代条件表达式）**

![](/img/0_refactor-34.png)

**七. 重构API**

Thinking...
We need to translate the given Markdown to Simplified Chinese, preserving Markdown structure. The text is "**以查询取代参数（Replace Parameter with Query）**". It's already in Chinese plus English. We need to translate English parts into Simplified Chinese. The Chinese part "以查询取代参数" means "Replace Parameter with Query". The English part in parentheses can be translated to Simplified Chinese: "(用查询取代参数)" maybe. But original had parentheses. They want to keep proper nouns when appropriate. "Replace Parameter with Query" is a phrase. We could translate it to Chinese but also keep English? The rule: "Translate the given Markdown to Simplified Chinese." So translate the whole string to Chinese. We can translate the English part. Let's produce: "**以查询取代参数（用查询取代参数）**". But it's redundant? "Replace Parameter with Query" is same as Chinese. But original might include product names. Not sure. I think it's fine.

Thus output: **以查询取代参数（用查询取代参数）**.
...done thinking.

**以查询取代参数（用查询取代参数）**

![](/img/0_refactor-35.png)

**函数的参数列表应该总结该函数的可变性**，标示出函数可能体现出行为差异的主要方式。和任何代码中的语句一样，**参数列表应该尽量避免重复**，并且参数列表越短就越容易理解。

使用场景：调用函数时传入了一个值，而这个值由函数自己来获得也是同样容易

什么是"同样容易"：函数可以承担这份原本由调用方所承担的"获得正确的参数值"的责任。

什么时候不适用：移除参数可能会给函数体增加不必要的依赖关系。

Thinking...
We just translate the heading: "**以参数取代查询（Replace Query with Parameter）**" is already Chinese. We might keep it same. No translation needed. But maybe the heading is already Chinese. The original includes both Chinese and English inside parentheses. We keep same. So output same.
...done thinking.

**以参数取代查询（Replace Query with Parameter）**

![](/img/0_refactor-36.png)

好处：**改变依赖关系**，去掉令人不快的引用。

注意：**要考虑责任分配问题，会增加函数调用者的复杂度，而设计接口时又需要考虑易用性**。

**八. 处理继承关系**

Thinking...
We need translate to Simplified Chinese. The Markdown is just a line: **以委托取代超类（Replace Superclass with Delegate）**. We must preserve structure, so bold remains. The content inside is already Chinese: "以委托取代超类（Replace Superclass with Delegate）". But maybe we need translate to Chinese: The part before parentheses is Chinese already. The part inside parentheses is English. We might keep as is. The instruction: "Translate the given Markdown to Simplified Chinese." The whole string includes Chinese already. We might just keep as is. The rule: preserve Markdown structure exactly. So output is same string.

We must ensure no additional commentary. Output: **以委托取代超类（Replace Superclass with Delegate）**.
...done thinking.

**以委托取代超类（Replace Superclass with Delegate）**

![](/img/0_refactor-37.png)

继承：子类继承父类的特征和行为 （车-交通工具）

组合：通过对现有对象进行拼装即组合产生新的具有更复杂的功能 （车-轮胎）

以组合取代继承。

**一个经典的误用继承的例子：**

**让栈（stack）继承列表（list）**。这个想法的出发点是想复用列表类的数据存储和操作能力。虽说复用是一件好事，但这个继承关系有问题：列表类的所有操作都会出现在栈类的接口上，然而其中大部分操作对一个栈来说并不适用。**更好的做法应该是把列表作为栈的字段，把必要的操作委派给列表就行了**。

Thinking...
We need to translate the Markdown to Simplified Chinese, preserving markdown structure. The input Markdown is:

```
-------------------------------------------------
Java\
public class Stack<E> extends Vector<E> {
<br/>
public E push(E item) {
addElement(item);
return item;
}
<br/>
public synchronized E pop() {
E obj;
int len = size();
obj = peek();
removeElementAt(len - 1);
return obj;
}
}
```

But the original is not well-structured. There are backslashes for line breaks? The code fence is not indicated. Actually the snippet has no code fences, it's just raw text with backslashes to escape newline maybe.

We must preserve Markdown structure exactly. There's a line of dashes: "-------------------------------------------------". Then "Java\" then code. But there is no code fences. They want to preserve the markdown exactly. So we should keep "Java\" unchanged? We translate? The rule: Keep proper nouns/product names. The code is Java class. "Java" is a proper noun; we should keep as "Java". But we can translate the rest of the text? There's no other text except code. But the code includes comments like public class Stack<E> extends Vector<E> {. Should we translate the words like "public", "class", etc? No, they are code; we should not translate code. The rule says: Do NOT translate code fences or inline code spans wrapped in backticks. But here code is not in fences. It's raw text but is code. But the instruction might mean treat code as is. The snippet is code, but it's not wrapped in fences. They might want to keep it unchanged. The only non-code text is "Java\" and the dashes. Possibly they want to translate "Java" or leave it? Since "Java" is a proper noun, keep it. There's no other translation needed. So translation is essentially same as input. But we must ensure the backslashes for line breaks? "Java\" is a line that ends with a backslash. That indicates a line break. But we keep it.

Thus output will be same as input. But maybe they expect translation of the description "Java\" as just "Java" and remove backslash? But we must preserve structure exactly. So we keep backslashes.

Thus output:

```
-------------------------------------------------
Java\
public class Stack<E> extends Vector<E> {
<br/>
public E push(E item) {
addElement(item);
return item;
}
<br/>
public synchronized E pop() {
E obj;
int len = size();
obj = peek();
removeElementAt(len - 1);
return obj;
}
}
```

But is there a newline at the end? Should preserve. The final markdown should be exactly as input but in Chinese? There's no Chinese content. So basically identical. Let's produce that.
...done thinking.

-------------------------------------------------
Java\
public class Stack<E> extends Vector<E> {
<br/>
public E push(E item) {
addElement(item);
return item;
}
<br/>
public synchronized E pop() {
E obj;
int len = size();
obj = peek();
removeElementAt(len - 1);
return obj;
}
}


  -----------------------------------------------------------------------

Thinking...
We need to translate the given Markdown to Simplified Chinese. Let's examine the source text:

"Stack真正需要的只有四个方法，push/pop/size/isEmpty， Stack只用到了
Vector的两个方法 isEmpty 和 size，而 push 和 pop 是 Stack 自有的实现，
Vector 有大量的方法， 不适用于stack。"

We need to preserve Markdown structure exactly. However, there is no Markdown syntax (headings, lists, emphasis) except plain text. But we need to preserve line breaks as they exist. The text includes commas and Chinese punctuation. It's not using Markdown. So we need to translate into Simplified Chinese. It's already in Chinese. But maybe we need to translate some English words? Actually the text is Chinese but with some English words like "push/pop/size/isEmpty", "Vector". The question: "Translate the given Markdown to Simplified Chinese." The text is already Chinese. But there might be some English terms like "Vector" that may be kept as is. But maybe they want to keep them as is. The rule: Keep proper nouns/product names when appropriate. Vector is a proper class name in Java. So we keep "Vector". push/pop/size/isEmpty are methods. We keep them. The translation might just be same as original? But maybe they want to translate the entire text into Chinese. But it's already Chinese, but maybe some words like "Stack" might be kept. "Stack" is a class name. But they might want to keep "Stack". The original text uses "Stack真正需要的只有四个方法，push/pop/size/isEmpty， Stack只用到了 Vector的两个方法 isEmpty 和 size，而 push 和 pop 是 Stack 自有的实现， Vector 有大量的方法， 不适用于stack。"

The translation to Simplified Chinese would be identical. But maybe the original had some English words that need to be transliterated or kept. The instructions: "Keep proper nouns/product names when appropriate." So keep "Stack", "Vector". The rest is Chinese. Also "push/pop/size/isEmpty" are method names. They can remain as is. There's "stack" at the end; maybe it's also a proper noun. Keep "stack" or "Stack"? The original had "stack" in lower-case. Should keep as "stack". So the translation remains same.

But perhaps we need to adjust punctuation? It's already Chinese punctuation. But it's a bit weird: "Vector有大量的方法， 不适用于stack。" The comma after methods, space before "不". That might be due to formatting. But we preserve exactly. So final output is same text.

But we must ensure we preserve line breaks: The text shows line break after "Stack只用到了". So we need to preserve that line break. Let's copy it:

Stack真正需要的只有四个方法，push/pop/size/isEmpty， Stack只用到了
Vector的两个方法 isEmpty 和 size，而 push 和 pop 是 Stack 自有的实现，
Vector 有大量的方法， 不适用于stack。

We should keep that. Also note the space after "Stack只用到了" line break. The new line has "Vector的两个方法". In Chinese, there is no space between "Vector" and "的". In original it's "Vector的两个方法". That's okay.

Also, there is a space after the comma before "不适用于stack。". Keep same.

Thus final translation: same as original.
...done thinking.

Stack真正需要的只有四个方法，push/pop/size/isEmpty， Stack只用到了
Vector的两个方法 isEmpty 和 size，而 push 和 pop 是 Stack 自有的实现，
Vector 有大量的方法， 不适用于stack。

**所以，如果父类的一些函数对子类并不适用，就说明我不应该通过继承来获得超类的功能。**

同时也要避免走弯路：完全避免使用继承，如果符合继承关系的语义条件（超类的所有方法都适用于子类，子类的所有实例都是超类的实例），那么继承是一种简洁又高效的复用机制。

建议：**首先（尽量）使用继承，如果发现继承有问题，再使用以委托取代超类。**

**范例**

背景：

Thinking...
We need translate to Simplified Chinese. Original already in Chinese. We just translate? The content is Chinese. But might need adjust. It's already Chinese. Should keep same. But need keep Markdown structure. It's just a paragraph. So output same text in Chinese. No translation needed. But we may need to re-translate? The instruction: translate given Markdown to Simplified Chinese. It's already Chinese. But maybe it's simplified already. It's Chinese, likely simplified. So we can output unchanged. Ensure no markdown changes. Just same paragraph. Let's output.
...done thinking.

给一个古城里存放上古卷轴（scroll）的图书馆做了咨询。他们给卷轴的信息编制了一份目录（catalog），每份卷轴都有一个ID号，并记录了卷轴的标题（title）和一系列标签（tag），这些古老的卷轴需要日常清扫，因此代表卷轴的Scroll类继承了代表目录项的CatalogItem类，并扩展出与"需要清扫"相关的数据。

![](/img/0_refactor-38.png)

![](/img/0_refactor-39.png)

这就是一个常见的建模错误。真实存在的卷轴和只存在于纸面上的目录项，是完全不同的两种东西。比如说，关于"如何治疗灰鳞病"的卷轴可能有好几卷，但在目录上却只记录一个条目。这样的建模错误很多时候可以置之不理。像"标题"和"标签"这样的数据，可以认为就是目录中数据的副本。如果这些数据从不发生改变，可以接受这样的表现形式。但如果需要更新其中某处数据，就必须非常小心，确保同一个目录项对应的所有数据副本都被正确地更新。

就算没有数据更新的问题，把目录类作为卷轴类的父类，依然会让后来的开发者感到迷惑。

Thinking...
We need to translate the given Markdown to Simplified Chinese. The text: "首先在Scroll类中创建一个属性，令其指向一个新建的CatalogItem实例。"

This is already Chinese. Maybe it's English? It's Chinese. But we have to translate to Simplified Chinese. It's already Simplified Chinese. But maybe they expect translation to English? Wait the instruction: "Translate the given Markdown to Simplified Chinese." The given text is Chinese. But it's fine to preserve as is. But check for proper nouns. The text has no code fences. So we just output same content. No change.

Check for punctuation: There's a period at end. So output same.

Thus output exactly the same string.
...done thinking.

首先在Scroll类中创建一个属性，令其指向一个新建的CatalogItem实例。

![](/img/0_refactor-40.png)

然后对于子类中用到所有属于超类的函数，我要逐一为它们创建转发函数。

![](/img/0_refactor-41.png)

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

![](/img/0_refactor-42.png)

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

Thinking...
We need to translate to Simplified Chinese. The sentence: "旧的接口标记为"不推荐使用"（deprecated）。" Already looks Chinese? It says "旧的接口标记为"不推荐使用"（deprecated）。" Actually it might need translation to Simplified Chinese. But it's already Chinese? The translation likely would be "旧的接口被标记为“已弃用”（deprecated）" or similar. But we must preserve Markdown structure exactly. It's a single sentence. So we produce the translated Markdown. Probably: "旧的接口被标记为“已弃用”（deprecated）。" Should we translate the parentheses content? The word deprecated is an English term, usually used as "已弃用" or "过时". The original says "（deprecated）". So keep parentheses with English? We can translate into Chinese: "（已弃用）". The instruction: keep proper nouns/product names when appropriate. So we keep deprecated? But it's a term. I'd translate to Chinese. Let's produce: "旧的接口被标记为“已弃用”（deprecated）。" Wait duplication? Maybe: "旧的接口被标记为“已弃用”（deprecated）。" But that still has both Chinese and English. Might be fine. I'll produce that.
...done thinking.

旧的接口被标记为“已弃用”（deprecated）。

**分支**

Thinking...
We need to translate to Simplified Chinese. The text is already in Chinese: "持续集成（Continuous Integration，CI），也叫"基于主干开发"（Trunk-Based Development）。" It's a statement. We need preserve Markdown structure exactly. It's just a paragraph. The translation may not need changes. Maybe we keep as is. We should not alter code fences, but there's no code. Should keep links? No. So output same. Probably keep the same. So output:

持续集成（Continuous Integration，CI），也叫"基于主干开发"（Trunk-Based Development）。
...done thinking.

持续集成（Continuous Integration，CI），也叫"基于主干开发"（Trunk-Based Development）。

**重构、架构和YAGNI**

重构对架构最大的影响在于，通过重构，我们能得到一个设计良好的代码库，使其能够优雅地应对不断变化的需求。"在编码之前先完成架构"这种做法最大的问题在于，它假设了软件的需求可以预先充分理解。

**重构与软件开发过程**

既牢固可靠又能快速响应变化的需求。

**自动化重构**

不仅能处理文本，还能处理语法树，这是IDE相比于文本编辑器更先进的地方。重构工具不仅需要理解和修改语法树，还要知道如何把修改后的代码写回编辑器视图。如果我给一个变量改名，工具会提醒我修改使用了旧名字的注释。能借助语法树来分析和重构程序代码，这是IDE与普通文本编辑器相比具有的一大优势。

**第3章　代码的坏味道**

Thinking...
The user provides a Markdown snippet: "**神秘命名（Mysterious Name）**". It already has Chinese and English. The instruction: "Translate the given Markdown to Simplified Chinese." It's already in Simplified Chinese. But maybe they want to translate the English part: "Mysterious Name" to Chinese. But the Chinese part is "神秘命名". It is already translated. However the snippet is: **神秘命名（Mysterious Name）**. This is a bold heading. The translation might keep the Chinese and optionally remove the English? But the instruction says "Translate to Simplified Chinese" preserving Markdown. So we should translate the English "Mysterious Name" to Chinese. But it's already there. So perhaps we need to remove the English parentheses. But it's ambiguous. They want translation of given markdown. The given markdown includes Chinese. They might want to keep Chinese and also translate the English part? But it's already translated. I'd output the same? Possibly just keep the markdown as is. The instruction: "Translate the given Markdown to Simplified Chinese." The text includes Chinese already. Maybe we should remove the English part and keep only Chinese. But the instructions don't say to remove. It says "Translate", not "Edit". The safe approach is to leave as is because it's already in Simplified Chinese. But maybe we need to keep the translation consistent: "**神秘命名**" instead of including parentheses. But I'll output the original: **神秘命名（Mysterious Name）**. It's already correct. So final answer: **神秘命名（Mysterious Name）**.
...done thinking.

**神秘命名（Mysterious Name）**

命名是编程中最难的两件事之一\[mf-2h\]。正因为如此，改名可能是最常用的重构手法，包括改变函数声明（用于给函数改名）、变量改名、字段改名。

Thinking...
We need to translate Markdown to Simplified Chinese. The Markdown: "**重复代码（Duplicated Code）**". The instruction: keep proper nouns when appropriate. "Duplicated Code" is a term. We might translate it as "重复代码" but it's already given. Wait: original: **重复代码（Duplicated Code）**. That is "重复代码（Duplicated Code）". They used Chinese "重复代码" plus English "Duplicated Code". We just need to translate entire Markdown? But the text is already in Chinese plus English. Maybe we keep as is? But instruction: "Translate the given Markdown to Simplified Chinese." It's already partly Chinese. But we need to translate any English parts. The English "Duplicated Code" should be translated to Simplified Chinese, but the Chinese part already says "重复代码". Maybe we should keep both Chinese and English? The example is like "重复代码（Duplicated Code）". We could translate to "重复代码（重复代码）"? But that's redundant. Possibly they want to keep English inside parentheses? But the instruction says translate to Simplified Chinese, keep proper nouns. "Duplicated Code" is a term; we might translate to "重复代码". So maybe final: **重复代码**? But the parentheses could be removed. But the original had Chinese inside parentheses plus English. We might translate to **重复代码（重复代码）**? That seems odd.

Maybe the rule is to translate all text into Simplified Chinese. So "Duplicated Code" -> "重复代码". But we already have Chinese word. So final result: **重复代码（重复代码）**? But that is duplication. Or we could keep the English as is: but the instruction says translate to Simplified Chinese. So we should translate the English to Chinese. So we might produce **重复代码（重复代码）**. But maybe better: **重复代码（重复代码）** but that duplicates. Maybe we drop the parentheses and keep only Chinese: **重复代码**. But the original had both. Let's decide: final output should be **重复代码（重复代码）**? Hmm.

Let's read instructions carefully: "Translate the given Markdown to Simplified Chinese." So all English should be translated. The heading "Duplicated Code" should be translated to "重复代码". Already there. The parentheses maybe originally had English, but we can just translate to Chinese. So the entire line would become "**重复代码**". But that would remove the parentheses entirely. But we might keep parentheses and Chinese translation inside. So "**重复代码（重复代码）**" is redundant but matches rule. But perhaps they expect to keep the English part if it's a proper noun, but "Duplicated Code" is a term but not a proper noun. But still it's a term. It's not a proper noun like "Apple". So we can translate. Let's output "**重复代码（重复代码）**" or "**重复代码**"? I'm leaning to "**重复代码（重复代码）**" to preserve parentheses.

But maybe they want to keep the original formatting: "**重复代码（Duplicated Code）**" and only translate the English part: "Duplicated Code" -> "重复代码". So result: "**重复代码（重复代码）**". That matches the rule: keep markdown structure. Yes.

Thus final answer: **重复代码（重复代码）**.
...done thinking.

**重复代码（重复代码）**

Thinking...
We just need to translate "**过长函数（Long Function）**" to Chinese? The original is in Chinese already: "过长函数（Long Function）". That phrase seems already Chinese with English parenthetical. The translation would be same. We should preserve formatting: bold. So just output same line. Should not change. The instructions say translate to Simplified Chinese; it's already Chinese. But we might translate "Long Function" to "过长函数". But already there. Maybe the translation should be "**过长函数（Long Function）**" unchanged. Provide only that line.
...done thinking.

**过长函数（Long Function）**

积极地分解函数.

原则：每当感觉需要以注释来说明点什么的时候，我们就把需要说明的东西写进一个独立函数中，并以其用途（而非实现手法）命名。关键不在于函数的长度，而在于函数"做什么"和"如何做"之间的语义距离。

如何确定该提炼哪一段代码呢？一个很好的技巧是：寻找注释。它们通常能指出代码用途和实现手法之间的语义距离。

条件表达式和循环常常也是提炼的信号。你可以使用分解条件表达式处理条件表达式。

Thinking...
We need to translate the Markdown to Simplified Chinese, preserving structure. The text is simple: "对于庞大的switch语句，其中的每个分支都应该通过提炼函数变成独立的函数调用。如果有多个switch语句基于同一个条件进行分支选择，就应该使用以多态取代条件表达式。"

We need to translate to Simplified Chinese. The content is already in Simplified Chinese. Wait it's Chinese. The prompt says "Markdown to translate" includes Chinese. Maybe it's actually English? Let's read: "对于庞大的switch语句，其中的每个分支都应该通过提炼函数变成独立的函数调用。如果有多个switch语句基于同一个条件进行分支选择，就应该使用以多态取代条件表达式。"

This is Chinese. The translation request: "Translate the given Markdown to Simplified Chinese." It is already Simplified Chinese. So translation would be identical. But maybe they want to keep as is. But perhaps the original was English but given Chinese? Let's double-check. The content: "对于庞大的switch语句，其中的每个分支都应该通过提炼函数变成独立的函数调用。如果有多个switch语句基于同一个条件进行分支选择，就应该使用以多态取代条件表达式。"

Maybe they want to keep Chinese as is. Since it's already in Simplified Chinese, translation would be same. We must preserve Markdown structure. There's no Markdown markup here except maybe paragraph. So output same content.

Thus output: same Chinese paragraph.

Return only translated Markdown, no commentary.

...done thinking.

对于庞大的switch语句，其中的每个分支都应该通过提炼函数变成独立的函数调用。如果有多个switch语句基于同一个条件进行分支选择，就应该使用以多态取代条件表达式。

应该将循环和循环内的代码提炼到一个独立的函数中。如果你发现提炼出的循环很难命名，可能是因为其中做了几件不同的事。如果是这种情况，请勇敢地使用拆分循环将其拆分成各自独立的任务。

Thinking...
We need to translate to Simplified Chinese: "过长参数列表（Long Parameter List）". The original is "**过长参数列表（Long Parameter List）**". It's bold. Should translate the English part: "Long Parameter List" to Chinese? But the Chinese part is already "过长参数列表". The English part is presumably kept? We might translate the English to Chinese: "过长参数列表（过长参数列表）"? Wait no, we need to translate the entire markdown to Simplified Chinese. The original string has Chinese and English. So we should translate the English part "Long Parameter List" to Chinese. But we should keep the Chinese part. So final: "**过长参数列表（过长参数列表）**". But that would be duplicate. Maybe we want to translate only the English part: "Long Parameter List" to "过长参数列表". Then we might remove the Chinese part? But the original had Chinese already. We could do "**过长参数列表（过长参数列表）**". But that's redundant. The requirement: "Translate the given Markdown to Simplified Chinese." The given markdown has Chinese and English. But translation only necessary for English parts. So we convert "Long Parameter List" to Chinese. We keep the original Chinese. So final: "**过长参数列表（过长参数列表）**". That seems acceptable. Or we could keep "Long Parameter List" untranslated as it's a product name. But it's not a proper noun. But the instructions say keep proper nouns/product names when appropriate. It's not a product name. So translation is correct.

Thus output: **过长参数列表（过长参数列表）**.
...done thinking.

**过长参数列表（过长参数列表）**

如果可以向某个参数发起查询而获得另一个参数的值，那么就可以使用以查询取代参数去掉这第二个参数。

如果你发现自己正在从现有的数据结构中抽出很多数据项，就可以考虑使用保持对象完整手法，直接传入原来的数据结构。如果有几项参数总是同时出现，可以用引入参数对象将其合并成一个对象。

如果某个参数被用作区分函数行为的标记（flag），可以使用移除标记参数。

使用类可以有效地缩短参数列表。如果多个函数有同样的几个参数，引入一个类就尤为有意义。你可以使用函数组合成类，将这些共同的参数变成这个类的字段。

Thinking...
We just translate the heading. It is Markdown heading with bold text. The translation is: "**全局数据（Global Data）**". But we need to translate the text inside, preserving Markdown. The original has "**全局数据（Global Data）**". Actually the original has "全局数据（Global Data）". Wait: The given markdown: **全局数据（Global Data）**. So inside the bold, Chinese "全局数据" plus parentheses with "Global Data". So we translate "全局数据" which is already Chinese. "Global Data" maybe keep? The instruction says keep proper nouns product names when appropriate. "Global Data" maybe translation needed? The instruction: "Translate the given Markdown to Simplified Chinese." So we translate everything into Simplified Chinese, but we might keep the English phrase inside parentheses? But likely we translate "Global Data" to "全局数据". But it's already Chinese; we might just keep it as is. But we need to translate everything to Simplified Chinese, but the English phrase might be replaced with Chinese. But the instruction says "Keep proper nouns/product names when appropriate." "Global Data" might be a product name? It's likely a term, not a product. We might translate. The original Chinese is same as translation. So the result will be identical: **全局数据（全局数据）**? But that would duplicate Chinese. Might be confusing. But perhaps the original had the English term "Global Data" as translation? Actually original is Chinese plus English inside parentheses. We need to translate to Simplified Chinese: maybe just keep Chinese and English. The English is maybe not necessary. Could keep as is: **全局数据（Global Data）**. But that is already Chinese. So translation yields same. So output is the same.

Thus the answer is: **全局数据（Global Data）**.
...done thinking.

**全局数据（Global Data）**

封装变量。有少量的全局数据或许无妨，但数量越多，处理的难度就会指数上升。

Thinking...
The user wants to translate the given Markdown to Simplified Chinese. They provided: "**可变数据（Mutable Data）**". The content is already in Chinese with the English term inside parentheses. But they might want to translate the English part? The original English is "Mutable Data". So translation of "Mutable Data" is "可变数据". But they already have "可变数据（Mutable Data）". The requirement: preserve Markdown structure, do NOT translate code fences, inline code, etc. Just translate. The given Markdown is just bold. The translation likely should be "**可变数据**" or maybe "**可变数据（Mutable Data）**" but they already have it. However maybe they want to remove the English? The instruction: translate given Markdown to Simplified Chinese. The content is already Chinese. But maybe they want to translate the English part "Mutable Data" to Chinese, but keep the English in parentheses? It's already "可变数据（Mutable Data）". In Chinese, you might translate the English part to Chinese too? But we are told to translate the given Markdown to Simplified Chinese. The English phrase "Mutable Data" is inside parentheses. We might translate that to Chinese: "可变数据". But it's redundant. But maybe we keep the English in parentheses? The instruction: "Keep proper nouns/product names when appropriate." There's no proper nouns. The phrase "Mutable Data" is a technical term. But we might translate it to Chinese. So final output should be "**可变数据（可变数据）**"? That seems weird. Actually maybe we remove parentheses: "**可变数据**". But given the original contains the parentheses, we preserve structure. The best answer: "**可变数据（Mutable Data）**" is already correct. But maybe they want to translate the English part: "**可变数据（可变数据）**". But that duplicates. They might want just "**可变数据**". But I think they just want the translation of the phrase "Mutable Data" to Chinese: "可变数据". Since the Chinese part is already there, maybe it's a mistake. They might want to output "**可变数据**". I'll output "**可变数据**".
...done thinking.

**可变数据**

可以用封装变量来确保所有数据更新操作都通过很少几个函数来进行，使其更容易监控和演进。

如果一个变量在不同时候被用于存储不同的东西，可以使用拆分变量将其拆分为各自不同用途的变量，从而避免危险的更新操作。使用移动语句和提炼函数尽量把逻辑从处理更新操作的代码中搬移出来，将没有副作用的代码与执行数据更新操作的代码分开。设计API时，可以使用将查询函数和修改函数分离。

尽早使用移除设值函数，缩小变量作用域。

Thinking...
We need to translate the given markdown to Simplified Chinese. The text is only "**发散式变化（Divergent Change）**". Actually it is already in Chinese? Wait: "**发散式变化（Divergent Change）**" The content in bold: "发散式变化（Divergent Change）". It includes the Chinese phrase "发散式变化" and the English term "Divergent Change" inside parentheses. The translation requirement: "Return ONLY the translated Markdown, no extra commentary." So we need to translate the Markdown to Simplified Chinese, preserving structure. But the original is already partly Chinese. Maybe we need to translate the English part "Divergent Change" into Chinese? The text: "**发散式变化（Divergent Change）**". The English part is already translated? But it's "Divergent Change". The instruction says "Translate the given Markdown to Simplified Chinese." The English "Divergent Change" should be translated into Chinese? But it is inside parentheses. Should we translate to Chinese or leave as is? The original is "发散式变化（Divergent Change）" where Chinese phrase already has the translation. Maybe it's a heading that includes both Chinese and English. The requirement is to translate the Markdown to Simplified Chinese. So we should keep Chinese phrase, but maybe we need to translate "Divergent Change" into Chinese. But it's inside parentheses after Chinese phrase. Maybe the original text had the English term inside parentheses. The translation could be "发散式变化（发散变化）"? But that duplicates. However, "Divergent Change" is the English term for "发散式变化". Usually you'd keep the English as well for reference. But the instruction is to translate the given Markdown to Simplified Chinese. We can keep the English part as is, because it's already part of the original text. But the English part is not translated. But since the whole text is "发散式变化（Divergent Change）", which is partially translated. We might be expected to keep the same. The instruction says "Preserve Markdown structure exactly". The heading is bold. So we should output "**发散式变化（Divergent Change）**" unchanged. The only translation needed is possibly converting the English to Chinese, but it's inside parentheses. However, the original may have both Chinese and English. The translation should keep the same. So final output: "**发散式变化（Divergent Change）**". Let's produce that.
...done thinking.

**发散式变化（Divergent Change）**

如果某个模块经常因为不同的原因在不同的方向上发生变化，发散式变化就出现了。

提炼拆分。

Thinking...
The user wants to translate the given Markdown to Simplified Chinese. The given text:

**霰弹式修改（Shotgun Surgery）**

This already includes Chinese text. It says "霰弹式修改（Shotgun Surgery）" which is presumably a translation of "Shotgun Surgery" (a software design smell). The text is inside bold markup **...**. So we keep the bold. We need to preserve the Markdown exactly, so output:

**霰弹式修改（Shotgun Surgery）**

But maybe we need to translate the entire phrase? The Chinese part is "霰弹式修改", the English part is "Shotgun Surgery". We might not need to translate. The user wants translation to Simplified Chinese. The provided text is already in Chinese. But we could confirm if "霰弹式修改" is correct. In Chinese, the common term is "霰弹式修改" or "散弹式修改"? Might be "霰弹式修改（Shotgun Surgery）". The Chinese is correct. Since it's already in Simplified Chinese, no change needed. So we output the same string.

Thus final answer:

**霰弹式修改（Shotgun Surgery）**
...done thinking.

**霰弹式修改（Shotgun Surgery）**

如果每遇到某种变化，你都必须在许多不同的类内做出许多小修改，你所面临的坏味道就是霰弹式修改。

搬移函数和搬移字段把所有需要修改的代码放进同一个模块里。如果有很多函数都在操作相似的数据，可以使用函数组合成类。如果有些函数的功能是转化或者充实数据结构，可以使用函数组合成变换。如果一些函数的输出可以组合后提供给一段专门使用这些计算结果的逻辑，这种时候常常用得上拆分阶段。

Thinking...
We need to translate the provided Markdown into Simplified Chinese. The given text:

"一个常用的策略就是使用与内联（inline）相关的重构------如内联函数（1或是内联类------把本不该分散的逻辑拽回一处。完成内联之后，你可能会闻到过长函数或者过大的类的味道，再用与提炼相关的重构手法将其拆解成更合理的小块。"

We need to keep Markdown structure. The text includes hyphens and dashes. There's no markdown headings, no lists, no code fences. Just a paragraph.

We need to translate into Simplified Chinese. It's already in Chinese. Maybe it's partially translated? The phrase "内联（inline）" includes English in parentheses; "重构" is Chinese. The translation should preserve that.

But maybe we need to correct the text? The request: "Translate the given Markdown to Simplified Chinese." The text is already Chinese. Maybe we translate it to simplified Chinese from some other variant? It's already simplified Chinese. But maybe it's originally in another language? The text seems partially Chinese. Actually it appears to be a Chinese paragraph describing a strategy. It uses some English words: "inline". But it's mostly Chinese. Maybe the instruction is to translate to Simplified Chinese, but it's already simplified Chinese. But we might keep it as is.

We need to preserve markdown structure exactly. No code fences. There's no markdown structure except plain paragraph.

Thus we just output the same paragraph.

But the translation might be "一个常用的策略就是使用与内联（inline）相关的重构——比如内联函数或内联类——把本不该分散的逻辑拽回一处。完成内联之后，你可能会闻到过长函数或者过大的类的味道，再用与提炼相关的重构手法将其拆解成更合理的小块。"

The original had dashes '------'. We can keep them? The request says preserve Markdown structure exactly. So we should keep them as they are. But maybe we can correct them? It's ambiguous. They used 6 hyphens? It's maybe a separator. It's not markdown. We should preserve it.

Thus we output:

"一个常用的策略就是使用与内联（inline）相关的重构------如内联函数（1或是内联类------把本不该分散的逻辑拽回一处。完成内联之后，你可能会闻到过长函数或者过大的类的味道，再用与提炼相关的重构手法将其拆解成更合理的小块。"

But maybe they want the phrase "如内联函数（1或是内联类" to be translated to "比如内联函数或内联类". But the instruction didn't say to correct errors, only to translate.

Thus output same.
...done thinking.

一个常用的策略就是使用与内联（inline）相关的重构------如内联函数（1或是内联类------把本不该分散的逻辑拽回一处。完成内联之后，你可能会闻到过长函数或者过大的类的味道，再用与提炼相关的重构手法将其拆解成更合理的小块。

Thinking...
We need to translate the Markdown to Simplified Chinese. The content is "**依恋情结（Feature Envy）**". We must preserve Markdown structure exactly. So the translation should keep the bold markers. So "**依恋情结（Feature Envy）**" is the same? Actually the original text is Chinese? It's "依恋情结（Feature Envy）". It seems already Chinese with English part. The instruction says: translate the given Markdown to Simplified Chinese. It's already simplified Chinese. But maybe they want "Attachment Tendency (Feature Envy)"? But "依恋情结" is simplified Chinese. There's no translation needed. But maybe "Feature Envy" is an English term that might need translation: "Feature Envy" can be "特征妒忌" or "属性妒忌" (common translation for feature envy). In Chinese, "Feature Envy" is usually "属性嫉妒" or "特征妒忌". Let's consider standard translation: In programming, "Feature Envy" is a code smell where a method seems to depend too much on data of another class. Usually it's translated as "属性/特征妒忌". In Chinese, "Feature Envy" is often called "属性妒忌" (shǔxìng dùjì). Or "特征嫉妒". The phrase "依恋情结" is not usual translation for Feature Envy. So maybe the original was Chinese translation: "Feature Envy" => "依恋情结". But the instruction is to translate the Markdown to Simplified Chinese, and it's already simplified Chinese. But we can consider that "Feature Envy" should be translated to "特征妒忌" or "属性嫉妒". But the original had parentheses "Feature Envy". So we may translate that part too. The original has "**依恋情结（Feature Envy）**". The phrase inside parentheses is English. We need to translate it. We might produce "**依恋情结（特征妒忌）**" or "**依恋情结（属性嫉妒）**". Which one is more common? In Chinese literature, I think "Feature Envy" is translated as "特征嫉妒" (Zhèng). But also "属性妒忌" is used. The typical translation for "Feature Envy" in Chinese is "属性妒忌". Let's go with "属性妒忌". So the translation would be "**依恋情结（属性妒忌）**". But maybe they want to translate the Chinese too: "依恋情结" maybe should be "依赖情结"? But "依恋情结" seems okay. But maybe "Attachment" is "依恋" which is okay. So final output: "**依恋情结（属性妒忌）**". Should we keep original? The instruction says "Return ONLY the translated Markdown". So we output that. No other commentary.
...done thinking.

**依恋情结（属性妒忌）**

模块化，就是力求将代码分出区域，最大化区域内部的交互、最小化跨区域的交互。

一个函数跟另一个模块中的函数或者数据交流格外频繁，远胜于在自己所处模块内部的交流，这就是依恋情结的典型情况。

Thinking...
The user wants to translate the markdown into Simplified Chinese. There's a heading? The text is "**数据泥团（Data Clumps）**" which is a bold. In Chinese, "数据泥团" is Chinese translation. The original has "Data Clumps". Possibly keep the English term? The rule: Keep proper nouns/product names when appropriate. "Data Clumps" is a term. So we might keep it as is? But "数据泥团" is translation. We need to translate the whole markdown. So "**数据泥团（Data Clumps）**". That's the entire content. So translation: "**数据泥团（Data Clumps）**". Already Chinese translation included. So we need to return that. No extra commentary.
...done thinking.

**数据泥团（Data Clumps）**

总是绑在一起出现的数据真应该拥有属于它们自己的对象。

Thinking...
We need to translate to Simplified Chinese. The heading is just a bold text: **基本类型偏执（Primitive Obsession）**. The part after parentheses is in English: "Primitive Obsession". Should we translate that? The instructions: "Keep proper nouns/product names when appropriate." Primitive Obsession is a term from design patterns; likely keep as is. The Chinese part "基本类型偏执" is translation. So entire line should be: **基本类型偏执（Primitive Obsession）**. No change. But we might need to translate "Primitive Obsession" maybe keep original? The instruction: Keep proper nouns/product names when appropriate. "Primitive Obsession" is a concept. Might keep as is. So output same line. Return only the translated Markdown.
...done thinking.

**基本类型偏执（Primitive Obsession）**

把钱当作普通数字来计算的情况、计算物理量时无视单位（如把英寸与毫米相加）的情况以及大量类似if
(a \< upper && a \> lower)这样的代码。

运用以对象取代基本类型。

Thinking...
We need to translate the given Markdown to Simplified Chinese, preserving markdown structure, headings, lists, emphasis. The given text: "**重复的switch （Repeated Switches）**". This is a bold title with Chinese and English. The translation should be Simplified Chinese. We preserve bold. The phrase "Repeated Switches" is the translation of "重复的switch". But we have "重复的switch （Repeated Switches）". So it's already in Chinese with English translation in parentheses. We need to translate to Simplified Chinese: presumably the English translation may remain as is or could be replaced? The instruction: "Translate the given Markdown to Simplified Chinese." So the entire content should be translated to Simplified Chinese. The original already has Chinese. The English translation in parentheses might be considered as translation of the title. If we translate the whole content, we might keep the parentheses with the English translation? The content is "重复的switch （Repeated Switches）". That already contains Chinese and English. We might translate the English part to Chinese as well. But the phrase "Repeated Switches" is the English meaning. In Simplified Chinese translation we might write "重复的switch（重复的switch）"? But we need to preserve structure. But we can translate the English part to Chinese, like "重复的switch（重复的switch）" but that duplicates. Another approach: keep the English translation as is, but we are translating the whole text to Simplified Chinese, which may keep it. But the instruction: "Translate the given Markdown to Simplified Chinese." The original is partially Chinese. The English part is likely not needed. We could translate "Repeated Switches" to "重复的switch". So final: "**重复的switch（重复的switch）**". But maybe keep the English in parentheses for context? But translation likely expects only Chinese: "**重复的switch（重复的switch）**". That seems redundant but okay.

Alternatively, we could keep the English translation to explain it. But the instruction says translate to Simplified Chinese, so maybe we should translate the English part to Chinese. So I'd output: **重复的switch（重复的switch）**. That's the only content.

We need to preserve Markdown: bold. The original had double asterisks. We'll keep that.

Return ONLY translated Markdown.
...done thinking.

**重复的switch（重复的switch）**

多态。

**循环语句（Loops）**

Thinking...
We need to translate "？管道操作（如filter和map）" into Simplified Chinese. The original text is partially already in Chinese? The phrase starts with a question mark "？". Actually it's a Chinese heading or question: "？管道操作（如filter和map）". This seems like the heading for a question: "？管道操作（如filter和map）". It might be a heading, maybe it's a heading for a section on pipeline operations. We need to translate. However "管道操作" is already Chinese for pipeline operations. The phrase "如filter和map" means "such as filter and map". So the whole is "？管道操作（如filter和map）". The question mark at the beginning is maybe part of the title? It might be a heading like "Question: Pipeline Operations (like filter and map)". The heading might be a markdown heading but we don't have heading markers. The content is just a line "？管道操作（如filter和map）". Since we need to preserve markdown structure exactly, but we only have this line. So we should translate it.

But the phrase is already Chinese. We can leave as is. But maybe we need to translate to Chinese: "？管道操作（如filter和map）" is fine. The only possible translation could be "？管道操作（例如 filter 和 map）". Slight change in punctuation. But we need to preserve the original. Maybe keep the same. I think best to keep as is.

But the instruction: "Translate the given Markdown to Simplified Chinese." It's already Simplified Chinese. But maybe the original was English but partially Chinese. Actually "filter" and "map" are English. So we could translate them as "filter" and "map" remain unchanged. So the translation remains the same. So output the same line. Probably no change needed.

Thus return exactly "？管道操作（如filter和map）".
...done thinking.

？管道操作（如filter和map）

Thinking...
The user asks: translate given Markdown to Simplified Chinese. The input is "**冗赘的元素（Lazy Element）**". It's already Chinese. Actually it's in Chinese: "冗赘的元素（Lazy Element）". Possibly the original was English? But we need to translate to Simplified Chinese. It's already Chinese. Maybe the title is in English? Wait: The phrase "Lazy Element" is English. The title is "**冗赘的元素（Lazy Element）**". We need to translate to Simplified Chinese. The Chinese part "冗赘的元素" is Chinese. The parentheses contain English "Lazy Element". We need to translate that as well? The instruction: "Translate the given Markdown to Simplified Chinese." The content is already partially Chinese. We need to keep Markdown formatting. So we should translate "Lazy Element" into Chinese. In Chinese that might be "懒惰元素" or "懒加载元素". Probably "懒惰元素". But maybe "懒元素". The phrase "Lazy Element" is a technical term. In Chinese context, we might translate it as "懒元素" or "延迟元素". But "懒惰元素" is a direct translation. The original text has Chinese first part "冗赘的元素". So we could write "**冗赘的元素（懒惰元素）**". Or maybe keep "Lazy Element" unchanged? The instruction: "Translate the given Markdown to Simplified Chinese." So we should translate "Lazy Element". So I'll translate "Lazy Element" to "懒惰元素". Provide the result.

Thus final output: **冗赘的元素（懒惰元素）**.

We must preserve markdown. No extra commentary.
...done thinking.

**冗赘的元素（懒惰元素）**

随着重构的进行越变越小，类最后只剩了一个函数。及时删除这个类，使用内联函数或是内联类。

Thinking...
The user wants translation to Simplified Chinese. The text is:

**夸夸其谈通用性（Speculative Generality）**

But this already appears to be a translation of "Speculative Generality" in Chinese: "夸夸其谈通用性". However, maybe the original English phrase was "Speculative Generality". The user provides that Markdown to translate. We need to translate to Simplified Chinese. The phrase is in bold. The translation should preserve bold. So "**Speculative Generality**" would be "**夸夸其谈通用性**". But the text includes both Chinese and English: "**夸夸其谈通用性（Speculative Generality）**". They likely want to translate the entire phrase to Chinese. But the phrase already contains Chinese. Possibly the original English phrase "Speculative Generality" should be translated to Chinese: "夸夸其谈通用性". The bracket contains the English. Maybe we should translate to Chinese only: "**夸夸其谈通用性**". Or we might translate the whole phrase, including the English in brackets? The instructions: "Translate the given Markdown to Simplified Chinese." The original Markdown includes Chinese characters. There's no English. So we just translate to Simplified Chinese. But it's already Chinese. But maybe the original phrase is in English, and the user inserted a translation incorrectly? The phrase includes both Chinese and English. The proper Chinese translation of "Speculative Generality" is "夸夸其谈通用性". The parenthesis is the English. We might keep the English or we might remove it. The instruction says: "Preserve Markdown structure exactly." The structure is a bold phrase containing Chinese and English in parentheses. We need to translate to Simplified Chinese, but maybe keep the English in parentheses? But that would be redundant. But the instruction says "Translate the given Markdown to Simplified Chinese." That implies we should translate any English to Chinese. The given Markdown already has Chinese. There's no English except the phrase in parentheses. So we should translate that phrase to Chinese. But the phrase is already Chinese. So we might just keep it. But we need to decide whether to keep the English in parentheses or remove it.

The original user likely expects translation of "Speculative Generality" into Chinese. But the provided Markdown already includes Chinese. Possibly the user mistakenly provided both languages. So we could remove the English part. But the instructions say preserve structure exactly. Removing part changes structure. But maybe we can keep the parentheses with the English phrase but it's not required? The instruction: "Translate the given Markdown to Simplified Chinese." If we keep the parentheses with the English phrase, that is not purely Chinese. But the instruction says "Return ONLY the translated Markdown, no extra commentary." It doesn't forbid keeping English parentheses. But translation is to Chinese. So I think we should translate the phrase inside the parentheses to Chinese too. But that phrase is "Speculative Generality". The translation is "夸夸其谈通用性". So if we translate the entire bold phrase, it becomes "**夸夸其谈通用性**". But that duplicates the Chinese. The parentheses become redundant. We could replace the entire bold phrase with just the Chinese translation.

Let's examine the original phrase: "**夸夸其谈通用性（Speculative Generality）**". The user might have inserted Chinese translation of "Speculative Generality" already. So we could simply output the same: "**夸夸其谈通用性（Speculative Generality）**". But that is not translation. But maybe they want to keep the Chinese translation. It's ambiguous. But the safest is to keep the Chinese phrase exactly. Since translation is already there, we might just preserve. There's no transformation needed. But we might still output the same.

However, the user said "Translate the given Markdown to Simplified Chinese." The given text is already Chinese. So translation is trivial. We can output the same. That satisfies the requirement.

But we need to preserve Markdown structure exactly. The given Markdown has bold and parentheses. So we output exactly "**夸夸其谈通用性（Speculative Generality）**".

Hence final answer: same string.
...done thinking.

**夸夸其谈通用性（Speculative Generality）**

用不上的装置只会挡你的路，所以，把它搬开吧。

Thinking...
We need to translate to Simplified Chinese, but keep markdown structure. The content is "**临时字段（Temporary Field）**". They already have Chinese and English. The instruction: keep proper nouns when appropriate. The phrase is already bilingual. Should we translate? It's already bilingual: Chinese "临时字段" and English in parentheses. Possibly no translation needed. The instruction says "translate the given Markdown to Simplified Chinese." It is already partly Chinese. We should produce the translation but keep markdown structure. The content is bold. So we need to output **临时字段（Temporary Field）** as is. But maybe we need to translate the English part? The English part is in parentheses; we can keep it. The rule: keep proper nouns. "Temporary Field" is a translation of "临时字段". So we can keep that. So final output: **临时字段（Temporary Field）**.
...done thinking.

**临时字段（Temporary Field）**

其内部某个字段仅为某种特定情况而设。

Thinking...
We just translate the heading. It's a heading? Actually it's in bold? The original text: **过长的消息链（Message Chains）** That's already Chinese. There's no translation needed? It's already Chinese plus English in parentheses. The instruction says translate the given Markdown to Simplified Chinese. It's already simplified Chinese. The translation is maybe same. There's no change. So we output the same. Ensure preserve Markdown. So just output: **过长的消息链（Message Chains）**.
...done thinking.

**过长的消息链（Message Chains）**

先观察消息链最终得到的对象是用来干什么的，看看能否以提炼函数把使用该对象的代码提炼到一个独立的函数中，再运用搬移函数把这个函数推入消息链。

Thinking...
We need to translate the given Markdown. The content is:

**中间人（Middle Man）**

Actually original is "**中间人（Middle Man）**". Wait, the original is the title in Chinese with English. It is already partially translated? The user wants to translate the given Markdown to Simplified Chinese. The given text already contains Chinese "中间人" and English "Middle Man". The instruction: translate given Markdown to Simplified Chinese. But it's already Chinese. Maybe it's a mistake; but we should translate the English parts into Chinese while preserving the Chinese parts? Actually "中间人（Middle Man）" includes Chinese. The English "Middle Man" is in parentheses. We should translate that to Chinese within parentheses? Or keep the Chinese? The instruction says "Translate the given Markdown to Simplified Chinese." So we should translate the English words "Middle Man" into Chinese within the parentheses? Possibly replace "Middle Man" with "中间人"? But then we'd get Chinese duplicated: "中间人（中间人）". That seems odd.

Alternatively, perhaps we should keep Chinese as is and translate English part "Middle Man" to Chinese inside parentheses. But the heading already has Chinese, maybe the English part is for reference. But we need to produce a Chinese version, but it's already Chinese. But maybe the "Middle Man" is a product name that should not be translated. But instructions: "Keep proper nouns/product names when appropriate." "Middle Man" might be a proper noun (product name). So we should keep it as "Middle Man". So the translation of "Middle Man" would not be necessary because it's a proper noun. So we keep "Middle Man" as is. So the result is same as input: "**中间人（Middle Man）**". But we need to translate to Simplified Chinese; the Chinese part is already simplified. So the output remains the same. There's no code fences or inline code spans.

Thus output is "**中间人（Middle Man）**".

Check if any formatting changes needed: The headings? It's bold. So we just output the same. Done.
...done thinking.

**中间人（Middle Man）**

某个类的接口有一半的函数都委托给其他类，这样就是过度运用。这时应该使用移除中间人。

Thinking...
We just translate "内幕交易（Insider Trading）". Keep heading formatting? It's just bold. We translate to Simplified Chinese: "内幕交易（Insider Trading）". It's same because product names? It's just phrase. So translation: "内幕交易（Insider Trading）". The Chinese is same. But maybe keep same? It already in Chinese. Might need translation? Actually phrase "内幕交易" is Chinese, parentheses contain English. So just keep as is. So final.
...done thinking.

**内幕交易（Insider Trading）**

模块之间大量交换数据，因为这会增加模块间的耦合。

在实际情况里，一定的数据交换不可避免，但我们必须尽量减少这种情况，并把这种交换都放到明面上来。

**过大的类（Large Class）**

Thinking...
We just translate the phrase. Keep markdown bold. So "**异曲同工的类（Alternative Classes with Different Interfaces）**" Should translate title to Chinese? It already partly Chinese. The phrase "Alternative Classes with Different Interfaces" can be translated to "不同接口的替代类" but maybe keep in parentheses. The overall phrase: "**异曲同工的类（Alternative Classes with Different Interfaces）**" could be translated to "**异曲同工的类（不同接口的替代类）**". Let's output that.
...done thinking.

**异曲同工的类（不同接口的替代类）**

**纯数据类（Data Class）**

纯数据类：它们拥有一些字段，以及用于访问（读写）这些字段的函数，除此之外一无长物。

Thinking...
We need translate title in markdown. Should keep markdown structure. "**被拒绝的遗赠（Refused Bequest）**" already Chinese? It's "被拒绝的遗赠（Refused Bequest）". The translation may keep the English in parentheses? The original is in Chinese already, with English in parentheses. We might keep same. But maybe translation required: it's already Chinese. The instruction: "Translate the given Markdown to Simplified Chinese." The given markdown already contains Chinese. But we might translate the English part? It says keep proper nouns/product names. "Refused Bequest" maybe proper noun. But the Chinese part is "被拒绝的遗赠". It is already Chinese. But we can translate the English to Chinese: "被拒绝的遗赠（拒绝遗赠）"? But original shows parentheses. Maybe we translate the English to Chinese: "被拒绝的遗赠（被拒绝的遗赠）"? That seems redundant. But likely keep original. The translation maybe just preserve same. So output same markdown. Let's do that.
...done thinking.

**被拒绝的遗赠（Refused Bequest）**

子类应该继承超类的函数和数据。

不愿意支持超类的接口，就不要虚情假意地糊弄继承体系，应该运用以委托取代子类或者以委托取代超类彻底划清界限。

Thinking...
We just need to translate "**注释（Comments）**". That's already Chinese: "注释（Comments）". But the instruction says translate given Markdown to Simplified Chinese. The phrase is already Chinese with parentheses containing English. We can keep as is. Perhaps we keep it unchanged. There's no other text. So output:

**注释（Comments）**.

That's it.
...done thinking.

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

Thinking...
We need to translate into Simplified Chinese. The original has "**提炼函数（Extract Function）**". Wait, it's already in Chinese? It says "提炼函数（Extract Function）". It's bilingual: Chinese and English. The translation request is to translate the given Markdown to Simplified Chinese. But the text is already partly in Simplified Chinese, plus an English phrase "Extract Function" within parentheses. Perhaps we need to translate that phrase to Chinese as well. In such case, we would translate "提炼函数（Extract Function）" to "提炼函数（提取函数）"? But we need to preserve the structure exactly: headings, lists, emphasis. The text uses bold (**). So we should keep that. It may be a heading? No, just bold text. The instruction: "Return ONLY the translated Markdown, no extra commentary." So we need to provide just the Markdown after translation. The only line is "**提炼函数（Extract Function）**". We might translate the English part: "提炼函数（Extract Function）" -> "**提炼函数（提取函数）**". Or we could keep the English? The instruction says to translate to Simplified Chinese. So we should translate "Extract Function" into Chinese: "提取函数" or "提炼函数"? The original Chinese part already says "提炼函数". That is the same as the translation? "提炼函数" means "Extract Function". So maybe "Extract Function" is already "提炼函数". But it's repeated? They wrote "提炼函数（Extract Function）" meaning "提炼函数 (Extract Function)". That is typical. So the English part is the same as Chinese. We can translate to Chinese "提炼函数" maybe. But the Chinese part is already there. But we could keep the English part in parentheses or translate it. Usually we keep the English if it's a known name. But instruction: translate to Simplified Chinese. So we may translate the English phrase to Chinese. So final result: "**提炼函数（提炼函数）**"? But that's redundant. Might be better to translate to "提取函数" which is another term. But likely we keep "提炼函数（提炼函数）" or "提炼函数（提取函数）"? Let's consider. The typical translation of "Extract Function" is "提取函数". But "提炼函数" is also used. The original Chinese part uses "提炼函数". So maybe we keep the Chinese part unchanged and translate the English part to Chinese: "提炼函数（提炼函数）" or "提炼函数（提取函数）". But "提炼函数" appears twice. That seems odd but maybe acceptable.

Alternatively, we could remove the English entirely: "**提炼函数**" if we don't need parentheses. But the original had parentheses, so we might keep them but translate inside. Let's produce "**提炼函数（提取函数）**" because that keeps the meaning and provides translation.

Let's output that.
...done thinking.

**提炼函数（提取函数）**

![](/img/0_refactor.png)

![](/img/0_refactor-1.png)

**动机**

**将意图与实现分开**：如果你需要花时间浏览一段代码才能弄清它到底在干什么，那么就应该将其提炼到一个函数中，并根据它所做的事为其命名。因为大多数时候根本不需要关心函数如何达成其用途（这是函数体内干的事）

好名字：在一个大函数中，一段代码放着一句注释，提炼成函数，注释往往提示一个好名字。

**做法**

创造一个新函数：以"做什么"而非"怎么做"来命名。

无局部变量，直接提炼成函数；

有局部变量但只读，作为参数传递给目标函数

局部变量被赋值：只在提炼函数中被使用则可直接声明在提炼函数中；在提炼函数外也被使用则可作为提炼函数的返回值；多个变量被修改可考虑返回一个对象或者使用其他重构手法（以查询取代临时变量、拆分变量）

Thinking...
We need to translate to Simplified Chinese. The original text is in English: "**Inline Function (Inline Function)**" or "**内联函数（Inline Function）**" Wait the given Markdown to translate: "**内联函数（Inline Function）**". The translator should preserve Markdown structure, no code fences etc. It's just a bold heading: **内联函数（Inline Function）**. But the translation likely should be: "**内联函数（Inline Function）**" is already Chinese and English. But maybe we need to translate the English part? The rule: translate the given Markdown to Simplified Chinese. The text contains Chinese already, but maybe we need to keep both? It's "内联函数（Inline Function）" meaning "Inline Function (Inline Function)". We might translate "Inline Function" to Chinese "内联函数". But it's already there. Maybe they want to keep Chinese but also translate the English part. The English part inside parentheses is "Inline Function". Already Chinese translation is inside parentheses. Actually original maybe was "**Inline Function (Inline Function)**"? The given is "**内联函数（Inline Function）**". So we can keep same. No changes needed. But we might translate the English portion "Inline Function" to Chinese? But inside parentheses it's already Chinese? Wait it's Chinese inside parentheses? Let's examine: **内联函数（Inline Function）**: the Chinese is before parentheses, the English inside parentheses. So maybe we should translate the English part inside parentheses to Chinese, but it's already Chinese inside parentheses? No it's English inside parentheses. So we need to translate that to Chinese: "Inline Function" -> "内联函数". But that would duplicate Chinese. But maybe we should replace the English text with Chinese, or we can keep both? The rule: translate to Simplified Chinese. So we should translate entire content: "**内联函数（内联函数）**"? But that would be double Chinese. Probably the translator would keep the original Chinese and also translate the English inside parentheses. But given that the Chinese already present, it's ambiguous. But best is to translate the English part, resulting in "**内联函数（内联函数）**". That is consistent. However some might think to keep the English as is. But instructions say translate Markdown to Simplified Chinese. So we should translate the English phrase. So output: "**内联函数（内联函数）**". Let's produce that.
...done thinking.

**内联函数（内联函数）**

![](/img/0_refactor-2.png)

![](/img/0_refactor-3.png)

![](/img/0_refactor-4.png)

**动机**

**间接性可能带来帮助，但非必要的间接性总是让人不舒服。**

某些函数其内容和名称清晰易读

一群函数的组织不甚合理，先内联到一个大函数，再提炼。

**做法**

确定函数不具多态性

找到所有调用点执行替换（重点在于始终小步前进）

Thinking...
The user wants translation of a small Markdown snippet: "**提炼变量（Extract Variable）**". It is already in Chinese? The original is in English? Wait the snippet is "**提炼变量（Extract Variable）**" where inside parentheses there's English phrase "Extract Variable". The translation probably would be "**提炼变量（Extract Variable）**" as is, but maybe translate the English part to Chinese? The instructions: "Return ONLY the translated Markdown". Should we translate the entire phrase? The original snippet is in Chinese: "提炼变量（Extract Variable）". It's likely a heading. They want translation into Simplified Chinese. But it's already Chinese. The English phrase inside parentheses maybe should remain English or translate to Chinese? The instruction: "Translate the given Markdown to Simplified Chinese." That means we translate all English parts to Chinese. The phrase "Extract Variable" should be translated to "提炼变量" (but that is same as Chinese). Wait the Chinese phrase outside parentheses is "提炼变量" which is translation of "Extract Variable". So maybe the original is from a bilingual document where the heading shows both Chinese and English. So translating to Simplified Chinese would likely remove the English part or replace it with Chinese? But the rule: preserve structure; don't translate code fences etc. So maybe we keep the heading but translate the English part too: "提炼变量（提炼变量）"? That seems redundant. But we might translate the English part to Chinese: "提炼变量（变量提炼）"? That seems wrong.

Maybe the original snippet is from a doc that shows both Chinese and English. In translation, we only need Chinese, but the parentheses may keep the English term. The instructions: "Translate the given Markdown to Simplified Chinese." So we should convert English words to Chinese. So the heading would become "**提炼变量（提炼变量）**" or "**提炼变量（提取变量）**". But the heading originally is "**提炼变量（Extract Variable）**". The Chinese part "提炼变量" means "Extract Variable". So the English phrase is the same concept. So translation might produce: "**提炼变量（提炼变量）**" which is redundant but follows rule.

But maybe the correct translation would be "**提炼变量（提取变量）**" or "**提炼变量（变量提炼）**". But the original phrase includes Chinese part already. I think the translation to Simplified Chinese would keep Chinese part unchanged and translate the English part within parentheses to Chinese, maybe "提炼变量". So final would be "**提炼变量（提炼变量）**". But maybe we should keep the parentheses? Yes.

Thus output: **提炼变量（提炼变量）**.
...done thinking.

**提炼变量（提炼变量）**

![](/img/0_refactor-5.png)

![](/img/0_refactor-6.png)

**动机**

**提供了合适的上下文**：帮助我们将表达式分解为比较容易管理的形式，也便于理解一部分代码是干什么的。

Thinking...
We need to translate into Simplified Chinese, preserving Markdown. The phrase "**内联变量（Inline Variable）**" is already partly Chinese? Actually it's a heading maybe? It's in bold. It's "内联变量（Inline Variable）". The translation might keep both Chinese and English. But we need to translate the Markdown to Simplified Chinese. It is already Chinese. The phrase "Inline Variable" in parentheses might be left as is or translate to "内联变量"? But we already have Chinese. Maybe we should translate the English part to Chinese: "(Inline Variable)" -> "(内联变量)". But we have Chinese inside. The phrase might be redundant. But as a professional translator, I'd translate the English part: "Inline Variable" to "内联变量". So we get "**内联变量（内联变量）**". But that seems repetitive. However, we preserve structure. The original includes both. Maybe we can keep both: "**内联变量（Inline Variable）**" is fine. But the instruction: "Translate the given Markdown to Simplified Chinese." The given already includes Chinese. So minimal change: maybe we translate the English word to Chinese. So "Inline Variable" -> "内联变量". Then we get "**内联变量（内联变量）**". That might be acceptable.

But is the phrase inside parentheses needed? The translation might be simply "**内联变量**" but that would change structure? They want preserve Markdown exactly, but translation can change content. The original has bold. We should keep bold. So we might keep "**内联变量（Inline Variable）**". But it's already partially Chinese. They might want to translate the English part.

I think the safest: keep as is, because it's already Chinese. But the instruction says "Translate to Simplified Chinese." The English part "Inline Variable" should be translated. So I will change to Chinese: "**内联变量（内联变量）**". That might be weird but it's translation. Possibly better: "**内联变量（Inline Variable）**" stays same because already Chinese. But I'll translate the English: "**内联变量（内联变量）**". Let's produce that.
...done thinking.

**内联变量（内联变量）**

![](/img/0_refactor-7.png)

![](/img/0_refactor-8.png)

**动机**

有时候，变量名字并不比表达式本身更具表现力。还有些时候，变量可能会妨碍重构附近的代码。

Thinking...
We need to translate to Simplified Chinese. Preserve markdown structure. So "**改变函数声明（Change Function Declaration）**" is a bold text with parentheses. The English phrase "Change Function Declaration" is the translation. We can translate as "更改函数声明" or "修改函数声明". The given phrase in Chinese already is "改变函数声明". We can translate the English part. The Chinese part remains. The phrase includes Chinese first "改变函数声明（Change Function Declaration）". The translation should preserve the Markdown. So produce "**改变函数声明（Change Function Declaration）**". But we might need to translate "Change Function Declaration" to Chinese. The instruction: "Translate the given Markdown to Simplified Chinese." So the entire phrase is to be translated. The Chinese part "改变函数声明" is already Chinese. Maybe the original is in English? The original includes Chinese and English. We need to translate the entire text. But the English is inside parentheses. We can translate "Change Function Declaration" to Chinese, maybe "更改函数声明". So result: "**改变函数声明（更改函数声明）**". However, the Chinese inside parentheses is original Chinese "改变函数声明". The original has the same Chinese as the first part. So maybe it's a bilingual title. To translate, we should translate the English part. The result should have Chinese text for the English part. So output: "**改变函数声明（更改函数声明）**". That is correct. Keep bold. Let's output that.
...done thinking.

**改变函数声明（更改函数声明）**

![](/img/0_refactor-10.png)

**动机**

一个好名字能让人一眼看出函数的用途；

函数的参数列表阐述了函数如何与外部世界共处，修改参数列表不仅能增加函数的应用范围，还能改变连接一个模块所需的条件，从而去除不必要的耦合。

Thinking...
We just translate the heading text: "**封装变量（Encapsulate Variable）**". In Simplified Chinese, we keep the same meaning. The original English is "Encapsulate Variable". So translation: "**封装变量（Encapsulate Variable）**". It's already Chinese? It's partially Chinese: "封装变量（Encapsulate Variable）". Actually the text is in Chinese with English in parentheses. So no translation needed? We need translate to Simplified Chinese. The English part "Encapsulate Variable" might remain? The instruction says "Keep proper nouns/product names when appropriate." But "Encapsulate Variable" is likely a term; but translation: "封装变量". It already exists. So maybe just keep it as is? The given text is already translated. So output same. Let's produce that.
...done thinking.

**封装变量（Encapsulate Variable）**

![](/img/0_refactor-15.png)

**动机**

对于所有可变的数据，只要它的作用域超出单个函数，我就会将其封装起来，只允许通过函数访问。数据的作用域越大，封装就越重要。

Thinking...
We need translate to Simplified Chinese. The heading "**变量改名（Rename Variable）**". The original is in bold: **Variable rename (Rename Variable)**. So translate: **变量重命名（Rename Variable）**? Wait "变量改名" already in Chinese. The title shows "变量改名（Rename Variable）". So we keep it. We might translate to "**变量改名（Rename Variable）**". That's already the given. But translation maybe "变量重命名（Rename Variable）". But we need keep Markdown exactly. The text: **变量改名（Rename Variable）**. That is the translation. So we just output that.
...done thinking.

**变量改名（Rename Variable）**

![](/img/0_refactor-9.png)

**动机**

解释一段程序在干什么，**对于作用域超出一次函数调用的字段，则需要更用心命名。**

Thinking...
We need to translate the given Markdown into Simplified Chinese. The text is: "**引入参数对象（Introduce Parameter Object）**"

We must preserve Markdown structure exactly. It is a bold heading? It appears as bold text, maybe a heading but it's just bold.

Thus translation: "**引入参数对象（Introduce Parameter Object）**" This is already in Chinese with parentheses. We might need to translate the English portion? The original contains both Chinese and English. The instructions: "Translate the given Markdown to Simplified Chinese." The original already has Chinese. We might translate the English portion "Introduce Parameter Object" to Chinese. The Chinese part "引入参数对象" is translation. The parentheses show original English. The instruction says translate the entire markdown to Simplified Chinese. The English portion likely should be translated. But it's already Chinese. The phrase in parentheses is English. In the original, they likely want the translation of the English portion to Chinese. But maybe keep the original English as reference. The original uses both Chinese and English. It might be a title: "引入参数对象（Introduce Parameter Object）". In translation, we could keep the English in parentheses or maybe translate it as "引入参数对象（Introduce Parameter Object）". But that contains English. The instruction: translate the given Markdown to Simplified Chinese. That implies that all English should be translated. But the parentheses might be part of the original. However, if we translate the English to Chinese, then it would become "引入参数对象（引入参数对象）"? That seems redundant. Alternatively, we could leave the parentheses as original, but maybe we can translate "Introduce Parameter Object" to Chinese inside parentheses: "引入参数对象（引入参数对象）" or "引入参数对象（Introduce Parameter Object）"? The instruction: "Translate the given Markdown to Simplified Chinese." So we should translate everything. The original had Chinese. So we could keep it same or maybe remove parentheses. But let's preserve Markdown structure. The bold is present. So final output: "**引入参数对象（Introduce Parameter Object）**"? But that hasn't changed. But maybe we keep the English? But instruction: translate to Simplified Chinese. The English part should be translated. So we translate "Introduce Parameter Object" to Chinese. So it becomes "**引入参数对象（引入参数对象）**"? But that's duplicate. Maybe we translate the parentheses to Chinese: "引入参数对象（引入参数对象）"? That is redundant.

Alternatively, maybe the original had Chinese title and English explanation. We might keep English in parentheses as a note. But the instruction says translate to Simplified Chinese. So I'd produce: "**引入参数对象（Introduce Parameter Object）**" Actually that is original. But we might keep English? Not sure.

However the best is to translate the entire content to Chinese: "**引入参数对象（Introduce Parameter Object）**" Already contains Chinese, so no change. The English phrase in parentheses might be kept as is, or we could translate it to Chinese. But the instruction says "translate the given Markdown to Simplified Chinese." It's ambiguous.

Let's check similar tasks. Usually, if the text already includes Chinese, the translation may keep Chinese and translate English into Chinese. So I'd translate "Introduce Parameter Object" to Chinese: "引入参数对象". But then you'd get duplicate. But maybe we can keep the English as reference: "引入参数对象（Introduce Parameter Object）" But that would not be fully Chinese. But we could keep English in parentheses. The instruction might allow that.

Given the original is "引入参数对象（Introduce Parameter Object）". This is already the translation of the English phrase. So no need to change. So final output is same.

Thus produce: **引入参数对象（Introduce Parameter Object）**
...done thinking.

**引入参数对象（Introduce Parameter Object）**

![](/img/0_refactor-11.png)

**动机**

将数据组织成结构，使数据项之间的**关系更清晰**；

**缩短参数列表**；

**代码一致性**：所有使用该数据结构的函数都可以通过相同的名字来访问其中元素。

改变代码的概念图景，将这些数据结构提升为新的抽象概念

Thinking...
We need to translate to Simplified Chinese. Title is bold. "函数组合成类（Combine Functions into Class）". Should preserve Markdown structure: bold. We translate the part outside parentheses? Actually the parentheses contain English phrase. We might translate entire phrase? They want translate to Simplified Chinese, but keep product names maybe. The title is "函数组合成类（Combine Functions into Class）". Should we translate the English inside parentheses? They said keep proper nouns when appropriate. But "Combine Functions into Class" is a phrase; not a proper noun. We could translate: "函数组合成类（Combine Functions into Class）". Maybe keep the English inside parentheses unchanged? The rule: translate the given Markdown. They might expect translation of both English and Chinese? The parentheses maybe optional. I'd translate both: "函数组合成类（Combine Functions into Class）" maybe we leave English. But to be consistent, we could translate: "函数组合成类（Combine Functions into Class）" is fine. The English phrase maybe translation. But maybe better: "函数组合成类（Combine Functions into Class）" - keep English part unchanged. The instruction: "Return ONLY the translated Markdown". So output: **函数组合成类（Combine Functions into Class）**. That is fine.
...done thinking.

**函数组合成类（Combine Functions into Class）**

![](/img/0_refactor-12.png)

**动机**

如果发现一组函数形影不离地操作同一块数据（通常是将这块数据作为参数传递给函数），是时候组建一个类了。类能明确地给这些函数提供一个共用的环境，在对象内部调用这些函数可以少传许多参数，从而简化函数调用。

Thinking...
We just need to translate that single line. It's Markdown: **函数组合成变换（Combine Functions into Transform）**. Wait it's already Chinese? It's Chinese with English in parentheses. Should translate English part into Chinese: "Combine Functions into Transform". But the Chinese translation should maybe be "将函数组合为变换". The original text: "**函数组合成变换（Combine Functions into Transform）**". The Chinese part already says "函数组合成变换". Might be the translation: "**将函数组合成变换**"? The English part to translate: "Combine Functions into Transform". So new translation: "**将函数组合成变换**" and maybe keep English in parentheses? But rule: translate to Simplified Chinese. So remove English? Probably keep the English part? It says translate the given Markdown to Simplified Chinese. So remove English or translate. So I'd produce "**将函数组合成变换**". That matches. No code fences.

Return only the translated Markdown.

Let's provide that.
...done thinking.

**将函数组合成变换**

![](/img/0_refactor-43.png)

**动机**

在软件中，经常需要把数据"喂"给一个程序，让它**再计算出各种派生信息**。这些派生数值可能会在几个不同地方用到，因此**这些计算逻辑也常会在用到派生数据的地方重复**。把所有计算派生数据的逻辑收拢到一处，这样始终可以在固定的地方找到和更新这些逻辑，避免到处重复。

**函数组合成变换**与**函数组合成类**区别：

如果代码中会对源数据做更新，那么使用类要好得多；如果使用变换，派生数据会被存储在新生成的记录中，一旦源数据被修改，我就会遭遇数据不一致。

**拆分阶段（Split Phase）**

![](/img/0_refactor-13.png)

**动机**

一段代码在**同时处理两件不同的事**，可以考虑把它**拆分成各自独立的模块**，因为这样到了需要修改的时候，可以单独处理每个主题。

**例子**

重构前：

![](/img/0_refactor-44.png)

重构后：

提炼函数、引入中转数据结构：

![](/img/0_refactor-45.png)

**第七章 封装**

Thinking...
We just need to translate the given Markdown to Simplified Chinese. The only content is a header bold: "**封装记录（Encapsulate Record）**". Wait it's already Chinese. The title in Chinese is "封装记录（Encapsulate Record）". The translation likely just keep same. But maybe we need to translate the English portion "Encapsulate Record" to Chinese. But the Chinese is given already. The heading might be: "**封装记录（Encapsulate Record）**". The instruction: Translate given Markdown to Simplified Chinese. The English part "Encapsulate Record" is inside parentheses; we might need to translate that to Chinese too, but it's already Chinese. But maybe we need to keep "Encapsulate Record" as is? The instruction: "Keep proper nouns/product names when appropriate." "Encapsulate Record" might be a term. But it's inside parentheses, maybe a translation. The heading includes both Chinese and English. Usually you'd keep both: Chinese heading then English. But translation might be just keep the same.

The Markdown: **封装记录（Encapsulate Record）**. Already includes Chinese and English. So we might keep as is. But maybe we need to translate "Encapsulate Record" to Chinese, but it's already Chinese. So maybe the translation is simply keep the same. The rules: preserve Markdown structure exactly, don't translate code fences. There's no code. So output same.

Thus final output: **封装记录（Encapsulate Record）**.
...done thinking.

**封装记录（Encapsulate Record）**

![](/img/0_refactor-14.png)

**动机**

对象可以隐藏结构的细节，有助于字段的改名，方便拓展以应对变化。

Thinking...
The user wants translation of given markdown to Simplified Chinese. Provided text:

**封装集合（Encapsulate Collection）**

They already have the Chinese translation? The original maybe English: "**Encapsulate Collection**". But they want translation? The given text already includes Chinese. But we need translate to Simplified Chinese. The given is "封装集合（Encapsulate Collection）". In Chinese, that is fine. Maybe we need translate the English part? The Chinese translation remains same. Possibly we just keep as is. But the requirement: "Translate the given Markdown to Simplified Chinese." The given Markdown contains Chinese already. But still we return same. There's no code fences. So we just output same.
...done thinking.

**封装集合（Encapsulate Collection）**

![](/img/0_refactor-16.png)

**动机**

封装集合时人们常常犯一个错误：只对集合变量的访问进行了封装，但依然让取值函数返回集合本身。这使得集合的成员变量可以直接被修改，而封装它的类则全然不知，无法介入。

做法：

在类上提供一些修改集合的方法------通常是"添加"和"移除"方法。

Thinking...
We need to translate to Simplified Chinese, preserve markdown. The heading: "**以对象取代基本类型（Replace Primitive with Object）**" It already partly in Chinese. The part in parentheses should be translated to Simplified Chinese? The original heading in English: "Replace Primitive with Object" in parentheses. The Chinese translation might be "以对象取代基本类型（用对象替代原始类型）" But the given text already has "Replace Primitive with Object" inside parentheses. We need to translate entire heading to Chinese. Keep bold and parentheses. So "**以对象取代基本类型（用对象替代原始类型）**" That is the translation. Ensure we keep bold markers. So final answer.
...done thinking.

**以对象取代基本类型（用对象替代原始类型）**

![](/img/0_refactor-46.png)

Thinking...
We just need to translate the title. The original: "**以查询取代临时变量（Replace Temp with Query）**". The part in parentheses is English phrase. The instruction: Keep proper nouns/product names when appropriate. Replace Temp with Query is a phrase. Should translate? We need to translate entire heading into Simplified Chinese, but we need to keep code fences and inline code? There's none. We must preserve markdown structure. The heading is **bold** text. Should we translate the English phrase? It's part of the heading: (Replace Temp with Query). We might translate it into Chinese: (用查询替代临时变量). But keep proper nouns? "Temp" might be proper noun? It's variable name. In Chinese, the phrase is "用查询替代临时变量". That would be translation. But the heading currently is "**以查询取代临时变量（Replace Temp with Query）**". Wait it's already Chinese. The heading has Chinese "以查询取代临时变量" and parentheses with English "Replace Temp with Query". So translation: we need to translate the Markdown to Simplified Chinese. The English inside parentheses maybe keep? Should translate the whole heading into Simplified Chinese: we could keep the English phrase? But the instruction: "Keep proper nouns/product names when appropriate." Not relevant. Probably translate the entire heading: "**用查询替代临时变量（Replace Temp with Query）**" or maybe "**用查询替代临时变量（用查询替代临时变量）**"? But the English phrase remains, we can keep the English phrase. The original heading: "**以查询取代临时变量（Replace Temp with Query）**". It's already Chinese with English. Perhaps the translation would keep the same structure but adjust Chinese wording: "**用查询替代临时变量（Replace Temp with Query）**". But the original Chinese says "以查询取代临时变量". That's already correct. So maybe we don't need to change. But the instruction says translate the given Markdown to Simplified Chinese. It's already in Simplified Chinese. So we keep as is. But we might ensure proper punctuation. The parentheses contain English phrase; it's fine. So final output: "**以查询取代临时变量（Replace Temp with Query）**". Probably we keep same.
...done thinking.

**以查询取代临时变量（Replace Temp with Query）**

![](/img/0_refactor-47.png)

Thinking...
We need to translate to Simplified Chinese. The given markdown is:

**提炼类（Extract Class）**

But actually that is already Chinese: "提炼类（Extract Class）" The title is in Chinese with English in parentheses. We should translate the English portion? The rule says keep proper nouns/product names when appropriate. Extract Class is a refactoring pattern. It's likely proper noun. So keep it. The heading is bold. So we keep it.

Thus output same as input.
...done thinking.

**提炼类（Extract Class）**

![](/img/0_refactor-48.png)

**动机**

如果某些数据和某些函数总是一起出现，某些数据经常同时变化甚至彼此相依，这就表示你应该将它们分离出去。

如果你发现子类化只影响类的部分特性，或如果你发现某些特性需要以一种方式来子类化，某些特性则需要以另一种方式子类化，这就意味着你需要分解原来的类。

Thinking...
The user: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: ... Return ONLY the translated Markdown." The original Markdown:

```
**内联类（Inline Class）**
```

Wait original: "**Inline Class**" in English. We must translate to Simplified Chinese: "内联类". Bold remains. So translation: "**内联类**". But we need to preserve heading? It's just bold. So final output: "**内联类**". No extra commentary.
...done thinking.

**内联类**

![](/img/0_refactor-49.png)

Thinking...
We just need to translate to Simplified Chinese: "**隐藏委托关系（Hide Delegate）**". The title is bold. In Chinese, maybe translate "Hide Delegate" to "隐藏委托" but we keep the English in parentheses? Actually original: **隐藏委托关系（Hide Delegate）**. We could translate "Hide Delegate" as "隐藏委托". The entire phrase: "**隐藏委托关系（Hide Delegate）**". It may mean "Hide Delegate" is a feature name. In Chinese, "隐藏委托关系" is enough, and parentheses show English. So we keep that. But the original text already has Chinese heading: "隐藏委托关系（Hide Delegate）". Wait the provided text already includes Chinese. We need to translate that? The heading is already in Chinese, no translation needed? But we need to translate to Simplified Chinese. It's already Simplified Chinese. Perhaps just keep as is. However we might consider translation of "Hide Delegate" inside parentheses to "隐藏委托". So final: **隐藏委托关系（隐藏委托）**? That duplicates? Let's think: The heading is "隐藏委托关系（Hide Delegate）" meaning "Hide Delegate Relationship" maybe. The English inside parentheses is the feature name. So we can keep it as is, but might translate it to Chinese. But requirement: "Translate the given Markdown to Simplified Chinese." The text is already Simplified Chinese, except English inside parentheses. So we should translate the English inside parentheses: "Hide Delegate" to "隐藏委托". But that would create redundancy. Perhaps the original translation expects to keep the parentheses but translate inside. I'll do that.

So output: **隐藏委托关系（隐藏委托）**. Let's keep heading formatting.

...done thinking.

**隐藏委托关系（隐藏委托）**

![](/img/0_refactor-50.png)

Thinking...
We just translate title. The original has a heading with bold. It is a bold heading. The translation: "**移除中间人（Remove Middle Man）**" But we should keep product names, but it's the same phrase. The title is in English inside parentheses. Should we translate? The instruction: "Translate the given Markdown to Simplified Chinese." We keep the English inside parentheses as is? The original has Chinese plus English? Actually original has "**Remove Middle Man**" inside parentheses? The original text: "**移除中间人（Remove Middle Man）**" So the Chinese phrase plus English translation. We should keep the English translation maybe. The instruction: "Keep proper nouns/product names when appropriate." That includes "Remove Middle Man" maybe not proper noun. The parentheses are presumably translation. We might translate Chinese but keep English in parentheses. But the translation is already Chinese. So maybe we keep same. But maybe they want to translate the English inside parentheses too? But that would be duplication. I'd keep the structure. So final output same.

But we must output only translated Markdown. So output "**移除中间人（Remove Middle Man）**".

Check if any modifications: It's already Chinese. So keep.

Thus final.
...done thinking.

**移除中间人（Remove Middle Man）**

![](/img/0_refactor-51.png)

"合适的隐藏程度"。

Thinking...
We need to translate the markdown. The text: "**替换算法（Substitute Algorithm）**". Wait that is already partially translated. Original maybe: "**Replacement Algorithm (Substitute Algorithm)**"? Actually the text shows both Chinese and English: "替换算法（Substitute Algorithm）". They want to translate the markdown to Simplified Chinese. The content is already Chinese. But we must preserve structure. The heading is bold. It might be a heading? There's no heading marker (#). It's just bold. But maybe they want translation of "Substitute Algorithm" to Chinese. But it's already there. They might want translation of the English part: "Substitute Algorithm" to Chinese? But they already have "替换算法". So maybe the original was "Substitute Algorithm". But it's given as "**替换算法（Substitute Algorithm）**". So we might translate to Chinese: "**替换算法（替代算法）**" but maybe we keep "Substitute Algorithm" as is? They ask to keep proper nouns/product names. "Substitute Algorithm" is a term; maybe keep as is. But we can translate to Chinese: "替代算法" maybe. But original is "替换算法（Substitute Algorithm）". I'd translate to "替代算法（Substitute Algorithm）"? However, we have to translate the Markdown to Simplified Chinese. It is already partially Chinese. The English part may be left as is? Might translate to Chinese. But rule: keep proper nouns. "Substitute Algorithm" might be considered a proper noun; maybe keep. But maybe better to translate to Chinese. However, we don't know. But I'll assume they want Chinese translation: "替代算法". Let's output "**替代算法（Substitute Algorithm）**". That preserves the Markdown. That should be fine.
...done thinking.

**替代算法（Substitute Algorithm）**

![](/img/0_refactor-17.png)

**第8章　搬移特性**

另一种类型的重构也很重要，那就是**在不同的上下文之间搬移元素**。

Thinking...
We just translate heading and text: "**搬移函数（Move Function）**". But the original had that already in Chinese plus English. We need to translate the given Markdown to Simplified Chinese. The phrase "搬移函数（Move Function）" already includes Chinese. But maybe we translate the English part? The original is "**搬移函数（Move Function）**". The Chinese is "搬移函数", the English is "Move Function". Since we are translating to Simplified Chinese, we might keep the Chinese, but maybe remove English? But rules: "Translate the given Markdown to Simplified Chinese." The English portion inside parentheses might be kept? But we could translate that as "移动函数" or keep "Move Function" as is? They might want "搬移函数（Move Function）" unchanged? But they ask to translate to Simplified Chinese. In this case the phrase already contains Chinese. Perhaps we keep the same. Maybe they want to translate "Move Function" to "搬移函数"? Already done. So final output same. No other content.

Return ONLY the translated Markdown. So output the line unchanged.

But maybe we should also translate the header if there was one? The line is "**搬移函数（Move Function）**". We'll keep that.

Thus final output:

**搬移函数（Move Function）**
...done thinking.

**搬移函数（Move Function）**

![](/img/0_refactor-18.png)

**任何函数都需要具备上下文环境才能存活**。

搬移函数最直接的一个动因是，它频繁引用其他上下文中的元素，而对自身上下文中的元素却关心甚少，将函数移动到联系更紧密的上下文那么系统别处就可以减少对当前模块的依赖，**获得更好的封装效果。**

整理代码时，发现需要频繁调用一个别处的函数；或者函数内部定义了一个帮助函数，而该帮助函数可能在别的地方也有用处，此时就可以将它搬移到某些更通用的地方。

**是否需要搬移函数常常不易抉择，但决定越难做，通常说明"搬移这个函数与否"的重要性也越低。**

**范例：搬移内嵌函数至顶层**

Thinking...
We have to translate "before：" into Simplified Chinese. The content is just "before：" maybe there is no more content? The original message shows:

Markdown to translate:
before：

So probably the Markdown file contains a heading or something? It just says "before：". That's not valid Markdown. Could be the content is just "before：". We need to translate that to Simplified Chinese. "before" can translate as "之前" or "在之前". But "before：" with colon. So likely the translation is "之前：" maybe "before：" means "before:" as a label or a heading. I'd translate to "之前：".

We must preserve Markdown structure exactly. There is no markup aside from the colon. So output "之前：" maybe with no preceding spaces. The original had a trailing space? It shows "before：" then line break. So output exactly "之前：" line.

Thus final answer: "之前："
...done thinking.

之前：

![](/img/0_refactor-19.png)

Thinking...
The user says: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: ..."

The markdown to translate is:

```
after：
```

It appears to be just "after：" with a Chinese colon. So the translation of "after：" is "之后："? Actually the original is "after：" which is English "after:" but with Chinese colon. They want to translate to Simplified Chinese. So "after" should become "之后". So the line would be "之后：" and keep the colon as is.

Check the rules: Preserve Markdown structure exactly. There is no code fences. Just a line. So translation should be "之后：". That is all.

Return only the translated Markdown. So answer is:

```
之后：
```

That's it.
...done thinking.

之后：

![](/img/0_refactor-20.png)

**范例：在类之间搬移函数**

Thinking...
We have a prompt: "before：". They want to translate the given Markdown to Simplified Chinese. But the Markdown content is just "before：". It's unclear what to translate. The input says "Markdown to translate: before：". So likely the content is just "before：". Maybe they want to translate that single line: "before：" meaning "before:"? In Chinese that would be "之前：" maybe. But the original text is just "before：". The colon is a fullwidth colon? The colon after "before" is a Chinese colon? Actually it's "：" which is Chinese colon. So "before：" would translate to "之前：" maybe. But let's think: the rule: "Translate the given Markdown to Simplified Chinese." We need to preserve Markdown structure exactly. The content is "before：" which is just a plain line, maybe it's a heading? No it's just a line. So we translate "before：" to "之前：" preserving the colon. The colon used is fullwidth colon. So "之前：" is appropriate. But we need to preserve formatting: no Markdown markup. So just output "之前：" . They want only translated Markdown, no extra commentary. So output "之前：" . However, the original might be "before：" with an English word. So translate to Simplified Chinese: "之前：". That is the only line.

But maybe the "before：" is a heading like "before："? It's not a header. So output "之前：" . Ensure no code fences. So final answer: "之前：".
...done thinking.

之前：

![](/img/0_refactor-52.png)

Thinking...
The user says: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese.
Rules:
- Preserve Markdown structure exactly (headings, lists, emphasis).
- Do NOT translate code fences or inline code spans wrapped in backticks.
- Do NOT alter links or image paths.
- Keep proper nouns/product names when appropriate.
Return ONLY the translated Markdown, no extra commentary.

Markdown to translate:
after："

It seems the Markdown to translate is "after："? The content maybe empty after? The user wrote "after：" maybe meaning they want translation of "after:"? But it's ambiguous. It could be that the original Markdown is "after：" and they want translation. So translate "after：" to Chinese. "after" in English might be "之后" or "在...之后". In this context it's likely "after:" as a label. So translate to "之后：" or "后："? The punctuation "：" is Chinese colon. So translate to "之后：" or "后："?

Given the minimal content, I'd translate as "之后：" which is natural. Could also be "后：" but "之后" more common. Let's produce "之后：" as the translation.

But the instruction: "Return ONLY the translated Markdown, no extra commentary." So just output the translated content. So output:

之后：

Check the colon: In English it's a colon ":", Chinese uses Chinese colon "：". So we output "之后：". Good.

Thus final answer: "之后：".
...done thinking.

之后：

![](/img/0_refactor-53.png)

**搬移字段（Move Field）**

![](/img/0_refactor-54.png)

**范例**

Thinking...
The user: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: Preserve Markdown structure exactly (headings, lists, emphasis). Do NOT translate code fences or inline code spans wrapped in backticks. Do NOT alter links or image paths. Keep proper nouns/product names when appropriate. Return ONLY the translated Markdown, no extra commentary.

Markdown to translate: before：

" Then maybe there is more content? The user only provided "before：" but maybe truncated? The instruction is to translate the given Markdown. But the markdown to translate is "before：" which is not actual content. It might be incomplete. The instruction expects to translate a markdown snippet but it's not provided. Possibly user omitted. So we must respond with nothing? But we must return only translated Markdown. But if there's no content to translate, we can't produce output. Might return empty? But maybe they expect "before：" as heading? It might be a heading "before：" that we need to translate to Chinese: "before：" maybe "before：" is not Chinese, we could translate "before:" to "之前：" or "之前：" with colon. But we don't know context. The user wrote "before：" maybe it's a heading or a snippet. We need to preserve markdown structure. The original: "before：" - maybe it's a heading? But there's no hash symbol. It's just text. So we translate "before：" to "之前：" or "before：" might remain? We might need to translate "before" to "之前". So output: "之前：" ?

But we need to keep punctuation. So "before：" -> "之前："?

But maybe the user expects translation of "before："? That seems trivial.

Given no further content, I'll output "之前：" in markdown (just plain text). No extra commentary.
...done thinking.

之前：

![](/img/0_refactor-55.png)

Thinking...
We need to translate the given Markdown into Simplified Chinese, preserving structure. The provided text: "after：" So the markdown snippet is:

after：

So we just translate "after" to Chinese? It's a heading maybe? There's no heading syntax, but "after：" looks like text.

The translation: "after" => "之后" (or "后面"). The colon ":" remains. So it becomes "之后：" likely.

But maybe we need preserve punctuation. So translation: "之后："

Thus final output:

之后：

No markdown headings needed.

Thus answer: "之后："
...done thinking.

之后：

![](/img/0_refactor-56.png)

![](/img/0_refactor-57.png)

**范例：搬移字段到共享对象**

Thinking...
We have to translate the given Markdown to Simplified Chinese. The content: "before：" and nothing else? Let's see the user provided "Markdown to translate:" then a line "before：" So the markdown content is just "before：". There's a line break, maybe. So we need to translate it to Simplified Chinese. "before：" is "before："? Should translate "before" to "之前". So "之前：" . But must preserve Markdown structure exactly. This is not a heading, just plain text. Should produce the translated Markdown.

Thus output: "之前：" Probably with the same colon (Chinese colon? In original it's a colon colon? "before：" uses colon with a Chinese full-width colon? The colon appears as "：" (full-width). The original: "before：" contains a full-width colon. So we preserve that. The translation: "之前：". That is it.

Thus final answer: "之前："
...done thinking.

之前：

![](/img/0_refactor-58.png)

Thinking...
We have a user instruction: They want translation of given Markdown to Simplified Chinese. The Markdown to translate is:

"after："

That's it? It says:

Markdown to translate:
after：

So the content to translate is "after：" preceded by a line break? The formatting: "after：" probably with a colon. So we need to translate into Simplified Chinese. "after" in Chinese is "之后" or "后面". The colon remains. So output: "之后：" . Need to preserve punctuation. There's no code fences. So just output the translated text.

Thus final output: "之后："
...done thinking.

之后：

![](/img/0_refactor-59.png)

![](/img/0_refactor-60.png)

Thinking...
We need translate to Simplified Chinese. The given Markdown: **搬移语句到函数（Move Statements into Function）**. Wait: The heading is bold with Chinese and English. The translation: maybe keep original English? But instructions: "Translate the given Markdown to Simplified Chinese." So we need translate all text to Simplified Chinese. But there is English within parentheses "Move Statements into Function". Should translate to Chinese. Keep markup same. So produce **搬移语句到函数（将语句移动到函数中）**? The Chinese already says "搬移语句到函数". The English part likely can be translated: "(Move Statements into Function)" -> "(将语句移动到函数)". So final: **搬移语句到函数（将语句移动到函数）**. But maybe the parentheses content is same as heading? But fine.

Return only translated markdown.

Let's output.
...done thinking.

**搬移语句到函数（将语句移动到函数）**

![](/img/0_refactor-21.png)

**"消除重复"**：如果发现调用某个函数时，总有一些相同的代码也需要每次执行，则考虑将此段代码合并到函数里头。

如果某些语句与一个函数放在一起更像一个整体，并且更**有助于理解**，则将语句搬移到函数里去。如果它们与函数不像一个整体，但仍应与函数一起执行，可以用提炼函数将语句和函数一并提炼出去。

**范例**

Thinking...
We need to translate the given Markdown to Simplified Chinese. The original text is:

```
before：

```

That's the entire content: "before：" followed by a code block? Actually there's "before：" line. After that, there's a blank line and then a code fence? Let's check: Provided:

before：

The user says: "Markdown to translate:" and then shows

before：

So maybe the content to translate is "before：" alone? That seems odd. Maybe they omitted content? Possibly the input is just "before："? So translation: "before：" becomes "之前：" maybe. But keep the structure. There's no markdown heading. Just a line: "before：" So we output "之前："? But also preserve punctuation. Use Chinese colon? In Chinese we can keep the colon. They used a colon after before: So output "之前：" Probably that.

Return only the translated Markdown.

Thus answer: "之前："
...done thinking.

之前：

![](/img/0_refactor-61.png)

Thinking...
We have input: "after：" and nothing else. The Markdown to translate: "after：" . It seems incomplete. But we must translate. It's a heading? "after：" maybe a heading? There's no markdown syntax. Just a phrase "after：". It could be a heading but no markdown. The instructions: preserve Markdown structure exactly. There's no code fences. We translate "after：" to Chinese: "之后：" . So output: "之后：" . Should we keep the colon? The colon is Chinese full-width? The original colon is half-width. Keep same? Should we translate colon? In Chinese, colon may be full-width or half-width. It's okay. We'll just keep half-width colon.

Return only translated Markdown. So output: "之后：" .
...done thinking.

之后：

![](/img/0_refactor-62.png)

Thinking...
We need to translate to Simplified Chinese. Title: "搬移语句到调用者（Move Statements to Callers）". The original includes "**搬移语句到调用者（Move Statements to Callers）**". Wait the original is "**搬移语句到调用者（Move Statements to Callers）**". But the original text shows "**搬移语句到调用者（Move Statements to Callers）**". Actually the provided markdown to translate is:

**搬移语句到调用者（Move Statements to Callers）**

It seems already Chinese and English inside parentheses. We might need to translate the English part into Chinese, but maybe keep the same? The instruction: "Translate the given Markdown to Simplified Chinese." The content already partly Chinese. The English part likely should be translated: "Move Statements to Callers". That phrase could be translated as "将语句移至调用者". So the Chinese translation would be something like **搬移语句到调用者（将语句移至调用者）**? But we need to preserve structure exactly. The original has "**搬移语句到调用者（Move Statements to Callers）**". So we can replace the parentheses content with Chinese translation. But the original already has Chinese in the title, but we need to translate the English part. So new Markdown: **搬移语句到调用者（将语句移至调用者）**.

But we should also consider that "Move Statements to Callers" might be a phrase used in a technical document; but the translation could be "移动语句到调用者". But the Chinese part "搬移语句到调用者" is already "Move Statements to Callers". So maybe we don't need translation, but the instructions say translate to Simplified Chinese. The English inside parentheses may be part of the title; but the title is likely bilingual. However, it's safe to translate. So final output: **搬移语句到调用者（将语句移至调用者）**.

Check that we don't alter code fences or inline code; none here. So final answer.
...done thinking.

**搬移语句到调用者（将语句移至调用者）**

![](/img/0_refactor-63.png)

随着系统能力发生演进，原先设定的抽象边界总会悄无声息地发生偏移。对于函数来说，这样的边界偏移意味着曾经视为一个整体、一个单元的行为，如今可能已经分化出两个甚至是多个不同的关注点。

**范例**

Thinking...
We have input: "before：" then presumably more content? Let's re-read user message:

"You are a professional technical translator. Translate the given Markdown to Simplified Chinese.
Rules:
- Preserve Markdown structure exactly (headings, lists, emphasis).
- Do NOT translate code fences or inline code spans wrapped in backticks.
- Do NOT alter links or image paths.
- Keep proper nouns/product names when appropriate.
Return ONLY the translated Markdown, no extra commentary.

Markdown to translate:
before：

"

It seems incomplete? The content to translate is just "before：" maybe with some trailing whitespace? Possibly the content includes something after but not captured. The user wrote:

Markdown to translate:
before：

So the Markdown string to translate is:

```
before：
```

So only that. So we just translate "before：" to Simplified Chinese. But "before" in context? "before：" maybe as heading? It's just a line with "before：". It includes a colon (fullwidth). The original "before：" maybe used as heading? Could be a header. But we have to preserve structure: it's a line with "before：". There's no Markdown syntax like #. So it's just plain text. We translate to "之前：". But keep the colon, maybe same colon type? The original colon is fullwidth. We keep same? They didn't mention to modify punctuation. So we keep same fullwidth colon. So translation: "之前：" (Chinese). So output:

```
之前：
```

Return only that. No extra commentary.
...done thinking.

之前：

![](/img/0_refactor-64.png)

Thinking...
We need to translate the Markdown that is given after the word "after：". It seems the input has "Markdown to translate:" then the text "after：" followed by presumably some content. But the content is not provided? The question: "Markdown to translate: after：" maybe it's an incomplete. Let's re-read: The prompt says:

Markdown to translate:
after：

So it seems the content is "after：" with no actual markdown beyond that. Maybe the translator should translate "after：" into Simplified Chinese. That phrase "after：" is presumably a heading? There's a colon. In Chinese, "after" could be "之后" or "后" etc. But maybe they want "after：" to be "after："? Wait, the original text is just "after：". Maybe it's a heading or label. We need to preserve markdown structure. The content is just the string "after：". This is not code. So we should translate "after：" to "after："? No, we need to translate into Chinese: "after：" -> "after："? Actually the word "after" is in English, we translate to Chinese. "After" can be translated as "之后" or "后". But it's unclear context. The colon suggests a label or maybe it's part of a bullet list. But we don't have more context.

We must preserve markdown structure. So output "after："? But we need to translate the word. So "after：" becomes "之后：" maybe. But the colon is a punctuation. But original had "after：" with a full-width colon or half? It's a colon. They likely want "after：" -> "after："? But they want to translate. So we can output "after："? Wait, maybe the colon is used as a header like "after：" maybe a label in a list like "after:". So we might translate "after:" as "之后:".

Thus the translated markdown would be:

```
之后：
```

But if we want to keep it same style: "after：" with a colon. But translation: "after：" -> "之后：". So output:

```
之后：
```

But we need to preserve markdown structure. There's no markdown tags. So just output "之后：".

Therefore answer: "之后：".
...done thinking.

之后：

![](/img/0_refactor-65.png)

Thinking...
We need to translate the given Markdown to Simplified Chinese. The given Markdown is "**以函数调用取代内联代码（Replace Inline Code with Function Call）**". We need to preserve formatting. It's already Chinese but includes English phrase. We translate the English part. The translation: "**以函数调用取代内联代码（用函数调用替换内联代码）**" or similar. But we keep the parentheses: Chinese translation inside. The heading is bold. We can translate the English to Chinese inside parentheses. Probably: "**以函数调用取代内联代码（将内联代码替换为函数调用）**". But we should translate "Replace Inline Code with Function Call". The literal Chinese translation: "用函数调用替换内联代码". Let's use that. So final output:

**以函数调用取代内联代码（用函数调用替换内联代码）**

Return only that.
...done thinking.

**以函数调用取代内联代码（用函数调用替换内联代码）**

![](/img/0_refactor-66.png)

Thinking...
We need to translate the Markdown: "**移动语句（Slide Statements）**" to Simplified Chinese, preserving Markdown structure. The content is bold. It's "移动语句（Slide Statements）". In Chinese we can translate "移动语句" as "移动语句"? It's already Chinese. They want Simplified Chinese. The phrase inside parentheses is English. We keep it. So final output: "**移动语句（Slide Statements）**". That is exactly same? It is already in Chinese. Wait it's already Chinese. Possibly we might translate "移动语句" to "Slide Statements"? But the parenthetical already says Slide Statements. So translation is same. They might want Chinese translation of "Slide Statements" is "移动语句"? Already there. So output same. Let's just output that.
...done thinking.

**移动语句（Slide Statements）**

![](/img/0_refactor-67.png)

让存在关联的东西一起出现，可以使代码更容易理解。

Thinking...
We have to translate the given markdown into Simplified Chinese. The given markdown is:

**命令查询分离原则**（Command-Query Separation,CQS原则）：

Wait, it seems already Chinese. Actually "Command-Query Separation" abbreviation is in English. The content is already Chinese. But we are to translate to Simplified Chinese. It's already Chinese. But maybe they want keep the English abbreviation? It says "Translate the given Markdown to Simplified Chinese." The input already is partly Chinese but includes English. So we should translate the whole thing into Simplified Chinese, but keep proper nouns. The text: "**命令查询分离原则**（Command-Query Separation,CQS原则）：" The phrase "Command-Query Separation" is English; but we can translate it to "命令-查询分离" but maybe we keep the English because it's a proper noun? The rule: "Keep proper nouns/product names when appropriate." The phrase "Command-Query Separation" is a proper name of the principle, but it's already translated as 命令查询分离原则. We could keep it as is. The rest "CQS原则" is already Chinese. So maybe no changes needed. The punctuation maybe adjust: Should we translate "Command-Query Separation" to "命令-查询分离"? Already used? In parentheses it includes both English and Chinese. Maybe we keep the same.

So translation would be identical. But we must preserve markdown: headings, lists, emphasis. The content is bold text. Keep it.

Thus final output: **命令查询分离原则**（Command-Query Separation,CQS原则）：

Check if there is any trailing whitespace or something. Probably keep exactly.

Return only the translated Markdown.

Thus answer: same.

...done thinking.

**命令查询分离原则**（Command-Query Separation,CQS原则）：


**查询：**方法返回结果，但不改变任何系统状态(无副作用)。

**命令：**方法没有结果，但会改变系统状态。

优点如下

查询类型的方法，对于调用者来讲不用在顾虑各个查询方法的调用顺序和次数(忽略性能的因素)。

命令类型的方法，从语义上来讲更准确。

**范例**

![](/img/0_refactor-68.png)

思考：哪些语句可以移动？

**范例：包含条件逻辑的移动**

Thinking...
We need to translate the given Markdown to Simplified Chinese. But the provided content: "before：" and then presumably nothing? The snippet: 
```
before：

```
So there's "before：" maybe a heading? Actually it's just a line with "before：" followed by an empty line and code fence? The snippet shows "before：" then a blank line then maybe a code block? But the prompt shows "before：" followed by blank lines and then "```" is not shown but might be the code fence. Wait: The snippet:

```
before：

```
There is no closing backticks in the snippet. But the user said "Markdown to translate:" then "before：" and a blank line. There's no content after "before：".

Thus likely they want to translate "before：" to Chinese? The content might be part of a larger file but only the snippet is shown. We need to output the translated Markdown exactly.

Thus "before：" likely is a label or a heading? It's not a heading because there's no '#' prefix. It's just a line. So translation: "before：" => "之前："

Thus the output would be:

```
之前：

```
We need to preserve the blank line. The original has a newline after "before：". The output should be the same.

Also the user had "before：" with a Chinese colon? It's a colon in ascii? Actually "before：" the colon is a Chinese fullwidth colon "：" not ascii. So translation: "之前：" using Chinese characters.

So final output:

```
之前：

```

Ensure no code fences. Just the line.

Thus answer.
...done thinking.

之前：

![](img/0_refactor-69.png)

Thinking...
We have a task: translate the given Markdown to Simplified Chinese. The given Markdown is:

```
after：
```

The content after the backticks is "after：". So it's a single line containing "after：" with colon punctuation.

We need to translate to Simplified Chinese. "after：" in Chinese would be "之后：" maybe. The colon punctuation is an English colon but Chinese also uses the full-width colon "：" after the Chinese word. So translation is "之后：".

We must preserve markdown structure exactly: It is a code fence? The text shows:

```
after：
```

Yes it shows code fence? Actually the given snippet has backticks: "```\nafter：\n```" It is a fenced code block. The instructions say: "Do NOT translate code fences or inline code spans wrapped in backticks." That means we should not translate inside code fences. Actually the rule: "Do NOT translate code fences or inline code spans wrapped in backticks." This is ambiguous: code fences are the triple backticks that create a block; inside the code block, we are not to translate? Usually we are to preserve them exactly as code fences and not translate the content inside. But the instruction is: "Do NOT translate code fences or inline code spans wrapped in backticks." That likely means do not translate the markers themselves (the backticks). But we can translate content inside? Actually the phrase "or inline code spans wrapped in backticks" indicates that we should not translate code fences themselves or code spans. But the content inside a code fence is usually not to be translated? The instruction might be ambiguous. But typical practice: we keep the code block exactly, no translation inside. So we leave "after：" unchanged inside the code block. So we just output:

```
after：
```

No translation. Because it's code block. The rule says not translate code fences or inline code spans. That means the code fences themselves and inline code must remain unchanged. But the content inside? Usually code fences contain code. Should we translate the content? I think we should not translate inside. The instruction might mean not to modify the code fences themselves (the backticks). It doesn't explicitly say don't translate inside. But typical translation guidelines: preserve code content. Because code may have variable names etc. So we keep inside unchanged. The text "after：" is inside a code block. So we keep it as is. So output exactly the same code block.

Thus answer:

```
after：
```
...done thinking.

```
after：
```


![](img/0_refactor-70.png)

**拆分循环（Split Loop）**

![](img/0_refactor-71.png)

**范例**

Thinking...
We need to translate the given Markdown to Simplified Chinese, preserving structure. The original text says: "before：". Actually the markdown to translate is just:

before：

That's all? The content is minimal. "before：" presumably heading? It's not a heading; it's just text "before：" maybe a bullet? The example: The user says "Markdown to translate:" and then shows:

before：

That's the only content. So we translate that to Simplified Chinese. "before：" likely means "before:" in English. The translation would be "之前：" in Chinese. But do we need to preserve the colon? Yes, colon is a punctuation. The Chinese version of colon is full-width colon? The user might expect full-width colon. But the text is "before：" with a colon maybe half-width colon. We might translate as "之前：" with half-width colon. It's simple.

Also ensure no code fences. It's plain text.

Thus output:

之前：

No extra commentary.
...done thinking.

之前：

![](img/0_refactor-72.png)

Thinking...
We need to translate the given Markdown to Simplified Chinese. The content is:

```
after：
```

The input has "after：" (with a colon). That is probably the entire content to translate. We need to preserve Markdown structure exactly. The line "after：" probably is a header or just a line? The syntax: "after：" no heading symbol. It could be a line in a document. The content includes a colon and a non-ASCII character? Actually the colon is the standard colon. The word "after" should be translated to Simplified Chinese: "之后". Then the colon should be kept. The "after：" is presumably plain text. So we translate "after：" to "之后：". Since we must keep the colon. The line might be inside a document.

We must preserve Markdown structure exactly. The original had no markup besides maybe a line. So output the translated line: "之后：". No extra commentary.

Check if the original had a line break? The Markdown snippet:

```
after：
```

This indicates maybe the content is "after：" alone. So output "之后：". No formatting.

Thus the answer: "之后：".
...done thinking.

之后：

![](img/0_refactor-73.png)

Thinking...
The user wants to translate given Markdown to Simplified Chinese. The given Markdown is:

**以管道取代循环（Replace Loop with Pipeline）**

We need to preserve formatting. The phrase is already partly in Chinese. It says "以管道取代循环（Replace Loop with Pipeline）". It might be the title of a section. The user wants translation to Simplified Chinese. The phrase already in Simplified Chinese. The part in parentheses is English. Probably we keep English or translate. The instructions: "Translate the given Markdown to Simplified Chinese." So we should translate the English into Chinese. The parentheses part "Replace Loop with Pipeline" is English; translate to Chinese: "用管道替代循环". So final output: **以管道取代循环（用管道替代循环）**? Wait that duplicates. The original Chinese phrase already says "以管道取代循环". So we could keep that. The translation of English phrase would be "用管道替代循环". So maybe we write: **以管道取代循环（用管道替代循环）**? But that seems redundant. But instruction says preserve structure. We just translate the English part. So:

**以管道取代循环（用管道替代循环）**

But that repeats Chinese phrase. Maybe better to write: **以管道取代循环（Replace Loop with Pipeline）** stays same because it's already Chinese. But they ask to translate to Simplified Chinese. The given Markdown is already in Simplified Chinese. The English inside parentheses may be removed or translated. I'd translate to Chinese. So final:

**以管道取代循环（用管道替代循环）**.

But we might want to use the same phrase "Replace Loop with Pipeline" replaced by Chinese: "用管道替代循环". That duplicates. Another option: keep the Chinese part but translate only the English phrase to Chinese: **以管道取代循环（用管道替代循环）**. That is weird but fine.

Alternatively, we can keep the original phrase and leave the English. But the instruction says translate to Simplified Chinese. So I think we should translate the English portion. So produce: **以管道取代循环（用管道替代循环）**.

Let's output that.
...done thinking.

**以管道取代循环（用管道替代循环）**

![](img/0_refactor-74.png)

Thinking...
We need to translate the Markdown into Simplified Chinese. But the text is already Chinese: "map运算是指用一个函数作用于输入集合的每一个元素上，将集合变换成另外一个集合的过程；filter运算是指用一个函数从输入集合中筛选出符合条件的元素子集的过程。运算得到的集合可以供管道的后续流程使用。"

The translation to Simplified Chinese is already in Simplified Chinese. But perhaps they want to translate to English? Wait: The task: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese." But the source is Chinese. Maybe it's originally in English and they accidentally posted Chinese? But they said to translate to Simplified Chinese. Since it's already Chinese, we might keep it unchanged. Ensure not to change code fences or inline code. There are none. So just output same content.

But maybe there is a hidden expectation: The original content might be in English but shown in Chinese because of misinterpretation? Actually the content is Chinese. They might want to translate to Simplified Chinese? But it's already Chinese. Maybe they want to translate to Traditional Chinese? But no, they ask Simplified Chinese.

Therefore we should output the same text. Ensure to keep punctuation.

Return ONLY the translated Markdown.

Thus output:

map运算是指用一个函数作用于输入集合的每一个元素上，将集合变换成另外一个集合的过程；filter运算是指用一个函数从输入集合中筛选出符合条件的元素子集的过程。运算得到的集合可以供管道的后续流程使用。
...done thinking.

map运算是指用一个函数作用于输入集合的每一个元素上，将集合变换成另外一个集合的过程；filter运算是指用一个函数从输入集合中筛选出符合条件的元素子集的过程。运算得到的集合可以供管道的后续流程使用。

**范例**

Thinking...
We have a user message: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: ... Return ONLY the translated Markdown, no extra commentary. Markdown to translate: before：". Then it seems incomplete? There's no content after "before：". The original prompt might have omitted the actual markdown to translate. The user only wrote "before：" and nothing else. So perhaps we need to interpret what to translate. But likely the user wants to translate the word "before："? Or they forgot to include content. The safest is to output nothing? But we must return the translated Markdown. If there's no content, maybe output an empty string? Or output the translation of "before："? The instructions: "Markdown to translate: before：". That's a line "before：" in Markdown. We translate that to Simplified Chinese. "before：" would be "之前：" or "在之前：". Usually "before:" is "之前：" or "前面：". But since it's just "before：" maybe it's a heading? It's not preceded by any Markdown syntax. It might be a label. So translation: "之前：" (including colon). So output that. Keep Markdown structure exactly. There's no list, etc. So just output the translated text. Probably "之前：" in Chinese. Ensure no extra commentary. So final answer: "之前：".
...done thinking.

之前：

![](img/0_refactor-75.png)

![](img/0_refactor-76.png)

Thinking...
We need to translate the Markdown after "after：" which is "after："? Wait the input says: "Markdown to translate:
after：" The text after the colon is "after：" and then presumably nothing else? Possibly they want to translate the word "after：" into Chinese? The instruction: "Translate the given Markdown to Simplified Chinese." The given markdown is just "after：" which maybe includes newline after colon. So we need to translate it: "after：" becomes "after："? Actually "after" in Chinese is "之后" or "在...之后". But it's just a word. The punctuation colon. In Chinese, we would write "after：" maybe "after：" remains "after："? They might want "after：" translated as "after："? But rule: translate content. So we should translate "after：" to Chinese: "after：" might be "after："? Probably "after：" should become "after：" but in Chinese we would say "after：" maybe "after："? The instructions might want a Chinese translation: "after：" -> "之后：" or "after:" -> "之后:"? But we need to preserve Markdown exactly, only translate content. The content is "after：" which is not code. So we translate "after：" to Chinese. That yields "after："? Wait "after" to Chinese: "after" is "之后". So we can replace "after" with "之后". So output: "之后：" with same colon. The newline after? It is just one line. We need to keep markdown exactly. So output "之后：" followed by a newline? Provide the same? Probably yes.

Thus final answer: "之后："
...done thinking.

之后：

![](img/0_refactor-77.png)

Thinking...
We need to translate the given markdown to Simplified Chinese, preserving structure, but the content is basically a title in bold: "**移除死代码（Remove Dead Code）**". We should translate the English part inside parentheses? Wait original: "**移除死代码（Remove Dead Code）**". The translation should keep proper nouns. The English is a translation of the Chinese. But the requirement: "Translate the given Markdown to Simplified Chinese." The text is already in Chinese. The English part "Remove Dead Code" is a translation of the Chinese. Since the target language is Simplified Chinese, we might not need to translate that part. But maybe they want to translate the whole string. However the instruction says to preserve Markdown structure, etc. Should we replace "Remove Dead Code" with Chinese? It's already in Chinese. So maybe keep as is. But the instruction says "Translate the given Markdown to Simplified Chinese." Since the original includes Chinese and English. But the English part "Remove Dead Code" is likely not required; it is in English inside parentheses. The translation would just keep the Chinese and the English. The translation might be to keep Chinese text, maybe convert "Remove Dead Code" to Chinese? But that would conflict with "Keep proper nouns/product names when appropriate." "Remove Dead Code" is a phrase, not a proper noun. In this case maybe we translate it to Chinese: "删除死代码"? Actually "Remove Dead Code" means "删除死代码". But since the Chinese already says "移除死代码", it's the same concept. So maybe we should keep as is. But maybe we should translate the English part to Chinese for consistency: "删除死代码"? But that duplicates the Chinese part. But the instruction says "Translate the given Markdown to Simplified Chinese." The English phrase might be a note. But I think the expectation is to keep the phrase in English? Not sure.

Look at other tasks: Usually they'd translate the entire text. So we would translate the English part into Chinese. So result: "**移除死代码（删除死代码）**" But that duplicates. That might be acceptable? But maybe they'd prefer keep English phrase because it's a common phrase used in code comments? Not sure.

But I'd interpret: "Translate the given Markdown to Simplified Chinese." That means the content in English inside parentheses should be translated to Chinese. So produce: "**移除死代码（删除死代码）**". That is weird but okay.

However maybe we just keep original: "**移除死代码（Remove Dead Code）**" Because it's already Chinese and the English part is translation. The instruction may not require translation of that part.

I think better to keep as is, because it's already in Chinese. The instruction "Translate the given Markdown to Simplified Chinese" is to ensure the Markdown is Chinese, but the English part is already in English and not required. But I think they'd want to translate that part.

Let's examine other example tasks: They usually have English headings and they translate to Chinese. They keep parentheses translations. For example: "**移除死代码（Remove Dead Code）**" they'd keep Chinese inside parentheses? Actually the heading is in Chinese with English in parentheses. The translation might keep Chinese and English? But if the original is "Remove Dead Code", the translation would be "删除死代码". But here the original already Chinese. So maybe they'd want to keep it.

I think keep as is: "**移除死代码（Remove Dead Code）**". No translation needed. So final answer same.
...done thinking.

**移除死代码（Remove Dead Code）**

![](img/0_refactor-78.png)

**第9章　重新组织数据**

Thinking...
We need to translate the heading "拆分变量（Split Variable）". The title is already in Chinese? It says "拆分变量（Split Variable）". We need to translate the Markdown to Simplified Chinese. The heading is "**拆分变量（Split Variable）**". It's already Chinese and English. Should we translate "Split Variable"? But the rule: Keep proper nouns/product names when appropriate. "Split Variable" may be a term. But it's already translated "拆分变量" then parentheses. We might keep both. The original is already in Chinese, so maybe nothing changes. But maybe we need to translate "Split Variable" to Chinese? But it's already in parentheses. The instruction: "Translate the given Markdown to Simplified Chinese." The text already contains Simplified Chinese. We might keep it. The heading is "**拆分变量（Split Variable）**". The parentheses part is English. Maybe we should translate that part to Chinese? But it's a proper term. The phrase "Split Variable" is the name of a concept. We might keep it as is. But the rule: Keep proper nouns/product names when appropriate. "Split Variable" might be a term; but if it's a translation of a concept, we could leave it. The heading is in bold. The content is empty. The translation likely remains identical. So we just output same heading. No extra commentary.
...done thinking.

**拆分变量（Split Variable）**

![](img/0_refactor-22.png)

除"循环变量"和"结果收集变量"外，还有很多变量用于保存一段冗长代码的运算结果，以便稍后使用。这种**变量应该只被赋值一次。**如果它们被赋值超过一次，就意味它们在函数中承担了一个以上的责任。如果变量承担多个责任，它就应该被替换（分解）为多个变量，**保持职责单一**。

**范例：对输入参数赋值**

Thinking...
We need to translate the given markdown to Simplified Chinese, preserving markdown. The content is:

"before：

"

The text says "before：" with a space after before and colon? Actually "before：" maybe Chinese colon. Let's assume the content is:

before：

That's it. No code fences, no links.

We need to translate to Simplified Chinese. "before：" could be translated to "之前：" maybe. But we should preserve heading? There's no heading indicator. It's just "before：" as plain text. So translation: "之前：" .

But also maybe "before：" could mean "之前：" in Chinese. Yes.

Return only the translated markdown.

So output:

之前：

But keep the line break. So output exactly that.
...done thinking.

之前：

![](img/0_refactor-23.png)

Thinking...
We need to translate "after：" into Simplified Chinese? The original markdown includes "after：" (the colon maybe part of Chinese? They want translation of the Markdown to Simplified Chinese. The input is just "after：" which is a fragment. There's no heading or list. Just a word "after:".

We need to preserve Markdown structure exactly. So we need to output "after：" translated to Chinese. "after" in Chinese is "之后". So "之后：" maybe. But the colon is part of punctuation. The original has a colon at the end, likely after the word. So we translate "after:" to "之后：". That would keep punctuation. The Markdown is just a word, not a code block. So output that line.

Thus output:

之后：

That's all.
...done thinking.

之后：

![](img/0_refactor-24.png)

Thinking...
We just translate the heading text to Simplified Chinese. The original is "**字段改名（Rename Field）**". It is bold markup. We need to keep markdown same. The text is Chinese already? Wait "字段改名（Rename Field）" includes Chinese characters "字段改名" and English "Rename Field" in parentheses. It is already bilingual. So translation? It's same. But maybe we need to translate the entire heading? But we can't translate code fences or inline code. This is plain text. Should we translate "字段改名" to something else? It's already Chinese. The instruction: "Translate the given Markdown to Simplified Chinese." But it's already in Simplified Chinese partly. The English part should be translated? "Rename Field" -> "字段重命名"? But the heading is "字段改名（Rename Field）" which is Chinese "字段改名" and English "Rename Field". We should translate the English portion. The requirement: "Keep proper nouns/product names when appropriate." There's no proper noun. So we should translate the English phrase to Simplified Chinese. Should we replace parentheses with Chinese? The original had parentheses around the English. We can keep parentheses but change inside to Chinese: "字段改名（字段重命名）" or maybe "字段改名（字段改名）" but that duplicates. Wait the heading is about "Rename Field". So translation would be "字段改名（字段重命名）" or maybe "字段改名（改字段）"? I think "字段重命名" is better. So final output: **字段改名（字段重命名）**. Keep bold markers. Yes.
...done thinking.

**字段改名（字段重命名）**

![](img/0_refactor-79.png)

**范例：给字段改名**

Thinking...
We need to translate the given Markdown to Simplified Chinese. The Markdown to translate: "before：" followed by presumably nothing else? The content after "before：" might be omitted in the prompt; maybe they intend to translate the snippet "before："? Actually the Markdown to translate is:

```
before：
```

It seems just a heading or text "before：" in English? The colon in English, but colon is same in Chinese. In Chinese, "before：" maybe "before："? They may want to translate to Simplified Chinese: "before：" => "before："? The word "before" should be translated to "之前" or "之前："? But we preserve punctuation. The colon stays. So "before：" -> "之前：" in Chinese. Or could be "before：" is maybe a heading in Markdown? But there's no markdown heading symbol. It's just "before：" maybe part of code snippet? The content after "before：" is missing. Perhaps the snippet is incomplete; maybe they want to translate "before：" as part of a sample? But the instruction: "Markdown to translate:" and then "before：" So it's a piece of text to translate.

Thus we produce "之前：" as translation.

But we must preserve Markdown structure exactly. There's no code fences. So just output "之前：".

Thus final answer: "之前："
...done thinking.

之前：

![](img/0_refactor-80.png)

Thinking...
We have only "after：" as input? The prompt says "Markdown to translate:" then "after：". So translation is likely "after：" to Simplified Chinese. "after：" translates to "之后：" or "after:"? In Chinese context maybe "after:" as heading? The input is literally "after：" with a colon and maybe full-width colon? It's "after：" using ASCII colon? The output should preserve structure exactly. There's a line "after：" maybe it's heading? It's just a word and colon. So translation should be "after：" -> "after："? No translation? We need to translate to Simplified Chinese: "after：" becomes "之后：" or "后面：" but "after:" usually translated as "之后". I'd output "之后：". Ensure preserve same punctuation. So final answer: "之后：".
...done thinking.

之后：

![](img/0_refactor-81.png)

Thinking...
We need to translate the given Markdown. The heading is "**以查询取代派生变量（Replace Derived Variable with Query）**". Actually it's bold, not heading. There's no heading markers. It is just bold text. We translate to Simplified Chinese while preserving formatting. The text inside the bold is "以查询取代派生变量（Replace Derived Variable with Query）". The part inside parentheses is already English, we can keep it as is. But "Replace Derived Variable with Query" is an English phrase. Should we translate the English phrase inside parentheses? The instruction says "Keep proper nouns/product names when appropriate." The phrase "Replace Derived Variable with Query" might be a proper phrase? It's not a product name. It might be a translation of a term. We need to translate the entire line. But the original text has both Chinese and English in the same line: "**以查询取代派生变量（Replace Derived Variable with Query）**". That might be part of a bilingual title. The translation request says "Translate the given Markdown to Simplified Chinese." So we might translate everything into Chinese, but keep English parts? But the instruction: "Keep proper nouns/product names when appropriate." We might keep "Replace Derived Variable with Query" as is? Or translate it to Chinese: "用查询替代派生变量". But since the phrase "Replace Derived Variable with Query" is already in parentheses as an English translation, the original might be bilingual. The task: "Translate the given Markdown to Simplified Chinese." So we should translate the entire thing to Chinese. But we need to preserve the parentheses and the English part? Usually we might translate the English phrase too. However, the instruction says "Keep proper nouns/product names when appropriate." This phrase is not a proper noun. So we can translate it.

But we must preserve Markdown structure exactly. So we keep the bold markers.

Thus we output: **以查询取代派生变量（用查询替代派生变量）**.

But the parentheses may cause double Chinese. But we need to decide.

Alternatively, we could keep the English phrase in parentheses unchanged, as it's already a translation. The request is to translate the given Markdown to Simplified Chinese. The original had Chinese and English. Possibly the English is a translation of the Chinese. So translating the English would be redundant.

Let's examine instructions: "Translate the given Markdown to Simplified Chinese." That suggests we should produce a version that is all Chinese. So we should translate the English phrase to Chinese. But we need to preserve parentheses? We can keep parentheses but inside Chinese.

Thus the final answer: **以查询取代派生变量（用查询替代派生变量）**.

But we must not translate code fences or inline code. There is none. So okay.

Return only the translated Markdown.

Thus answer: **以查询取代派生变量（用查询替代派生变量）**.
...done thinking.

**以查询取代派生变量（用查询替代派生变量）**

![](img/0_refactor-82.png)

**范例**

即时计算，不必每次更新。

Thinking...
The user says: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese." Then shows rules. Then "Markdown to translate:" and then "before：" followed by a blank. It seems incomplete. Possibly they want to translate the phrase "before：" into Chinese? Actually the markdown to translate includes only "before：" maybe with some formatting? It shows "before：" and nothing else. The translation would be "before：" -> "before："? Wait, they might want "before：" to be translated? That seems trivial: "before：" in Chinese is "之前：" . So the output should be "之前：" with the colon. But keep the Markdown structure exactly. There's no markdown structure beyond a line. It could be a heading? But it's just a line. So output "之前：" only. They said return only the translated Markdown. So just output "之前：" . Ensure no extra commentary. Let's do that.
...done thinking.

之前：

![](img/0_refactor-83.png)

Thinking...
We have a user message: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: - Preserve Markdown structure exactly (headings, lists, emphasis). - Do NOT translate code fences or inline code spans wrapped in backticks. - Do NOT alter links or image paths. - Keep proper nouns/product names when appropriate. Return ONLY the translated Markdown, no extra commentary.

Markdown to translate:
after："

It seems incomplete. The user says "Markdown to translate: after：" maybe expecting some content after? They wrote "after：" and nothing else. The content maybe omitted. We cannot translate nothing. So output nothing? The instruction says "Return ONLY the translated Markdown, no extra commentary." But if there is no markdown content, we might just output nothing. But maybe they intended to provide "after:" as a heading? But likely they want to translate a heading "after：" into Chinese? But they might have mis-structured. The "after：" is presumably part of a sentence "after:" then content? It's unclear.

Let's consider possibility: The heading is "after：" maybe they want translation of "after:" which is "之后：" or "完成后：" etc. But no further context.

We might respond with "after：" unchanged? But the rule: "Preserve Markdown structure exactly". If we have a heading "after：" we translate to "之后：" but maintain the colon.

We have "after：" as maybe a heading with a colon, no text after. That is Markdown text. The translation would be "之后：" in Simplified Chinese. But we need to preserve formatting. So we output "之后：" as the only line.

But we don't know if it's a heading (#). It's just "after：" no preceding #. So it's a plain paragraph. So translation: "之后：" maybe.

Alternatively maybe they want to keep "after：" as code? No.

Let's translate: "after：" -> "之后：" The colon in Chinese is the same. So we output "之后："

Let's do that.
...done thinking.

之后：

![](img/0_refactor-84.png)

![](img/0_refactor-85.png)

**范例：不止一个数据来源**

Thinking...
We have a user prompt: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: - Preserve Markdown structure exactly (headings, lists, emphasis). - Do NOT translate code fences or inline code spans wrapped in backticks. - Do NOT alter links or image paths. - Keep proper nouns/product names when appropriate. Return ONLY the translated Markdown, no extra commentary.

Markdown to translate:
before：

"

So the text to translate is just:

before：

No other text. So we need to translate that to Simplified Chinese: "before：" presumably means "before：" and maybe we need to translate "before：" into Chinese, but "before" as a heading? The original has "before：" plain. That may be the text: "before：" maybe just a word "before" with colon. In Chinese that would be "before："? Or we translate "before" to "之前". But we should preserve punctuation. So "before：" becomes "之前：". That is likely. There's no code fences or anything. So output: "之前：" on its own line. So final answer: "之前：".
...done thinking.

之前：

![](img/0_refactor-86.png)

Thinking...
We have a user asking: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: Preserve Markdown structure exactly (headings, lists, emphasis). Do NOT translate code fences or inline code spans wrapped in backticks. Do NOT alter links or image paths. Keep proper nouns/product names when appropriate. Return ONLY the translated Markdown, no extra commentary. Markdown to translate: after：" Then presumably the content is "after：" but nothing else. Maybe the Markdown content is just the word "after："? That seems incomplete. Perhaps the content is "after：" only. The instructions: "Markdown to translate:" then a line "after：" and then nothing else. So we need to translate that into Simplified Chinese. The word "after：" likely is a heading or text. It might be a heading "after：". The colon is a Chinese colon. We should translate "after" to Chinese, but we should keep the colon. "after" in Chinese could be "之后". So "after：" becomes "之后：". Also preserve Markdown. If it's a heading? The original has "after：" with no preceding hash. So it's just text. So we translate to "之后：". Should we keep the trailing colon. Yes. No code fences. Just produce "之后：" as the output. According to rule, return only the translated Markdown, no extra commentary. So final output: "之后："
...done thinking.

之后：

![](img/0_refactor-87.png)

引入断言：

![](img/0_refactor-88.png)

Thinking...
We need to translate that heading? Actually it's bold. The content is "**将引用对象改为值对象（Change Reference to Value）**". They want to translate to Simplified Chinese. But it's already partly Chinese: "将引用对象改为值对象（Change Reference to Value）". That seems to be a bilingual heading: Chinese and English. The rule: "Translate the given Markdown to Simplified Chinese." The given markdown already includes Chinese, but the English part remains. Should we translate the English part into Chinese? The English part is "Change Reference to Value". That is the translation: "将引用改为值"? But the Chinese is already "将引用对象改为值对象". So we could translate the English part into Chinese to produce Chinese phrase. But maybe the instruction: translate entire markdown to Simplified Chinese. The content: "**将引用对象改为值对象（Change Reference to Value）**". Since Chinese already present, we could translate the English phrase inside parentheses to Chinese, but that would duplicate. But maybe we keep the English phrase? But instruction says translate to Simplified Chinese. We should translate all text, including the English inside parentheses. However, "Change Reference to Value" might be a title; maybe we can keep the English as is? But the instruction says "Translate the given Markdown to Simplified Chinese." So we should translate that part.

The translation of "Change Reference to Value" is "将引用改为值" or "将引用转换为值". The Chinese title already says "将引用对象改为值对象". So we could adjust to "将引用对象改为值对象（将引用改为值）" or "将引用对象改为值对象（将引用改为值）". But it's a bit redundant. Maybe we keep the parentheses with Chinese translation: "（将引用改为值）". But that might not match the instruction to preserve structure exactly except translation. However, we can modify the text. The structure remains bold with parentheses.

Thus output: **将引用对象改为值对象（将引用改为值）**. That seems fine.

Return only the translated markdown.

Let's output that.
...done thinking.

**将引用对象改为值对象（将引用改为值）**

不需要共享一个对象。

![](img/0_refactor-89.png)

**范例**

Thinking...
We have a prompt: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese." The Markdown to translate includes just "before：" and then presumably some code or text that hasn't been shown? The given Markdown to translate is:

```
before：
```

It seems incomplete. Possibly the user forgot to paste the actual content. We need to respond. According to policy, if the user request cannot be performed due to insufficient data, we can ask for clarification. The instruction: "Return ONLY the translated Markdown, no extra commentary." But there's no content to translate beyond "before：" which is a single word and colon. We should translate that. "before：" in Chinese would be "之前：" or "前置：" depending context. But likely "before：" as a heading or something. They might want translation of "before：" as a heading. The colon is part of punctuation. So we should produce "之前：" or "前面：" or "在之前：" but the best is "之前：".

We must preserve Markdown. It might be just a line. So output "之前：" only. That should satisfy.

But also, there might be more content that was truncated. But we can't ask to add. We need to respond. The user might want the translation of "before：" as the only content.

Thus final answer: "之前："
...done thinking.

之前：

![](img/0_refactor-90.png)

Thinking...
The user says: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: ... Return ONLY the translated Markdown, no extra commentary."

The Markdown to translate: 
```
after：
```

It seems to be just "after："? That might be incomplete? But we must translate the given Markdown to Simplified Chinese. The content is "after：" maybe a heading? But it's not a heading, it's just a line "after：". We need to translate "after：" to Chinese. "after" -> "之后". So "之后：" (with colon). But the colon is Chinese full-width colon. But original used colon "：". It is Chinese colon already. So we translate "after：" to "之后：" or maybe "之后："? The colon is already Chinese. So the translation would be "之后：".

Thus the output is just the line "之后：". Let's output that.

...done thinking.

之后：

![](img/0_refactor-91.png)

Thinking...
We need to translate Markdown to Simplified Chinese, preserve structure, headings, etc. The given text is a heading? Actually it's bold: **将值对象改为引用对象（Change Value to Reference）**. But the original is English? It says: "**将值对象改为引用对象（Change Value to Reference）**". Wait, the original might be: "**Change Value to Reference**" but translated? Actually the markdown to translate includes Chinese and English inside parentheses. The rule says preserve proper nouns etc. Here "Change Value to Reference" is likely an English term. The translation might be "将值对象改为引用对象（Change Value to Reference）" which is already Chinese plus the English phrase in parentheses. But the instruction: "Translate the given Markdown to Simplified Chinese." We should translate English to Chinese. The original text is "**将值对象改为引用对象（Change Value to Reference）**". That contains Chinese already. The parentheses contain English phrase "Change Value to Reference". Should we translate that? The rule says preserve proper nouns/product names when appropriate. "Change Value to Reference" might be a concept name. The Chinese translation would be "将值对象改为引用对象". The English phrase might be the original title. We may translate both parts. The Chinese part is already there. The parentheses maybe optional. But to keep as translation, we can translate "Change Value to Reference" to Chinese "将值对象改为引用对象". But then duplication. Hmm.

The original given Markdown includes both Chinese and English. The instruction says translate to Simplified Chinese. So the output should be Chinese only. But the heading includes Chinese already. The parentheses part is English and should be translated too, but maybe the entire phrase is a heading with English in parentheses. We could keep the heading as Chinese only. But the instruction to keep proper nouns when appropriate; "Change Value to Reference" might be a term but we can translate it to Chinese: "将值对象改为引用对象".

Thus final output: **将值对象改为引用对象**. The parentheses removed? Maybe keep the parentheses with Chinese translation: (将值对象改为引用对象) but redundant.

Better: **将值对象改为引用对象（将值对象改为引用对象）**? Not good.

I think simplest: **将值对象改为引用对象**. No parentheses. Let's output that.

...done thinking.

**将值对象改为引用对象**

共享一个对象。

![](img/0_refactor-92.png)

**范例**

Thinking...
We need to translate the given Markdown to Simplified Chinese, preserving structure, but not translating code fences or inline code. The content is just "before："? The Markdown to translate is:

```
before：
```

But we need to preserve Markdown structure exactly. "before：" maybe a heading? It looks like "before：" alone. Might be a heading with no markup. But there is no markdown heading symbol. The string is "before：" (with a colon). That is the entire content.

Thus we translate "before：" to Chinese: "之前：" (since "before" in Chinese context is "之前"). The colon stays same? There's Chinese colon ":"? The original has "：" (full-width colon). They used "：" after "before". That is a full-width colon. Should keep that. So we produce "之前：" (with Chinese full-width colon). That's it.

Return only translated Markdown. No extra commentary.

Thus answer: "之前：".

...done thinking.

之前：

![](img/0_refactor-93.png)

Thinking...
We need to translate the given Markdown to Simplified Chinese, preserving structure. The input is:

after：

It seems there's just a line: "after：" That's a heading? Actually "after：" could be a heading or a paragraph. It's a line with "after：" which is an English word "after" and a colon. Possibly a heading? In markdown, if we want a heading we need #, but here it's just text.

Thus translation: "after：" becomes "after："? But we need translate "after" into Chinese: "之后" or "后". The colon remains. So "after：" becomes "之后："? Or "后："?

Simplest: "after：" => "之后："

Thus final answer is just that line.

We must keep Markdown exactly, no extra commentary. Just output "之后：" in a line.

Ensure no code fences. There's no markdown headings or lists. Just the line. Should we preserve newline? The original has a newline after? It says "after：" on a line, then a blank line. We'll output "之后：" and maybe a blank line.

Return only the translated Markdown.
...done thinking.

之后：

![](img/0_refactor-94.png)

![](img/0_refactor-95.png)

存在的问题：构造函数与一个全局的仓库对象**耦合**。

改进的办法：**将仓库对象作为参数传递给构造函数**。

**第10章　简化条件逻辑**

Thinking...
We need to translate to Simplified Chinese. The phrase: "**分解条件表达式（Decompose Conditional）**". Already has Chinese "分解条件表达式" plus parentheses. They might want to translate "Decompose Conditional" but keep translation? They said keep proper nouns/product names when appropriate. "Decompose Conditional" is likely a concept term maybe should be translated into Chinese as "分解条件". Already in Chinese. They might keep English? The original says "**分解条件表达式（Decompose Conditional）**". The Chinese is there. They might want to keep it same. But translation might be to translate the Markdown to Simplified Chinese. The heading is already in Chinese. Should we translate "Decompose Conditional" to Chinese? It is inside parentheses. Might translate to "分解条件" again? But it's already Chinese. Maybe keep as is. But maybe the translation of "Decompose Conditional" into Chinese could be "分解条件". But the Chinese phrase already is there. But the original heading is exactly that. So we can keep the same string. But maybe they want translation to Chinese but it's already Chinese. But we still need to keep the same structure. So we output exactly the same heading. But check: the heading is not preceded by a heading marker (#). It's just bold text. We should preserve that. So the output: "**分解条件表达式（Decompose Conditional）**". That's it.

But maybe the Chinese text should be "分解条件表达式（Decompose Conditional）". Already. So just copy.

Therefore final answer: same.
...done thinking.

**分解条件表达式（Decompose Conditional）**

![](img/0_refactor-25.png)

程序之中，复杂的条件逻辑是最常导致复杂度上升的因素之一。

对于条件逻辑，**将每个分支条件分解成新函数**还可以带来更多好处：可以突出条件逻辑，更清楚地表明每个分支的作用，并且突出每个分支的原因。

注：实际上为提炼函数的一个应用场景。

**范例**

Thinking...
We have a short markdown snippet:

```
before：

```

But actually it's:

"before："

Probably there's a line break after colon? The input shows:

```
before：

```

It might be "before：" maybe with a newline after. There's no code fences. So translation: "before：" -> "之前：" or "之前：" or "before:"? In Chinese, "before" as a heading? But it's just text. They want to translate to Simplified Chinese. So "before：" becomes "之前：" (with Chinese colon "："? The original colon is a full-width colon "：" after before. So we preserve it. So output:

```
之前：

```

But maintain Markdown structure. There is no markup, just text. So output that.
...done thinking.

之前：

![](img/0_refactor-96.png)

Thinking...
We have to translate a Markdown content. The content is "after：" with a line break? The content is:

after：

That's the entire input? The user says: "Markdown to translate:" and then shows

after：

So they want translation of "after：" to simplified Chinese. But "after：" is not a full sentence. Perhaps they want translation of "after:"? In English, "after:" is a heading? But "after：" maybe is part of a sentence. The colon is Chinese punctuation "：". So translation is "之后：" ?

"after：" likely means "之后：" or "完成后："?

But the simplest: "after：" -> "之后："

They want to preserve Markdown structure. So just output:

之后：

with Chinese colon. The input had a space before "after". The input: "after：" maybe with a space? There's a space before "after" but likely not needed. Just output "之后：". Probably no heading markers.

Thus the answer is:

之后：

Return only that.

...done thinking.

之后：

![](img/0_refactor-97.png)

Thinking...
We need to translate the given Markdown into Simplified Chinese. It contains only one line: "**合并条件表达式（Consolidate Conditional Expression）**". Wait that's already Chinese with English in parentheses. It says "合并条件表达式（Consolidate Conditional Expression）". Actually the original might be English but translated. But we need to translate entire markdown. So we keep headings etc. The line is bold. So we just keep it same? Should we translate the Chinese part? It says "合并条件表达式" which is Chinese. There's also "Consolidate Conditional Expression" English. The instruction says to keep proper nouns/product names when appropriate. We need to translate the entire markdown into Simplified Chinese. It already is partly Chinese. But perhaps the original was "Consolidate Conditional Expression" and the translation is "合并条件表达式". We keep the English in parentheses? Usually translation would not have English. But we should keep the entire text: "**合并条件表达式（Consolidate Conditional Expression）**". Since the English is inside parentheses, maybe we keep it. The instruction says preserve markdown structure exactly. So we need to output the same bold formatting. So the answer is:

**合并条件表达式（Consolidate Conditional Expression）**

No other modifications.
...done thinking.

**合并条件表达式（Consolidate Conditional Expression）**

![](img/0_refactor-26.png)

Thinking...
We need to translate to Simplified Chinese. The original: **以卫语句取代嵌套条件表达式（Replace Nested Conditional with Guard Clauses）**. Already partially translated? The phrase in Chinese "以卫语句取代嵌套条件表达式" is fine. Then parentheses contain the English title. Should we translate entire? The instruction: "Translate the given Markdown to Simplified Chinese." So translate the entire content. The original includes both Chinese and English. So we need to translate the English part as well. So "Replace Nested Conditional with Guard Clauses" to Chinese: "用守卫语句取代嵌套条件表达式". That is likely. Keep heading and bold. So final Markdown: **以卫语句取代嵌套条件表达式（用守卫语句取代嵌套条件表达式）**? Wait that repeats Chinese twice. Should just have Chinese phrase and parentheses Chinese translation. So maybe: **以卫语句取代嵌套条件表达式（用守卫语句取代嵌套条件表达式）**. But Chinese original "以卫语句取代嵌套条件表达式" seems same as "Use guard clauses instead of nested conditional". So maybe better: **以守卫语句取代嵌套条件表达式（用守卫语句取代嵌套条件表达式）**. The original Chinese "以卫语句" seems incomplete. I'd use "守卫" is correct. Let's choose: **以守卫语句取代嵌套条件表达式（用守卫语句取代嵌套条件表达式）**.

But keep original structure exactly. So final output: **以守卫语句取代嵌套条件表达式（用守卫语句取代嵌套条件表达式）**.
...done thinking.

**以守卫语句取代嵌套条件表达式（用守卫语句取代嵌套条件表达式）**

![](img/0_refactor-27.png)

Thinking...
We need to translate the given Markdown to Simplified Chinese. Already the text is in Chinese. We need to translate it? But it's Chinese already. Probably it's a snippet to translate from English? Actually text is Chinese. The instruction says translate to Simplified Chinese. So if it's already Chinese, maybe keep same? But maybe it's originally in English? The text says "if 两条分支都是正常行为...". It's Chinese with some English words. We might need to translate the English parts into Chinese? But it's a mixture. The instruction says "translate the given Markdown to Simplified Chinese." The text is already Simplified Chinese. But maybe the parts like "if...else..." and "guard clauses" should be translated. But those are code constructs, not translated. The instruction says "Do NOT translate code fences or inline code spans wrapped in backticks." But there are none. So maybe we translate "if…else…" to "if…else…" (kept as is) and "guard clauses" into "守卫语句"? Actually "guard clauses" is a term. In Chinese often "守卫语句" or "防卫语句"? In Chinese, "guard clauses" is often translated as "守卫语句" or "防守语句". But the original uses "卫语句" (maybe a typo). The phrase "卫语句" is missing "守". They might want to correct to "守卫语句"? But it's unclear. But we can keep as is: "卫语句".

The translation: "如果两条分支都是正常行为，就应该使用形如if...else...的条件表达式；如果某个条件极其罕见，就应该单独检查该条件，并在该条件为真时立刻从函数中返回。这样的单独检查常常被称为'卫语句'（guard clauses）。"

Maybe keep the English part as is. So we output that same line. There's no code fences. So final answer: the same line.

But we must preserve Markdown. There's no headings, lists. So we output that line.

Thus final answer: the given Chinese text. No commentary.
...done thinking.

如果两条分支都是正常行为，就应该使用形如if…else…的条件表达式；如果某个条件极其罕见，就应该单独检查该条件，并在该条件为真时立刻从函数中返回。这样的单独检查常常被称为"卫语句"（guard clauses）。

**如果使用if-then-else结构，则对if分支和else分支的重视是同等的；以卫语句取代嵌套条件表达式的精髓就是：给某一条分支以特别的重视。**

"每个函数只能有一个入口和一个出口"的观念未必有用，保持代码清晰才是最关键的。

**范例**

Thinking...
We need to translate "before" but preserve markdown structure. The input is:

```
before
```

But that's not markdown heading; it's plain text. We need to translate to simplified Chinese: "before" => "之前" or "在前" depending context. Usually "before" as noun could be "之前". So translation: "之前".

Thus output only that line.
...done thinking.

之前

![](img/0_refactor-28.png)

Thinking...
The user says: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: ... Return ONLY the translated Markdown, no extra commentary."

The markdown to translate is:

after

Hmm. There's just the word "after". That seems to be the entire markdown content? So we need to translate "after" to Chinese. In Simplified Chinese, "after" could be "之后". But the context is unclear. But the instruction is to translate the given Markdown to Simplified Chinese. The Markdown is just "after". So we translate that to "之后". Also, maintain Markdown structure. There's no heading or list, just plain text. So we output "之后".

No extra commentary. Just the translated markdown.

Thus final output: "之后".
...done thinking.

之后

![](img/0_refactor-29.png)

**范例：将条件反转**

初始

![](img/0_refactor-30.png)

反转

![](img/0_refactor-31.png)

合并条件表达式

![](img/0_refactor-32.png)

删除可变变量

![](img/0_refactor-33.png)

Thinking...
We just translate that heading. The heading is "**以多态取代条件表达式（Replace Conditional with Polymorphism）**". In markdown double asterisks produce bold. We should translate the content inside but keep the links? No links. Just translation: The Chinese already is there: "以多态取代条件表达式". The rest is English: Replace Conditional with Polymorphism. We might translate to Chinese: "以多态取代条件表达式（用多态替代条件）"? But we must translate to Simplified Chinese. The heading already partly Chinese. The bracket contains English. We should translate the English part to Chinese: "用多态取代条件表达式". But that duplicates the Chinese phrase. Maybe keep the English phrase but translate? The instruction: "Translate the given Markdown to Simplified Chinese." So entire text should be Chinese. The phrase inside parentheses should be translated. So we might write "**以多态取代条件表达式（用多态取代条件）**". But maybe more natural: "用多态替代条件表达式". So parentheses maybe "用多态替代条件表达式". So the final heading: **以多态取代条件表达式（用多态替代条件表达式）**. That seems repetitive but okay.

Let's produce that.
...done thinking.

**以多态取代条件表达式（用多态替代条件表达式）**

![](img/0_refactor-34.png)

Thinking...
We need to translate the given Markdown to Simplified Chinese. The input Markdown: "**引入特例（Introduce Special Case）**". That seems to be a title bolded with a translation already partially present. The translation required: we have the original Chinese "引入特例（Introduce Special Case）" which already includes Chinese text plus English in parentheses. The instruction: "Translate the given Markdown to Simplified Chinese." So we should translate the English part into Chinese, but the Chinese part is already there. We might also keep the parentheses with English or translate them? The rule: "Translate the given Markdown to Simplified Chinese." So we should convert all English into Chinese. That means we should replace "Introduce Special Case" with Chinese. But it's already inside parentheses. We should translate that part. The Chinese phrase is already there. So maybe the translation should be just "**引入特例**" or maybe keep parentheses with Chinese translation. Let's read the input carefully: **引入特例（Introduce Special Case）**. The English is inside parentheses. The translation should be Chinese, but the phrase is already in Chinese. So maybe the output should be **引入特例** (since we don't need English). But if we preserve the parentheses we could replace with Chinese translation: **引入特例（引入特例）**? That seems redundant. The instructions: "Translate the given Markdown to Simplified Chinese." So the entire Markdown should be in Simplified Chinese. Since the Chinese is already present, we just remove the English part. So final: **引入特例**. But keep bold? Yes. So "**引入特例**". That should be the output. No other content.

Double-check: We have to preserve Markdown structure exactly. There's only one line of Markdown. So we output "**引入特例**".

Let's respond.
...done thinking.

**引入特例**

![](img/0_refactor-98.png)

Thinking...
We need to translate given markdown to Simplified Chinese, preserve markdown. Input text is:

"特例"（Special
Case）模式：创建一个特例元素，用以表达对这种特例的共用行为的处理，**从而用一个函数调用取代大部分特例检查逻辑**。

It includes quotes, parentheses, newline? The text is:

"特例"（Special
Case）模式：创建一个特例元素，用以表达对这种特例的共用行为的处理，**从而用一个函数调用取代大部分特例检查逻辑**。

Need to translate, but we keep the original "Special Case" presumably as product name? It's in parentheses. We need keep proper nouns. "Special Case" is in parentheses and maybe refers to a name. We should preserve it. But the Chinese part "特例" is the translation. The parenthesis contains "Special Case". In the translation we might keep that as is, but perhaps translate inside? The instruction: Keep proper nouns/product names when appropriate. "Special Case" might be a term; maybe keep it. So output should have the Chinese translation.

Original: "特例"（Special
Case）模式：创建一个特例元素，用以表达对这种特例的共用行为的处理，**从而用一个函数调用取代大部分特例检查逻辑**。

But maybe we translate "Special Case" to "特例"? It's already there. Might need to remove the duplicate? The original text seems to have both Chinese and English "Special Case" inside parentheses, maybe a bilingual name. We might translate "Special Case" to "特例"? But that would duplicate Chinese. Maybe we keep it as "Special Case" unchanged. Let's keep as is.

We should preserve markdown: ** ... ** stays. There's a newline inside parentheses: "Special\nCase". That is maybe a line break. In Markdown, parentheses contain a line break. We should preserve exactly. So we need to keep the newline inside. The input has:

"特例"（Special
Case）模式...

So there is a line break after Special. We'll keep that. The translation should keep that structure. We need to translate the rest: "模式：创建一个特例元素，用以表达对这种特例的共用行为的处理，**从而用一个函数调用取代大部分特例检查逻辑**。"

We translate to: "模式：创建一个特例元素，用以表达对这种特例的共用行为的处理，**从而用一个函数调用取代大部分特例检查逻辑**。"

The Chinese part is already Chinese. We just need to ensure it's correct. Actually the whole original text is Chinese plus English. We just need to translate into Simplified Chinese. The Chinese is already simplified Chinese. So we just keep it as is? But the instruction: "Translate the given Markdown to Simplified Chinese." The given text is already simplified Chinese. But maybe the English parts need translation? Only "Special Case" is English. That may be a proper noun; we might keep it as is. So translation is identical to original. But we might need to translate the English word "Special Case" to Chinese? But the instruction says keep proper nouns when appropriate. "Special Case" is a term that maybe needs translation. It's ambiguous. The original Chinese part uses "特例" which is the translation. So "Special Case" maybe refers to a special case. Might not be a proper noun. I'd keep as is? Might not.

Let's just output the same text, no changes. The only difference: The original text had "特例" in quotes, and parentheses. We preserve that. No markdown to preserve beyond that. So final output is the same string. But the user might expect translation of "Special Case" to Chinese. Let's decide. "Special Case" is an English phrase; the Chinese translation "特例" is already provided. So maybe they want us to keep "Special Case" as "特例". But that duplicates Chinese? Wait, the string is: "特例"（Special Case）模式。 So maybe it's like "Special Case" mode. They are showing a bilingual name. Perhaps we keep both. The translation may keep the English in parentheses? The instruction: Keep proper nouns/product names when appropriate. "Special Case" may be a proper noun (the mode name). So keep it. So no changes.

Thus output identical.
...done thinking.

"特例"（Special
Case）模式：创建一个特例元素，用以表达对这种特例的共用行为的处理，**从而用一个函数调用取代大部分特例检查逻辑**。

Thinking...
We need to translate to Simplified Chinese. The original is "**引入断言（Introduce Assertion）**". Wait original already has Chinese "引入断言" plus English. We need to translate? The original is bilingual. We must translate entire content into Simplified Chinese. So we likely translate "Introduce Assertion" into Chinese "引入断言". But the Chinese already there. Perhaps keep both? The original line: **引入断言（Introduce Assertion）**. The Chinese part "引入断言" is the Chinese translation of the English "Introduce Assertion". So the entire string includes both. When translating to Simplified Chinese, we may just keep the Chinese part and remove the English? But the rule: preserve markdown, no other commentary. The original has both. We may keep as is? But the instruction: "Translate the given Markdown to Simplified Chinese." The given markdown includes Chinese already. The English portion is "Introduce Assertion". We need to translate that to Chinese, which is "引入断言". Since Chinese already present, we can just remove the English part, but then we would have duplicate? Maybe the translation should produce Chinese only: "**引入断言**" (but that duplicates Chinese). But we might keep parentheses? Might want to keep Chinese and the original English? But the instruction says translate to Simplified Chinese. So we need to translate English parts. The parentheses contain English, so we should replace that with Chinese. So final: **引入断言（引入断言）**? That's odd. Actually maybe we should remove parentheses and keep just Chinese? The original had Chinese then parentheses with English. After translation, we might only keep Chinese. So final: **引入断言**. That is simplest. Let's output that.
...done thinking.

**引入断言**

![](img/0_refactor-99.png)

**第11章 重构API**

Thinking...
We need to translate the given Markdown to Simplified Chinese, preserve structure. The heading is in bold? The original: **将查询函数和修改函数分离（Separate Query from Modifier）**. Actually the content is already Chinese with English parenthetical. The instruction: translate the given Markdown to Simplified Chinese. So we need to translate the heading into Simplified Chinese. It's already Chinese. But we may translate the English phrase: Separate Query from Modifier. But it's already included. Maybe they want to translate the whole string. The Chinese part is Chinese. The English part remains. Maybe we translate to "将查询函数和修改函数分离（Separate Query from Modifier）" is already Chinese. So translation would be same? Maybe they want translation of English part to Chinese? The English phrase is in parentheses. We can translate that too: "将查询函数与修改函数分离". But it's repeated? The original heading includes Chinese and English. But the instruction: "Translate the given Markdown to Simplified Chinese." The content is already Chinese but includes English. Maybe we translate the English portion to Chinese. But we need to preserve structure. Let's produce "**将查询函数和修改函数分离（将查询与修改函数分离）**" or we could keep the English part. It's ambiguous. They might want translation of everything, including English. I'd translate the English inside parentheses to Chinese. So final: **将查询函数和修改函数分离（将查询与修改函数分离）**. That might be acceptable.

Let's do that.
...done thinking.

**将查询函数和修改函数分离（将查询与修改函数分离）**

![](img/0_refactor-100.png)

**范例**

Thinking...
We need to translate the given Markdown to Simplified Chinese. The input contains:

"before" as a heading? Actually the snippet shows:

before

But there might be a heading indicator? The snippet: 
```
before
```
But likely it's a heading. In markdown, "before" alone might be a level-1 heading if preceded by "#"? But not shown. It just shows "before" as a plain text. The instruction says "Translate the given Markdown". The Markdown snippet just has the word "before" on a line. So we translate "before" to Simplified Chinese: "之前" or "在前". Likely "之前". So output should be "之前" alone. But need to preserve Markdown structure. So if it's just a line, keep it as is. So output:

之前

But ensure no extra commentary. So final output is:

```
之前
```

But the rule says do not alter code fences or inline code spans. There's no code. So just produce "之前".

Thus final.
...done thinking.

之前

![](/img/0_refactor-101.png)

Thinking...
We need to translate the markdown content. The provided markdown to translate: "After". That is a single word. The instruction: preserve markdown structure, no translation of code fences or inline code. We just translate "After" to Simplified Chinese: "之后". It might be a heading? But it's just text "After". No markdown syntax. Just plain word. Should we translate it to Chinese? Yes.

Return only translated markdown. So just output "之后".
...done thinking.

之后

![](/img/0_refactor-102.png)

![](/img/0_refactor-103.png)

Thinking...
We just translate heading. It's bold text. Keep Markdown. So "**函数参数化（Parameterize Function）**". No translation needed? Wait it's already Chinese. But need to translate "Parameterize Function" into Chinese? It's already bilingual. We can keep Chinese. Probably keep original. Just return same.
...done thinking.

**函数参数化（Parameterize Function）**

![](/img/0_refactor-104.png)

范例

Thinking...
We need to translate given Markdown to Simplified Chinese, preserving structure. The given Markdown content is "before". That seems like the only content? The prompt: "Markdown to translate:" followed by a line "before". So just the word before? Should translate "before" to Chinese. "before" in Chinese could be "之前" or "在...之前". Since just a word, we translate to "之前". Should preserve Markdown structure: it's a plain line, no headings or lists. So output "之前". No extra commentary.
...done thinking.

之前

![](/img/0_refactor-105.png)

Thinking...
We need to translate "After" to Simplified Chinese. The original text is "After". Just that. But we need to preserve Markdown. "After" is a heading? It's ambiguous. It could be a top-level heading "After". But in Markdown, "After" alone is just a paragraph. No heading syntax. The instructions: Preserve Markdown structure exactly. So if the source had "After" as a heading, but we can't see if it's a heading or just a paragraph. The snippet: "After" is on its own line, no #. So it's a paragraph. We'll translate to Chinese "之后". Possibly "After". But "After" as a heading? I'd translate as "之后". But keep no markdown changes. So output "之后".

We need to output only the translated markdown. So answer: "之后".

Check if any code fences etc. None.

Thus answer.
...done thinking.

之后

![](/img/0_refactor-106.png)![](/img/0_refactor-107.png)g)

Thinking...
We just need to translate heading into Simplified Chinese: "移除标记参数（Remove Flag Argument）" already includes Chinese title, but maybe we keep same. Actually the heading is bold "**移除标记参数（Remove Flag Argument）**". So we need to output same but with translation? It already is translation. Should we keep? Possibly we need to translate the whole content: It's already in Chinese. But maybe the translation of the phrase is needed? But it's bilingual. The instruction: "Translate the given Markdown to Simplified Chinese." So maybe the original had English but is already Chinese. But we can still leave as is. Since it's already Chinese. We just output same content.
...done thinking.

**移除标记参数（Remove Flag Argument）**

![](/img/0_refactor-108.png)

**"标记参数"是这样的一种参数：调用者用它来指示被调函数应该执行哪一部分逻辑。**

**范例**

Thinking...
We have only one heading? The markdown given: "Before". Likely heading level? The text shows "Before" as plain text? It says "Markdown to translate: Before". So likely a heading level 1? Could be plain. It might be a heading? Actually Markdown: "Before" could be a heading if preceded by "#". But the prompt didn't show a "#". It's just "Before". So treat as plain text.

We need to translate to Simplified Chinese: "Before" -> "之前" or "先前". Common translation: "之前".

We must preserve markdown. So just output "之前".
...done thinking.

之前

![](/img/0_refactor-109.png)

Thinking...
We need to translate given Markdown to Simplified Chinese. The content is just "After". That's plain text. We preserve structure: it's presumably a heading? Actually "After" is just a word. It might be a heading? No header marks. It's just a line of text. So translation: "之后". Or "After" is maybe heading level? But there's no markup. So just output "之后".

We should keep exactly structure. So output "之后".

...done thinking.

之后

![](/img/0_refactor-110.png)

Thinking...
We just need to translate the heading and text. It's a single line bold. The phrase: "**保持对象完整（Preserve Whole Object）**". In Chinese, "保持对象完整" is correct. But we need to translate the English "Preserve Whole Object" into Chinese but keep the Chinese part. The original text is Chinese with parentheses containing English. The translation should be: "**保持对象完整（Preserve Whole Object）**" is already the same. But maybe they want to translate the English part too? The instruction: "Translate the given Markdown to Simplified Chinese." So we need to translate all text. The English phrase "Preserve Whole Object" should be translated to Chinese. But we can keep the original as in parentheses? Wait the original already contains Chinese "保持对象完整" then parentheses with English "Preserve Whole Object". So we might need to translate the English inside parentheses as well. But the rule says preserve Markdown. We can translate the entire string: "**保持对象完整（保持对象完整）**"? That would be redundant. The English part is a translation of the Chinese. So maybe they expect to keep the Chinese and translate English? But since the original already had Chinese, maybe they want to keep Chinese only. But the instruction says "Translate the given Markdown to Simplified Chinese." The English part should be translated. So we should replace "Preserve Whole Object" with Chinese translation: "保持对象完整" or "完整保持对象"? Actually translation is "保持对象完整". So the final should be "**保持对象完整（保持对象完整）**". But that's odd double. Might be better to remove parentheses and keep only Chinese. But the instruction says preserve Markdown structure exactly. It doesn't say we must keep parentheses. But we cannot alter the structure too much. The original had parentheses. We can keep them but replace content. So final: "**保持对象完整（保持对象完整）**". But maybe we keep the original Chinese and English translation? We can keep "保持对象完整（Preserve Whole Object）" unchanged, because it's already in Chinese. But it's ambiguous.

Given typical translation tasks, we would translate the English part inside parentheses. So I'd produce "**保持对象完整（保持对象完整）**". Let's do that.
...done thinking.

**保持对象完整（保持对象完整）**

![](/img/0_refactor-111.png)

减少函数参数长度，方便后续拓展。

Thinking...
The user wants to translate a markdown to Simplified Chinese. They gave a short text:

**以查询取代参数（Replace Parameter with Query）**

They ask: "Return ONLY the translated Markdown, no extra commentary."

We must translate the phrase into simplified Chinese. But we already have Chinese: "**以查询取代参数（Replace Parameter with Query）**". That is already in Chinese. They might want to translate the English part "Replace Parameter with Query" into Chinese? The phrase is a combination of Chinese and English. They might want to translate that into simplified Chinese? The entire line maybe is already Chinese. Maybe they want to translate the English part? Let's examine: "**以查询取代参数（Replace Parameter with Query）**"

Maybe they want to translate the English part to Chinese? But it's already in parentheses with English. The phrase "Replace Parameter with Query" is English. They might want to translate it to Chinese: "用查询替代参数" or "以查询替代参数" but that's the same as the Chinese part. The whole line maybe: "**以查询取代参数（Replace Parameter with Query）**" We could translate the English part to Chinese: "以查询取代参数（用查询替代参数）" but that's redundant. The original might be from a manual, so they include English and Chinese. The request is to translate the Markdown to Simplified Chinese. The line is already Chinese. So translation might be unnecessary, but they might want to translate the English inside parentheses. So we can produce: "**以查询取代参数（用查询替代参数）**"

But we must preserve the Markdown structure exactly. It's a bold heading. So we keep it as "**以查询取代参数（用查询替代参数）**"

However the Chinese is already there, but they might want to replace the English with Chinese. The original line has Chinese heading, then parentheses with English. We should translate the English portion to Chinese, as per "Translate the given Markdown to Simplified Chinese." The English phrase is the only part that needs translation.

Thus final output: "**以查询取代参数（用查询替代参数）**"

But is "Replace Parameter with Query" literally translated as "用查询替代参数" or "以查询替代参数"? Both are fine. In the heading we already have "以查询取代参数". The parentheses can be "用查询替代参数" or "以查询替代参数". Which is best? The heading already uses "以查询取代参数". The parentheses might just repeat the translation. So "用查询替代参数" is a slightly different phrasing. But it's okay.

Thus answer: "**以查询取代参数（用查询替代参数）**"

Let's produce that.
...done thinking.

**以查询取代参数（用查询替代参数）**

![](/img/0_refactor-35.png)

**函数的参数列表应该总结该函数的可变性**，标示出函数可能体现出行为差异的主要方式。和任何代码中的语句一样，**参数列表应该尽量避免重复**，并且参数列表越短就越容易理解。

使用场景：调用函数时传入了一个值，而这个值由函数自己来获得也是同样容易

什么是"同样容易"：函数可以承担这份原本由调用方所承担的"获得正确的参数值"的责任。

什么时候不适用：移除参数可能会给函数体增加不必要的依赖关系。

Thinking...
We need to translate the given Markdown to Simplified Chinese. The provided text is already Chinese, but maybe the translation needed is to Simplified Chinese? It appears the source might be a mix of Chinese and English. Let's read:

"留意：如果在处理的函数具有**引用透明性**（referential transparency，即，不论任何时候，只要传入相同的参数值，该函数的行为永远一致），这样的函数既容易理解又容易测试，不会去除参数，让它访问一个可变的全部变量。"

So the text is partly Chinese, partly English. We need to translate to Simplified Chinese. The output should be the translated Markdown.

We need to translate the English parts to Chinese. The Markdown structure: heading? It's just a paragraph. The bold part "**引用透明性**" remains. The code is "referential transparency" which should be translated to "引用透明性" which is already there. The rest of the parentheses: "（referential transparency，即，不论任何时候，只要传入相同的参数值，该函数的行为永远一致）" So the phrase "referential transparency" is in parentheses and already Chinese translation. The rest after that: "这样的函数既容易理解又容易测试，不会去除参数，让它访问一个可变的全部变量。" This might need translation: maybe "这些函数既容易理解又容易测试，不会去除参数，让它访问一个可变的全部变量。" But "不去除参数，让它访问一个可变的全部变量" sounds odd. Maybe the original phrase is: "such functions are both easy to understand and easy to test, they won't remove parameters, letting it access all mutable variables." Wait, the original English: "Such functions are easy to understand and easy to test, they don't remove parameters, letting them access all mutable variables." Actually original: "Such functions are easy to understand and easy to test, they won't remove parameters, letting them access a mutable whole variable." The Chinese translation: "这样的函数既容易理解又容易测试，不会去除参数，让它访问一个可变的全部变量。" The phrase "可变的全部变量" may be wrong. Perhaps "可变的全部变量" means "the entire mutable variable"? It could be "mutable state" maybe "可变状态"? The original "a mutable whole variable" maybe "mutable state" or "mutable global state"? Hard to say.

Given we need to translate to Simplified Chinese, but the content is already Chinese. We need to translate the English parts that are in parentheses. The phrase "referential transparency" is already in Chinese: "引用透明性". There's a small part: "即" means "that is". The rest after parentheses is Chinese. So no need to translate. The only English content is "referential transparency" inside parentheses. It's already Chinese translation. So maybe no translation needed? The instruction says "translate the given Markdown to Simplified Chinese". It's already Simplified Chinese. But we may need to fix grammar or translate minor English words. There is "i.e." "i.e." is "即". So it's fine.

The entire text is: 
"留意：如果在处理的函数具有**引用透明性**（referential transparency，即，不论任何时候，只要传入相同的参数值，该函数的行为永远一致），这样的函数既容易理解又容易测试，不会去除参数，让它访问一个可变的全部变量。"

Thus no translation needed; but we could ensure proper punctuation: maybe remove the comma after the parentheses. But it's okay.

Thus output the same. But we need to preserve Markdown. It's just a paragraph with bold. So output exactly the same text.

Thus answer: same.
...done thinking.

留意：如果在处理的函数具有**引用透明性**（referential transparency，即，不论任何时候，只要传入相同的参数值，该函数的行为永远一致），这样的函数既容易理解又容易测试，不会去除参数，让它访问一个可变的全部变量。

Thinking...
We need to translate the heading and text. The original: "**以参数取代查询（Replace Query with Parameter）**"

We must preserve Markdown. So we translate "以参数取代查询" to Chinese? It's already Chinese. Actually it's already in Chinese. The parenthetical part is English "Replace Query with Parameter". They want to translate into Simplified Chinese. The text inside bold is "以参数取代查询（Replace Query with Parameter）". We keep it in Markdown. So we replace "Replace Query with Parameter" with Chinese translation: "用参数替换查询" maybe. But since the first part already says "以参数取代查询", the translation might duplicate. But we translate the English inside parentheses.

Thus result: **以参数取代查询（用参数替换查询）**.

We need to preserve Markdown: bold. So output exactly that line. No extra commentary.

...done thinking.

**以参数取代查询（用参数替换查询）**

![](/img/0_refactor-36.png)

好处：改变依赖关系，去掉令人不快的引用。

注意：要考虑责任分配问题，会增加函数调用者的复杂度，而设计接口时又需要考虑易用性。

Thinking...
We just translate heading: "**移除设值函数（Remove Setting Method）**" to Simplified Chinese. But the heading already includes Chinese and English. It says "移除设值函数（Remove Setting Method）". The translation might be same? The instruction: translate the given Markdown to Simplified Chinese. But it's already in Chinese. The English part "Remove Setting Method" should be translated. Should we translate it to "移除设值方法"? The heading has both Chinese and English in parentheses. We should translate English inside parentheses. So change to "移除设值方法". So final heading "**移除设值方法**". Probably remove parentheses. But might preserve parentheses? The original has Chinese and English separated by parentheses. We can translate English portion and keep Chinese. So produce "**移除设值方法**". That matches simplified Chinese.

Return only the translated Markdown.
...done thinking.

**移除设值方法**

![](/img/0_refactor-112.png)

去除不必要的设值函数。

Thinking...
We need translate Markdown. Title in Chinese: "**以工厂函数取代构造函数（Replace Constructor with Factory Function）**". They ask: translate the given Markdown to Simplified Chinese. The content is only that line. We preserve Markdown structure. So output same string with translation? Already Chinese. Actually it's bilingual: Chinese + English. Maybe we translate the English part too? The title contains Chinese and English. They might want to keep both? The rule: "Translate the given Markdown to Simplified Chinese." The line is already Chinese, but includes English phrase. We may translate English part to Chinese, but keep Chinese? The phrase: "(Replace Constructor with Factory Function)". Maybe we translate to Chinese: "(用工厂函数替代构造函数)". So entire line: "**以工厂函数取代构造函数（用工厂函数替代构造函数）**" But duplication. Maybe we remove English part: "**以工厂函数取代构造函数**". But rule says preserve Markdown exactly, not content. We need to translate English to Chinese but keep heading formatting. We might convert parentheses content.

Thus final: "**以工厂函数取代构造函数（用工厂函数替代构造函数）**". But that's repeating same Chinese. Might be okay.

Alternatively maybe just keep Chinese part, drop English. I'd produce:

**以工厂函数取代构造函数**.

But original had both. The instruction: "Translate the given Markdown to Simplified Chinese." So translation of entire line. So we produce Chinese-only. That might be best.

Thus output: "**以工厂函数取代构造函数**".
...done thinking.

**以工厂函数取代构造函数**

![](/img/0_refactor-113.png)

工厂函数的实现更为灵活。

Thinking...
We just translate title and emphasis to Simplified Chinese. The original is "**以命令取代函数（Replace Function with Command）**". This is already Chinese but includes English in parentheses. Should we translate? The instruction says "Keep proper nouns/product names when appropriate." The phrase in parentheses is English, it's a translation title. Might keep it. But maybe translate? It says translate the given Markdown to Simplified Chinese. The content already is Chinese plus English. The English part is a subtitle. Usually translate that part too: "Replace Function with Command". In Chinese: "以命令取代函数". That is already Chinese. But maybe we want to keep "Replace Function with Command" as is? It's in parentheses, could keep as is. The instruction says preserve markdown structure exactly. So we keep the parentheses. Should we translate the English to Chinese? Might not be necessary but maybe better. But the original says "以命令取代函数（Replace Function with Command）". So it's the Chinese plus English translation. We could translate the English into Chinese but that would duplicate. Might keep as is. So final answer: "**以命令取代函数（Replace Function with Command）**".
...done thinking.

**以命令取代函数（Replace Function with Command）**

![](/img/0_refactor-114.png)

Thinking...
We just need to translate the markdown. The content: "**以函数取代命令（Replace Command with Function）**". It is already Chinese and English inside parentheses. We might need to translate "Replace Command with Function" maybe keep it in English? The instruction: Keep proper nouns/product names when appropriate. "Replace Command with Function" is likely a phrase, not a proper noun. We might translate it into Chinese: "用函数替代命令". The parentheses originally: (Replace Command with Function). It can be translated into Chinese within parentheses. So produce "**以函数取代命令（用函数替代命令）**". Ensure formatting preserved. Return only translated Markdown.
...done thinking.

**以函数取代命令（用函数替代命令）**

![](/img/0_refactor-115.png)

处理的逻辑不是特别复杂，则命令对象可能显得费而不惠。

**第12章　处理继承关系**

Thinking...
We need to translate the given Markdown to Simplified Chinese. Input is:

**函数上移（Pull Up Method）**

This is bold text. We should translate the phrase inside bold. "函数上移（Pull Up Method）" likely meaning "Function pull up method". In Chinese we would say "函数上移（Pull Up Method）" but "Pull Up Method" may be left as is because it's a term? The rule says keep proper nouns/product names when appropriate. Pull Up Method might be a technical term. But translation: "**函数上移（Pull Up Method）**". The phrase inside is "函数上移（Pull Up Method）". We might translate to "函数上移（Pull Up Method）". Maybe keep "Pull Up Method" as English. So final is "**函数上移（Pull Up Method）**". No changes. It's already Chinese for 函数上移, with parentheses. Should we translate "Pull Up Method" to Chinese? Could be "拉升方法"? But likely keep it. Let's keep "Pull Up Method". So output:

**函数上移（Pull Up Method）**
...done thinking.

**函数上移（Pull Up Method）**

![](/img/0_refactor-116.png)

消除重复代码。

**字段上移（Pull Up Field）**

![](/img/0_refactor-117.png)

同样也是消除重复代码。

Thinking...
The user says: "You are a professional technical translator. Translate the given Markdown to Simplified Chinese. Rules: Preserve Markdown structure exactly (headings, lists, emphasis). Do NOT translate code fences or inline code spans wrapped in backticks. Do NOT alter links or image paths. Keep proper nouns/product names when appropriate. Return ONLY the translated Markdown, no extra commentary."

Markdown to translate:

**构造函数本体上移（Pull ...**

Wait the given text: "**构造函数本体上移（Pull Up Constructor Body）**". Already seems in Chinese with parentheses. The phrase "Pull Up Constructor Body" is an English phrase, but the Chinese translation is "构造函数本体上移". It might be from a refactoring tool like IntelliJ or JetBrains, with the English name.

The user might want the translation of the entire line into Simplified Chinese. The text currently is "**构造函数本体上移（Pull Up Constructor Body）**". This is already partially translated, but maybe they want the Chinese version only, replacing the English phrase in parentheses with its Chinese translation.

We need to keep Markdown emphasis: **...**. So we can translate inside. Probably "构造函数本体上移（提取构造函数主体）" or "构造函数主体上移" but we have "构造函数本体上移" already.

The English phrase is "Pull Up Constructor Body". We can translate that as "将构造函数主体上移" but maybe better: "提取构造函数主体". The phrase might be used as a refactoring name, so maybe keep "Pull Up Constructor Body" untranslated. But the instruction: Keep proper nouns/product names when appropriate. Here "Pull Up Constructor Body" is a proper noun? It's a refactoring name. Might be kept as is? The instruction says keep proper nouns/product names when appropriate. So "Pull Up Constructor Body" might be a proper noun (refactoring name) but it's in English. It's fine to leave it. The current text has that phrase inside parentheses.

But the instruction: Do NOT translate code fences or inline code spans. This is not code. So we can translate. But we need to preserve structure. The heading might not be a heading but bold. So we just output "**构造函数本体上移（Pull Up Constructor Body）**" or possibly change Chinese translation inside parentheses to Chinese.

But the given text is already "**构造函数本体上移（Pull Up Constructor Body）**". The user says translate the Markdown to Simplified Chinese. It already contains Chinese and English. The English part is "Pull Up Constructor Body". We may translate that as "构造函数主体上移" inside parentheses. But that would duplicate. Actually might be better: keep Chinese heading: "构造函数本体上移（Pull Up Constructor Body）" is already Chinese with English in parentheses. Possibly they want to translate the English portion into Chinese. So we could output: "**构造函数本体上移（将构造函数主体上移）**" but that's a bit redundant.

Alternatively, maybe they just want to keep the translation as is. However, the instruction is to translate Markdown to Simplified Chinese. So we should translate any English words into Chinese. That includes "Pull Up Constructor Body". So we will translate that phrase.

Simplified Chinese translation: "构造函数主体上移" maybe. But we need to be consistent. The heading has "构造函数本体上移" (with 本体). Should be "构造函数主体上移" or keep 本体? It's a translation difference. But we can keep the heading as is, but the phrase inside parentheses will be Chinese.

So final output: "**构造函数本体上移（构造函数主体上移）**"

But that might sound odd. Usually refactoring names: "提取构造函数主体" or "构造函数主体提取" but "Pull Up" means moving up. So "构造函数主体上移". So we keep that.

Thus final Markdown:

**构造函数本体上移（构造函数主体上移）**.

Yes.
...done thinking.

**构造函数本体上移（构造函数主体上移）**

![](/img/0_refactor-118.png)

提炼各个子类函数中的重复部分至父类中，同样也是消除重复代码。

Thinking...
We need to translate the given Markdown to Simplified Chinese while preserving structure. The Markdown is:

**函数下移（Push Down Method）**

So it's bold. We need to translate to Chinese but keep the formatting. The content inside ** is "函数下移（Push Down Method）". That's already Chinese with the method name in parentheses. But perhaps we need to translate the title: "函数下移（Push Down Method）" maybe it's already bilingual. The instruction: translate the given Markdown to Simplified Chinese. So maybe we need to keep "Push Down Method" but it's already included. The content is already Chinese. But we might need to translate "函数下移" which is Chinese. So maybe the title is fine. Possibly we should keep the original.

But maybe we need to translate the English part "Push Down Method" into Chinese as well? The title is "函数下移（Push Down Method）" already includes both. The instruction says: "Translate the given Markdown to Simplified Chinese." So we need to ensure the output is in Simplified Chinese. The given text is already Simplified Chinese. The English part is an English phrase. We might keep it or translate to Chinese. The instruction says: "Keep proper nouns/product names when appropriate." "Push Down Method" is a proper noun term, maybe keep it. It's already inside parentheses. So we keep it.

Thus output should be exactly same: **函数下移（Push Down Method）**. No changes.

Let's double-check: No code fences or inline code. Good.

Thus final answer: **函数下移（Push Down Method）**.
...done thinking.

**函数下移（Push Down Method）**

![](/img/0_refactor-119.png)

如果超类中的某个函数只与一个（或少数几个）子类有关，那么最好将其从父类中挪走，放到真正关心它的子类中去。

**字段下移（Push Down Field）**

![](/img/0_refactor-120.png)

如果某个字段只被一个子类（或者一小部分子类）用到，就将其搬移到需要该字段的子类中。

Thinking...
We just translate the heading? The original Markdown: "**以子类取代类型码（Replace Type Code with Subclasses）**". It's bold text. It includes Chinese part already. We need to translate the English part? The instruction: "Translate the given Markdown to Simplified Chinese." The Chinese part is already there. The English part "Replace Type Code with Subclasses" should be translated into Chinese. However the heading is in bold: "**以子类取代类型码（Replace Type Code with Subclasses）**". The Chinese part "以子类取代类型码" is already Chinese. Maybe we need to translate the English part too, but it's already inside parentheses. We need to translate into Chinese but keep the original. But we must not translate code fences etc. It's just heading. The instructions: "Translate the given Markdown to Simplified Chinese." So the English part inside parentheses should be translated into Chinese? But the parenthetical is English already. The entire bold line is a title. We might keep Chinese part but maybe also translate the English part into Chinese. Since the Chinese part is Chinese, we keep it. For the English part we translate to Chinese. But there is no instruction to remove parentheses. Could we translate into Chinese like "以子类取代类型码（用子类替代类型码）"? But that duplicates Chinese. Actually the original English phrase "Replace Type Code with Subclasses" is a translation of "以子类取代类型码". The Chinese phrase might be a translation. So maybe the text is redundant: Chinese with parentheses containing English translation. We are to translate entire Markdown to Simplified Chinese. The English part is already English; we should translate it into Chinese, but then we would have Chinese in parentheses: "以子类取代类型码（以子类替代类型码）" which is duplicate. But maybe the original had English in parentheses to show translation. But we are to translate to Chinese; we could replace English with Chinese but we might keep Chinese part? But that would produce duplicate Chinese.

Alternatively, maybe we keep original Chinese and English as is, because it's already bilingual? The instruction says "Translate the given Markdown to Simplified Chinese." The heading already contains Chinese. So maybe no translation needed. But the English portion is not Chinese. We might translate it to Chinese to preserve Chinese only. So new text: "**以子类取代类型码（用子类取代类型码）**"? But that would be duplication. Possibly we should keep only Chinese: "**以子类取代类型码**"? But then we lose the parentheses. But the instruction says preserve markdown structure exactly. That includes the parentheses. But we could change the inside? The structure still includes parentheses. But if we translate the content inside, the parentheses remain. So we can translate English to Chinese inside parentheses.

Thus final output: **以子类取代类型码（以子类替代类型码）**. Wait Chinese translation "以子类替代类型码" or "用子类替代类型码". The original Chinese "以子类取代类型码" vs "替代类型码". We can use "以子类替代类型码". That's fine.

Thus final.
...done thinking.

**以子类取代类型码（以子类替代类型码）**

![](/img/0_refactor-121.png)

可以用多态来处理条件逻辑，而不是根据不同的类型码采取不同的行为。

有些字段或函数只对特定的类型码取值才有意义，子类的形式能更明确地表达数据与类型之间的关系。

Thinking...
We just translate heading and bold. The content is "**移除子类（Remove Subclass）**". Actually the original is in English? Wait the given is "**移除子类（Remove Subclass）**". That's already Chinese plus translation in parentheses. They want translate the Markdown to Simplified Chinese. It's already Chinese. Maybe they want translation of "Remove Subclass" part. But the phrase "移除子类" is Chinese for Remove Subclass. The translation inside parentheses is English. They might want to translate entire line to Chinese: "**移除子类（移除子类）**"?? But the original had Chinese and English, but the instruction says "translate the given Markdown to Simplified Chinese." Since it's already Chinese, maybe just keep as is. But we need to translate the English portion into Chinese. So output should be "**移除子类（移除子类）**". But that would duplicate Chinese. Maybe they want to remove English part and keep Chinese only. But instruction: "Translate the given Markdown to Simplified Chinese." So convert any English words to Chinese. So "Remove Subclass" -> "移除子类". So final is "**移除子类（移除子类）**". However it's redundant. Maybe we can keep Chinese in both places? The parentheses would have Chinese translation. But the original Chinese part is outside parentheses, English inside. They want to convert to Chinese. So we can just keep Chinese outside, Chinese inside. So final: "**移除子类（移除子类）**". But that's weird duplication. Could also be "**移除子类（移除子类）**" or "**移除子类（移除子类）**". Ok.

Let's produce.
...done thinking.

**移除子类（移除子类）**

![](/img/0_refactor-122.png)

如果子类的用处太少，可以移除子类，将替换为父类的一个字段。

Thinking...
We need to translate the given Markdown to Simplified Chinese. But the original is in Chinese: "**提炼超类（Extract Superclass）**". That already seems Chinese. We might keep it as is, but maybe translate "提炼超类" to Chinese? It's already Chinese. "Extract Superclass" is English. So maybe keep it as is. But the instruction: Translate the given Markdown to Simplified Chinese. So maybe translate "Extract Superclass" to "提炼超类". But the phrase is already "提炼超类（Extract Superclass）". So maybe keep it. Or maybe the instruction to preserve code fences etc. The phrase includes backticks? No. So just output the same line? The original is "**提炼超类（Extract Superclass）**". So we might not need to change. But translation might be same. But "提炼超类" is Chinese. So no change. So we just output the same.

Thus output same.

...done thinking.

**提炼超类（Extract Superclass）**

![](/img/0_refactor-123.png)

目的在于把重复的行为收拢一处。

Thinking...
We need to translate into Simplified Chinese. The original text is **折叠继承体系（Collapse Hierarchy）**. Already includes Chinese "折叠继承体系" and English "(Collapse Hierarchy)". Should we translate the English in parentheses? The rule: Keep proper nouns/product names when appropriate. "Collapse Hierarchy" might be a term; we may translate it or keep it? Usually, in translation, we might translate the term into Chinese, maybe keep original in parentheses? The given example includes Chinese and English. In translation, we can keep English, or translate into Chinese. The rule: "Keep proper nouns/product names when appropriate." Collapse Hierarchy is a proper noun or product name? It's a concept. Could be kept. But we might translate to "折叠继承体系（Collapse Hierarchy）". Already present. The translation request: "Translate the given Markdown to Simplified Chinese." So the Chinese is already there. But the parentheses English might remain. Maybe we should translate the English part to Chinese as well: "(Collapse Hierarchy)" => "(折叠继承体系)"? That would duplicate. Might be acceptable. But guidelines: Keep proper nouns/product names when appropriate. We can translate term "Collapse Hierarchy" to Chinese. But it's the same Chinese phrase. So maybe leave as is. The original already has Chinese, so translation might not need changes. But the parentheses English is a proper noun? The concept name could be left as is. But we may translate entire phrase into Chinese only: **折叠继承体系**. But that removes the English part. The original had both. But the translation request may require translation into Chinese, so we can remove English. However, we may keep the parentheses but translate. I'd produce **折叠继承体系（Collapse Hierarchy）**? Actually original has that. Since it's already Chinese, translation is maybe trivial. But the instruction: "Translate the given Markdown to Simplified Chinese." So maybe we need to translate the English part: "Collapse Hierarchy" to Chinese. The Chinese phrase is already provided, but we might keep the parentheses? Let's do: **折叠继承体系（Collapse Hierarchy）**? No translation needed. But we might keep as is. Let's produce same string. Since no changes needed, output same.
...done thinking.

**折叠继承体系（Collapse Hierarchy）**

![](/img/0_refactor-124.png)

随着继承体系的演化，有时会发现一个类与其父类差别不大，此时可以把父类和子类合并起来。

Thinking...
We just translate title. The content is just "**以委托取代子类（Replace Subclass with Delegate）**". That is already Chinese? Actually original was maybe "**Replace Subclass with Delegate**" in English but the Chinese translation is given. Wait the original: "**以委托取代子类（Replace Subclass with Delegate）**". The Chinese phrase is "以委托取代子类" and then the English in parentheses. The translation might be only the English part? The instruction: "Translate the given Markdown to Simplified Chinese." But the Markdown already contains Chinese and English. So we need to translate the whole thing to Simplified Chinese. The phrase "Replace Subclass with Delegate" should be translated to Chinese: "用委托取代子类". But we already have Chinese preceding. So we could keep Chinese, but also maybe replace the English parentheses with Chinese translation. The given text: "**以委托取代子类（Replace Subclass with Delegate）**". We should translate the entire phrase to Simplified Chinese. So final would be "**以委托取代子类（用委托取代子类）**" or just the Chinese phrase. But we must preserve structure exactly: bold text. Keep parentheses. The English part should be translated. So result: "**以委托取代子类（用委托取代子类）**". Let's produce that.
...done thinking.

**以委托取代子类（用委托取代子类）**

![](/img/0_refactor-125.png)

![](/img/0_refactor-126.png)

与继承关系相比，使用委托（即组合）关系时接口更清晰、耦合更少。

Thinking...
We need translate title. The content: "**以委托取代超类（Replace Superclass with Delegate）**". The markdown is bold. We need keep bold. The translation should preserve markdown and link names. The title is already in Chinese and English parentheses. Maybe we translate Chinese part? Already Chinese. Possibly we need translate English part? The rule: keep proper nouns. "Replace Superclass with Delegate" maybe keep as is? But it's an English phrase. It might be okay to translate to "以委托取代超类" and keep the English in parentheses. The text already includes Chinese translation of phrase. So maybe just keep as is. But we might need translate entire line: "**以委托取代超类（Replace Superclass with Delegate）**". There's no code fences. So just output same line? But we could adjust translation of parentheses? It's already translation inside parentheses. So it's correct.

Thus output the same line.

...done thinking.

**以委托取代超类（Replace Superclass with Delegate）**

![](/img/0_refactor-37.png)

以组合取代继承。

一个经典的误用继承的例子：让栈（stack）继承列表（list）。这个想法的出发点是想复用列表类的数据存储和操作能力。虽说复用是一件好事，但这个继承关系有问题：列表类的所有操作都会出现在栈类的接口上，然而其中大部分操作对一个栈来说并不适用。更好的做法应该是把列表作为栈的字段，把必要的操作委派给列表就行了。

**所以，如果超类的一些函数对子类并不适用，就说明我不应该通过继承来获得超类的功能。**

同时也要避免走弯路：完全避免使用继承，如果符合继承关系的语义条件（超类的所有方法都适用于子类，子类的所有实例都是超类的实例），那么继承是一种简洁又高效的复用机制。

建议：首先（尽量）使用继承，如果发现继承有问题，再使用以委托取代超类。
