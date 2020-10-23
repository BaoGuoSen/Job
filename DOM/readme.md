## dom节点
1. 节点属性
- node.parentNode (指向父节点，不存在就为空）
- node.childNodes (返回nodeList的实例，一个类数组对象，包含所有字节点）
- node.previousSibling (指向兄弟节点的上一个，若没有返回null）
- node.nextSibling (指向兄弟节点的下一个，若没有返回null）
- node.firstChild (指向子节点列表的第一个）
- node.lastChild (指向字节点列表的最后一个）

2. 节点方法
- node.hasChildNodes() （判断是否含有字节点）
- node.appendChild() (在childNOdes列表末尾添加节点）
