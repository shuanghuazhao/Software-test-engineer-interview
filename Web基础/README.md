[](#anchor_1)

[](#anchor_2)1\. 描述用浏览器访问 www.baidu.com 的过程
-------------------------------------------

先要解析出 baidu.com 对应的 ip 地址：

1.  要先使用 arp 获取默认网关的 mac 地址
2.  组织数据发送给默认网关 （ip 还是 dns 服务器的 ip，但是 mac 地址是默认网关的 mac 地址）
3.  默认网关拥有转发数据的能力，把数据转发给路由器
4.  路由器根据自己的路由协议，来选择一个合适的较快的路径转发数据给目的网关
5.  目的网关 （dns 服务器所在的网关），把数据转发给 dns 服务
6.  dns 服务器查询解析出 baidu.com 对应的 ip 地址，并原路返回请求这个域名的 client 得到了 baidu.com 对应的 ip 地址之后，会发送 tcp 的 3 次握手，进行连接
7.  使用 http 协议发送请求数据给 web 服务器
8.  web 服务器收到数据请求之后，通过查询自己的服务器得到相应的结果，原路返回给浏览器
9.  浏览器接收到数据之后通过浏览器自己的渲染功能来显示这个网页
10.  浏览器关闭 tcp 连接，即 4 次挥手结束，完成整个访问过程

[](#anchor_3)2\. 常用浏览器有哪些？
--------------------------

IE，Chrome，Safari，Firefox，Opera

[](#anchor_4)3\. 如何测试购买下单和退货流程
------------------------------

产品经理设计了单品优惠，组合优惠，订单优惠，优惠券优惠（优惠券优惠包含通用券，定向券， 满减券，折扣券）和礼品卡，其中礼品卡上需要单独购买的。

请问如何测试购买下单和退货流程，需要注意什么？（包含数据存储）

[](#anchor_5)4\. 什么是 sql 注入，什么是跨站脚本，什么是跨站请求伪造？
----------------------------------------------

SQL 注入攻击是注入攻击最常见的形式（此外还有 OS 注入攻击（Struts 2 的高危漏洞就是通过 OGNL 实施 OS 注入攻击导致的）），当服务器使用请求参数构造 SQL 语句时，恶意的 SQL 被嵌入到 SQL 中交给数据库执行。SQL 注入攻击需要攻击者对数据库结构有所了解才能进行，攻击者想要获得表结构有多种方式：

1.  如果使用开源系统搭建网站，数据库结构也是公开的（目前有很多现成的系统可以直接搭建 论坛 ，电商网站，虽然方便快捷但是风险是必须要认真评估的）；
    
2.  错误回显（如果将服务器的错误信息直接显示在页面上，攻击者可以通过非法参数引发页面错误从而通过错误信息了解数据库结构，Web 应用应当设置友好的错误页，一方面符合最小惊讶原则，一方面屏蔽掉可能给系统带来危险的错误回显信息）；
    
3.  盲注。防范 SQL 注入攻击也可以采用消毒的方式，通过正则表达式对请求参数进行验证，此外， 参数绑定也是很好的手段，这样恶意的 SQL 会被当做 SQL 的参数而不是命令被执行，JDBC 中的 PreparedStatement 就是支持参数绑定的语句对象，从性能和安全性上都明显优于 Statement。
    

XSS（Cross Site Script，跨站脚本攻击）是向网页中注入恶意脚本在用户浏览网页时在用户浏览器中执行恶意脚本的攻击方式。跨站脚本攻击分有两种形式：

*   反射型攻击（诱使用户点击一个嵌入恶意脚本的链接以达到攻击的目标，目前有很多攻击者利用论坛、 微博发布含有恶意脚本的 URL 就属于这种方式）
*   持久型攻击（将恶意脚本提交到被攻击网站的数据库中，用户浏览网页时，恶意脚本从数据库中被加 载到页面执行，QQ 邮箱的早期版本就曾经被利用作为持久型跨站脚本攻击的平台）。

CSRF 攻击（Cross Site Request Forgery，跨站请求伪造）是攻击者通过跨站请求，以合法的用户身份进行非法操作（如转账或发帖等）。CSRF 的原理是利用浏览器的 Cookie 或服务器的 Session，盗取用户身份，其原理如下图所示。防范 CSRF 的主要手段是识别请求者的身份，主要有以下几种方式：

1.  在表单中添加令牌（token）；
2.  验证码；
3.  检查请求头中的 Referer（前面提到防图片盗链接也是用的这种方式）。

令牌和验证都具有一次消费性的特征，因此在原理上一致的，但是验证码是一种糟糕的用户体验， 不是必要的情况下不要轻易使用验证码，目前很多网站的做法是如果在短时间内多次提交一个表单未获得成功后才要求提供验证码，这样会获得较好的用户体验。

[](#anchor_6)5\. 给你一个网站怎么开展测试？
------------------------------

1.  首先，查找需求说明、网站设计等相关文档，分析测试需求。
    
2.  制定测试计划，确定测试范围和测试策略，一般包括以下几个部分：功能性测试，界面测试，性能 测试，数据库测试，安全性测试，. 兼容性测试
    
3.  设计测试用例：
    
    1.  功能性测试可以包括，但不限于以下几个方面：链接测试；链接是否正确跳转，是否存在空 页面和无效页面，是否有不正确的出错信息返回等；提交功能的测试；多媒体元素是否可以正确加载 和显示；多语言支持是否能够正确显示选择的语言等
    2.  界面测试可以包括但不限于以下几个方面：页面是否风格统一，美观。页面布局是否合理， 重点内容和热点内容是否突出。控件是否正常使用。对于必须但为安装的空间，是否提供自动下载并 安装的功能。文字检查。
    3.  性能测试一般从以下两个方面考虑：压力测试，负载测试，强度测试
    4.  数据库测试要具体决定是否需要开展。数据库一般需要考虑连结性，对数据的存取操作，数 据内容的验证等方面。
    5.  安全性测试：基本的登录功能的检查；是否存在溢出错误，导致系统崩溃或者权限泄露；相 关开发语言的常见安全性问题检查，例如 SQL 注入等；如果需要高级的安全性测试，确定获得专业安全公司的帮助，外包测试，或者获取支持。
    6.  兼容性测试，根据需求说明的内容，确定支持的平台组合：浏览器的兼容性；操作系统的兼 容性； 软件平台的兼容性；数据库的兼容性。
4.  开展测试，并记录缺陷。合理的安排调整测试进度，提前获取测试所需的资源，建立管理体系（例 如， 需求变更、风险、配置、测试文档、缺陷报告、人力资源等内容）。
    
5.  定期评审，对测试进行评估和总结，调整测试的内容。
    

[](#anchor_7)6\. 电商支付模块的测试如何展开？
-------------------------------

支付流程里面就涉及到了第三方支付接口：

1.  下单接口
    
    商户提交下单请求到第三方支付接口，第三方支付收单成功后返回下单成功结果给到商户系统。（下单接口的最终处理结果分为下单成功和下单失败，若未收到明确结果可调用单笔订单查询接口查 询结果。）
    
2.  支付接口
    
    调用该接口时指定支付参数，完成买家账户向商户账户的支付，采用页面跳转交互模式和后台通 知交互模式。（结果分为两路返回：一路为前台在 return\_url 页面跳转显示支付结果；一路为后台在 notify\_url 收到支付结果通知后进行响应。）
    
3.  退款接口
    
    调用第三方支付的支付请求接口返回付款成功后，在需要做退款处理时调用退款请求接口发起退 款处理。（退款接口的最终处理结果分为退款成功和退款失败，若未收到明确结果可调用退款查询接 口查询结果。）
    
4.  单笔订单查询接口
    
    根据订单号查询单笔订单信息和状态。退款订单查询接口：调用第三方支付的退款接口返回后， 在需要查询退款请求状态可调用退款订单查询接口查询退款订单的状态和订单信息。
    

测试过程中需要注意的主要测试点及异常场景：

1.  首先要保证接口都能正常调用；
    
2.  生成一笔订单，支付完成后，同步或异步重复回调，只有一次有效；
    
3.  生成一笔订单，复制订单号和金额，再次生成一笔订单，用 fiddler 设置断点，用第一笔已完成的订单号和订单金额去替换现有的订单号和金额，无法完成支付；
    
4.  生成一笔订单，跳转到第三方时修改金额，无法到账，或者如果是游戏充值游戏币的话，到账为 篡改后的金额对应的游戏币；
    
5.  异步通知屏蔽，同步有效，进行支付，同步能够正常到账；
    
6.  同步设置无效，异步有效，进行支付，异步能够正常到账；
    
7.  同步异步都设置无效，在第三方支付完成后，在重发机制时间范围内，设置异步有效，到下次通 知时间点时，能够正常通知到账（补单机制的验证，如果商户收到第三方支付成功的通知后，要 告知第三方支付收到了成功的通知，如果第三方支付收到商户应答不是 ok 或超时，第三方支付就会认为通知失败，会在规定的时间内持续调用 notify_url，一般有时间或次数的限制）；
    
8.  针对支付订单在数据库中存储是否完整和正确进行校验（比如：第三方订单号 \-\- 方便与第三方对账 和问题排查、订单金额、订单状态等）；
    
9.  如果是用户购买实物商品，用户发起退货，要保证退货流程正常，资金能正常返还，要考虑下并 发情况的验证以确保安全性；
    
10.  如果是用户购买虚拟商品，比如话费、油卡之类的商品，只有在发货失败的时候才能发起退货，注意验证；
    

[](#anchor_8)7\. 如何开展兼容性测试？
---------------------------

1.  Web 兼容性测试
    
    *   首先开展人工测试，测试工程师测试主流浏览器和常用操作系统测试主流程和主界面，看看主流 程和主界面是否有问题，如果存在问题，那么记录下 bug 情况，以及浏览器型号和版本，以及操作系统，准确定位 bug 产生的原因，提交 bug，告知开发人员修改。所有的主流设备都需要进行测试， 只关注主流程和主界面，毕竟每个系统主流程和主界面不是很多，所以这个工作量还是可以承受的。
    *   其次借助第三方测试工具，目前我觉得比较好用的第三方 Web 测试工具有 IEtester（离线）、SuperPreview（离线）和 Browsershots：browsershots.org（在线），一款可以测试 IE 的兼容， 一款可以测试主流浏览器的兼容，包括谷歌、火狐、Opera 等等。借助第三方测试工具，找到 bug 产生的位置，分析测试结果，告知程序员调整。
2.  APP 兼容性测试
    
    *   APP 的兼容性测试和 Web 测试类似，首先开展人工测试，测试工程师借助测试设备对主流程和主功能，主界面进行测试；收集所有的能收集到的不同型号的测试设备测试主流程和主界面，看 看主流程和主界面是否有问题，如果存在问题，综合考虑设备的使用率等因素，看看是否需要调 整，如果需要，那么记录下 bug 情况以及测试设备的型号和操作系统，准确定位 bug 产生的原因，提交 bug，告知开发人员修改。
    *   其次借助第三方测试工具，对于 APP 的兼容性测试，推荐的是百度众测平台和云测平台，我经常使用的是云测平台，这两款测试工具里面包含了安卓和 iOS 的测试；测试很齐全，包括功能测试、深度兼容测试、性能测试、网络环境测试，还可以模拟海量用户测试，还可以导入自己编写的测试用例进行功能测试，里面还包括测试专家的测试，当然了找专家是要花钱滴。基本进行兼容性测试是不需要花钱的；测试工程师把打包好的 apk 或者 IPA 文件，上传到测试平台，选择需要测试的设备型号，开始任务即可；等待一段时间，在等待的时间你是不需要盯着的，你可以做其他的工作。测试完成后会生成一份测试报告，可以查看错误页面和错误日志，如果需要调整，那么提交 bug， 告知程序员修改即可。

[](#anchor_9)8\. nginx,tomcat,apache 都是什么？
------------------------------------------

Nginx (engine x) 是一个高性能的 HTTP 和反向代理服务器，也是一个 IMAP/POP3/SMTP 服务器。

Apache HTTP Server 是一个模块化的服务器，源于 NCSAhttpd 服务器

Tomcat 服务器是一个免费的开放源代码的 Web 应用服务器，属于轻量级应用服务器，是开发和调试 JSP 程序的首选。

[](#anchor_10)9\. apache 和 nginx 的区别？
-------------------------------------

Nginx 相对 Apache 的优点：

轻量级，同样起 web 服务，比 apache 占用更少的内存及资源；

抗并发，nginx 处理请求是异步非阻塞的，支持更多的并发连接，而 apache 则是阻塞型的，在高并发下 nginx 能保持低资源低消耗高性能；

配置简洁；

高度模块化的设计，编写模块相对简单； 社区活跃。

Apache 相 对 Nginx 的 优 点

1.  rewrite ，比 nginx 的 rewrite 强大；
2.  模块超多，基本想到的都可以找到；少 bug ，nginx 的 bug 相对较多；
3.  超稳定。

[](#anchor_11)10\. Selenium 有哪些定位元素方法
-------------------------------------

1.  id 定位
2.  name 定位
3.  class_name
4.  tag_name
5.  link_text
6.  partial\_link\_text
7.  Xpath
8.  css

当定位一个元素是，如果存在 ID 属性值时，我们可以优先考虑 ID 定位，当没有 ID，有 name 属性值和 class 属性值时也可以采用 name 和 class\_name 定位。当次能确定该元素的标签为页面唯一时， 可以采用 tag\_name 定位，一般来说采用 link\_text 定位的方法比较少。如果 ID ，name，class\_name 单个定位不了，可以采用 css 和 xpath 定位。
