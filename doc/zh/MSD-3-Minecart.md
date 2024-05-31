# Minecart 标准草案 3 - 矿车规范

## 矿车

英文名：`minecart`

矿车实质是整个mod管理流程的抽象框架。

### 矿车文件

矿车文件通常以 `minecart.json` 的形式存储在游戏根目录。

```json5
{
  "game": { // 游戏信息
    "name" : "example-game", // 游戏的名称
    "version": "1.0.0", // 游戏的版本
    "launch": "Launcher.exe" // 启动游戏的程序
  },
  "furnace": "minecart-minecraft.exe", // 高炉程序
  "mine": [ // 矿山列表
    "https://example.com/mine.json", // 矿山基址
  ],
  "manifest": { // 原矿/矿脉清单
    "example-mod": "^1.0.0",
    "private-mod": {
      "url": "private-mod.json"
    }
  }
}
```

### 矿车锁

矿车锁通常以 `minecart.lock` 的形式存储在游戏根目录。

```json5
{
  "game": { // 游戏信息
    "name" : "example-game", // 游戏的名称
    "version": "1.0.0", // 游戏的版本
    "launch": "Launcher.exe" // 启动游戏的程序
  },
  "furnace": "minecart-minecraft.exe", // 高炉程序
  "manifest": [ // 按安装顺序排列的原矿/矿脉清单
    {
      "name": "example-mod",
      "version": "1.0.0",
      "url": "https://example.com/exmaple-mod.jar",
      "meta": {},
    },
    {
      "name": "private-mod",
      "version": "1.0.0",
      "url": "file://D:/private-mod.jar",
      "meta": {},
    }
  ]
}
```

