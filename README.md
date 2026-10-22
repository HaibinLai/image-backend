# Haibin Blog Image Backend

这个仓库存放 [Haibin's Blog](https://haibinlai.github.io/haibinblog/) 的文章缩略图。

## 目录规范

图片按文章的发布年月分组，并使用文章 slug 作为文件名：

```text
YYYY-MM/<slug>.webp
```

例如：

```text
2026-09/ting-tianyin-xu-lao-shi-de-bo-ke.webp
```

## 访问地址

文件推送到 `main` 分支后，可通过以下 Raw URL 访问：

```text
https://raw.githubusercontent.com/HaibinLai/image-backend/main/YYYY-MM/<slug>.webp
```

例如：

```text
https://raw.githubusercontent.com/HaibinLai/image-backend/main/2026-09/ting-tianyin-xu-lao-shi-de-bo-ke.webp
```

## 生成与更新

图片由 `haibinblog/scripts/sync_thumbnails.py` 生成和同步。脚本会根据文章的 `publishedAt` 与 slug 确定目标路径，并将图片统一转换为 WebP。

`manifest.json` 记录每篇文章的来源、目标路径、输入指纹与文件哈希，供脚本在后续运行中校验并复用未变化的图片。

**请勿手工重命名、移动或覆盖图片文件。** 路径会被博客文章的 frontmatter 直接引用，手工改名会导致线上图片失效。
