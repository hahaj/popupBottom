
uniapp底部弹窗组件,带过渡动画，scrollview滚动不穿透，弹窗自动高度，超过最大高度自动滚动条，触底监听


Props

| 参数名 |类型  |默认值  | 说明
| --- | --- | --- | --- |
| visible | Boolean  | false |组件显示标识,支持sync修饰符  |
| title | String |  |标题，不写隐藏标题栏  |
| radius | String, Number |0  |顶部圆角，支持百分比，数字，数字带单位，例如10%或30或'30px'，默认单位rpx  |
|maxHeight  | String, Number |  '75%'| 弹窗最大高度,支持百分比，数字，数字带单位，超过此高度将出现滚动条 |
| animaTime | Number | 0.2 |弹窗动画时间，单位s，0关闭动画  |
| bottom | String, Number | 0 |控件与页面底部距离，默认单位rpx  |
| zindex | String, Number |1000  |内容区域显示层级 |
| maskZindex | String, Number | 999 |遮罩层显示层级  |
| always | Boolean | false |是否响应式显示内容区域高度，开启每次弹出将重新计算内容区域高度，适用于内容区域动态数据填充  |


Event

| 事件名 |作用  |
| --- | --- |
| @close |关闭弹窗触发  
| @open | 打开弹窗触发 |
| @reachBottom | 内部滚动触底触发 |




Slot
匿名插槽


手动刷新内容区域高度：
 this.$refs['xxxx'].setContViewHeight()



示例

vue2:
```
<popupBottom ref="popup"  :visible.sync="popupVisible" title="标题"  radius="40"  maxHeight="900"   @close="onClose" @reachBottom="onPopupReachBottom">
	<view class="cot">内容</view>
</popupBottom>
```

```javascript
   this.popupVisible=true;
   this.$refs['popup'].setContViewHeight();//手动刷新内容区域高度
```

vue3:

```
<popupBottom  ref="popup"  v-model:visible="popupVisible" title="标题"  radius="40"  maxHeight="900"  @close="onClose" @reachBottom="onPopupReachBottom">
	<view class="cot">内容</view>
</popupBottom>
```

```javascript
     const popupVisible=ref(false);
     const popup=ref();
     popupVisible.value=true;
     popup.value.setContViewHeight();//手动刷新内容区域高度
```

app端滚动条穿透问题请在页面级别做限制，弹窗时候隐藏页面滚动
