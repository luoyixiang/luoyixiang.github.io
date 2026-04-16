# 从零部署 Gmeek：一个完全跑在 GitHub 上的博客

> “When I'm six feet under, this will still be running on GitHub's servers rent-free.”

## 为什么选 Gmeek？

我不想买服务器、不想配数据库、不想折腾 WordPress。

我只想写东西，写完就能发，最好还能白嫖。

Gmeek 正好满足：**GitHub Issues 写文章 + GitHub Actions 自动构建 + GitHub Pages 免费托管**。

All in GitHub，一分钱不用花。

## 第1步：创建仓库

登录 GitHub，点击 [Gmeek 模板链接](https://github.com/new?template_name=Gmeek&template_owner=Meekdai)，创建一个新仓库。

**关键点**：仓库名必须是 `你的用户名.github.io`。

比如我的用户名是 `luoyixiang`，仓库名就是 `luoyixiang.github.io`。

> ⚠️ 注意：你登录的账号是谁，Owner 就是谁。如果想用另一个账号的域名，需要切换账号登录。

## 第2步：启用 GitHub Pages

进入仓库的 **Settings → Pages → Build and deployment**，把 Source 改成 **GitHub Actions**。

这一步告诉 GitHub：用 Actions 来自动构建博客，而不是默认的 Jekyll。

## 第3步：写第一篇文章

点击 **Issues → New issue**。

- 标题：文章标题
- 正文：Markdown 格式的内容
- **最重要**：右边 Labels 必须至少添加一个标签（比如“随笔”）

没有标签，Gmeek 不会生成这篇文章。

保存 Issue 后，GitHub Actions 会自动触发构建。等几分钟，访问 `https://你的用户名.github.io` 就能看到了。

## 第4步：个性化配置

仓库根目录下的 `config.json` 是配置文件。

### 基础配置示例

```json
{
    "title": "我的博客",
    "subTitle": "记录学习与思考",
    "avatarUrl": "https://github.com/用户名.png",
    "GMEEK_VERSION": "last"
}
```

### 修改配置后必须手动触发

修改 `config.json` 后，需要去 **Actions → build Gmeek → Run workflow** 手动运行一次，修改才会生效。

> 💡 经验：改配置不生效，先检查是不是没点 Run workflow。

### 其他常用配置

| 配置项 | 说明 |
|--------|------|
| `displayTitle` | 头像旁边显示的名字 |
| `homeUrl` | 博客地址，自定义域名时用 |
| `i18n` | 语言，CN/EN/RU |
| `needComment` | 是否开启评论（需安装 utteranc） |
| `bottomText` | 页脚版权文字 |

## 第5步：关于那个 Node.js 警告

构建日志里偶尔会出现一行提示：

> Node.js 20 actions are deprecated...

这不是错误，**不影响博客运行**。只是提醒未来 GitHub 会升级环境。

想消除也很简单：在 `.github/workflows/build.yml` 的 `build` job 下加一行环境变量：

```yaml
env:
  FORCE_JAVASCRIPT_ACTIONS_TO_NODE24: true
```

加了之后，提示会变成“已强制使用 Node.js 24”，问题解决。不处理也完全没问题。

## 现在的状态

- 博客地址：`https://你的用户名.github.io`
- 写作方式：GitHub Issues + 标签
- 维护成本：零
- 运行费用：零

## 写在最后

这句话是我自己调侃自己用的：

**“I'm mortal. This repo lives rent-free on GitHub forever.”**

我不是什么大人物，写的也不是什么传世经典。但这个博客会像一个安静的幽灵，一直跑在 GitHub 的服务器上。

不占资源，不要钱，也不需要我。

白嫖到地底下。
```