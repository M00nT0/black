# Windows权限维持后门、持续反弹shell，60s/1次、目前已实现最新版360、火绒免杀(免杀已失效，欢迎师傅们找我讨论程序的任何问题！)
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

![image](https://user-images.githubusercontent.com/33219753/120927097-3eb01d00-c712-11eb-83c4-3fd6ec350b37.png)
![image](https://user-images.githubusercontent.com/33219753/120927201-9ea6c380-c712-11eb-9019-27319e377eff.png)
![image](https://user-images.githubusercontent.com/33219753/120927298-0eb54980-c713-11eb-8413-f127810afbf3.png)





