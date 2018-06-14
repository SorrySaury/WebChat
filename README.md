#仿QQWeb即时聊天系统解释
此即时聊天系统基于WebSocket，在需要实时处理信息的情况下，一般想到的方法都是采用轮询的方式每隔一段时间向服务器发送请求从而获得最新的数据，但这样会浪费掉很多的资源并且也不是实时的，于是随着HTML5的推出带来了WebSocket可以根本的解决以上问题实现真正的实时传输。
WebSocket主要运用于社交聊天、弹幕、多玩家游戏、协同编辑、股票基金实时报价、体育实况更新、基于位置的应用、在线教育、在线客服等需要高实时数据通信的场景。
在了解WebSocket之前需要了解的两种软件体系结构以及通讯协议。
C/S结构：Client/Server模式，传统运用比较广泛的软件体系结构。在通信方面如QQ、MSN、QT、YY语音等需要用户安装客户端。
 
B/S结构：Browser/Server模式，当下运用的最广泛的软件体系结构，基于浏览器建立和服务器之间的数据通信。该模式下不需要用户安装客户端，只要有浏览器即可，比如在通信方面运用最多的网页在线客服功能。
 
HTTP协议：客户端-服务器之间单向通信，通常方式是客户端和服务器端之间通过请求-应答方式建立通信。HTTP完整的通信过程是，用户在浏览器中主动向服务器端发送请求，服务器端接收到客户端请求之后进行数据处理，将处理结果给予客户端应答。
 
WebSocket协议：客户端-服务端之间进行双向通信，客户端和服务器端之间建立”握手”通道，握手通道一旦建立后，客户端和服务器端之间可以互相主动向对方发送数据，在这个过程中双方可以多次连续向对方推送数据但不需要重新建立连接。
 
2.	仿QQWeb即时聊天系统功能

聊天室登录、退出功能。登陆时，浏览器自动向服务器发起WebSocket连接，退出时自动切断
登陆后，用户可查看到聊天室在线的用户列表，服务器端通过一个hashmap始终记录了当前在线的用户列表
登陆的用户可以点击一个在线的其他用户，并给他发送消息，消息先提交给服务器，再通过服务器转发给另一端用户
支持群发消息的功能，使用时，服务器会将收到的消息群发给当前在线的所有用户
添加好友上线提醒和下线提醒功能，当有好友上线或下线时自动通知所有其他在线用户
