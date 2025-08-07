# todo-list
一个简单的vue入门项目

## 静态模板设计
<img width="1192" height="1031" alt="image" src="https://github.com/user-attachments/assets/cd127d48-d897-4594-b1e6-9052b0b8b752" />

* **模板结构如下：**

html

  <body>
    <todo-app> 
      <title></titlle>
      <todo-form>
        <input></input>
        <span class="todo-button"></span>
        <complete>
          <input type="checkbox"/>
          <span class="name"></span>
        </complete>
      </todo-form>
    </todo-app>
  </body>

* 笔记：
* margin是外边框，padding是内边框
* 背景色关键字：background
* display:flex是平排
* justify-content: space-between;分别排在最两边


## 动态设计(**见App.vue**)

* 功能：
* 1.add：输入框todo-input内输入字符，点击todo-button添加到下方item内
* 2.del:点击del时删除所在item
* 3.check：点击checkbox将item样式从item转变为completed

* 功能实现：
* 1.add:
* 1)新建字符串ref变量value，在todo-input内使用v-model="value"双向绑定value变量
* 2）使用@事件监听todo-button，当click todo-button时，执行add函数
* 3）使用list变量存储item，item对象具有isComplete，与text两个属性，add执行时list.value.push({新对象，默认isCoplete:false,text绑定value.value})
* 4)使用v-for="item in list"列表渲染，用{{item.text}}渲染name

* 2.del:
* 1)对del进行事件监听，@click=del(index)
* 2)index从列表渲染中获取,更新列表渲染为v-for="(item,index) in list"，便可获取index参数
* 3)del(index){list.value.splice(index,1)}实现删除item

* 3.check:
* 1)使用v-model="item.isComplete"双向绑定单个item中checkbox与对应isComplete的值(因为都是布尔型，所以点击便可更改isComplete)
* 2）使用:class="[item.isComplete? 'completed' : 'item']" :为动态绑定标志，将类名动态绑定至item.isComplete变量，若为真则类名为completed，若为否则为item




