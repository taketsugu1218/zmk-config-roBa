# roBa キーマップ構成

## 基本情報

- **キーボード**: roBa (左右分割キーボード)
- **MCU**: Seeeduino XIAO BLE
- **トラックボール**: PMW3610 (右手側)
- **ファームウェア**: ZMK (v0.3-branch)
- **長押し判定**: 120ms (全hold-tap共通、balanced flavor)

---

## レイヤー一覧

| Layer | 名前 | 用途 | 入り方 |
|-------|------|------|--------|
| 0 | Base | Mac用の通常レイヤー | ベース |
| 1 | Windows | Windows用オーバーレイ (Ctrl/Cmdの入れ替え等) | L6でtog |
| 2 | NUM+FN | テンキー + ファンクションキー | Space/L 長押し |
| 3 | NAV+SYM | 矢印・ナビゲーション + 記号 | 無変換/Enter 長押し |
| 4 | Mouse | マウスボタン (automouseで自動切替) | トラックボール移動で自動 |
| 5 | Scroll | トラックボールスクロールモード | I 長押し |
| 6 | System | Bluetooth設定 + RHOモード入口 | 変換/Del 長押し |
| 7 | RHO_MAC | 右手のみモード (Mac) | L6からHポジション |
| 8 | RHO_WIN | 右手のみモード (Windows) | L6からJポジション |

---

## トラックボール設定

- **automouse-layer**: Layer 4 (トラックボール動かすと自動でMOUSEレイヤーに切替)
- **scroll-layers**: Layer 2, 5 (これらのレイヤーではトラックボールがスクロールになる)

---

## Layer 0: Base (Mac)

### 長押し動作

| キー | タップ | 長押し (120ms) |
|------|--------|----------------|
| Z | Z | Left Shift |
| I | I | mo Layer 5 (SCROLL) |
| L | L | mo Layer 2 (NUM+FN) |
| 変換 | 変換 (INT_HENKAN) | mo Layer 6 (System) |
| Space | Space | mo Layer 2 (NUM+FN) |
| 無変換 | 無変換 (INT_MUHENKAN) | mo Layer 3 (NAV+SYM) |
| Enter | Enter | mo Layer 3 (NAV+SYM) |
| Del | Del | mo Layer 6 (System) |

### キー配置

| | Col1 | Col2 | Col3 | Col4 | Col5 | 端列 | | 端列 | Col1 | Col2 | Col3 | Col4 | Col5 |
|-|------|------|------|------|------|------|-|------|------|------|------|------|------|
|R0| Q | W | E | R | T | | | | Y | U | I(L5) | O | P |
|R1| A | S | D | F | G | Cmd+Sh+S | | : | H | J | K | L(L2) | SQT |
|R2| Z(Sh) | X | C | V | B | Tab | | - | N | M | , | . | / |
|R3| Ctrl | Cmd | Alt | 変換(L6) | Space(L2) | 無変換(L3) | | BS | Enter(L3) | | | | Del(L6) |

**ロータリーエンコーダ**: PG_UP / PG_DOWN

---

## Layer 1: Windows (オーバーレイ)

Layer 0 の上に重なる透過レイヤー。以下のキーのみ変更:

| キー位置 | Layer 0 | Layer 1 (Windows) |
|----------|---------|-------------------|
| 左下1 | Ctrl | Cmd (=Win) |
| 左下2 | Cmd | Ctrl |
| 左端列 Row1 | Cmd+Shift+S | Ctrl+Shift+S |

**切替方法**: Layer 6 で Q位置のキーを押す (tog 1)

---

## Layer 2: NUM+FN

Space長押し or L長押しで一時的に有効。トラックボールはスクロール動作。

**左手: テンキー / 右手: ファンクションキー**

| | Col1 | Col2 | Col3 | Col4 | Col5 | 端列 | | 端列 | Col1 | Col2 | Col3 | Col4 | Col5 |
|-|------|------|------|------|------|------|-|------|------|------|------|------|------|
|R0| + | 7 | 8 | 9 | - | | | | F1 | F2 | F3 | F4 | F5 |
|R1| / | 4 | 5 | 6 | * | Ctrl+Alt+0 | | F13 | F6 | F7 | F8 | F9 | F10 |
|R2| 0(Sh) | 1 | 2 | 3 | . | = | | | | | | | F11 |
|R3| | | | | | | | | | | | | F12 |

---

## Layer 3: NAV+SYM

無変換長押し or Enter長押しで一時的に有効。

**左手: ナビゲーション / 右手: 記号**

| | Col1 | Col2 | Col3 | Col4 | Col5 | 端列 | | 端列 | Col1 | Col2 | Col3 | Col4 | Col5 |
|-|------|------|------|------|------|------|-|------|------|------|------|------|------|
|R0| ESC | Ctrl+Sh+Tab | Up | Ctrl+Tab | | | | | ^ | & | ~ | ( | ) |
|R1| Home | Left | Down | Right | End | | | _ | ! | @ | # | $ | % |
|R2| Shift | Cmd+Sh+Left | | Cmd+Sh+Right | | | | | [ | ] | { | } | \ |
|R3| | | | | | | | | | | | | \| |

**ロータリーエンコーダ**: Ctrl+PG_UP / Ctrl+PG_DOWN (タブ切替)

---

## Layer 4: Mouse (automouse)

トラックボールを動かすと自動で有効化。
右手中段: MB1 (左) / MB3 (中) / MB2 (右)

---

## Layer 5: Scroll

I長押しで一時的に有効。トラックボールがスクロール動作に切り替わる。
全キー透過 (trans)。

---

## Layer 6: System

変換キー長押し or Delキー長押しで一時的に有効。

| 機能 | キー位置 |
|------|----------|
| tog 1 (Mac/Win切替) | Q位置 (左手) |
| to 7 (RHO_MAC) | H位置 (右手) |
| to 8 (RHO_WIN) | J位置 (右手) |
| BT_SEL 0-4 | 右手 Row0 (Y-P位置) |
| bootloader | 右手左端列 Row2 |
| BT CLR | 右手 Row2 右端 |
| BT CLR ALL | 右手 Row3 右端 |

**右手のみでRHOに入る方法**: Del長押し -> H or Jポジション

---

## Layer 7: RHO_MAC (右手のみ・Mac)

右手のみで操作するモード。マウス+基本ショートカット。
左手キーは全て無効 (none)。トラックボールはスクロール動作。

**入り方**: Layer 6 -> Hポジション (to 7)
**戻り方**: 右端列の2箇所 (to 0)

| 端列 | Col1 | Col2 | Col3 | Col4 | Col5 |
|------|------|------|------|------|------|
| | ESC | Cmd+Z | Ctrl+Up | Cmd+Tab | Cmd+W |
| MB1 | Cmd+A | Ctrl+Left | Ctrl+Down | Ctrl+Right | Cmd+S |
| MB2 | Enter | Space | Cmd+C | Cmd+V | ->L0 |
| | BS | Del | | | ->L0 |

---

## Layer 8: RHO_WIN (右手のみ・Windows)

Layer 7 と同じ構成だが Cmd->Ctrl、Cmd+Tab->Alt+Tab に変更。
トラックボールはスクロール動作。

**入り方**: Layer 6 -> Jポジション (to 8)
**戻り方**: 右端列の2箇所 (to_win_base = L0に戻り + tog 1でWindows維持)

| 端列 | Col1 | Col2 | Col3 | Col4 | Col5 |
|------|------|------|------|------|------|
| | ESC | Ctrl+Z | Ctrl+Up | Alt+Tab | Ctrl+W |
| MB1 | Ctrl+A | Ctrl+Left | Ctrl+Down | Ctrl+Right | Ctrl+S |
| MB2 | Enter | Space | Ctrl+C | Ctrl+V | ->Win |
| | BS | Del | | | ->Win |

---

## レイヤー遷移まとめ

```
              +-------------+
      +------>|  Layer 0    |<--------------------+
      |       |   (Base)    |                     |
      |       +--+--+--+---+                      |
      |          |  |  |                          |
      |  tog 1   |  |  |                          | to 0 / to_win_base
      |  +-------+  |  |                          |
      |  v          |  |                          |
      | Layer 1     |  |                          |
      | (WINDOWS)   |  |                          |
      |             |  |                          |
      |  Space/L    | 無変換/Enter  変換/Del       |
      |  長押し     |  長押し        長押し        |
      |  +----------+  +------+  +----------+     |
      |  v                    v  v          |     |
      | Layer 2            Layer 3    Layer 6|     |
      | (NUM+FN)           (NAV+SYM)  (System)    |
      |                                |    |     |
      |  I長押し              H位置  J位置    |     |
      |  +-----+             +----+ +---+   |     |
      |  v     |             v    v         |     |
      | Layer 5|          Layer 7  Layer 8  |     |
      |(SCROLL)|          (RHO    (RHO      |     |
      |        |           MAC)    WIN)-----+-----+
      +--------+

  ※ Layer 4 (MOUSE) はトラックボール操作で自動切替
  ※ mo = 長押し中のみ有効、tog = ON/OFF切替、to = 完全切替
```
