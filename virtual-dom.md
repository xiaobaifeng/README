# virtual-dom（虚拟dom）

## 定义

一个JavaScript DOM模型，支持[元素创建](https://github.com/livoras/simple-virtual-dom/blob/master/lib/element.js)，[差异计算](https://github.com/livoras/simple-virtual-dom/blob/master/lib/diff.js)和[补丁操作](https://github.com/livoras/simple-virtual-dom/blob/master/lib/patch.js)，以实现高效的重新渲染

***注意:*** 
 1. [定义来自于 Matt-Esch/virtual-dom](https://github.com/Matt-Esch/virtual-dom);
 2. 定义中关键词的相关链接来自 [livoras/simple-virtual-dom](https://github.com/livoras/simple-virtual-dom)(简单的虚拟dom算法。它只有~500行代码，包括virtual-dom算法的基本思想。);

## 动机

手动DOM操作很乱，跟踪以前的DOM状态很难。解决这个问题的方法是编写代码，就像在状态发生变化时重新创建整个DOM一样。当然，如果每次应用程序状态发生变化时实际上都重新创建了整个DOM，那么您的应用程序将非常慢，输入字段将失去焦点。

virtual-dom是一组模块，旨在为您的应用程序提供表示DOM的声明方式。因此，不是在应用程序状态更改时更新DOM，而只是创建一个虚拟树，或者VTree看起来像您想要的DOM状态。virtual-dom然后将弄清楚如何有效地使DOM看起来像这样，而无需重新创建所有DOM节点。

virtual-dom允许您通过创建完整VTree视图然后有效地修补DOM以完全按照您的描述来更新状态更新视图。这样可以保持手动DOM操作和以前的状态跟踪不受应用程序代码的影响，从而为Web应用程序提供清晰且可维护的呈现逻辑。
