# python:slim との違いは、 curl 等の基本的なツールが入っていることやデフォルトのユーザが非 root であることなどが挙げられる。
# 通常のローカル環境としてはこちらが便利そう。
FROM mcr.microsoft.com/devcontainers/python:3.10

USER vscode

# uv をインストール
RUN curl -LsSf https://astral.sh/uv/install.sh | sh
