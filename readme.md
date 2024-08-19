@wymjs/vite-auto-alias
===

> 將 tsconfig.json 的 alias 同步到 vite alias 裡

## 安裝

```shell
# jsonc-parser 為相關依賴
$ pnpm i -D @wymjs/vite-auto-alias jsonc-parser
```

## 使用

tsconfig.json 配置 path 後在 plugins 引入就可以關聯到了，自己用的陽春版差件，所以只匹配 `baseUrl` 為 `.` 的路徑

```json
{
  "compilerOptions": {
    "paths": {
      "@/*": [
        "src/*"
      ]
    }
  }
}
```

```typescript
import { defineConfig } from 'vite'
import { autoAlias } from '@wymjs/vite-auto-alias'

export default () => {
  return defineConfig({
    plugins: [
      // 配置下去就會自動同步 tsconfig.compilerOptions.paths 到 alias 裡
      autoAlias(),
    ],
  })
}
```
