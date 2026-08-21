# Nextcloud 資源總站（教學 · 銷售 · 提示詞 · Skill）

Nextcloud 自架雲端的四本手冊集中地，繁體中文靜態網站：

| 分類 | 頁面 | 給誰 | 下載 |
|---|---|---|---|
| **入住教學** | [`tutorial.html`](https://nextcloud-guide.woowtech.io/tutorial.html) ＋ 22 章＋3 附錄 | 用戶 | 整站 zip（GitHub archive） |
| **銷售手冊** | [`sales.html`](https://nextcloud-guide.woowtech.io/sales.html) | 客戶與經銷商 | 自包含單檔 HTML |
| **API/WebDAV 提示詞庫** | [`prompts.html`](https://nextcloud-guide.woowtech.io/prompts.html) | 用戶（40+ 條可複製） | 自包含單檔 HTML |
| **Skill 手冊** | [`skills.html`](https://nextcloud-guide.woowtech.io/skills.html) | 進階用戶（型錄＋速查） | 自包含單檔 HTML |

四類共用一個對外入口 [`index.html`（資源總覽）](https://nextcloud-guide.woowtech.io/)。

- **讀者**：會用手機與網頁、不需會架伺服器的家庭用戶
- **語言**：繁體中文（台灣用語）
- **授權**：CC BY 4.0

## 部署

GitHub Pages ＋ 自訂網域：**https://nextcloud-guide.woowtech.io/**（DNS 為 Cloudflare 上的 CNAME → `woowtech.github.io`，proxied）

## 站內結構（hub 模式）

```
index.html          資源總覽 hub    ← 人手維護，build_nav 不碰
tutorial.html       教學目錄        ← build_nav 產生（chapters.json 的 hub.catalog）
ch*.html / appendix_*  教學內容頁   ← head/側欄/pager/footer 由 build_nav 產生
sales.html          銷售手冊        ← 自包含單檔（自帶樣式與圖示，可直接下載）
prompts.html        API/WebDAV 提示詞庫 ← 自包含單檔，同上
skills.html         Skill 手冊      ← 自包含單檔，同上
chapters.json       單一來源        ← 章節順序/文案/SEO + hub 設定（catalog、pages）
```

## 本地開發

```bash
node scripts/build_nav.js --check
node scripts/check_links.js
node scripts/build_nav.js
```

所有 `<head>`、側欄、pager、footer、教學目錄卡片、`sitemap.xml` 由 `scripts/build_nav.js` 產生（`index.html` 與三本單檔手冊除外）。新章節寫作規範見 [`STYLE.md`](STYLE.md)。

## 授權與致謝

《Nextcloud 自架雲端指南》與三本分冊由 [WoowTech](https://github.com/WOOWTECH) 製作，以 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.zh-hant) 授權釋出。截圖取自 Nextcloud 官方介面。Nextcloud 為其權利人的商標，本站與其無隸屬關係。
