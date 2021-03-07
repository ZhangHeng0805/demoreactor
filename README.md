# demoreactor
Spring5框架新功能（Webflux）
   ## 1、SpringWebFlux介绍
       ### （1）是Spring5添加的新模块，用于web开发的，功能和SpringMVC类似，Webflux使用当前一种比较流行的响应式编程，因为它而出现的框架。
        ###（2）使用传统web框架，比如SpringMVC，这些基于Servlet容器，Webflux是一种异步非组塞的框架，异步非阻塞的框架在Servlet3.1以后才支持
            核心是基于Reactor的相关API实现的
        ###（3）解释什么是异步非阻塞
            *异步和同步
            *非阻塞和阻塞
            **上面都是针对对象不一样
            **异步和同步针对调用者，调用者发送请求，如果等着对方回应之后才做其他事情就是同步
                如果发送请求之后，不等着对方回应就去做其他事情就是异步
            **阻塞和非阻塞针对被调用者,被调用者受到请求之后，做完请求任务之后才给出反馈就是阻塞；
                受到请求之后马上给出反馈然后再去做其他事情就是非阻塞
       ### （4）Webflux特点：
            第一 非阻塞式：在有限的资源下，提高系统吞吐量和伸缩性，以Reactor为基础实现响应式编程
            第二 函数式编程：Spring5框架基于java8，Webflux使用java8函数式编程方式实现路由请求
        ###（5）比较SpringMVC：
            第一 两个框架都可以使用注解方式，都可以在Tomcat等容器中运行
            第二 SpringMVC采用命令式编程，Webflux采用异步响应式编程
   ## 2、响应式编程
        ###（1）什么是响应式编程
            响应式编程是一种面向数据流和变化传播的编程范式。
            这意味着可以在编程语言中很方便地表达静态或动态的数据流，而相关的计算模型会自动将变化的值通过数据流进行传播。
            电子表格程序就是响应式编程的一个例子。单元格可以包含字面值或类似"=B1+C1"的公式，而包含公式的单元格的值会依据其他单元格的值的变化而变化。
        ###（2）java8及其之前版本
            *提供了观察者模式的两个类：Observer和Observable
                public class ObserverDemo extends Observable {
                    public static void main(String[] args) {
                        ObserverDemo observer=new ObserverDemo();
                        //添加观察者
                        observer.addObserver((o,arg)->{
                            System.out.println("发生了变化");
                        });
                        observer.addObserver((o,arg)->{
                            System.out.println("被观察者通知，准备改变");
                        });
                        observer.setChanged();//数据变化
                        observer.notifyObservers();//通知
                    }
                }
        ###（3）响应式编程（Reactor实现）
            1）响应式编程操作中，Reactor是满足Reactive规范框架
            2）Reactor有两个核心类，Mono和Flux，这两个类实现接口Publisher，提供丰富操作符。Flux对象实现发布者，返回N个元素；
                Mono实现发布者，返回0或1个元素
            3）Flux和Mono都可以发出三种信号：元素值，错误信号，完成信号，错误信号和完成信号都代表终止信号，终止信号用于告诉订阅者数据流结束了
                错误信号终止数据流同时把错误信息传递给订阅者
   ## 3、WebFlux执行流程和核心API
   ## 4、SpringWebflux（基于注解模型）
   ## 5、SpringWebflux（基于函数式编程模型）
