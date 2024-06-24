# bigH-webtopo


> 基于 vue2+js 实现的 svg 可视化 web 组态编辑器。用户可直接将组件引入进自己系统，只需按要求配置好api，其他工作全部都组态系统完成。

编辑器预览：https://bighhhh.github.io/webtopo-ph-pages/<br>
正式环境预览：https://bighhhh.github.io/webtopo-ph-pages/?key=preview<br>

有问题请提[issue](https://gitee.com/huohuo0408/webtopo/issues)，以便帮助更多有相同问题的人


## 项目优点

### 组态软件核心功能都具备

只需在系统引入当前组件，开发好你自己的api就可直接使用

### 学习成本低

`svg`文件即组件，引入之后无需进行额外配置，编辑器会自适应解析加载组件

### 易拓展

图元支持自定义追加样式属性，也支持自定义图元，自定义图元直接放入你本地项目的指定目录，组件会自动加载自定义图元，如果配置了上传到服务器的api，则支持直接拖拽到画布上传图元（svg、img）

### 易于集成

项目已经编写好了库模式脚本，组件已经发布到[npm](https://www.npmjs.com/package/webtopo-svg-edit)，支持外部传入自定义组件，支持组件事件订阅等
组件的引用支持npm直接安装，在你的项目中只要以vue组件形式引用，并配置好你的api就可以直接使用，简单示例：
```
<template>
  <div id="app">
    <Webtopo :webtopoAPI="webAPI"></Webtopo>
  </div>
</template>

<script>
  import * as webAPI from './api/index.js';
  export default {
    name: 'App',
    data() {
      return {
        webAPI
      };
    }
  };
</script>
```

### 服务

项目长期升级，每次升级和在项目中直接升级到最新版本
## 移动端效果
移动端横屏<br>
![输入图片说明](img/%E7%A7%BB%E5%8A%A8%E7%AB%AF%E6%A8%AA%E5%B1%8F.jpg)
移动端竖屏<br>
![输入图片说明](img/%E7%A7%BB%E5%8A%A8%E7%AB%AF%E7%AB%96%E5%B1%8F.jpg)

## 电脑端效果
![输入图片说明](img/%E7%94%B5%E8%84%91%E7%AB%AF%E6%95%88%E6%9E%9C.png)
## 功能介绍

### 图元库

目前系统集成了上百个图元（部分图元为网络素材，如有侵权请告知），你也可以在系统中追加自己的图元
![](https://gitee.com/huohuo0408/webtopo/raw/main/img/%E5%9B%BE%E5%85%83%E5%BA%93.png)
项目中追加自定义图元：<br>
只需要将你的图元放入项目public/webtopo/custom文件夹中，系统就会自动加载到组态编辑器中<br>
![输入图片说明](img/%E8%87%AA%E5%AE%9A%E4%B9%89%E5%9B%BE%E5%85%83.png)<br>
![输入图片说明](img/%E8%87%AA%E5%AE%9A%E4%B9%89%E5%9B%BE%E5%85%83%E5%B1%95%E7%A4%BA.png)

### 装饰
系统目前集成了上百种装饰供使用（部分图元为网络素材，如有侵权请告知）包括顶部装饰、方块装饰、文本装饰等，也可将你的装饰图元（img、svg）直接拖拽入编辑器使用，编辑器会使用你提供的api将图元上传到你的文件服务器中<br>
![输入图片说明](img/%E8%A3%85%E9%A5%B0.png)

### 图纸管理
待升级~~
### 工具栏
除了包括常用的 对齐、分布、层级、撤销、锁定外目前还集成了一些方便使用的布局，包括水平并列分布、垂直并列布局、田字格布局等<br>
![输入图片说明](img/%E5%B7%A5%E5%85%B7%E6%A0%8F.png)

#### 水平并列布局
![输入图片说明](img/%E6%B0%B4%E5%B9%B3%E5%B9%B6%E5%88%97%E5%B8%83%E5%B1%80.gif)

#### 垂直并列布局
![输入图片说明](img/CPT2404241107-1870x868.gif)
#### 田字格布局（可做数据表格）
![输入图片说明](img/%E7%94%B0%E5%AD%97%E6%A0%BC%E5%B8%83%E5%B1%80.gif)
#### 显示事件：可查看在哪些图元上添加了左键事件、右键事件、鼠标悬浮事件等
![输入图片说明](img/%E6%98%BE%E7%A4%BA%E4%BA%8B%E4%BB%B6.gif)
### 右键菜单
右键菜单中集成了常用的如绘制管道、节点分布、节点对齐、复制粘贴等功能外，还追加了严格框选模式、自由模式、画布拖拽模式等功能<br>
![输入图片说明](img/%E5%8F%B3%E9%94%AE%E8%8F%9C%E5%8D%95.png)

#### 严格框选
启用后必须完全框选住图元才能选中当前图元，不启动则在框选时只要有一部分在框中就选中图元
#### 自由模式（快捷键空格）
编辑器默认是有对齐线、吸附及网格来协助操作者画图的，但在某些情况下这些东西可能会影响到使用者一些比较细微的布局，或者管道拖拽时不想让管道锁定到图元上，这时候就可以启用自由模式，启用后就没有了这些自动化吸附功能
![输入图片说明](img/%E8%87%AA%E7%94%B1%E6%A8%A1%E5%BC%8F.gif)
#### 画布拖拽模式（快捷键alt）
在框选和画布拖拽模式之间切换
### 图元属性
#### 属性
![输入图片说明](img/%E5%9B%BE%E5%85%83%E5%B1%9E%E6%80%A7.png)
#### 图元样式
除了内置图元样式外，还可以追加图元样式，不同类型的图元可追加不同样式属性<br>
![输入图片说明](img/%E5%9B%BE%E5%85%83%E6%A0%B7%E5%BC%8F.png)
![输入图片说明](img/%E8%BF%BD%E5%8A%A0%E6%A0%B7%E5%BC%8F.gif)
### 绑定数据
#### 绑定数据
文本框可直接绑定数据进行展示，并可设置数据的写入位置（当一个图元包括两个文本框时，可选择数据写入到哪个文本框，如第一个文本框填变量名，第二个文本框绑定变量）、保留小数点、放大或缩小倍数（比如采集的数据为1000W可以在此处变为1kW）等
![输入图片说明](img/CPT2404241228-1020x594.gif)
#### 绑定时间
文本框可绑定绑定当前时间，并配置日期时间格式
![输入图片说明](img/%E7%BB%91%E5%AE%9A%E6%97%B6%E9%97%B4.gif)
### 绑定动画
目前系统中已有根据数据修改样式、修改状态、动画效果（闪烁、旋转）、进度效果、位移，一下分别介绍具体绑定方式
#### 绑定样式
在条件框中输入样式生效的boolean结果公式，并启用样式修改，并修改组件的样式，这等于给组件生成了一个新的快照，运行时当公式成立后就会为组件应用当前快照<br>
![输入图片说明](img/%E7%BB%91%E5%AE%9A%E6%A0%B7%E5%BC%8F.gif)
#### 绑定动画
在条件框中输入样式生效的boolean结果公式，并启用动画，选择动画效果，当公式条件成立时就会触发动画，可叠加多个动画，但动画之间可能会有冲突，请根据预览效果选择动画<br>
![输入图片说明](img/%E9%97%AA%E7%83%81.gif)
![输入图片说明](img/%E6%97%8B%E8%BD%AC.gif)
#### 进度效果
公式不在是boolean类型，可直接选择点位后通过加减乘除计算出百分比（小数），结果范围为0~1之间，所有组件都可绑定进度效果，并且内置组件还可以选择组件的哪些部分使用进度效果，并可选择进度效果的方向（上下左右）
![输入图片说明](img/%E8%BF%9B%E5%BA%A6%20(1).gif)
#### 位移动画
公式为采集到的实际位移距离，并录入实际最大距离，组件根据实际位移比例反映到图纸初始位置和目标位置中，也就是显示中如果最大距离100米，采集到移动了50米，则组态图中就行驶到50%的位置
![输入图片说明](img/%E4%BD%8D%E7%A7%BB.gif)
#### 组合动画
可以将多个效果组合展示，如下面的旋转加位移效果
![输入图片说明](img/%E7%BB%84%E5%90%88%E5%8A%A8%E7%94%BB.gif)
### 事件
所有图元都可以绑定鼠标的左键事件、右键事件、鼠标悬浮事件，设置项包括<br>
 **事件类型** ：左键、右键、悬浮<br>
 **行为类型** ：设置/显示数据、内部图纸钻取（图纸之间互相跳转）、外部链接（如设置为你自己网站的地址）<br>
 **展现形式** ：悬浮框、弹框<br>
 **菜单名称** ：只有右键有菜单名称选项，当同一组件设置多个右键事件时进行区分<br>
 **类型** ：只有行为类型选择“设置/显示数据”是才有，选项包括设置（向后台发送数据）、显示（显示配置的点位数据）<br>
 **显示类型** ：类型设置为“显示”是有的选项，包括文本（静态内容）、变量（采集点发送什么数据就显示什么数据）、状态（将后台数据映射为文本，比如 0 映射为 关闭，1 映射为 开启）<br>
当为设置数据时下面还有一个类型，选项包括按钮、整数、小数、文本，这个是方便用户设置数据用的，如果是按钮则悬浮框中展示的为按钮，用户点击按钮就向后台发送当前按钮预设的数据，如果选择为整数、小数、文本则悬浮框中显示的是输入框，需要用户输入数据后发送到后台，整数、小数、文本是这个输入框的校验类型
![输入图片说明](img/%E8%AE%BE%E7%BD%AE%E4%BA%8B%E4%BB%B6.gif)
![输入图片说明](img/%E4%BD%BF%E7%94%A8%E4%BA%8B%E4%BB%B6.gif)
![输入图片说明](img/%E4%BA%8B%E4%BB%B61.gif)
![输入图片说明](img/%E4%BA%8B%E4%BB%B62.gif)
### 告警
新增加越限告警配置及展示，本组件告警展示以滚动横幅、声音及折叠面板方式自动展示，不需额外拖拽告警列表组件，节省了页面空间，最大限度利用页面篇幅<br>
可一次配置多个点位的上下限，并配置告警时是否播放声音、告警级别等操作<br>
在用户处展示时，会页面底部滚动提示告警信息，并可点击底部按钮展开告警详细信息列表，并单独关闭每条告警的声音和滚动效果<br>
![输入图片说明](img/%E8%B6%8A%E9%99%90%E5%91%8A%E8%AD%A6%E9%85%8D%E7%BD%AE.gif)
![输入图片说明](img/%E8%B6%8A%E9%99%90%E5%91%8A%E8%AD%A6%E5%B1%95%E7%A4%BA.gif)

### 图表
支持拖拽图表、绑定数据，并且内置了10几种颜色方案，也支持自定义颜色方案，可在线配置标题、图例、提示、外间距、横轴、纵轴信息
#### 折线图
![输入图片说明](img/%E6%8A%98%E7%BA%BF%E5%9B%BE.gif)
### 绘制管道、电线、线条
![输入图片说明](img/%E7%BB%98%E5%88%B6%E7%AE%A1%E9%81%93.gif)
![输入图片说明](img/%E7%AE%A1%E9%81%93%E8%B7%AF%E7%94%B1.gif)
### 快速拖拽图元并关联管道
![输入图片说明](img/%E5%85%B3%E8%81%94%E7%AE%A1%E9%81%931.gif)
![输入图片说明](img/%E5%85%B3%E8%81%94%E7%AE%A1%E9%81%932.gif)

### 历史数据
用户除了可以看预设的实时数据和动画外，还可以随时查看图元绑定了哪些点位，和绑定的点位的历史曲线和数据详情，这个为组件自带的功能，不需要配置，只要你在画图是为某个图元使用了动画、事件、数据绑定等等并且使用到了点位，则用户在图元上右键都可以看到当前图元用到的所有点位的历史记录，方便用户在发现问题后通过历史记录及时排查问题
![输入图片说明](img/%E5%8E%86%E5%8F%B2%E6%95%B0%E6%8D%AE.gif)

### 快捷键
![输入图片说明](img/%E5%BF%AB%E6%8D%B7%E9%94%AE.png)
## 快速使用
### 编辑器接入
通过npm安装组件到自己系统中后，新建一个页面引入组件，并传入api后就可使用组态编辑器，后边会讲解详细api内容
```
<template>
  <div id="app">
    <Webtopo :webtopoAPI="webAPI"></Webtopo>
  </div>
</template>

<script>
  import * as webAPI from './api/index.js';
  export default {
    name: 'App',
    data() {
      return {
        webAPI
      };
    }
  };
</script>
```
webtopoAPI接口列表<br>
```
webtopoAPI: {
        getCaptcha: ({mps，startTime，endTime}) => {},//查询历史数据，历史图展示时使用
        getPoints: ({ page, limit }) => {},//查询你系统中所有点位信息，绑定点位时使用
        getAttrs: ({mpId, consId,readAndWriteVar}) => {},//根据点位（表计）查询遥信、遥测列表
        saveOrUpdate: ({cells, points, graph}) => {},//保存图纸信息，后台你是存到数据库还是存入文件系统都无所谓，只要用户展示是能查到就好
        getJSONById: (id) => {},//图纸id，这个地方需要后台保存好后生成一个唯一id，访问preview组件时将id传给组件，组件就会调用此方法获取图纸信息
        getImages: () => {},//获取拖拽到编辑器上传的所有图片或图元
        uploadFile: (file) => {},//拖拽到编辑器上传图片或图元的接口
        listNotPage: ({consId，notSearchId}) => {},//获取图纸列表，配置图纸跳转功能时，需要提供当前已有图纸让配置人员选择
        getMpAndMstypeNames: (mpAttrs) => {},//获取点位的名称，用户每次打开组态系统时组件都会去后台查一下点位名称，如果业务变动用户在你系统修改了点位名，渲染给用户时也会展示最新名称
        setData: (id,mpId,attrId,value) => {}//当用户在组态系统中向表计发送数据时，通过此接口发送给后台
      }
```
### 正式环境展示
 **图纸渲染：** 画好图纸后，只需要将编辑器生成的json信息存入后台数据库或文件管理系统，并根据要求写好接口，将图纸信息返回给渲染组件即可<br>
 **数据推送：** 数据推送和点位注册不限制技术，可以使用socket也可以使用轮训等技术，下面是使用socket时的教程，可以根据以下代码改成轮训方式，只需要记住两个组件方法<br>
 ```
    this.$refs.preview.getPointList()//获取图纸所有点位信息
    this.$refs.preview.changeData(data);//将获取到的数据发送给组件
```
```
<template>
  <preview
    :svgId="id"
    :webtopoAPI="webtopoAPI"
    :isConnect="isConnect"
    ref="preview"
    @register="register"
  ></preview>
</template>

<script>
  import * as webtopoAPI from '@/api/webtopo/index';
  import { getToken } from '@/utils/token-util';
  export default {
    data() {
      return {
        id: null,
        webtopoAPI,
        isConnect: false
      };
    }
    created() {
      this.id = this.$route.query.id;
      this.$socket.io.uri = `${location.protocol}//${location.hostname}:8031`;
      this.$socket.connect();
    },
    methods: {
      //点位注册，组件会将图纸用到的所有点位发送给register方法，如果使用socket需要向后台注册点位信息，方便数据推送
      register(pointList) {
        this.$socket.emit('register', {
          code: getToken(),
          points: pointList
        });
      }
    },
    sockets: {
     //重连时重新注册下点位信息
      connect: function () {
        this.isConnect = true;
        this.$socket.emit('register', {
          code: getToken(),
          points: this.$refs.preview.getPointList()
        });
      },
     //断开连接时通知组件，组件会提示用户后台断开连接，防止用户错过重要信息
      disconnect: function () {
        this.isConnect = false;
        console.log('断开连接');
      },
      //出错时提示用户
      autoError: function (msg) {
        this.$message.error(msg);
      },
      //重连时重新注册下点位信息
      reconnect: function () {
        this.isConnect = true;
        this.$socket.emit('register', {
          code: getToken(),
          points: this.$refs.preview.getPointList()
        });
        console.log('重新连接');
      },
      //数据接收函数，接收到数据变化发送给组件
      data(data) {
        this.$refs.preview.changeData(data);
      }
    },
    //关闭页面时断开连接
    beforeDestroy() {
      // 关闭 Socket
      this.sockets.disconnect();
    }
  };
</script>
```
### 权限标识
当用户需要控制权限时可以在保存时配置权限标识，并将权限标识写入shiro等框架的请求访问标识中，或者后台自己写请求过滤器，识别客户是否有图纸的权限标识，来过滤用户请求<br>
![输入图片说明](img/%E6%9D%83%E9%99%90%E6%A0%87%E8%AF%86.png)
## 联系作者
有问题可加作者qq：623037142，备注组态系统
