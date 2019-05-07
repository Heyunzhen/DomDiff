# 一、diff策略

###### 1.Web UI中DOM节点跨层级的移动特别少，可以忽略不计
###### 2.拥有相同类的两个组件将会生成相似的树形结构，拥有不同类的两个组件将会生成不同的树形结构
###### 3.对于同一层级的一组(具有相同父元素的)子节点，它们可以通过唯一id进行区分(即key)

# 二、tree diff（两棵组件树之间的比较。比较两棵树的结构）

######  基于策略1，React对树的算法进行了简洁明了的优化，即：对树进行分层比较，两棵树只会对 同一层次 的节点进行比较。

#### 类似于下图描述

![tree](https://upload-images.jianshu.io/upload_images/7566087-466bb3637b71a493.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/552/format/webp "树形结构图")

# 三、component diff（组件的差异比较过程）

 ###### 1.如果都是同一类型的组件(即：两节点是同一个组件类的两个不同实例，比如：<div id="before"></div>与<div id="after"></div>)，按照原策略继续比较Virtual DOM树即可2.如果出现不是同一类型的组件，则将该组件判断为dirty component，从而替换整个组件下的所有子节点（即：假如treeA(旧组件树)的某个节点A，在树状结构中，对应treeB(新组件树)的节点B。如果节点B和与节点A不是同一类型的组件，则节点A及其所有子节点，将全部被删除，并且重新创建节点B及其子节点）

# 真实DOM渲染，结构差异的比较

###### diff的差异化对比过程——【注意事项】：过程目的：为了找到由旧的树结构得到新的树结构，最高效的方式前提条件：已知新旧两棵Virtual DOM树的树结构diff的差异化对比过程——【总体流程】：依次取出新集合中的每个节点，通过key值，确定当前节点是否存在于旧集合中，如果存在，再进行其他的比较、判断，确定旧集合中的此节点是否需要移动。

![diff](https://upload-images.jianshu.io/upload_images/7566087-76e5ec97a7e7eafa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1000/format/webp "比较过程")