# 100kinSAT Advance Spresense

100kinSAT 向け Spresense SDK リポジトリです。

## セットアップ

### 1. ツールのインストール

[Spresense SDK セットアップガイド](https://developer.spresense.sony-semicon.com/development-guides/?page=sdk_set_up&lang=ja) の手順に従ってツールをインストールしてください。

```bash
wget https://raw.githubusercontent.com/sonydevworld/spresense/master/install-tools.sh
bash install-tools.sh
source ~/spresenseenv/setup
```

### 2. リポジトリのクローン

公式の Spresense リポジトリではなく、このリポジトリをクローンしてください。

```bash
git clone --recursive https://github.com/100kinsat/100kinSAT_advance_spresense.git
cd 100kinSAT_advance_spresense
```

すでにクローン済みの場合はサブモジュールを更新してください。

```bash
git pull
git submodule update
```

## 100kinsat/hello のビルドと書き込み

### ビルド

```bash
cd sdk
make distclean
tools/config.py 100kinsat/hello
make
```

`sdk/` フォルダに `nuttx.spk` が生成されます。

### ボードへの書き込み

[ボードへの書き込み方法](https://developer.spresense.sony-semicon.com/development-guides/?page=sdk_set_up&lang=ja#_%E3%83%9C%E3%83%BC%E3%83%89%E3%81%B8%E3%81%AE%E6%9B%B8%E3%81%8D%E8%BE%BC%E3%81%BF%E6%96%B9%E6%B3%95) に従って書き込んでください。

```bash
tools/flash.sh -c /dev/ttyUSB0 nuttx.spk
```

書き込み後、シリアルコンソールで `hello` コマンドを実行すると `Hello, 100kinSAT!!` と表示されます。

## リポジトリ構成

```
100kinSAT_advance_spresense
|-- nuttx        - NuttX カーネル (Spresense ポート)
|-- sdk
|   |-- apps     - NuttX アプリケーション (100kinsat カテゴリを追加)
|   `-- configs  - ビルド設定
|       `-- 100kinsat
|           `-- hello  - 100kinsat/hello 用設定
`-- externals
```
