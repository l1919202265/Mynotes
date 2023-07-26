```html
<meta 源标签>
<h1>标题标签</h1>	h1-h6由大变小	逐渐递减
<p>段落标签</p>
<em>字体倾斜</em> <i></i>
<strong>字体加粗</strong> <b>字体加粗</b>
<hr>水平线
<br>换行
<span>相当于小括号，没有任何影响 不独占一行，没有自己的样式</span>
&nbsp;空格
```

```html
href
1、网络图片	只写网络地址
2、本地图片	./后退一步	../后退两步
target目标对象
_blank空的
a标签路径为空的时候页面刷新
<a href="#" target="_blank">超链接</a>
```

```html
<link rel="stylesheet" href="./路径">引入css

src	图片的路径
1、网络图片	只写网络地址
2、本地图片	./后退一步	../后退两步
alt图片加载失败显示
<img src="./本地路径地址或网络地址" alt="图片加载失败的时候显示">
```

```html
快速生成
h1{我是第$个h1}*5
```

```html
无序列表
<ul>容器
    <li>无序列表</li>
    <li>无序列表</li>
</ul>
ul和li 搭配，ul内不可以放div，li内可以
```

```html
有序列表
<ol>容器
    <li>有序列表</li>
</ol>
```

```html
自定义列表
<dl>容器
    <dt>名词1</dt>
    <dd>名词1解释</dd>
    <dd>名词2解释</dd>
</dl>
```

```html
表格
<table>容器
    <th>表头</th>
    <tr>行
        <td>列
        </td>
    </tr>
</table>
```

```html
<input type="text&password&..."> 单标签 表单输入框 不独占一行
<input type="radio" name="">单选框 只能选择一个radio类型的表单 name一样
<input type="checkbox" checked="true&false">复选框 可以选择多个 checked true&false默认勾选 ckecked=""就可以了
<input type="file">上传文件
<input type="submit">提交
<button>按钮</button>
<input type="reset">重置 需要form表单容器包裹
<input type="image" src="./a.jpg">图像形式的按钮 不用！
placeholder提示信息
<label for=""></label>
```

```html
<textarea readonly只读 cols="每行中的字符数" rows="显示的行数">文本内容</textarea>

<div contenteditable="true"></div>

<select>下拉菜单 
    <option>请选择</option>
    <option>第一个选项</option>
    <option>第二个选项</option>
</select>

<form action="./a.html" method="get"></form>

<button hidden>隐藏按钮</button>
<button disabled>无法点击按钮 禁用 </button>
```

```html
盒子模型
padding 内边距 + border边框 + margin外边距
```

