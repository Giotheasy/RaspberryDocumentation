# Windows Terminal Configuration
```json
{
    "$schema": "https://aka.ms/terminal-profiles-schema",
    "actions": 
    [
        {
            "command": 
            {
                "action": "copy",
                "singleLine": false
            },
            "keys": "ctrl+c"
        },
        {
            "command": "paste",
            "keys": "ctrl+v"
        },
        {
            "command": "find",
            "keys": "ctrl+shift+f"
        },
        {
            "command": 
            {
                "action": "splitPane",
                "split": "auto",
                "splitMode": "duplicate"
            },
            "keys": "alt+shift+d"
        }
    ],
    "copyFormatting": "all",
    "copyOnSelect": false,
    "defaultProfile": "{9c1c3646-843c-4d29-981d-dd9b82c3f476}",
    "launchMode": "maximized",
    "profiles": 
    {
        "defaults": 
        {
            "antialiasingMode": "cleartype",
            "font": 
            {
                "face": "MesloLGS NF",
                "size": 10,
                "weight": "normal"
            },
            "suppressApplicationTitle": false,
            "useAcrylic": true
        },
        "list": 
        [
            {
                "acrylicOpacity": 0.0,
                "antialiasingMode": "cleartype",
                "colorScheme": "cyberpunk",
                "commandline": "powershell.exe",
                "experimental.retroTerminalEffect": false,
                "font": 
                {
                    "face": "MesloLGS NF",
                    "size": 10
                },
                "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
                "hidden": false,
                "name": "WindowsPowerShell",
                "startingDirectory": "%USERPROFILE%",
                "tabColor": "#4C2882",
                "useAcrylic": true
            },
            {
                "commandline": "cmd.exe",
                "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
                "hidden": false,
                "name": "CommandPrompt"
            },
            {
                "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
                "hidden": false,
                "name": "AzureCloudShell",
                "source": "Windows.Terminal.Azure"
            },
            {
                "acrylicOpacity": 0.0,
                "colorScheme": "cyberpunk",
                "commandline": "%PROGRAMFILES%/git/usr/bin/bash.exe -i -l",
                "font": 
                {
                    "face": "MesloLGS NF",
                    "size": 10
                },
                "guid": "{00000000-0000-0000-ba54-000000000002}",
                "hidden": false,
                "icon": "%PROGRAMFILES%/Git/mingw64/share/git/git-for-windows.ico",
                "name": "Bash",
                "startingDirectory": "%USERPROFILE%",
                "tabColor": "#CCFF00",
                "useAcrylic": true
            },
            {
                "acrylicOpacity": 0.0,
                "backgroundImage": null,
                "backgroundImageOpacity": 1.0,
                "backgroundImageStretchMode": "uniformToFill",
                "colorScheme": "cyberpunk",
                "commandline": "ssh.exe pi@192.168.0.114",
                "guid": "{9c1c3646-843c-4d29-981d-dd9b82c3f476}",
                "name": "Raspberry Pi",
                "padding": "8"
            }
        ]
    },
    "schemes": 
    [
        {
            "background": "#0E1019",
            "black": "#232323",
            "blue": "#008DF8",
            "brightBlack": "#444444",
            "brightBlue": "#0092FF",
            "brightCyan": "#67FFF0",
            "brightGreen": "#ABE15B",
            "brightPurple": "#9A5FEB",
            "brightRed": "#FF2740",
            "brightWhite": "#FFFFFF",
            "brightYellow": "#FFD242",
            "cursorColor": "#FFFFFF",
            "cyan": "#00D8EB",
            "foreground": "#FFFAF4",
            "green": "#8CE10B",
            "name": "Argonaut",
            "purple": "#6D43A6",
            "red": "#FF000F",
            "selectionBackground": "#FFFFFF",
            "white": "#FFFFFF",
            "yellow": "#FFB900"
        },
        {
            "background": "#0C0C0C",
            "black": "#0C0C0C",
            "blue": "#0037DA",
            "brightBlack": "#767676",
            "brightBlue": "#3B78FF",
            "brightCyan": "#61D6D6",
            "brightGreen": "#16C60C",
            "brightPurple": "#B4009E",
            "brightRed": "#E74856",
            "brightWhite": "#F2F2F2",
            "brightYellow": "#F9F1A5",
            "cursorColor": "#FFFFFF",
            "cyan": "#3A96DD",
            "foreground": "#CCCCCC",
            "green": "#13A10E",
            "name": "Campbell",
            "purple": "#881798",
            "red": "#C50F1F",
            "selectionBackground": "#FFFFFF",
            "white": "#CCCCCC",
            "yellow": "#C19C00"
        },
        {
            "background": "#012456",
            "black": "#0C0C0C",
            "blue": "#0037DA",
            "brightBlack": "#767676",
            "brightBlue": "#3B78FF",
            "brightCyan": "#61D6D6",
            "brightGreen": "#16C60C",
            "brightPurple": "#B4009E",
            "brightRed": "#E74856",
            "brightWhite": "#F2F2F2",
            "brightYellow": "#F9F1A5",
            "cursorColor": "#FFFFFF",
            "cyan": "#3A96DD",
            "foreground": "#CCCCCC",
            "green": "#13A10E",
            "name": "Campbell Powershell",
            "purple": "#881798",
            "red": "#C50F1F",
            "selectionBackground": "#FFFFFF",
            "white": "#CCCCCC",
            "yellow": "#C19C00"
        },
        {
            "background": "#282C34",
            "black": "#282C34",
            "blue": "#61AFEF",
            "brightBlack": "#5A6374",
            "brightBlue": "#61AFEF",
            "brightCyan": "#56B6C2",
            "brightGreen": "#98C379",
            "brightPurple": "#C678DD",
            "brightRed": "#E06C75",
            "brightWhite": "#DCDFE4",
            "brightYellow": "#E5C07B",
            "cursorColor": "#FFFFFF",
            "cyan": "#56B6C2",
            "foreground": "#DCDFE4",
            "green": "#98C379",
            "name": "One Half Dark",
            "purple": "#C678DD",
            "red": "#E06C75",
            "selectionBackground": "#FFFFFF",
            "white": "#DCDFE4",
            "yellow": "#E5C07B"
        },
        {
            "background": "#FAFAFA",
            "black": "#383A42",
            "blue": "#0184BC",
            "brightBlack": "#4F525D",
            "brightBlue": "#61AFEF",
            "brightCyan": "#56B5C1",
            "brightGreen": "#98C379",
            "brightPurple": "#C577DD",
            "brightRed": "#DF6C75",
            "brightWhite": "#FFFFFF",
            "brightYellow": "#E4C07A",
            "cursorColor": "#4F525D",
            "cyan": "#0997B3",
            "foreground": "#383A42",
            "green": "#50A14F",
            "name": "One Half Light",
            "purple": "#A626A4",
            "red": "#E45649",
            "selectionBackground": "#FFFFFF",
            "white": "#FAFAFA",
            "yellow": "#C18301"
        },
        {
            "background": "#002B36",
            "black": "#002B36",
            "blue": "#268BD2",
            "brightBlack": "#073642",
            "brightBlue": "#839496",
            "brightCyan": "#93A1A1",
            "brightGreen": "#586E75",
            "brightPurple": "#6C71C4",
            "brightRed": "#CB4B16",
            "brightWhite": "#FDF6E3",
            "brightYellow": "#657B83",
            "cursorColor": "#FFFFFF",
            "cyan": "#2AA198",
            "foreground": "#839496",
            "green": "#859900",
            "name": "Solarized Dark",
            "purple": "#D33682",
            "red": "#DC322F",
            "selectionBackground": "#FFFFFF",
            "white": "#EEE8D5",
            "yellow": "#B58900"
        },
        {
            "background": "#FDF6E3",
            "black": "#002B36",
            "blue": "#268BD2",
            "brightBlack": "#073642",
            "brightBlue": "#839496",
            "brightCyan": "#93A1A1",
            "brightGreen": "#586E75",
            "brightPurple": "#6C71C4",
            "brightRed": "#CB4B16",
            "brightWhite": "#FDF6E3",
            "brightYellow": "#657B83",
            "cursorColor": "#002B36",
            "cyan": "#2AA198",
            "foreground": "#657B83",
            "green": "#859900",
            "name": "Solarized Light",
            "purple": "#D33682",
            "red": "#DC322F",
            "selectionBackground": "#FFFFFF",
            "white": "#EEE8D5",
            "yellow": "#B58900"
        },
        {
            "background": "#000000",
            "black": "#000000",
            "blue": "#3465A4",
            "brightBlack": "#555753",
            "brightBlue": "#729FCF",
            "brightCyan": "#34E2E2",
            "brightGreen": "#8AE234",
            "brightPurple": "#AD7FA8",
            "brightRed": "#EF2929",
            "brightWhite": "#EEEEEC",
            "brightYellow": "#FCE94F",
            "cursorColor": "#FFFFFF",
            "cyan": "#06989A",
            "foreground": "#D3D7CF",
            "green": "#4E9A06",
            "name": "Tango Dark",
            "purple": "#75507B",
            "red": "#CC0000",
            "selectionBackground": "#FFFFFF",
            "white": "#D3D7CF",
            "yellow": "#C4A000"
        },
        {
            "background": "#FFFFFF",
            "black": "#000000",
            "blue": "#3465A4",
            "brightBlack": "#555753",
            "brightBlue": "#729FCF",
            "brightCyan": "#34E2E2",
            "brightGreen": "#8AE234",
            "brightPurple": "#AD7FA8",
            "brightRed": "#EF2929",
            "brightWhite": "#EEEEEC",
            "brightYellow": "#FCE94F",
            "cursorColor": "#000000",
            "cyan": "#06989A",
            "foreground": "#555753",
            "green": "#4E9A06",
            "name": "Tango Light",
            "purple": "#75507B",
            "red": "#CC0000",
            "selectionBackground": "#FFFFFF",
            "white": "#D3D7CF",
            "yellow": "#C4A000"
        },
        {
            "background": "#000000",
            "black": "#000000",
            "blue": "#000080",
            "brightBlack": "#808080",
            "brightBlue": "#0000FF",
            "brightCyan": "#00FFFF",
            "brightGreen": "#00FF00",
            "brightPurple": "#FF00FF",
            "brightRed": "#FF0000",
            "brightWhite": "#FFFFFF",
            "brightYellow": "#FFFF00",
            "cursorColor": "#FFFFFF",
            "cyan": "#008080",
            "foreground": "#C0C0C0",
            "green": "#008000",
            "name": "Vintage",
            "purple": "#800080",
            "red": "#800000",
            "selectionBackground": "#FFFFFF",
            "white": "#C0C0C0",
            "yellow": "#808000"
        },
        {
            "background": "#332A57",
            "black": "#000000",
            "blue": "#00BFFF",
            "brightBlack": "#000000",
            "brightBlue": "#1BCCFD",
            "brightCyan": "#99D6FC",
            "brightGreen": "#21F6BC",
            "brightPurple": "#E6AEFE",
            "brightRed": "#FF8AA4",
            "brightWhite": "#FFFFFF",
            "brightYellow": "#FFF787",
            "cursorColor": "#FFFFFF",
            "cyan": "#86CBFE",
            "foreground": "#E5E5E5",
            "green": "#00FBAC",
            "name": "cyberpunk",
            "purple": "#DF95FF",
            "red": "#FF7092",
            "selectionBackground": "#FFFFFF",
            "white": "#FFFFFF",
            "yellow": "#FFFA6A"
        }
    ]
}
```