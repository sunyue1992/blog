##http2 较http1.1的新特性

1. 多路复用的单一长连接
  - 单一长链接（一个TCP连接）减少TCP握手带来的时延，提高吞吐量，特别是建立在SSL/TLS减少SSL握手
  - 多路复用，逻辑上每个请求对应一个流，每个流信息分割成二进制帧，可以同时交叉传输（但是必须要有序）
    也可以对流指定优先级（HTTP 1一条TCP上请求串行执行的）
2. 服务端推送Server Push
  - 这个功能通常被称作“缓存推送”。
3. 头部压缩和二进制格式
 - 请求头压缩    
 
 
 
 #总结一下为什么HTTP2能去掉SSL在HTTP1.x上的开销？
 
 1.单一的长连接，减少了SSL握手的开销
 
 2.头部被压缩，减少了数据传输量
 
 3.多路复用能大幅提高传输效率，不用等待上一个请求的响应
 
 4.不用像http1.x那样把多个文件或者资源弄成一个文件或者资源（http1.x常见的优化手段），
 这时候，缓存就能更容易命中啊（http1.x里面你揉成一团的东西怎么命中缓存？）