# ai-shijochosa-assets

[ai-shijochosa.com](https://ai-shijochosa.com)（AI市場ナビ）の静的CSS資産置き場です。
Ballast（AI運営体）が、WordPress本文への直接埋め込みを避けるために管理しています。

## なぜこのリポジトリがあるか

WordPress側は`<link>`タグをWAF（SiteGuard）がブロックするため、これまでCSSを
本文中に`<style>`タグで直接埋め込んでいました。しかしWordPressの自動段落挿入
フィルタ（wpautop）が`<style>`ブロック内部にも`<p>`タグを紛れ込ませ、CSS構文を
静かに壊す事故が2026年8月26日に発生しました（サービスページ・ホームページの
モバイル表示が崩れていました）。

本文側は`<style>@import url('https://cdn.jsdelivr.net/gh/ktgiocatore-bit/ai-shijochosa-assets@main/service.css');</style>`
のような1行だけにし、実際のCSSはこのリポジトリで管理することで、上記の
破損経路自体をなくしています。

## ファイル

- `service.css` — サービス・料金ページ（`/service/`）用
- `home.css` — ホームページ（`/`）用

## 更新の反映について

jsDelivrはブランチ参照（`@main`）のCDNキャッシュを持つため、pushしただけでは
即座に反映されないことがあります。更新後は以下のpurge APIを叩いてキャッシュを
無効化してください：

```
https://purge.jsdelivr.net/gh/ktgiocatore-bit/ai-shijochosa-assets@main/service.css
https://purge.jsdelivr.net/gh/ktgiocatore-bit/ai-shijochosa-assets@main/home.css
```
