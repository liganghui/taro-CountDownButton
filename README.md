## taro 倒计时按钮组件

封装好的倒计时按钮组件 , 可自定义样式 , 避免重复造轮子 .  

已测试通过 : ```微信小程序```  ```H5```

原则上支持react-native  与 其他小程序 , 但在测试中发现taro(v1.3.17)在其他终端存在无法获取 ref 等情况 .

如有问题 可自行修改源码或提Issues

> ### 演示 
 <img    src='https://github.com/liganghui/taro-CountDownButton/blob/master/doc/demo.gif?raw=true'/>
 
> ### 使用方法

  1. 拷贝```CountDownButton```文件夹到你的```components```目录下 
  2. 引用组件到页面中 , 然后调用即可  
  
  最小化运行示例 :
  ``` javascript
  import CountDownButton from "../../components/DownButton";

  countDownButtonPressed(){
    //调用组件方法 开始按钮倒计时
    this.countDownButton.startCountDown();
  };

<CountDownButton
    onClick={this.countDownButtonPressed.bind(this)}
    ref={ref => {
        this.countDownButton = ref;
    }}
></CountDownButton>

  ```
 参数示例 :

``` javascript

<CountDownButton
    onClick={this.countDownButtonPressed.bind(this)}
    changeWithCount={count => {
        countDown = count;
        return count + "s";  //通过传入函数  调整秒数显示格式
    }}
    beginText='获取验证码' //初始状态按钮title
    endText='重新获取'  //读秒结束后按钮的title
    count={60}  //倒计时时间
    activeStyle='active-count-down-btn' //传入自定义样式名
    ref={ref => {
        this.countDownButton = ref;
    }}
></CountDownButton>


```




  3. 如不满意按钮默认样式 , 你可以打开组件下的```index.css```调整 .

> ### API

参数| 说明 |  类型 | 默认值 | 必填
-|-|-|-|-
id | 按钮的身份标识,同一个页面的按钮是同一个id | Number | 1 | false
beginText | 初始状态按钮title | String | 获取验证码 | false
endText | 读秒结束后按钮的title | String |  重新获取 | false
count | 总的计时数 单位是秒s | Number |  60 | false
onClick | 按下按钮的事件,但是触发倒数(startCountDown)需要你自己来调用 | Function |  Null | <b>true</b>
changeWithCount | 读秒变化的函数,该函数带有一个参数count,表示当前的剩余时间 , 通过传入函数可调整 文本的显示格式 | Function |  x秒(x为当前剩余秒) | false
end | 读秒完毕后的回调,读秒结束触发 | Function |  Null | false
disableStyle | 按钮禁用的时候样式名 | String |  有默认 见index.scss | false
activeStyle | active情况下按钮样式名 | String |  有默认 见index.scss | false
disableTextStyle | 按钮禁用的时候里面文字的样式名 | String |  有默认 见index.scss | false
activeTextStyle | active情况下按钮里面文字的样式名 | String |  有默认 见index.scss | false
frameStyle | 按钮追加的样式名 | String |  Null | false






