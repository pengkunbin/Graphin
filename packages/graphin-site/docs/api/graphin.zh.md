---
title: Graphin 组件
order: 1
---

本文档是 `<Graphin/>` React 组件的 API 文档。

## Props

|   属性   | 类型                  | 是否必选 | 说明          |
| -------- | --------------------- | -------- | ------------- |
| data     | [Data](#data)         | **是** | 图的节点和边数据      |
| layout   | [Layout](#layout)     | 否       | 布局配置      |
| options  | [Options](#option)    | 否       | G6 配置      |
| ref      | [Ref](#ref)           | 否       | Graphin 组件 Ref      |
| extend   | [Extend](#extend)     | 否       | 扩展配置   |
| register | [Register](#register) | 否       | G6 自定义节点/边/行为注册配置 |

## Data

图的节点和边数据

|   属性 | 类型                   | 是否必选 | 说明       |
| ------ | ---------------------- | -------- | ---------- |
| nodes  | [Node[]](#node) | 是       | 节点的集合 |
| edges  | [Edge[]](#edge) | 是       | 边的集合   |

### Node

节点

|   属性         | 类型                                  | 是否必选 | 说明                                              |
| -------------- | ------------------------------------- | -------- | ------------------------------------------------- |
| id             | string                              | **是** | 唯一标示 id                              |
| data           | [NodeData](#nodedata)                 | **是** | 节点附带的 key-value 数据 |
| shape          | string                              | 否       | 节点的图形类型（NodeShape）。默认值为内置的 `CircleNode`。可以通过 extend 对 NodeShape 进行扩展  |
| style          | [NodeDefaultStyle](#nodedefaultstyle) | 否       | 和 NodeShape 相对应的样式信息                     |
| x              | number                              | 否       | 节点的位置信息：X 坐标（在保存下来的图数据中会有位置信息）                            |
| y              | number                              | 否       | 节点的位置信息：Y 坐标（在保存下来的图数据中会有位置信息）                           |
| layout         | NodeLayoutType                    | 否       | 内置的某些布局在节点上附加的属性                                 |
| `[key:string]` | any                                 | 否       | 其余用户自定义的属性，也是支持挂载的              |
|                |

### NodeData

节点附带的 key-value 数据，properties 一般从后端返回，表示一些用于描述节点的属性。

|   属性         | 类型     | 是否必选 | 说明                    |
| -------------- | -------- | -------- | ----------------------- |
| id             | string | **是** | 节点的唯一标示 id |
| label          | string | 否       | 节点的标签文本          |
| properties     | any[]    | 否       | 节点的属性，任意的 key-value              |
| `[key:string]` | any    | 否       | 其余任意属性                |

### NodeDefaultStyle

和 NodeShape 相对应的样式信息

|   属性       | 默认值    | 说明           |
| ------------ | --------- | -------------- |
| nodeSize     | 20        | 节点的大小     |
| primaryColor | #9900EF | 节点的主要颜色 |
| fontSize     | 12        | 文本的字体大小 |
| fontColor    | #3b3b3b | 文本的字体颜色 |
| dark         | #eee    | 置灰状态下颜色      |

### Edge

边

|   属性         | 类型     | 是否必选 | 说明                         |
| -------------- | -------- | -------- | ---------------------------- |
| data           | { properties: any[], [key: string]:any }     | **是** | 边附带的数据               |
| source         | string | **是** | 边的**源节点** id         |
| target         | string | **是** | 边的**目标节点** id       |
| shape          | string | 否       | 边的形态类型，默认值为 `LineEdge` |
| label          | string | 否       | 边的标签文本                     |
| style          | any    | 否       | 节点的样式                   |
| spring         | number  | 否       | 边的弹簧长度，力导时使用     |
| `[key:string]` | any    | 否       | 其余边的属性，用户自行挂载   |

## Layout

布局配置，详见[Layout](/zh/docs/api/layout)文档


## Extend

扩展配置，详见[Extend](/zh/docs/api/extend)文档



## Register

G6 自定义节点/边/行为注册配置，详见[Register](/zh/docs/api/register)文档


## Options

详见 [G6 Options](https://www.yuque.com/antv/g6/graph#VjayE)


## Ref

|   属性 | 类型  | 是否必选 | 说明        |
| ------ | ----- | -------- | ----------- |
| graph  | [Graph](https://www.yuque.com/antv/g6/graph) | 是       | G6 的图实例 |
| apis   | [Apis](#apis)  | 否       | Graphin 提供的 API        |


### Apis


|   属性    | 类型                                                                                                                                              | 说明                                                 |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| search    | (words: string) => Node[ ]                                                                                                                         | 搜索节点，关键词可以为 id，label，或者 property 的值 |
| highlight | (nodeIds: string[ ]) => void                                                                                                                       | 高亮节点                                             |
| clear     | ( ) => void                                                                                                                                        | 重置 Graphin                                         |
| getInfo   | { layouts: { desc:string;icon:string;name:string}[ ], count: { nodes: number;edges:number; } }                                                     | 渲染数据                                             |
| history   | { redo: ( ) => void;undo: ( ) => void;save: ( ) => void;getInfo: ( ) => { currentStep:number;allStep:number;disableRedo:number;disableUndo:number;};} | 操作历史     

