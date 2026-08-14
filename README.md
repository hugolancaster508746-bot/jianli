# 简历网站 · 更新速查

固定网址：**https://hugolancaster508746-bot.github.io/jianli/**

这个网址绑定的是仓库，改多少次、推多少次都不变。改完内容 `git push` 后，等 30 秒~2 分钟刷新即可看到更新。

---

## 一、改内容

需要改的东西 → 直接编辑 `jianli-site/` 目录下的对应文件：

| 想改的东西 | 改哪个文件 |
|---|---|
| 简历文字 / 排版 | `index.html` |
| 真人头像 | 放一张 `avatar.png` 到本目录根（替换占位） |
| 证书图 | 更新 `zhengshu/` 里的图片 |
| 扫码分享卡 | 见「三、重新生成扫码卡」 |

> 注意：真正上线的是 `jianli-site/index.html` 这份，不是 `Documents/简历夹/jianli.html`。以后只改 `jianli-site/` 里的。

---

## 二、推上去（免密，走 SSH）

在本机打开终端，执行：

```bash
cd "C:/Users/16803/WorkBuddy/2026-08-14-10-03-02/jianli-site"
git add -A
git commit -m "更新简历"
git push
```

`git push` 走 SSH 免密（密钥已配好，不用再填 token）。
push 后等 30 秒~2 分钟，刷新上面的固定网址就是新内容。

---

## 三、重新生成扫码卡

扫码卡由 `gen_jianli_qr_card.py` 生成（在 WorkBuddy 项目根目录），二维码指向上面的固定网址。

```bash
# 默认用内置占位头像生成
python gen_jianli_qr_card.py

# 换成指定头像（如微信头像）
python gen_jianli_qr_card.py "头像图片路径.jpg"
```

生成后文件是 `jianli-qr-card.png`，要更新到网站就把它复制到 `jianli-site/` 再走「二」的 push 流程。

---

## 四、SSH 密钥（已配置，备查）

- 私钥：`C:\Users\16803\.ssh\id_ed25519_jianli`
- 公钥：`C:\Users\16803\.ssh\id_ed25519_jianli.pub`（已添加到 GitHub 账号）
- 配置：`C:\Users\16803\.ssh\config` 指定 GitHub 走此密钥

如果以后换电脑或密钥失效，重新生成一对 ed25519 密钥，把新公钥添加到 GitHub（Settings → SSH and GPG keys）即可。

---

## 五、安全提示

- 早期用过的 `ghp_...` 个人访问令牌已不再需要，建议到 GitHub（Settings → Developer settings → Personal access tokens）把它 Revoke 掉。
- 私钥 `id_ed25519_jianli` 只在你本机，不要外传。
