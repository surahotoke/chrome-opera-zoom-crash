# 💥 CSS `zoom` プロパティによるブラウザの強制終了 (Chrome / Opera)

特定の `input` 要素に対して `zoom` プロパティを一定値以上に設定すると、ブラウザが **100%の再現性でクラッシュ（強制終了）** する現象を実演するリポジトリです。

## 🔗 デモページ
https://surahotoke.github.io/chrome-opera-zoom-crash

## ⚠️ 対象ブラウザ
- **Google Chrome** (クラッシュを確認)
- **Opera** (クラッシュを確認)

### 🚀 影響を受けないブラウザ
以下のブラウザでは正常に動作し、クラッシュは発生しません。
- **Microsoft Edge** (Chromium-based, but stable)
- **Firefox** (Gecko engine)
- **Safari** (WebKit engine)

## 🧐 技術的詳細
このクラッシュは、特定の `input` タイプにおいて `zoom` の値がある閾値を超えた状態で、**その要素をクリック（フォーカス）した瞬間に発生します。**

デモページでは、各タイプにつき2つの要素を配置しています。1つ目は操作しても正常ですが、2つ目の要素をクリックすると即座にブラウザが強制終了します。

`scale` や `position` などの他のプロパティはレイアウト調整のために記述していますが、検証の結果、**クラッシュの直接的な原因は `zoom` プロパティの値**にあることが分かっています。

| inputのタイプ | 正常に動作する値 | **クラッシュする値 (閾値)** |
| :--- | :--- | :--- |
| `datetime-local` | 75 | **76以上** |
| `week` | 84 | **85以上** |
| `date` | 93 | **94以上** |
| `color` | 95 | **96以上** |
| `month` | 112 | **113以上** |
| `time` | 133 | **134以上** |

## 発見の経緯
まったくの偶然により発見されました。

---

# 💥 Consistent Crash on Chrome & Opera via CSS `zoom`

This repository demonstrates a **100% reproducible crash** in certain Chromium-based browsers when applying specific `zoom` property values to various `input` elements.

## 🔗 Live Demo
https://surahotoke.github.io/chrome-opera-zoom-crash

## ⚠️ Affected Browsers
- **Google Chrome** (Confirmed Crash)
- **Opera** (Confirmed Crash)

### 🚀 Not Affected
The following browsers remain stable and do not crash:
- **Microsoft Edge** (Chromium-based, but stable)
- **Firefox** (Gecko engine)
- **Safari** (WebKit engine)

## 🧐 Technical Summary
The crash is triggered when an `input` element with a `zoom` value exceeding the threshold is **clicked or focused.**

In the live demo, two elements are provided for each type: the first one is safe to interact with, while **clicking the second one triggers an immediate browser crash.**

While other CSS properties (like `scale` or `position`) are included in the code, the **`zoom` value is the primary catalyst** for the crash.

| Input Type | Stable Zoom | **Crash Zoom (Threshold)** |
| :--- | :--- | :--- |
| `datetime-local` | 75 | **76+** |
| `week` | 84 | **85+** |
| `date` | 93 | **94+** |
| `color` | 95 | **96+** |
| `month` | 112 | **113+** |
| `time` | 133 | **134+** |

## How I Found This
Discovered by pure chance.