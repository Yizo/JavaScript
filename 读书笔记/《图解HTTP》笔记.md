# 1. 网络基础TCP/IP
通常使用的网络是在`TCP/IP协议族`的基础上运作的。而HTTP属于它的一个子集 

[![](https://yihzo.com/wp-content/uploads/2020/02/1582788873-图片来自-图解HTTP，第-16-页.png)](https://yihzo.com/wp-content/uploads/2020/02/1582788873-图片来自-图解HTTP，第-16-页.png)
## 1.2 TCP/IP协议族
计算机与网络设备要相互通信，双方就必须基于相同的方法 
* 如何探测到通信目标
* 由哪一边先发起通信
* 使用哪种语言进行通信
* 怎样结束通信
* .... 

所有这一切所需要一种规则，而我们将这种规则称为协议,像这样把与互联网相关联的协议集合起来总称为 TCP/IP。 

## 1.3 TCP/IP的分层管理
| 层  | 作用  | 例子  |
| ------------ | ------------ | ------------ |
| **应用层**  | 应用层决定了向用户提供应用服务时通信的活动  | FTP, DNS |
| **传输层**  | 传输层对上层应用层，提供处于网络连接中的两台计算机之间的数据传输。  | TCP, UDP |
| **网路层**  | 网络层用来处理在网络上流动的数据包。数据包是网络传输的最小数 据单位。该层规定了通过怎样的路径（所谓的传输路线）到达对方计 算机，并把数据包传送给对方。  |   |
| **数据链路层**  | 用来处理连接网络的硬件部分。包括控制操作系统、硬件的设备驱 动、NIC（Network Interface Card，网络适配器，即网卡），及光纤等 物理可见部分（还包括连接器等一切传输媒介）  |   |

## 1.4 TCP/IP通信传输流
[![](https://yihzo.com/wp-content/uploads/2020/02/1582790966-图片来自-图解HTTP，第-18-页.png)](https://yihzo.com/wp-content/uploads/2020/02/1582790966-图片来自-图解HTTP，第-18-页.png) 

利用TCP/IP族进行网络通信时，会通过分层顺序与对方进行通信。发送端从应用层往下走，接收端则往应用层往上走。 

**以HTTP举例**

[![](https://yihzo.com/wp-content/uploads/2020/02/1582791117-图片来自-图解HTTP，第-19-页.png)](https://yihzo.com/wp-content/uploads/2020/02/1582791117-图片来自-图解HTTP，第-19-页.png)  

1. 客户端在应用层(HTTP协议)发出一个想看某个web页面的HTTP请求
2. 在传输层（TCP协议）把从应用层接收到的数据（HTTP请求报文）进行分割，并在各个报文上打上标记序号及端口号转发给网络层
3. 在网络层（IP协议），增加作为通信目的地的MAC地址后转发给链路层
4. 接收端接收到数据，按序往上层发送，一直到应用层。当到达应用层，本次请求完成。
5. 发送端在层与层之间传输数据时，没经过一层必定会被打上一个该层所属的首部信息。反之，接收端在层与层之间传输数据时，没经过一层会把对应的首部消去。

## 1.5 负责传输的 IP 协议
IP协议的作用是把各种数据包传给对方。而要确保确实传送到对方那里，则需要满足各种条件，其中两个重要条件是： **IP地址和MAC地址 ** 

1. IP 地址指明了节点被分配到的地址。
2. MAC 地址是指网卡所属的固定 地址。
3. IP 地址可以和 MAC 地址进行配对。
4. IP 地址可变换，但 MAC 地址基本上不会更改。
5. 使用 ARP 协议凭借 MAC 地址进行通信 

[![](https://yihzo.com/wp-content/uploads/2020/02/1582795546-图片来自-图解HTTP，第-21-页.png)](https://yihzo.com/wp-content/uploads/2020/02/1582795546-图片来自-图解HTTP，第-21-页.png)

## 1.6 确保可靠性的TCP协议
TCP提供可靠的`字节流服务`: 所谓字节流服务，将大块数据分割成以报文段为单位的数据包进行管理。 
为了将数九准确地将数据送达目标处，TCP采用三次握手策略 

[![](https://yihzo.com/wp-content/uploads/2020/02/1582796307-图片来自-图解HTTP，第-22-页.png)](https://yihzo.com/wp-content/uploads/2020/02/1582796307-图片来自-图解HTTP，第-22-页.png)

## 1.7 负责域名解析的DNS服务
DNS（Domain Name System）服务是和 HTTP 协议一样位于应用层的 协议。它提供域名到 IP 地址之间的解析服务。  

[![](https://yihzo.com/wp-content/uploads/2020/02/1582796411-图片来自-图解HTTP，第-23-页.png)](https://yihzo.com/wp-content/uploads/2020/02/1582796411-图片来自-图解HTTP，第-23-页.png)

## 1.8 各种协议与 HTTP 协议的关系
[![](https://yihzo.com/wp-content/uploads/2020/02/1582796469-图片来自-图解HTTP，第-24-页.png)](https://yihzo.com/wp-content/uploads/2020/02/1582796469-图片来自-图解HTTP，第-24-页.png)

## 1.9 URI和URL
与 URI（统一资源标识符）相比，我们更熟悉 URL（Uniform Resource Locator，统一资源定位符） 

URI 是 Uniform Resource Identifier 的缩写。RFC2396 分别对这 3 个单 词进行了如下定义。
|   | 定义  |
| ------------ | ------------ |
| Uniform  | 规定统一的格式可方便处理多种不同类型的资源，而不用根据上下文 环境来识别资源指定的访问方式。  |
|  Resource | 资源的定义是“可标识的任何东西”。  |
| Identifier  | 表示可标识的对象。也称为标识符。  | 

综上所述，URI 就是由`某个协议方案`表示的资源的定位标识符。协议方案是指访问资源所使用的协议类型名称。 
采用HTTP协议时，协议方案就是HTTP，除此以外还有ftp,mailto,telnet,file等。

# 2. 简单的HTTP协议
## 2.1 HTTP 协议用于客户端和服务器端之间 的通信
## 2.2 通过请求和响应的交换达成通信
请求报文的构成: 

[![](https://yihzo.com/wp-content/uploads/2020/02/1582798115-图片来自-图解HTTP，第-32-页.png)](https://yihzo.com/wp-content/uploads/2020/02/1582798115-图片来自-图解HTTP，第-32-页.png)

## 2.3 HTTP 是不保存状态的协议
HTTP 是一种不保存状态，即无状态（stateless）协议。HTTP 协议自 身不对请求和响应之间的通信状态进行保存。也就是说在 HTTP 这个 级别，协议对于发送过的请求或响应都不做持久化处理。

## 2.4 请求 URI 定位资源
当客户端请求访问资源而发送请求时，URI 需要将作为请求报文中的 请求 URI 包含在内。指定请求 URI 的方式有很多。 
1. URI为完整的URL
2. 在首部字段Host中写明网络域名或IP地址 

除此之外，如果不是访问特定资源而是对服务器本身发起请求，可以 用一个 * 来代替请求 URI。 
```js
OPTIONS * HTTP/1.1
```

## 2.5 告知服务器意图的HTTP方法
GET ：获取资源 
POST：传输实体主体 
HEAD：获得报文首部 
DELETE：删除文件 
OPTIONS：询问支持的方法 
TRACE：追踪路径 
CONNECT：要求用隧道协议连接代理 
LINK:建立和资源之间的联系 
UNLINE:断开连接关系

# 3. HTTP 报文内的 HTTP 信息
## 3.1 HTTP报文
1. 用于HTTP协议交互的信息被称为HTTP报文。
2. 分为请求报文和响应报文
3. HTTP 报文本身是由多行（用 CR+LF 作换行符）数据构成的字符串文本。
4. HTTP 报文大致可分为报文首部和报文主体两块。

## 3.2 请求报文及响应报文的结构
[![](https://yihzo.com/wp-content/uploads/2020/02/1582809803-图片来自-图解HTTP，第-49-页.png)](https://yihzo.com/wp-content/uploads/2020/02/1582809803-图片来自-图解HTTP，第-49-页.png) 
[![](https://yihzo.com/wp-content/uploads/2020/02/1582809821-图片来自-图解HTTP，第-49-页.png)](https://yihzo.com/wp-content/uploads/2020/02/1582809821-图片来自-图解HTTP，第-49-页.png)  

请求报文和响应报文的首部内容由以下数据组成: 
|   |   |
| ------------ | ------------ |
| 请求行  | 包含用于请求的方法，请求 URI 和 HTTP 版本。  |
| 状态行  | 包含表明响应结果的状态码，原因短语和 HTTP 版本。  |
| 首部字段  | 包含表示请求和响应的各种条件和属性的各类首部。  |

## 3.3 编码提升传输速率
HTTP 在传输数据时可以按照数据原貌直接传输，但也可以在传输过 程中通过编码提升传输速率。通过在传输时编码，能有效地处理大量 的访问请求。但是，编码的操作需要计算机来完成，因此会消耗更多 的 CPU 等资源。
### 3.3.1 报文主体和实体主体的差异
|   |   |
| ------------ | ------------ |
| 报文（message）  | 是 HTTP 通信中的基本单位，由 8 位组字节流组成，通过 HTTP 通信传输。  |
| 实体（entity）  | 作为请求或响应的有效载荷数据（补充项）被传输，其内容由实 体首部和实体主体组成。  |


[toc]