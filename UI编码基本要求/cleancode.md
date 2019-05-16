<link href="markdown.css" rel="stylesheet"></link>

# ManageOne ServiceCenter UI编码基本要求

## 一、遵守JS编码规范

<table class="table table-bordered table-striped table-condensed">
    <tr>
        <th>Classification<br>规范分类</th>
        <th>S.No<br>序号</th>
        <th>Checklist<br>检查项</th>
        <th>Remarks<br>说明</th>
    </tr>
    <tr>
        <td rowspan="6">第1部分：排版规范</td>
        <td>1</td>
        <td>代码使用4 个空格来进行缩进，避免使用TAB。</td>
        <td>换行缩进 8 个空格可以和代码段的缩进 4 个空格区分开，以增强代码的可阅读性。</td>
    </tr>
    <tr>
        <td>2</td>
        <td>语句应该以分号结束。文件内容以分号";"结尾，避免压缩时出错。</td>
        <td>
    <pre><code class="javascript">
    var name = "angular";
    var foo = function() {
    return true;
    };
    </code></pre>
        </td>
    </tr>
    <tr>
        <td>3</td>
        <td>关键字独占，if, for, do, while, switch, case, default 等语句自占一行，且这些关键字随后的执行语句无论多少都要加括号{}。</td>
        <td></td>
    </tr>
    <tr>
        <td>4</td>
        <td>
            空格应该用于如下情况：<br>
            1. 关键字后面跟左括号“(”之间应该用一个空格隔开。如if、for、while等<br>
            2. 函数名和的左括号“(”之间不要有空格；但匿名函数的function和左括号“(”之间要有空格 <br>
            3. 所有的二元操作符，除了“.”、“(”和“[”之外，都应该使用一个空格来和操作数隔开。如 a + b、a == b等 <br>
            4. 一元操作符和操作数之间不应该使用空格隔开，除了操作符是一个单词时，如typeof <br>
            5. for语句控制部分的每个分号“;”应该在后面跟一个空格 <br>
            6. 每个逗号“,”后面应该跟一个空格
        </td>
        <td>
            <pre><code class="javascript">
typeof(1);
if (current_time >= MAX_TIME_VALUE) 
a = b + c;
a *= 2;
a = b ^ 2;
flag = !isEmpty;
i++;
p.id = pid;
int a, b, c;
if (a >= b &amp;&amp; c > d)
            </code></pre>
        </td>
    </tr>
    <tr>
        <td>5</td>
        <td>简单语句：<br>每一行最多有一个语句，在每个语句末尾以分号结束。</td>
        <td>
            <pre><code class="javascript">
示例：
int a = 2;
对象字面量{firstname:'jone',lastname:'doe'}; 
数组字面量[1,3,4,5,6]; 
方法字面量function(){return true}; 
            </code></pre>
        </td>
    </tr>
    <tr>
        <td>6</td>
        <td>
            复合语句 ：<br>
            复合语句是包含一个用“{}”(大括号)包围语句列表的的语句。 <br>
            1. 包围的语句应该再缩进4个空格。 <br>
            2. “{”(左大括号)不新起一行。 <br>
            3. “}”(右大括号)新起一行并且和相匹配的“{”所在那行对齐。<br>
            4. 当语句是控制结构的一部分时，所有语句都应该用括号包围，即使是单行语句。
        </td>
        <td>
            <pre><code class="javascript">
function fn() {
}

if (expression) {
} 
            </code></pre>
        </td>
    </tr>
    <tr>
        <td rowspan="5">第2部分：注释规范</td>
        <td>7</td>
        <td>使用"//"作为代码行注释，"/* .... */"作为对整个代码段的注释或较正式的声明中，如方法参数、功能、文件功能等的描述中。</td>
        <td></td>
    </tr>
    <tr>
        <td>8</td>
        <td>
            文件注释：<br>
            /*<br>
            <span style="color: blue;"> * 文件名：[文件名]</span><br>
            <span style="color: blue;"> * 版权：〈版权〉</span><br>
             * 描述：〈描述〉<br>
             * 修改时间：YYYY-MM-DD    编写时间<br>
             */
        </td>
        <td>蓝色可选</td>
    </tr>
    <tr>
        <td>9</td>
        <td>
            /*<br>
             * 〈一句话功能简述〉<br>
             * 〈功能详细描述〉<br>
             * @version   [版本号, YYYY-MM-DD]<br>
             <span style="color: blue;"> * @see         [相关类/方法]</span><br>
             <span style="color: blue;"> * @since      [产品/模块版本]</span><br>
             <span style="color: blue;"> * @deprecated （表示不建议使用）</span><br>
             */
        </td>
        <td>蓝色可选</td>
    </tr>
    <tr>
        <td>10</td>
        <td>
            类属性注释：<br>
            /**<br>
             * 注释内容<br>
             */<br>
            var privateVariable;<br>
        </td>
        <td></td>
    </tr>
    <tr>
        <td>11</td>
        <td>
            类方法的注释：<br>
            /**<br>
             * 〈一句话功能简述〉<br>
             * 〈功能详细描述〉<br>
             * @param [参数1]     [参数1说明]<br>
             * @param [参数2]     [参数2说明]<br>
             * @return  [返回类型说明]<br>
             <span style="color: blue;"> * @exception/throws [违例类型] [违例说明]</span><br>
             <span style="color: blue;"> * @see          [类、类#方法、类#成员]</span><br>
             <span style="color: blue;"> * @since      [产品/模块版本]</span><br>
             <span style="color: blue;"> * @deprecated</span><br>
             */
        </td>
        <td>蓝色可选</td>
    </tr>
    <tr>
        <td rowspan="3">第3部分：命名规范</td>
        <td>12</td>
        <td>类、方法、变量、参数等都按驼峰命名规则进行命名。类使用首字母大写，构造器的名称首字母大写。</td>
        <td>
            functionNamesLikeThis, <br>
            variableNamesLikeThis,  <br>
            ClassNamesLikeThis,     <br>
            EnumNamesLikeThis, <br>
            methodNamesLikeThis, <br>
            foo.namespaceNamesLikeThis.bar<br>
        </td>
    </tr>
    <tr>
        <td>13</td>
        <td>常量名: 使用全大写的英文描述，英文单词之间用下划线分隔开。</td>
        <td>
            var MAX_VALUE = 1000;
        </td>
    </tr>
    <tr>
        <td>14</td>
        <td>文件名: 驼峰命名法，首字母小写。</td>
        <td>
            filenameLikeThis.js
        </td>
    </tr>
    <tr>
        <td rowspan="4">第4部分：编码规范</td>
        <td>15</td>
        <td>避免使用魔鬼数字。</td>
        <td></td>
    </tr>
    <tr>
        <td>16</td>
        <td>所有的变量应该在使用前进行声明。方法应该在调用前进行声明，内部方法应该在 var 声明内部变量的语句之后声明。</td>
        <td>
            <pre><code class="javascript">
var innerA = 1; 
function outF() 
{ 
    var innerA = 2; 
    function _inF() 
    { 
        alert("valueA="+innerA); 
    } 
   
    _inF(); 
} 
outF();  //output: valueA=2 
_inF();  //error: innerF is not defined           
            </code></pre>
        </td>
    </tr>
    <tr>
        <td>17</td>
        <td>使用===和!==操作符会更好，==和!=操作符会做类型强制转换。</td>
        <td>
            <pre><code class="javascript">
var valueA = "1"; 
var valueB = 1; 
if (valueA == valueB) 
{ 
  alert("Equal"); 
} 
else 
{ 
  alert("Not equal") 
} 
//output: "Equal"
if (valueA === valueB) 
{ 
  alert("Equal"); 
} 
else 
{ 
  alert("Not equal") 
} 
//output: "Not equal"     
            </code></pre>
        </td>
    </tr>
    <tr>
        <td>18</td>
        <td>JavaScript代码不应该嵌入在HTML文件里。</td>
        <td>HTML里的JavaScript代码大大增加了页面的大小，并且很难通过缓存和压缩来缓解。 </td>
    </tr>
    <tr>
        <td rowspan="8">第5部分：angularjs规范</td>
        <td>19</td>
        <td>angularJS编写module时推荐的风格</td>
        <td>
            <pre><code class="javascript">
define(["dependency, controller, service"], 
function(dependency, controller, service) {
    "use strict";

    var newModule = angular.module("moduleName", ["dependency-module"]);
    newModule.controller("controller", controller);
    newModule.service("service", service);

    return newModule;
});
            </code></pre>
        </td>
    </tr>
    <tr>
        <td>20</td>
        <td>angularJS编写controller时推荐的风格</td>
        <td>
            <pre><code class="javascript">
define(["dependency"], function(dependency) {
    "use strict";

    var newControl = ["$scope","dependency", function($scope, dependency) {
        //attribute

        //method
    }];

    var newModule = angular.module("moduleName", ["dependency-module"]);
    newModule.controller("controllName", newControl);
    return newModule;
});
//or
define(["existModule"], function(existModule) {
    "use strict";

    var newControl = ["$scope","dependency", function($scope, dependency) {
        //attributes
        this.attrs  = null;

        //method
        this.fn = null;
    }];

    return newControl;
});
            </code></pre>
        </td>
    </tr>
    <tr>
        <td>21</td>
        <td>angularJS编写service时推荐的风格</td>
        <td>
            <pre><code class="javascript">
define(["dependency"], function(dependency) {
    "use strict";

    var newService = ["dependency", function(dependency) {
        //attributes
        this.attrs  = null;

        //method
        this.fn = null;
    }];

    var newModule = angular.module("moduleName", ["dependency-module"]);
    newModule.service("serviceName", newService);
    return newModule;
});
//or
define(["dependency"], function(dependency) {
    "use strict";

    var newService = ["dependency", function(dependency) {
        //attributes
        this.attrs  = null;

        //method
        this.fn = null;
    }];

    return newService;
});
            </code></pre>
        </td>
    </tr>
    <tr>
        <td>22</td>
        <td>angularJS编写configure时推荐的风格</td>
        <td>
            <pre><code class="javascript">
define(["dependency"], function(dependency) {
    "use strict";

    var config = ["$stateProvider", "$urlRouterProvider", 
    function ($stateProvider, $urlRouterProvider) {
        //config url router

        //config state router
    }];

    var newModule = angular.module("moduleName", ["dependency-module"]);
    newModule.config(config);
    return newModule;
});
//or
define(["existModule"], function(existModule) {
    "use strict";

    var config = ["$stateProvider", "$urlRouterProvider", 
    function ($stateProvider, $urlRouterProvider) {
        //config url router

        //config state router
    }];

    return config;
});
            </code></pre>
        </td>
    </tr>
    <tr>
        <td>23</td>
        <td>推荐使用标签方式定义tiny控件</td>
        <td>
            <pre><code class="html">
&lt;div>
    &lt;tiny-table id="data.id" data="model.data" 
        columns="model.columns" >&lt;/tiny-table>
&lt;/div>
            </code></pre>
        </td>
    </tr>
    <tr>
        <td>24</td>
        <td>模块化编程，每个文件不超过800L</td>
        <td>View和Controller、Service分离，各个页面的Controller分离。</td>
    </tr>
    <tr>
        <td>25</td>
        <td>共享数据通过service实现，不要定义在$rootScope里面</td>
        <td></td>
    </tr>
    <tr>
        <td>26</td>
        <td>各服务内部的ctroller,service,router都以服务名开头，避免命名空间污染。</td>
        <td>如alarmList, alarmCtrl, alarmService</td>
    </tr>
</table>

## 二、无JSHint错误
    后续为保证客户端性能，所有js文件都有可能经过压缩，因此所有合入的js文件都必须保证压缩成功，保证JSHint检测无错误提示。
* Webstorm JSHint检测必须开启，请戳[这里](http://rnd-github.huawei.com/t00189093/web-xss/blob/master/chapter1-webstorm.md "JSHint配置")
* SHint修复参考文档，请戳[这里](http://jshint.com/docs/options/ "JSHint配置")
* Yuicompressor 压缩检测，请戳[这里](http://3ms.huawei.com/hi/group/2027323/blog_1486517.html?mapId=2069013)（<span style="color: red;">尤其注意JS关键字的使用，参考[这里](http://3ms.huawei.com/hi/group/2027323/blog_1486813.html?mapId=2069339&for_statistic_from=mail_share)</span>）


## 三、安全编码要求
    安全编码是基本的要求，UI编码主要有但不限于以下几个方面：
1. 所有Html、JavaScript、CSS文件中的文件描述信息中不能含有姓名和工号等敏感信息
2. 所有js语句中不能含有console控制台打印以及相关调试语句
3. Html、JavaScript、CSS文件中功能性注释代码必须删除
4. 防XSS攻击，基本排查项，请戳[这里](http://rnd-github.huawei.com/t00189093/web-xss/blob/master/chapter3-DOMBasedXSS.md)


## 四、遵守框架架构
1. 满足基本的angularJS编码规范，参考第一部分angularjs规范
2. 所有js语句中不能含有console控制台打印以及相关调试语句
3. Html、JavaScript、CSS文件中功能性注释代码必须删除
4. 防XSS攻击，基本排查项，请戳[这里](http://rnd-github.huawei.com/t00189093/web-xss/blob/master/chapter3-DOMBasedXSS.md)


## 五、满足高性能编码要求

### 1、scope管理
1. 排查with，try-catch, eval
2. 排查closures闭包
    ```javascript
        //Closure implementation
        function Pixel(x, y) {
            this.x = x;
            this.y = y;
            this.getX = function () {
                return this.x;
            };
            this.getY = function () {
                return this.y;
            }
        }

        //Prototype implementation
        function PixelP(x, y) {
            this.x = x;
            this.y = y;
        }
        PixelP.prototype.getX = function () {
            return this.x;
        };
        PixelP.prototype.getY = function () {
            retrun this.y;
        };
    ```
3. 排查全局变量，尽量采用局部变量

### 2、数据访问
js变量访问速度从高到低：literal->Local Variable->Array Item->Object Property

```javascript
    //literal
    var name = "Nicholas";
    //variable
    var name1 = name;
    //array item
    var name2 = items[0];
    //object property
    var name3 = object.name;
```
1. 排查一个对象属性被多次访问时，应该提取成一个局部变量
2. 排查当数组Item 被多次访问时，应该提取成一个局部变量
3. 排查搜索的深度

### 3、循环
1. 排查循环次数
2. 排查不要使用括号+引号
```javascript
    obj["proper1"]
    //修改为
    obj.proper1
```
3. 排查length属性，设置成一个局部变量
```javascript
    //length属性
    for (var i = 0; i < arr.length; i++) {
        console.log(arr[i]);
    }
    //修改为
    var len = arr.length;
    for (var i = 0; i < len; i++) {
        console.log(arr[i]);
    }
```

### 4、DOM
1. 提取选择器作为局部变量
```javascript
    $scope.params = $("#rebuildNetworkWindow").widget().option("params");
    $scope.bindedNetworks = $("#rebuildNetworkWindow").widget().option("bindedNetworks");
    $scope.modifyNetwork = $("#rebuildNetworkWindow").widget().option("modifyNetwork");
    $scope.mode = $("#rebuildNetworkWindow").widget().option("mode");

    //修改后
    var widget = $("#rebuildNetworkWindow").widget();
    $scope.params = widget.option("params");
    $scope.bindedNetworks = widget.option("bindedNetworks");
    $scope.modifyNetwork = widget.widget().option("modifyNetwork");
    $scope.mode = widget.option("mode");
```

