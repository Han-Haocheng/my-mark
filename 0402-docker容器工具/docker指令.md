## 基础操作

### 查看版本

```bash
docker --version
```

### 查看系统信息

```bash
docker info [OPTIONS]
```

`[OPTIONS]`
- `-f|--format <"PATTERN">`：使用给定的`Go`模板来格式化输出
	- `PATTERN`：格式化字符串
```bash
docker info --format "{{json .}}"
```

## 镜像操作

### 列出镜像

```bash
docker images [OPTIONS] [REPOSITORY[:TAG]]
```

`[OPTIONS]`：可选参数
- `-a|--all`: 显示所有镜像，包括中间层镜像
- `--digests`: 显示镜像的摘要信息
- `-f|--filter <"CONDITION">`: 根据提供的条件过滤输出
	- `CONDITION`：条件字符串
- `--format <"PATTERN">`: 使用 Go 模板格式化输出
	- `PATTERN`：格式化字符串
- `--no-trunc`: 显示完整的镜像 ID
- `-q|--quiet`: 只显示镜像ID

`[REPOSITORY[:TAG]]`：用于过滤特定仓库或标签的参数
- `REPOSITORY`：仓库名
- `TAG`：标签

### 从库中拉取镜像

```bash
docker pull [OPTIONS] <NAME[:TAG|@DIGEST]>
```

`[OPTIONS]`
- `--all-tags, -a`: 下载指定镜像的所有标签
- `--disable-content-trust`: 跳过镜像签名验证

`<NAME[:TAG|@DIGEST]>`：镜像的名称、标签、摘要
- `NAME`：镜像的名称，通常包含注册表地址（eg：`docker.io/library/ubuntu`）
- `TAG`：镜像的标签，默认为 `latest`
- `@DIGEST`：镜像的`SHA256`摘要
### 删除镜像

```bash
docker rmi [OPTIONS] <IMAGE [IMAGE...]> 
```

`[OPTIONS]`
- `-f|--force`：强制删除镜像，即使该镜像被容器使用
- `-a|--all-tags`：指定仓库名称时，删除该仓库下的所有镜像
- `--no-prune`：删除镜像时，不移除该镜像的过程镜像
- `-q|--quiet`：安静模式，不显示删除镜像的详细信息

`<IMAGE [IMAGE...]>`：是要删除的镜像的名称
- `IMAGE`：可以是镜像名、镜像ID或镜像`SHA256`摘要

### 构建镜像

```bash
docker build
```


## 容器操作

### 列出容器

```bash
docker ps [OPTIONS]
```

`[OPTIONS]`
- `-a|--all`: 显示所有容器，包括停止的容器。
- `-q|--quiet`: 只显示容器 ID。
- `-l|--latest`: 显示最近创建的一个容器，包括所有状态。
- `-n <NUM>`: 显示最近创建的 n 个容器，包括所有状态。
	- `NUM`：数量
- `--no-trunc`: 不截断输出。
- `-s|--size` : 显示容器的大小
- `--filter|-f <"CONDITION">`: 根据条件过滤显示的容器。
- `--format <"PATTERN">`: 格式化输出。

#### 列出容器输出的内容

- `CONTAINER ID`: 容器ID
- `IMAGE`: 使用的镜像
- `COMMAND`: 启动容器时运行的命令
- `CREATED`: 容器的创建时间
- `STATUS`: 容器状态
	- created：已创建
	- restarting：重启中
	- running：运行中
	- removing：删除中
	- paused：已暂停
	- exited：已存在
	- dead：已死亡
- `PORTS`: 容器的端口信息和使用的连接类型
	- tcp
	- udp
- `NAMES`: 自动分配的容器名称

### 创建容器

```bash
docker run [OPTIONS] <IMAGE> [COMMAND] [ARG...]
```

`[OPTIONS]`
- `-d`：后台运行容器并返回容器 ID
- `-it`：交互式运行容器，分配一个伪终端
- `--name <"NAME">`：给容器指定一个名称
	- `NAME`：名称
- `-p <HOST_PORT:CONTAINER_PORT>`：端口映射
	- `HOST_PORT`：主机端口
	- `CONTAINER_PORT`：容器端口
- `-v <HOST_DIR:CONTAINER_DIR>`：挂载卷
	- `HOST_DIR`：主机路径
	- `CONTAINER_DIR`：容器路径
- `--rm`：容器停止后自动删除容器
- `-e|--env <KEY:VAL> [-e|--env <KEY:VAL>...]`：设置环境变量
	- `KEY`：键
	- `VAL`：值
- `--network <bridge|host|container:<NAME|ID>|none>`：指定容器的网络模式
	- `bridge`：桥接模式
	- `host`：共享模式
	- `container`：容器网络连通
	- `none`：不配置网络
- `--restart [no|on-failure|on-failure<:NUM>|always|unless-stopped]`：容器的重启策略
	- `no`：这是默认策略，容器退出时不会重启
	- `on-failure`：只有当容器非正常退出（即退出状态非0）时，才会重启容器
	- `on-failure<:NUM>`：在容器非正常退出时重启容器，并且指定重启次数。`n` 是一个正整数。如果不指定次数，则会一直重启
	- `always`：无论容器退出原因是什么，都会重启容器
	- `unless-stopped`：容器退出时总是重启，但 Docker守护进程启动之前就已经停止运行的容器不算在内
- `-u <USERNAME>`：指定用户
	- `USERNAME`：用户名

`<IMAGE>`：指定要运行的 Docker 镜像名

`[COMMAND]`：在容器中执行的命令

`[ARG...]`：传递给命令的参数
### 停止容器

```bash
docker stop
```

### 启动容器
```bash
docker start
```

### 重启容器
```bash
docker restart
```

### 删除容器
```bash
docker rm
```

### 进入容器命令行终端

```bash
docker exec
```