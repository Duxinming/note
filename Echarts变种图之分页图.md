# 商业转载请联系作者获得授权，非商业转载请注明出处。

# For commercial use, please contact the author for authorization. For non-commercial use, please indicate the source.

# 协议(License)：署名-非商业性使用-相同方式共享 4.0 国际 (CC BY-NC-SA 4.0)

# 作者(Author)：AnLing

# 链接(URL)：https://anling.site/

# 来源(Source)：AnLing Blog

需求
​ 当类目轴足够的多时，往往不得不牺牲单个条目数据在统计图上渲染的大小。

也就是说，每一条目在统计图上的大小可能会非常小，就像下面这样

当然，我们可以使用和图中相同的方式来处理，使用 dataZoom 区域缩放系列的属性，亦或者是使用 brush 区域选择来处理。

但是对于一些客户而言，他们可能并不喜欢这两类解决方案，他们可能更希望每一个条目在 X 轴上都有对应的类目名，而非这样需要滑动或者拖动才能完全显示。当然还有一些客户也可能单纯的不习惯使用区域缩放来满足大量类目的显示。

实现
修改时序图主要修改它的 X 轴，将其修改为类目轴，以及它的控制器显示

下面是一个简单例子

效果图
![效果图1](https://pic-1255740060.cos.ap-shanghai.myqcloud.com/MarkDown/img/20211208201407.png)
![效果图2](https://pic-1255740060.cos.ap-shanghai.myqcloud.com/MarkDown/img/20211208201315.png)

import React, { Component } from 'react';
import ReactEcharts from 'echarts-for-react';

export default class PlanEchart extends Component {
getprops() {
return {
"baseOption": {
"timeline": {
"axisType": "category",
"data": [
"第 1 页",
"第 2 页"
],
"controlStyle": {
"itemSize": 24,
"showPlayBtn": false
},
"bottom": 0,
"padding": [
5,
5,
0,
5
]
}
},
"options": [
{
"tooltip": {
"trigger": "axis"
},
"yAxis": [
{
"type": "value",
}
],
"legend": {
"data": [
null
],
"bottom": 0,
"left": "center",
"top": 30
},
"xAxis": [
{
"data": [
"仪表",
"其他",
"动设备",
"土建",
"安全",
"工业设计",
"工艺",
"机械设计制造及自动化"
],
"axisLabel": {
"rotate": -45
}
}
],
"series": [
{
"data": [
{
"name": "仪表",
"value": 10,
"key": 12,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "其他",
"value": 1,
"key": 14,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "动设备",
"value": 20,
"key": 9,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "土建",
"value": 11,
"key": 13,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "安全",
"value": 20,
"key": 8,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "工业设计",
"value": 30,
"key": 4,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "工艺",
"value": 10,
"key": 7,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "机械设计制造及自动化",
"value": 30,
"key": 2,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
}
],
"type": "bar",
"name": null
}
],
"title": {
"text": "计划专业维度柱状图",
"x": "center"
},
"grid": {
"bottom": "25%"
}
},
{
"tooltip": {
"trigger": "axis"
},
"yAxis": [
{
"type": "value",
}
],
"legend": {
"data": [
null
],
"bottom": 0,
"left": "center",
"top": 30
},
"xAxis": [
{
"data": [
"材料成型及控制工程",
"特种设备",
"电气",
"设备",
"设备专业测试 01",
"过程装备及控制工程",
"静设备",
"项目"
],
"axisLabel": {
"rotate": -45
}
}
],
"series": [
{
"data": [
{
"name": "材料成型及控制工程",
"value": 10,
"key": 3,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "特种设备",
"value": 20,
"key": 15,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "电气",
"value": 30,
"key": 11,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "设备",
"value": 10,
"key": 6,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "设备专业测试 01",
"value": 0,
"key": 1,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "过程装备及控制工程",
"value": 10,
"key": 5,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "静设备",
"value": 4,
"key": 10,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
},
{
"name": "项目",
"value": 7,
"key": 16,
"categoryMeaning": null,
"categoryValue": null,
"sort": null
}
],
"type": "bar",
"name": null
}
],
"title": {
"text": "计划专业维度柱状图",
"x": "center"
},
"grid": {
"bottom": "25%"
}
}
]
}
}
render() {
return (
<ReactEcharts
notMerge
style={{ height: 400, width: 300 }}
option={
this.getprops()
}
/>
)
}
}
