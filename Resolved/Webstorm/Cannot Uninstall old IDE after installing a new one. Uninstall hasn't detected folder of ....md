
> 安装了新版本的 webstorm 后无法正常删除旧版本的 webstorm 的处理解决方案。

[Official webstorm resolved]([https://youtrack.jetbrains.com/issue/IDEA-220717](https://youtrack.jetbrains.com/issue/IDEA-220717))

![uninstall hasn't detected folder](https://youtrack.jetbrains.com/api/files/74-1556212?sign=MTY4NTgzNjgwMDAwMHwxMS0xfDc0LTE1NTYyMTJ8TGJPMEMzeVpYWXFvNGlRdjZPYWZGb2VsWGt2%0D%0AVlU5RVQyOXVZbm9uNjJRMA0K%0D%0A&updated=1675163039464](https://youtrack.jetbrains.com/api/files/74-1556212?sign=MTY4NTgzNjgwMDAwMHwxMS0xfDc0LTE1NTYyMTJ8TGJPMEMzeVpYWXFvNGlRdjZPYWZGb2VsWGt2%0D%0AVlU5RVQyOXVZbm9uNjJRMA0K%0D%0A&updated=1675163039464)

### 当前处理方案添加 IdeaWin64.dll

Found a working solution in linked thread ([Uninstaller doesn't cleanly remove an updated version : PY-35047 (jetbrains.com)](https://youtrack.jetbrains.com/issue/PY-35047/Uninstaller-doesnt-cleanly-remove-an-updated-version)) by . Created an empty IdeaWin64.dll file in the same place where Un_A.exe was (../bin) and the uninstallation process finally ran and worked!

> 在同文件目录下(bin)创建 IdeaWin64.dll 文件，然后再次运行 uninstall.exe 文件