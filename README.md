# rsync
sublime text 3 plugin for windows

## version
beta

## Dependencies
- cwRsync
- git

## Usage
- 安装 `cwRsync`
- 把 `cwRsync` 路径添加到环境变量中
- 安装 `git`
- 创建 `ssh-key`(通过`ssh-keygen`或者`git`)
- 环境变量中添加 HOME 值为 %HOMEDRIVE%%HOMEPATH% (解决`windows`下`ssh`无法找到已创建的`ssh-keys`时使用)
- 配置你的 winRSync 设置 Preferences -> Package Settings -> winRsync -> Setting-User
- 开始使用 Tools -> winRsync

## Remind
- 本插件会验证光标激活中的文件是否属于local_path，通过后才能使用期rsync相关功能
- 由于上一条，对于查看图片等sublime中无法让光标激活的文件，无法使用单文件同步，建议在确认修改完毕后使用rsync整个文件目录到远程
- (Todo later)同由于第一条，第一次rsync由于本地无文件无法正常使用，建议新建然后同步所有文件，然后删除；或者直接执行rsync命令进行同步；
- 本地删除不会rsync到远端，请手动删除远端文件，或使用Synchronize the whole tree to remote(s)操作

## Options
- `winrsync.hosts`远程地址配置，可配置多个
```json
"winrsync.hosts":
  [
    {
      "excludes":
        [
        ],
      "main": true,
      "remote_host": "111.111.111.111",
      "remote_path": "/home/user/remote_folder",
	  "remote_user": "user"
	}
  ]
```
- `winrsync.local_path`本地工作目录配置，windows中使用\\\\
```json
"winrsync.local_path": "X:\\loacl_folder"
```
- `winrsync.excludes`不rsync的文件
```json
"winrsync.excludes":
  [
    "excludes_file.xxx"
  ],
```
- `winrsync.remote_is_master`远程是否主代码
```json
"winrsync.remote_is_master": true|false
```
- `winrsync.use_ssh`使用ssh链接
```json
"winrsync.use_ssh": true
```
- `winrsync.check_remote_git`匹配远程和本地的git版本（本地和远程都已安装git，且同步的目录是基于git管理的）
```json
"winrsync.check_remote_git": true|false
```
- `winrsync.delete_slave`rsync时，是否删除文件
```json
"winrsync.delete_slave": true|false
```