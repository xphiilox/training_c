# Ubuntu + Docker + VS Code で C 言語開発

ソースコードは Mac のこのフォルダに保存されたまま、コンパイルとデバッグは Ubuntu 24.04 コンテナ内で行います。

## 最初に必要なもの

- Docker Desktop（起動しておく）
- Visual Studio Code
- VS Code 拡張機能 `Dev Containers`（ID: `ms-vscode-remote.remote-containers`）

## VS Code で開始する

1. VS Code でこのフォルダを開く。
2. コマンドパレット（`Cmd+Shift+P`）で `Dev Containers: Reopen in Container` を実行する。
3. 初回のコンテナビルドが終わったら `main.c` を開く。
4. 行番号の左をクリックしてブレークポイントを置く。
5. `F5` を押し、`C: debug active file` を選ぶ。

`Cmd+Shift+B` では、現在開いている C ファイルだけをビルドできます。生成物は `build/` に入ります。

## Docker CLI だけで動かす

Docker Desktopを起動してから、このフォルダで実行します。

```bash
docker compose build
docker compose run --rm c-dev bash -lc \
  'mkdir -p build && gcc -std=c17 -Wall -Wextra -Wpedantic -g main.c -o build/main && ./build/main'
```

対話型の Ubuntu シェルを開く場合:

```bash
docker compose run --rm c-dev bash
```

コンテナ内には GCC、GDB、Clang、CMake、Ninja、Valgrind、Git が入っています。
