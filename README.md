# Yunxi Wang 作品集 · GitHub Pages 部署版

这是独立静态网站，无需 npm、构建命令或自己的服务器。
包含当前英文首页、中文页面、项目详情、插画、视频和游戏试玩。

## 首次部署（推荐 GitHub Desktop）

1. 在 GitHub 创建一个公开仓库，例如 `yunxi-portfolio`，默认分支使用 `main`。
2. 使用 GitHub Desktop 克隆仓库到电脑上的新文件夹。
3. 把本部署文件夹**里面的全部内容**复制到仓库根目录，包含 `.github`、`.nojekyll` 和各个资源文件夹。不要把外层 `github-pages` 文件夹一起套进去。
4. 在 GitHub Desktop 中 Commit，再 Push origin。
5. 在 GitHub 仓库打开 Settings → Pages → Build and deployment → Source，选择 **GitHub Actions**。
6. 打开 Actions → Deploy portfolio to GitHub Pages。如果首次推送时 Pages 尚未开启导致失败，点击 Run workflow 重新执行。
7. 成功后在 Settings → Pages 或 workflow 的 github-pages 环境中打开网站。

普通仓库地址为 `https://你的用户名.github.io/yunxi-portfolio/`。
如仓库名是 `你的用户名.github.io`，网站地址则没有仓库名后缀。
链接使用相对路径，可以放在仓库子路径下。无需填写域名或购买服务器。

也可以不使用 Actions：将 Pages 的 Source 设为 Deploy from a branch，选择 main 和 /(root)，保存即可。根目录的 `.nojekyll` 会禁用 Jekyll。

## 文件较大时

请用 GitHub Desktop/Git 上传完整仓库。游戏资源存在超过网页上传限制的文件，不适合通过 GitHub 网页逐个上传。部署版所有文件均小于 100 MiB，无需 Git LFS。不要将整个 ZIP 当作网站文件上传。

## 视频与游戏

- 首页视频保留点击播放和 `preload="none"`，不自动播放。
- Bring the Spring 已使用完整本地 trailer 和新封面。
- EnlightenThem 已使用新封面，只有其视频说明靠右对齐。
- Inbetween 的 `.br` 构建资源已转换为普通 `.data`、`.js`、`.wasm` 文件，并修改播放器路径，不依赖自定义响应头；部署副本的资源体积会略有增加。
- Bring the Spring 原有 `.unityweb` 解压回退版本保持原样。
- 游戏实际运行效果仍需在部署后浏览器中确认；本次没有执行游戏运行测试。

## 更新网站

修改这个仓库中的网页/资源，Commit 并 Push 到 main，会自动部署。
如果继续修改原始项目，需要在原始项目根目录执行 `node scripts/package-github-pages.cjs`，再将生成的 github-pages 文件夹内容同步到 GitHub 仓库。
不要用原项目的 Inbetween `.br` 文件覆盖部署版已转换的资源。

## 本地预览

在此部署目录运行 `python -m http.server 8766 --bind 127.0.0.1`，访问 http://127.0.0.1:8766/。

## 打包范围

不包含本地备份、日志、设计过程截图、素材生成提示词或作者脚本。原始开发项目不受影响。
本地打包不等于发布；只有将这些文件推送至你自己的 GitHub 仓库并启用 Pages 后，网站才会上线。

参考：https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
