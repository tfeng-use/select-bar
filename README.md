# select-bar
下拉可拖动组件
### 1. 效果
![效果图片](https://github.com/tfeng-use/select-bar/blob/master/images/example.gif)
### 2. 介绍
该组件是基于vue2.0的一个组件，同时引入了Sortable.js，这是一个可以拖动排序的插件，由于该插件的兼容性并不是太好（IE10以下都不兼容），所以在该组件同时增加了手动输入的功能。
### 3. 使用方法
#### 安装
npm i selectbar

#### 引用
在需要使用该组件的地方
```
import selectBar from 'selectbar';

components: {
  selectBar
},
```

#### 在标签中使用
```
<select-bar 
@addSection="addSection" 
@editChapter="editChapter" 
@deleteChapter="deleteChapter"
@editSection="editSection" 
@deleteSection="deleteSection" 
@chapterHandleOrder="chapterHandleOrder"
@sectionHandleOrder="sectionHandleOrder"
@sectionDragOrder="sectionDragOrder"
@chapterDragOrder="chapterDragOrder"
:color="color" 
:accordion="accordion"
:defaultProps="defaultProps" 
:data="data"></select-bar>
```
#### 组件中的参数
* **data**： 传入的数据格式
```
data: {
  parent: [
    {
      name: '第一级',
      orderNum: 1,
      id: '1123412341',
      children: [
        {
          name: '第一节',
          orderNum: 1,
          id: '23412341234'
        },
        {
          name: '第二节',
          orderNum: 2,
          id: '213412341234'
        }
      ]
    },
    {
      name: '第二级',
      orderNum: 2,
      id: '123412341234',
      children: [
        {
          name: '第一节',
          orderNum: 1,
          id: '123412341234'
        },
        {
          name: '第二节',
          orderNum: 2,
          id: '123412341234'
        }
      ]
    }
  ]
},
```
* **defaultProps**：映射输入的参数，
chapter：是父集的key，
children：是子集的key，
orderNum：是对应的排序的key
```
defaultProps: {
  chapter: 'parent',
  children: 'children',
  orderNum: 'orderNum'
}
```
* **color**: 组件的颜色
chapterBackground: 章的背景颜色
sectionBackground：小节的背景颜色
chapterColor：章的文字颜色
sectionColor：小节的文字颜色
```
color: {
  chapterBackground: '#E6ECF0',
  sectionBackground: '#F4F7F9',
  chapterColor: '#656565',
  sectionColor: '#999999'
}
```

* **width** 组件的宽度
```
type: String,
default: '100%'
```

* **accordion** 是否每次只展开一个
```
type: Boolean,
default: false
```

* **sectionMarginTop** 小节的top值
```
type: Number,
default: 10
```

* **chapterMarginTop** 章的top值
```
type: Number,
default: 10
```

* **isSectionSortable** 小节是否可以拖动
```
type: Boolean,
default: true
```

* **isChaterSortable** 章是否可以拖动
```
type: Boolean,
default: true
```

* **isSectionClickToEdit** 是否可以通过点击小节本身触发小节编辑事件
```
type: Boolean,
default: false
```

* **isShowChapterOrder** 是否显示chapter手动排序输入框
```
type: Boolean,
default: true
```

* **isShowSectionOrder** 是否显示section手动排序输入框
```
type: Boolean,
default: true
```

* **maxLength** 可以输入最大长度
```
type: Number,
default: 2
```

#### 组件中的事件
##### * 编辑章
```
// item: 被编辑章对应的data内容
editChapter (item) {},
```

##### * 删除章
```
// item: 被删除章对应的data内容
deleteChapter (item) {},
```

##### * 增加小节
```
// item: 添加小节对应的data内容
addSection (item) {},
```

##### * 编辑小节
```
// item: 编辑小节对应的data内容
editSection (item) {},
```

##### * 删除小节
```
// item: 删除小节对应的data内容
deleteSection (item) {},
```

##### * 章通过手动输入改变排序
```
// order: 手动输入的排序值
// item: 被编辑的章对应的data内容
chapterHandleOrder(order, item) {},
```

##### * 小节通过手动输入改变排序
```
// order: 手动输入的排序值
// item: 被编辑的小节对应的data内容
sectionHandleOrder(order, item) {},
```

##### * 章通过拖动改变排序
```
// order: 为章拖动后新位置的排序
// item: 被拖动的章对应的data内容
chapterDragOrder(order, item) {}
```

##### * 小节通过拖动改变排序
```
// order: 为小节拖动后新位置的排序
// item: 被拖动的小节对应的data内容
sectionDragOrder(order, item) {},
```

