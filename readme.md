### 内网中使用 nvm 管理 node 版本

> 前提：内网访问不到外网（即不能正常使用 nvm install [version]）
> 解决：需要自己在内网搭建一个 node 依赖平台，方便 nvm 访问并安装

### 安装 nvm (windows)

> 在目录 nvm-setup 中解压 nvm-setup.zip 并安装 nvm
> 命令窗口输入 nvm version 查看是否安装成功

### 搭建 node 版本平台，方便 nvm 下载并安装

1.下载需要的 node 包到本地中

> 在外网 node 淘宝镜像（https://npm.taobao.org/mirrors/node/）中，下载需要的 node 版本（假设这里需要的版本是 14.15.0）
> 同当前 node 文件夹中已有的 v12.22.0 以及 v16.4.0 一样，创建 v14.15.0 目录，并创建 win-x64（因为本机是 64 位，如果是 32 为则创建 win-x86）子目录。
> 在镜像中找到对应的 v14.15.0 目录，找到 win-x64 下的 node.exe 下载并拷到本地创建好的 win-x64 目录中
> 在镜像中找到对应的 v14.15.0 目录，拷贝 SHASUMS256.txt 文件到本地中

2.下载 node 对应的 npm 包到本地中

> 查看镜像中的 index.json 文件，找到 node 对应版本的相关信息并拷贝到本地的 index.json 中
> 并在该信息中找到该 node 版本所依赖的 npm 版本号后，到 npm 淘宝镜像（https://npm.taobao.org/mirrors/npm/）中下载对应的zip包
> 将下载的 zip 包拷贝到本地的 npm 目录中
> 查看镜像中的 index.json 文件，找到 node 对应版本的相关信息并拷贝到本地的 index.tab

### 启动本地访问文件服务

> npx http-server
> 记录本地服务地址，一般为 http://127.0.0.1:8080

### 使用 nvm 管理 node 版本

1.修改 nvm 默认的镜像地址

> nvm node_mirror http://127.0.0.1:8080/node/
> nvm npm_mirror http://127.0.0.1:8080/npm/

2.使用 nvm 下载 node 包（启动的本地服务中拉取）

> nvm list available 查看从外网下载的 node 包是否能够访问到
> nvm install 14.15.0 下载该 node 版本
> nvm use 14.15.0
> node -v 查看是否切换成功
