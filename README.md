# dsh-plugin-index

DSH 官方插件管理（发现区）的社区插件索引源。

## 内容

- `index.json` — 插件市场索引格式 1（由官方 `@deepseek-ai/dsh-plugin-market-generator` 生成并校验）
- `plugins.txt` — 来源清单：从 GitHub `topic:dsh-plugin` 生态中筛选出的、声明了 `dsh.bundle` 的真实插件仓库（655 个）
- `icons/` — 超过内联阈值的插件图标

## 在 DSH 中使用

在「插件 → 发现」添加索引源：

```
git+ssh://git@github.com/Towzai/dsh-plugin-index.git
```

（或在 profile 的 `cordis.patch.yml` 中为 `plugin-market` 行配置 `indexes`。）

## 重建索引

```sh
cd D:\Documents\deepseek-harness
pnpm --filter @deepseek-ai/dsh-plugin-market-generator start \
  --input <本仓库>/plugins.txt --output <本仓库>/index.json \
  --title "DSH 社区插件索引" --concurrency 16
```

生成器带增量缓存（`.plugin-market-cache/`，不入本仓库），重复运行只读取变化的仓库。
