# Minecart 标准草案 4 - 矿山规范

## 矿山

英文名：`mine`

### 矿山基址

矿山基址提供对矿山基础信息的访问，也是一个矿山的最低级实现。

矿山基址应能提供下列 json 格式的数据：

```json5
{
  "name": "example-mine", // 矿山的名称
  "description": "An example mine.", // 矿山的描述
  "last_update": "2021-01-01T00:00:00Z", // 矿山的最后更新时间
  "dynamic": false, // 是否为静态矿山
  "endpoints": { // 矿山的接口
    "manifest": "https://example.com/manifest.json", // 矿山清单
  },
  "entries": 114 // 矿山中的原矿/矿脉数量，可选提供
}
```

#### `static`

`dynamic` 字段表示矿山是否为动态矿山，静态矿山不提供动态查询接口，动态矿山需要提供。
- 若为静态矿山，`endpoints` 对象中只能包含 `manifest` 字段，值为矿山清单的下载地址。
- 若为动态矿山，`endpoints` 对象的 `manifest` 字段为动态查询接口的基址，其他字段未定义。

### 矿山清单（静态矿山）

静态矿山至少应提供所存储的全部原矿/矿脉的最新版的列表，提供包含旧版的列表是可选的。

```json5
[
  { // 最新版本的 example-mod 是 2.0.0
    "name": "example-mod",
    "version": "2.0.0",
    "description": "An example mod.",
    "url": "https://example.com/example-mod/2.0.0.jar",
    "meta": {},
    "dependencies": {
      "example-lib": "^1.3.0",
    }
  },
  { // 旧版本的 example-mod 是 1.0.0，矿山提供者可选提供。
    "name": "example-mod",
    "version": "1.0.0",
    "description": "An example mod.",
    "url": "https://example.com/example-mod/1.0.0.jar",
    "meta": {},
    "dependencies": {
      "example-lib": "^1.0.0",
    }
  },
  { // 另一个 mod
    "name": "another-mod",
    "version": "1.4.5",
    "description": "Another mod.",
    "url": "https://example.com/another-mod/1.4.5.jar",
    "meta": {},
    "dependencies": {
      "another-lib": "^0.0.5",
    }
  }
]
```

### 矿山清单（动态矿山）

见 [动态矿山规范](./MSD-5-Dynamic-Mine.md)。
