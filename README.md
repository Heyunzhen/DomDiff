# 一、diff策略

###### 1.Web UI中DOM节点跨层级的移动特别少，可以忽略不计
###### 2.拥有相同类的两个组件将会生成相似的树形结构，拥有不同类的两个组件将会生成不同的树形结构
###### 3.对于同一层级的一组(具有相同父元素的)子节点，它们可以通过唯一id进行区分(即key)

# 二、tree diff（两棵组件树之间的比较。比较两棵树的结构）

######  基于策略1，React对树的算法进行了简洁明了的优化，即：对树进行分层比较，两棵树只会对 同一层次 的节点进行比较。

#### 类似于下图描述

![tree](https://upload-images.jianshu.io/upload_images/7566087-466bb3637b71a493.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/552/format/webp "树形结构图")
