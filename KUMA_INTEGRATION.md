# KUMA KINGDOM 連携情報（blackjack-app）

## アプリ情報

| 項目 | 値 |
|------|-----|
| appId | `blackjack` |
| アプリ名 | ブラックジャック |
| URL | https://tsuhira.github.io/blackjack-app/ |
| 説明 | チップを賭けてディーラーに挑もう |

---

## 認証連携

- KUMA KINGDOM のホーム画面（アプリハブ）からリンクをタップすると、`?kumaToken=...` 付きで開く
- Firebase Auth（カスタムトークン）でサインイン後、Firestore に累積スタッツを保存する
- kumaToken なし（直接アクセス）でも通常プレイ可能（スタッツ保存はスキップ）

---

## Firestore スタッツ（`apps/blackjack/users/{uid}/stats`）

| フィールド | 型 | 説明 |
|-----------|-----|------|
| `totalGames` | number | 総プレイ数 |
| `wins` | number | 勝利数 |
| `losses` | number | 敗北数 |
| `pushes` | number | 引き分け数 |
| `blackjacks` | number | ブラックジャック数 |
| `totalChipsWon` | number | 総獲得チップ |
| `totalChipsLost` | number | 総損失チップ |
| `netChips` | number | 純損益チップ |
| `currentBalance` | number | 直近セッション終了時のチップ残高（次回引き継ぎ） |
| `lastPlayedAt` | timestamp | 最終プレイ日時 |

---

連携全体仕様 → kuma-app の `docs/integration.md`
