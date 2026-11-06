# Nova 角色库

角色库页面读取这里的 `index.json`，封面和卡文件放在 `cards/`。

## 目录

```
library/
  index.json
  cards/
    daxia-cover.jpg
    daxia-xianzun.json
    daxia-xianzun.png
```

## index.json

```json
{
  "version": 1,
  "name": "Nova 角色库",
  "description": "一句话说明",
  "updatedAt": "2026-11-06",
  "cards": [
    {
      "id": "unique-id",
      "name": "角色名",
      "tagline": "一句话身份",
      "summary": "一两句简介",
      "author": "作者",
      "version": "1.0",
      "tags": ["标签"],
      "license": "授权说明",
      "cover": "cards/cover.jpg",
      "card": "cards/card.png",
      "featured": true
    }
  ]
}
```

- `id` 必须唯一，安装时用它找卡。
- `cover` 是列表封面，建议 3:4 或 2:3，单张控制在 200KB 内。卡文件是 `.json` 时，封面也会被复制成角色头像。
- `card` 支持 `.png` 角色卡（chara/ccv3）或 `.json`。
- `license` 写清楚授权；没有授权的卡不要放进公开仓库。

## 新增一张卡

1. 把 PNG/JSON 放进 `cards/`。
2. 做一张封面，放进 `cards/`。
3. 在 `index.json` 的 `cards` 里加一条。
4. 重启 Nova，角色库页面会读到。

## 从 GitHub 拉取

当前公共仓库：`https://github.com/xlmujian/nova-library`

`src/shared/library.ts` 现在指向 jsDelivr：

```ts
export const LIBRARY_INDEX_URL =
  'https://cdn.jsdelivr.net/gh/xlmujian/nova-library@main/library/index.json'
```

也可以换成 raw 地址；页面会优先拉远程索引，拉不到时回退到随包内置的 `library/`。

```ts
export const LIBRARY_INDEX_URL =
  'https://raw.githubusercontent.com/xlmujian/nova-library/main/library/index.json'
```

重新构建后生效。
