# Minecart 标准草案 5 - 动态矿山规范

## 动态矿山

动态矿山应提供动态查询接口，接口应能提供所存储的全部原矿/矿脉信息。

下方列出了动态矿山需实现的接口（基址已省略）：

### `GET /ore/{name}`

获取指定原矿/矿脉的全部版本信息。

```json
[
  {
    "name": "example-mod",
    "version": "2.0.0",
    "description": "An example mod.",
    "url": "https://example.com/example-mod/2.0.0.jar",
    "meta": {},
    "dependencies": {
      "example-lib": "^1.3.0",
    }
  },
  {
    "name": "example-mod",
    "version": "1.0.0",
    "description": "An example mod.",
    "url": "https://example.com/example-mod/1.0.0.jar",
    "meta": {},
    "dependencies": {
      "example-lib": "^1.0.0",
    }
  }
]
```

### `GET /ore/{name}/{version}`

获取指定原矿/矿脉的指定版本信息。

```json
{
  "name": "example-mod",
  "version": "2.0.0",
  "description": "An example mod.",
  "url": "https://example.com/example-mod/2.0.0.jar",
  "meta": {},
  "dependencies": {
    "example-lib": "^1.3.0",
  }
}
```
