# Cyclist's Rings

Runner's Ringsの自転車版。ロードバイク・ママチャリのGPX取り込み、地図表示、端末内記録保存に対応する初期版。

希望公開先: https://cycle.runnersrings.com/

## 公開設定

Settings → Pages → Deploy from a branch → main / (root) → Save。
Custom domainをcycle.runnersrings.comに設定（CNAMEファイルにも記載）。
その後、Cloudflare DNSにCNAME / cycle / atsuoebara.github.ioを追加。
プロキシはDNSのみ（灰色の雲）、TTLは自動。本体やメールの既存レコードは変更しない。
DNS確認後、GitHub PagesのEnforce HTTPSを有効にする。

## 保存と対応範囲

記録は専用localStorage cyclists-rings:rides:v1に保存。ランニングのSupabaseには接続しない。
以前のhttps://runnersrings.com/cycle/からの移行はバックアップ書き出し・復元で行う。
Journalはhttps://runnersrings.com/journal/を共用。
クラウド同期・Strava連携・レインボー・タイムラプスは未実装。

## 検証

node --check core.js
node --check app.js
node core.test.cjs

元の公開版でGPX取り込み・再読み込み後の保存・絞り込み・バックアップ書き出し・スマートフォン幅を確認。
独立ドメインでの動作確認はPagesとDNS設定後に実施。
