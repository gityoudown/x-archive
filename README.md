# 光影档案 · GitHub Pages 公开展示版

这是可直接推送到 GitHub Pages 的静态站点。

## 内容

- `index.html` + `assets/`：页面本身（相对路径，放在仓库根目录即可）
- `media/_previews/`：68 个低码率预览视频 / 网页版照片（灯箱里播放和显示）
- `media/_thumbs/`：68 张缩略图（列表封面）
- `.nojekyll`：必须保留，否则 Pages 的 Jekyll 会忽略 `_previews`、`_thumbs` 这类下划线开头的目录

总体积约 218 MB，单文件最大 31 MB，在 GitHub 限制内（单文件 100 MB、仓库建议 <1 GB）。

## 与「本机密码版」的差别

| 能力 | 本机版（server.mjs） | 本页 Pages 版 |
|---|---|---|
| 访问密码 | 有（服务端校验） | 无，任何人可打开 |
| 下载原片 | 有（独立下载密码） | 无（原片 4.85 GB 传不上来） |
| 手机加载速度 | 受家庭上行带宽限制 | 走 GitHub CDN，明显更快 |
| 依赖电脑开机 | 是 | 否 |

## 更新内容后重新发布

```powershell
cd 影像作品集网站\frontend
$env:BUILD_TARGET='pages'; $env:VITE_GATE='0'; $env:VITE_DL='0'; $env:VITE_DL_AVAILABLE='0'
npx vite build --outDir ../pages-site --emptyOutDir
# 媒体有变化时再同步一次
robocopy "E:\影像作品集媒体\_previews" "..\pages-site\media\_previews" /E
robocopy "E:\影像作品集媒体\_thumbs"   "..\pages-site\media\_thumbs"   /E
cd ..\pages-site
git add -A; git commit -m "update site"; git push
```
