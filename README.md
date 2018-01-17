* * *
### 1. 项目结构
```
[vue-cli webpack 配置说明](https://github.com/WeideMo/vuecli-webpack-configs)

├── build // vue-cli 配置文件
├── config  // vue-cli 配置文件 
├── node_modules // 模块依赖
├── src
│   ├── App.vue  // 入口组件
│   ├── main.js  // 入口文件配置
│   ├── permission.js  // 全局权限控制
│   ├── api  // api接口统一管理
│   │   ├── login.js
│   │   ├── selectOption.js
│   │   ├── simple.js
│   │   └── table.js
│   │   └── .......
│   ├── assets // 图片静态资源
│   │   ├── 401_images
│   │   └── 404_images
│   ├── components // 业务组件
│   ├── filters // 数据转换函数
│   ├── icons // 图标icons
│   ├── mock // mock模拟数据
│   ├── permission // 用户权限控制
│   ├── router // 前端路由管理
│   ├── store // 数据状态管理
│   ├── styles // sass 样式
│   │   ├── modules // 分模块管理样式
│   │   ├── commen.scss  // 通用样式统一管理
│   │   ├── element-ui.scss  // element-ui 样式覆盖
│   │   ├── index.scss  // scss 入口
│   │   ├── mixin.scss  // 菜单
│   │   ├── transition.scss  // 全局动画
│   │   ├── variables.scss  // 变量声明
│   ├── utils // 通用工具函数
│   ├── views // 视图模块
│   │   ├── login // 登录
│   │   ├── tree  // 菜单
│   │   └── ....
├── static // 项目答疑与总结 
├── .babelrc // ES6转义配置
├── .editorconfig // 项目缩进配置
├── .eslintignore // eslint忽略目录
├── .eslintrc.js // eslint代码规范 
├── .gitignore // git忽略目录
├── .postcssrc.js // postcss配置
├── index.html // 入口html
├── README.md // 项目说明
├── package.json // 项目依赖表
```

* * *

### 2. 代码检查
* base on [ESlint](https://eslint.org/): recommended 标准添加了部分自定义规范
* 根目录下 eslint_tanslate.json 为配置说明
* 更改检查配置，应共同商议后决定 。


### 3. 命名规范

####`强制` 文档目录全部以小驼峰命名 

### JavaScript 命名
#### `强制` 常量使用大写字符, 下划线连接
```javascript
const SECONDS_IN_A_MINUTE = 60;
```

#### `强制` 标准变量: 小驼峰
```javascript
var myCount = 1;
```

#### `强制` 构造函数: 驼峰且大写第一个字母
```javascript
function Point(x, y) {
    this.x = x;
    this.y = y;
}
```

#### `建议` 私有方法: 驼峰且加`_`前缀
```javascript
function MyClass() {
    var _privateNum;
    this.getNum = function() {
        return _privateNum;
    };
}

// 虽然不建议这么写一个对象(建议用闭包来写)
// 但如果真这么写了, 请把意图上不想暴露的变量, 用_开头
var myCounter = {
    _count: 1,
    get: function() {
        return this._count;
    }
};
```

#### `建议` 方法, 命名时 动词 + 名词 如 `filterNodes`
```javascript
var isDone = true;
```

#### `建议` 对布尔型的变量, 命名时加`is`,`has`,`can`前缀
```javascript
function filterNodes() {}
// 常见动词 
```

### 4. 代码调试与异常
#### 4.1 开发时断点调试
vue-cli 采用的是webpack进行构建的，所以如果要进行断点调试的话，可设置devtool为source-map。
具体做法是：到/build目录下的webpack.dev.config.js 搜索devtool，将其设置为source-map
![source-map](https://ws3.sinaimg.cn/large/006tNc79gy1fn4dwa09ulj30wl0ekdkm.jpg)

完成配置后，跑node服务npm run dev ，然后就可以在chrome浏览器中进入开发者模式。搜索（ctrl + p）具体的vue组件进行断点调试。调试效果如下：
![开发时调试](https://ws4.sinaimg.cn/large/006tNc79gy1fn4e30czo3j31bk172wrm.jpg)

#### 4.2 vue状态管理调试，vue-devtool
chrome应用商店 [vue-devtool]([https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)


![vue-devtools](https://ws4.sinaimg.cn/large/006tNc79gy1fn4ec8n38ej31kw0roafs.jpg)

#### 4.3 线上调试webpack打包后代码


