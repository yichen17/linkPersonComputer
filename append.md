# 待添加功能
1、远程传输视屏和文本， 文本使用堆成加密算法
2、心跳机制，断线重连，使用二进制退避算法,识别管道连接状态，一方失联，另一方监听并关闭
3、拆包 粘包问题，数据大的时候需要进行考虑


# 待研究问题
1、netty 心跳机制具体是怎么实现的
2、ctx.writeAndFlush()  同  ctx.channel().writeAndFlush()  区别
3、ctx.disconnect()     ctx.channel().closeFuture().sync()  区别  后者运行好像会报错