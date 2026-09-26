# UI Kit · 配色系統同 Welcome Page

> 一個 CSS 檔 drop 入任何 project 就用得。來源：LearnHub。

## 👉 睇效果

**https://kelvin0611.github.io/ui-kit/**

Style guide（色板、排版、元件、動效）＋ **Welcome Page 原樣 demo**，就喺同一版。

## 點用

```html
<link rel="stylesheet" href="ui.css">
```

跟住用 CSS 變數，唔使記色值：

```css
.my-thing {
  background: var(--brand-100);
  color:      var(--brand-900);
  box-shadow: 0 0 0 1px var(--line);   /* shadow-as-border */
  transition: background var(--dur-1) ease;
}
```

## 有咩喺入面

| 類別 | Tokens |
|---|---|
| **主色階** | `--brand-50` … `--brand-950`（11 級，`--brand-500 = #51B2D3` 本尊）|
| **中性** | `--ink` `--muted` `--line` `--surface` `--canvas` `--cta` |
| **語意** | `--ok` `--warn` `--danger`（附 `-bg`）|
| **動效** | `--dur-1/2/3`（120/240/480ms）、`--ease-out`、`--ease-in-out` |
| **DNA 四色** | `--base-a/t/c/g`（圖表、分類標記用）|
| **粒子** | `--dot-1/2/3`（背景裝飾）|
| **版面** | `--radius`、`--font`、`--font-mono`、`--rail`、`--sidebar`、`--bp-mobile` |

元件 class：`.btn`（`-primary` / `-dark` / `-ghost` / `-outline`）、`.card`、`.pill`、
`.nav-link`、`.label-mono`、`.slogan`、`.prose`、`.ring` / `.ring-t` / `.ring-b`、
`.fade-up`、`.m` + `.c`（mask reveal，逐個字升上嚟）、`.app-topbar`、`.app-sidebar`。

## 三條唔可以錯嘅規則

**① 白字唔好放 `--brand-500`**
白字喺 `#51B2D3` 上面只有 **2.5:1**，未過 WCAG AA。放 `--brand-700` 有 **4.6:1** ✓。
要淺底就配深字（`--brand-100` 配 `--brand-900`）。

**② 邊框用 shadow，唔用 border**
`box-shadow: 0 0 0 1px var(--line)` —— 唔會撐大版面，亦唔受 `box-sizing` 影響。

**③ `prefers-reduced-motion` 一定要清零 animation-delay**
只縮短 `duration` 唔夠。有 `animation-delay` 嘅元素會令開咗「減少動畫」嘅人
望住空白成分鐘。

## Welcome Page 原樣

`index.html` 最頂就係佢，可以直接抄。要點：

- 出場次序：**字 → 掣 → 圖**（大物件郁得慢啲，所以 DNA 最遲入場）
- 標題用 **mask reveal**（字由 mask 下面升上嚟），**唔加 opacity** —— mask 本身已經遮住
- DNA 係自己寫嘅 canvas 透視投影 + 深度排序，冇用 library
- 改大細／轉速：`ZOOM`、`SPEED` 兩個常數

## 檔案

```
ui.css        ← drop 入 project 嗰個
index.html    ← style guide + welcome page demo
```

## 相容

純 CSS，冇 build step、冇 dependency（除咗 Google Fonts 嘅 Geist／Noto Sans TC）。
`@media (max-width: 767px)` 係手機界線 —— 同 `--bp-mobile` 要一致。
