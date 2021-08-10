# linkPersonComputer
通过netty 连接私人电脑

# 介绍
都是通过springboot 开发的项目。
1、首先启动client, 因为我们是通过它来访问我们的个人电脑的相当于客户端。
2、然后启动server，即部署在我们私有电脑上的

# 功能
1、可以直接访问内网，即我在外面也能访问自己的电脑，查询东西。我的一个想法是通过这种途径查阅和修改我的各种私人账号
2、实现了心跳机制，可以追加新的功能(失败重连啥的)。

# 测试
1、如果部署在本地，访问 http://localhost:8090/get ，可以获取 server 返回给我们的数据，即获得个人数据。
如果是部署在阿里云上则修改端口前面的ip地址即可。


# 注意点
如果想自己开发点新的功能，如果涉及双方通信的话，推荐在channel写数据是对获取到的数据进行监听，可以方便很多。
我这里实现心跳机制，由于一开始没有监听，导致我卡了很久(心跳一直失败)，最终原因是序列化问题。
```
future.addListener(new ChannelFutureListener() {
    @Override
    public void operationComplete(ChannelFuture future) throws Exception {
        if(future.isSuccess()){
            System.out.println("发送心跳成功");
        }
        else{
            // 这里查看问题真的很方便。
            future.cause().printStackTrace();
        }
    }
});
```