# AI agent

AI agent 项目仓库。作为一枚计算机开发小白，我有幸深处AI时代，系统赋能！！！嗷，对了，请宿主抓紧学习Markdown简单语法😊

## Codex辅助Git、Github的项目建立🏗️

2022年以前，暴风雨前的宁静，Github社群项目上传的模式仍是......

### 场景一：本地先有文件夹，初始化后关联 GitHub

适合本地已经放了文件 / 写了代码，再关联到 GitHub 空仓库的情况（也就是你当前这个仓库的初始化方式）。

1. 打开终端，进入你的项目文件夹

```
cd D:\Desktop\git_test
```

2. 初始化本地 Git 仓库

```
git init
```

执行后文件夹里会生成隐藏的 `.git` 目录，本地版本管理正式生效。

3. 添加文件并完成第一次本地提交

```
git add .
git commit -m "Initial commit 初始提交"
```

4. 关联 GitHub 远程仓库
SSH / HTTPS 二选一，粘贴你自己的仓库地址：

```
# SSH 方式（推荐，前提是已配置好密钥）
git remote add origin git@github.com:Tonicdog-panicguy/AI-agent.git

# HTTPS 方式
git remote add origin https://github.com/Tonicdog-panicguy/AI-agent.git
```

5. 第一次推送到远程仓库

```
git push -u origin main
```

`-u` 的作用是把本地 `main` 分支和远程 `origin/main` 绑定，之后直接用 `git push` 即可，不用再加分支名。

### 场景二：直接从 GitHub 克隆仓库到本地（最省事，推荐新手）

适合 GitHub 上已经建好仓库，从零开始在本地开发的情况，一步完成「初始化 + 关联远程」。

1. 在 GitHub 仓库页面复制地址（SSH 或 HTTPS 均可）
2. 终端进入你想存放项目的目录，执行克隆：

```
# SSH 示例
git clone git@github.com:Tonicdog-panicguy/AI-agent.git

# HTTPS 示例
git clone https://github.com/Tonicdog-panicguy/AI-agent.git
```

3. 克隆完成后会自动生成项目文件夹，且已经配好了远程 origin 地址，直接就能提交推送。

### SSH 密钥配置完整步骤（Windows 环境）
PS：HTTPS地址建立新的仓库即可获得，SSH地址的创建方法较为复杂

#### 第一步：检查本地是否已有密钥

打开 Git Bash 或 PowerShell，执行：

```
ls ~/.ssh
```

如果输出里有 `id_ed25519.pub` 或 `id_rsa.pub` 文件，说明你之前生成过密钥，可以直接跳到第三步复制公钥。

#### 第二步：生成 SSH 密钥对

执行下面的命令生成新版加密的密钥（比传统 RSA 更安全、体积更小）：

```
ssh-keygen -t ed25519 -C "你的GitHub注册邮箱"
```

执行后连续按 3 次回车即可：

- 第一次：确认密钥保存位置（默认就行，不用改）
- 第二、三次：设置密钥密码（新手可以留空，不用密码；设置密码更安全但每次推送要输入）

生成完成后，密钥对会保存在 `C:\Users\你的用户名\.ssh\` 文件夹里：

- `id_ed25519`：私钥，绝对不能泄露给别人
- `id_ed25519.pub`：公钥，要粘贴到 GitHub 上

#### 第三步：复制公钥内容

在 PowerShell 里执行这条命令，可以一键把公钥内容复制到剪贴板：

```
Get-Content ~/.ssh/id_ed25519.pub | Set-Clipboard
```

也可以手动打开 `.ssh` 文件夹，用记事本打开 `id_ed25519.pub`，全选复制里面的所有内容，注意不要多复制空格和换行。

#### 第四步：把公钥添加到 GitHub 账号

1. 打开 GitHub 网页，点击右上角头像 → **Settings**
2. 左侧菜单找到 **SSH and GPG keys**
3. 点击右上角 **New SSH key**
4. Title 随便填，比如 “我的笔记本”，用来区分设备
5. Key type 保持默认 `Authentication Key`
6. 把刚才复制的公钥粘贴到 Key 输入框里，点击 **Add SSH key** 完成添加

#### 第五步：把本地仓库地址改成 SSH 格式/HTTPS格式

1. 先查看当前远程地址：

```
git remote -v
```

2. 修改地址（你的仓库地址如下）：
SSH 格式
```
git remote set-url origin git@github.com:Tonicdog-panicguy/AI-agent.git
```
HTTPS格式
```
git remote set-url origin https://github.com/Tonicdog-panicguy/AI-agent.git
```

#### 第六步：测试连接是否成功

SSH执行：

```
ssh -T git@github.com
```

第一次连接会提示 `Are you sure you want to continue connecting`，输入 `yes` 回车。
如果出现 `Hi 你的用户名! You've successfully authenticated...` 就说明配置成功了。

HTTPS 没有类似 `ssh -T` 这样的纯连通性命令，最标准的轻量测试方式是读取远程仓库的引用信息，不需要拉取代码：

```
git ls-remote origin
```

- 如果能正常返回一串哈希值和分支名（比如 `refs/heads/main`），说明 HTTPS 连接和权限都正常。
- 如果报错「认证失败」「无法访问」，就说明 HTTPS 的凭据有问题或者网络不通。

### Codex🤖辅助进行配置该怎么做？

方法：读懂上文，接上Github插件，直接下命令哈哈哈哈哈🤣🤣🤣🤣🤣

## Codex辅助下的Git工程管理🧑‍💼
