slowdos
=======

慢连接攻击

1.准备被攻击服务的ip、端口、URL请求header。通过正常的请求能够降低被防御的几率。
2.将以上信息填写入程序中，并执行。
3.程序启动后，进入循环。
  每次循环首先创建100个POST请求连接，但仅发送请求header，不发送数据。
  然后对连接池中已创建的每一个连接只发送两个字节的数据。因为header中声明数据长度为300000，即可保持该连接不被服务器断开。
  本次循环结束。
4.循环期间可通过^C将已创建连接全部关闭，攻击停止。