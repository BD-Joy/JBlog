# MVVM 回顾
## 1、什么是MVVM？
> From *百度百科*  
> MVVM是Model-View-ViewModel的简写。微软的WPF带来了新的技术体验，如Silverlight、音频、视频、3D、动画……，这导致了软件UI层更加细节化、可定制化。

> From *维基百科*  
> Model–view–view-model (MVVM) is a software architectural pattern.  
> MVVM facilitates a separation of development of the graphical user interface – be it via a markup language or GUI code – from development of the business logic or back-end logic (the data model). The view model of MVVM is a value converter;[1] meaning the view model is responsible for exposing >(converting) the data objects from the model in such a way that objects are easily managed and presented. In this respect, the view model is more model than view, and handles most if not all of the view's display logic.[1] The view model may implement a mediator pattern, organizing access to the back-end logic around the set of use cases supported by the view.  
> 更多阅读:  
> [Model–view–viewmodel](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel)

从上定义中可以看出，MVVM解决的问题为：**从业务逻辑中分离显示逻辑(eg: php,asp...)**。

![MVVM](https://upload.wikimedia.org/wikipedia/commons/8/87/MVVMPattern.png)

## 2、为什么使用MVVM？

### 2.1、事件驱动模型
使用*Pallet Assembly*来举例(IR第2复杂UI。去年一年，为我们贡献了6~7个Online bug。鼓掌...)。

此功能的特点为：
* UI代码太多(2280行)。
* UI控制逻辑太过复杂，同一控件需要完成不同的逻辑处理。因此，牵一发动全身，Bug应运而生。

对开发人员的困扰为：  
* 2280行代码已让我眩晕。
* 赋值&取值，已做到手软。
* 修改业务逻辑时，大量的时间用于关注和控制显示逻辑，还经常出Bug。（如：控件取值是否争取？UI流程控制是否正确？）

### 2.2、MVVM能为我们带来什么？

#### 2.2.1 MVVM职责解析
（略）

#### 2.2.2 View和ViewModel的沟通方式
* **DataBinding**  
    ![DataBinding](http://www.syscom.com.tw/PicUpload/Cht/rd4/Pic_2909.jpg)
* **Command & Command Binding**  
    ![Command](http://www.syscom.com.tw/PicUpload/Cht/rd4/Pic_2910.jpg)

为什么需要Command？
* Command提供封装。从而使View仅用于显示，不需要包含任何逻辑。
* Command能够被重复使用。
* Command Binding使代码阅读更加友好（个人总结）。

更多阅读：
[Why use commands in MVVM](http://stackoverflow.com/questions/30343129/why-use-commands-in-mvvm)

#### 2.2.2 MVVM能让我轻松一点
* 解耦，向控件的取值/赋值说再见。
* UI代码再简洁一点。
* 分离关注点，维护业务逻辑时，不要在担心影响显示逻辑。（话说的太早？实践中再看看。）

### 2.3 MVVM就是万金油？
**当然不是！！！**  

我们并没有否决*事件驱动模型*，面对一些小型UI，它仍然可以做的更好，为什么呢？(使用看似并不简单的UI*Item Inventory Count History Log*来举例)
* ViewModel越多，对其管理的难度也会逐渐增大。
* ViewModel同时也会为代码阅读带来相应负担，并没有*事件驱动模型*来的直观。

引用大牛的一句话：
>  For simple UI, M-V-VM can be overkill. 

这也将成为成为我*后期MVVM设计和实践*的重要目标。

更多阅读:  
[Advantages and disadvantages of M-V-VM](https://blogs.msdn.microsoft.com/johngossman/2006/03/04/advantages-and-disadvantages-of-m-v-vm/)  
[被误解的MVC和被神化的MVVM](http://www.infoq.com/cn/articles/rethinking-mvc-mvvm)  
[What are the problems of the MVVM pattern? ](http://stackoverflow.com/questions/883895/what-are-the-problems-of-the-mvvm-pattern)

## 3、MVVM与MVC,MVP的横向比较
总所周知，MVVM和MVP都是由MVC演化而来，
