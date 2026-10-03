# adventure-board-pcb

PicoRubyKaigi 向け RP2350 ボード「adventure-board」の基板設計データです（KiCad 9）。

現在のリビジョン: **V1**（量産版）

## 基板仕様

| 項目 | 値 |
|---|---|
| 外形 | 130 × 90 mm |
| 層数 | 4 層 |
| 板厚 | 1.6 mm |
| 表面処理 | HASL |

## ファイル構成

```
adventure-board.kicad_pro / .kicad_sch / .kicad_pcb   KiCad プロジェクト
fp-lib-table, sym-lib-table                          プロジェクトローカルライブラリ定義
lib/, libs/                                          シンボル・フットプリント（3D モデルは含みません）
docs/adventure-board-schematic.pdf                   回路図 PDF
production/v1/                                       V1（量産版）の製造データ
  adventure-board.zip    ガーバー + ドリル
  bom.csv                BOM（JLCPCB 形式, LCSC 部品番号付き）
  positions.csv          部品配置データ（CPL）
  designators.csv        リファレンス一覧
  netlist.ipc            IPC-D-356 ネットリスト
production/pv1/                                      PV1（量産試作）発注時の製造データ（参考）
```

## リビジョン履歴

| リビジョン | 内容 |
|---|---|
| V1 | 量産版。下側 2 つの取付穴を上側と同じく角から 4.5 mm の位置に変更、シルクの「PV1」表記を削除 |
| PV1 | 量産試作 |

## 再発注手順（JLCPCB）

> 暫定版です。発注オプションは今後見直します。

製造データは KiCad の [Fabrication Toolkit](https://github.com/bennymeg/Fabrication-Toolkit) プラグインで出力したものです。

1. JLCPCB の PCB 注文画面で `production/v1/adventure-board.zip` をアップロードする
2. 層数 4、板厚 1.6 mm、表面処理 HASL を指定する
3. PCB Assembly を有効にし、`production/v1/bom.csv` と `production/v1/positions.csv` をアップロードする
4. 部品の配置・回転をプレビューで確認して発注する

データを再生成する場合は、KiCad 9 で `adventure-board.kicad_pcb` を開き、Fabrication Toolkit で出力してください。

## 3D モデルについて

3D モデル（STEP/WRL）は同梱していません。基板エディタの 3D ビューアで一部部品が表示されませんが、ERC/DRC や製造データの出力には影響しません。

## 第三者由来のデータ

- `libs/RP2350_60QFN_minimal.pretty`: Raspberry Pi RP2350A Minimal Board（RP-006440-DD-2）の設計データ由来のフットプリント
- `lib/easyeda2kicad`, `libs/PicoBoard.*`: LCSC/EasyEDA の部品ライブラリを easyeda2kicad で変換し、必要に応じて修正したもの

## ライセンス

Copyright PicoRubyKaigi 2026.

This source describes Open Hardware and is licensed under the CERN-OHL-P v2.
You may redistribute and modify this documentation and make products using it
under the terms of the CERN-OHL-P v2 (https://cern.ch/cern-ohl).
This documentation is distributed WITHOUT ANY EXPRESS OR IMPLIED WARRANTY,
INCLUDING OF MERCHANTABILITY, SATISFACTORY QUALITY AND FITNESS FOR A
PARTICULAR PURPOSE. Please see the CERN-OHL-P v2 for applicable conditions.

全文は [LICENSE](LICENSE) を参照してください。
