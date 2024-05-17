# langflow 安装调试说明

# 前置准备

安装python3.10或3.11

```shell
# 输入以下命令校验python是否安装成功
python --version

# 输入以下命令校验pip是否安装成功
pip --version
```

Pip镜像源更换

```shell
# 配置清华源
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
# 配置备用阿里源   部分包清华源没有最新版
pip config set extra-index-url https://mirrors.aliyun.com/pypi/simple
# 配置trusted-host 两个站点都要配置
pip config set install.trusted-host '\npypi.tuna.tsinghua.edu.cn\nmirrors.aliyun.com'
```

安装poetry

```shell
# 在命令行中输入以下命令：
pip install poetry
```

安装make

```shell
# 在命令行中输入以下命令安装：
@powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin

# 再输入以下命令安装make
choco install make

# 输入以下命令校验是否安装成功
make --version
```

# 部署包安装运行说明

- 创建langflow文件夹
- 在文件夹下打开cmd，
- 创建虚拟环境：python -m venv env
- 激活虚拟环境：env\Scripts\activate
- 安装langflow：pip install langflow
- 启动langflow：python -m langflow run
- 更新langflow：pip install --upgrade langflow

# 源码安装运行说明

项目初始化 （使用make）

```shell
# 在命令行中输入以下命令初始化：
make init
```

项目初始化 （手动安装前后端）

```shell
# 在命令行中输入以下命令初始化后端：
poetry install

# 在命令行中输入以下命令初始化前端：
cd src/frontend
npm install
```

项目运行

```shell
# 在命令行中输入以下命令启动整个项目：
make start

# 在命令行中输入以下命令启动前端：
make run_frontend

# 在命令行中输入以下命令启动后端：
make backend
```

前后端独立调试

- 配置python虚拟环境

```shell
# 虚拟环境会在poetry install命令执行时打印出来如下所示：
Creating virtualenv langflow-Nncoset4-py3.10 in C:\Users\Wilson\AppData\Local\pypoetry\Cache\virtualenvs

# 也可以在命令行中输入以下命令查看
poetry env use python
```

- 调试后端

```shell
\langflow\src\backend\base\langflow\__main__.py
搜索 backend_only  修改为True

添加运行形参run

启动__main__.py
```

- 调试前端

```shell
#命令行中依次输入以下命令
cd src/frontend
npm start
```
