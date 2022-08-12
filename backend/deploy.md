

# 部署

## docker compose一键部署方式

请按照如下步骤编译和运行：

1. 安装预编译环境

   ```
   - Golang 1.17 or later
   - docker engine version 20.10.17 or later
   ```

2. 编译和运行im仓库代码

   ```shell
   # 下载源码仓库 参考：https://github.com/txchat/im
   $ git clone https://github.com/txchat/im.git
   # 初始化docker环境
   $ cd im && make init-compose
   # 打包镜像及运行容器
   $ make docker-compose-up
   ```

3. 编译和运行dtalk仓库代码

   ```shell
   # 下载源码仓库 参考：https://github.com/txchat/dtalk
   $ git clone https://github.com/txchat/dtalk.git
   # 初始化docker环境
   $ cd dtalk && make init-compose
   # 打包镜像及运行容器
   $ make docker-compose-up
   ```

4. 验证是否部署成功

   1. 安装im-util仓库下的[pressure](https://github.com/txchat/im-util/tree/master/pressure)工具
      ```shell
      # 下载源码仓库 参考https://github.com/txchat/im-util/tree/master/pressure
      $ git clone https://github.com/txchat/im-util.git
      # 编译
      $ cd im-util/pressure && make build
      ```

   2. 执行pressure命令行工具：
      ```shell
      # <ip>为comet服务ip地址
      $ ./pressure pre -s "<ip>:3102" -u 2 -t 5s
      ```

   3. 等待命令执行成功后会在可执行文件目录下生成pressure_output.txt文件，再执行：
      ```shell
      $ ./pressure ana
      
      # 控制台打印出如下内容表示发送的消息全都成功 failed count: 0
      {"level":"info","time":"2022-07-26T11:10:27.879292+08:00","message":"message tranport success count: 10 -- failed count: 0"}
      ```

      
