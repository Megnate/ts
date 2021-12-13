在 vs code 中添加 `git bash`，可以直接使用 git 命令来提交 GitHub

- 在 settings.json 文件中，是设置中的，添加以下语句：

```json
"terminal.integrated.profiles.windows": {
    "PowerShell": {
        "source": "PowerShell",
        "icon": "terminal-powershell"
    },
    "Command Prompt": {
        "path": [
            "${env:windir}\\Sysnative\\cmd.exe",
            "${env:windir}\\System32\\cmd.exe"

        ],
        "args": [],
        "icon": "terminal-cmd"
    },
    "GitBash": {
        // "source": "Git Bash",
        "icon": "terminal-bash",
        "path": "D:\\Git\\bin\\bash.exe",
    }
},
"terminal.integrated.defaultProfile.windows": "GitBash"  // 视情况开启（且应当直接在设置中更改）
```

正常输入 key 就会出现别的，所以我们通常只需要添加 Git Bash 即可。

未启用原因之一：

上面存在该配置：`"terminal.integrated.shell.windows": "C:\\WINDOWS\\System32\\cmd.exe"`，需将其注释（其该方法已经被弃用）
