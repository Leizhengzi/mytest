JSX 介绍
思考一下下面这个变量声明：
const element = <h1>Hello, world!</h1>;
这个有趣的标签语法既不是字符串也不是HTML。
它被称为JSX，它是对Javascrip语法的扩展。我们推荐使用这种方式用React来描述UI的样子。JSX让你感觉像是一个模板语言，
但是它实际是来自于强大的javascript。

JSX生产React"elements"。我们将在下一节探索渲染它们到DOM。下面，你将能发现学习JSX的一些所需要的基本内容。

在JSX中嵌套表达式
你能够在大括号里面嵌套任何Javascript表达式。
例如，