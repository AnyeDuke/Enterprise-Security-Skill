## Draw.io用于威胁建模

发布于2018年10月5日

我最近花了很多时间试图找到威胁模型图表的好工具。我定义了几个要求并开始评估那里有什么：

- **支持数据流图（DFD）和攻击树**：我认为这些对威胁建模至关重要。序列图也是一个优点。
- **令人愉快且易于使用**：必须易于创建图表，并且没有任何奇怪的错误，使其工作变得笨重或繁琐。这很重要，不仅是为了我自己的理智，也是为了让开发人员采用这种做法。如果你没有为他们提供一个好的工具，他们可能不会这样做。
- **免费和跨平台**：它必须是免费的，适用于Windows，Mac和Linux。如果该工具仅适用于Windows，或者您必须处理许可证，则会使在业务中引入威胁建模变得更加困难。
- **不是基于Web或“基于云”**：它应该感觉像一个适当的桌面应用程序和存储应该是很好的旧本地文件。云（也称为其他人的计算机）可能很好，但不适用于威胁建模。基于文件的存储还可以轻松地将图表检查到版本控制中，并使其在代码旁边生效。

我检查了很多不同的工具，但没有一个满足要求。许多人没有DFD和攻击树的元素，[微软威胁建模工具](https://www.microsoft.com/en-us/download/details.aspx?id=49168)只能在Windows上运行，[Threat Modeler](https://threatmodeler.com/)是基于网络的，[威胁龙](https://threatdragon.org/)感觉很尴尬，而[Dia](http://dia-installer.de/index.html.en)是老旧，笨重和错误。

我对我发现的东西感到非常失望，所以我抓住了自己的痒，开始研究一个新的基于电子的应用程序，我希望这个应用程序非常适合我，希望很多其他人。为此做了初步研究，我遇到了[mxgraph](https://github.com/jgraph/mxgraph)项目，它似乎是完美的核心图表组件。然后我看到它被用作一个名为[draw.io](https://www.draw.io/)的工具的一部分，幸运的是，这是一个完美的契合，有一些配置和定制......

## draw.io中的DFD和攻击树

Draw.io没有为DFD和攻击树提供专用库，但它具有所有元素。它们只分布在几个不同的图书馆。在使用该工具之后，我发现自定义元素并将它们添加到自定义库中非常容易，这些库可以导出以便于重用。我为DFD和攻击树创建了两个新库，[并将它们放在Github上](https://github.com/michenriksen/drawio-threatmodeling)。

## 数据流图

这些是*dfd.xml*库中可用的元素：

![img](http://michenriksen.com/images/drawio/dfd-elements_thumbnail.png)

### DFD库中的所有元素。

除了经典的DFD元素之外，该库还包含一个注释元素，资产标签，威胁参与者，安全控件以及用于直接在图中记录它们的便捷表。

为了向您展示它如何一起工作，我创建了一个简单，虚构系统的图表：

![img](http://michenriksen.com/images/drawio/dfd_thumbnail.png)

### 简单，虚构系统的DFD。

## 攻击树木

这些是*attack-tree.xml*库中可用的元素：

![img](http://michenriksen.com/images/drawio/attack-tree-elements_thumbnail.png)

### DFD库中的所有元素。

为了向您展示这些如何协同工作，我重新创建了经典的*Open Safe*攻击树：

![img](http://michenriksen.com/images/drawio/attack-tree_thumbnail.png)

### 探索如何打开保险箱的攻击树。

## 设置好

为了威胁建模而设置draw.io非常容易：

1. [下载](https://about.draw.io/integrations/#integrations_offline)并安装适用于您的操作系统的draw.io.
2. 克隆或下载[Github存储库](https://github.com/michenriksen/drawio-threatmodeling)
3. 打开draw.io应用程序并创建一个新的空白图表
4. 单击*文件*菜单，然后单击*打开库...*
5. 导航到放置Github存储库的位置并打开其中一个XML文件

恭喜！您现在已准备好威胁模型。为了使draw.io甚至更好，我可以推荐接通*最小*通过单击主题的*附加功能*菜单，并选择最小的主题。这使得UI更干净，并为实际图表提供了更多空间。

我希望您会发现这对您和您的团队来说更有帮助，并使威胁模型更容易，更快乐。