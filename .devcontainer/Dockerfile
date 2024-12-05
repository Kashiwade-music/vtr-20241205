# Ubuntu 22.04をベースに使用
FROM ubuntu:22.04

# パッケージリストの更新と必要なパッケージのインストール
RUN apt-get update && \
    apt-get install -y sudo \
    && apt-get install -y curl wget git zsh python3-pip build-essential \
    && apt-get clean

# kashiwadeユーザーの作成
RUN useradd -m -s /bin/bash kashiwade && \
    echo "kashiwade:password" | chpasswd && \
    usermod -aG sudo kashiwade

# sudoersファイルの設定を行い、パスワードなしでsudoを許可
RUN echo "kashiwade ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/kashiwade

# 作業ディレクトリの設定
WORKDIR /home/kashiwade

# ボリュームをマウントするディレクトリを作成
RUN mkdir /home/kashiwade/mount

# zshの設定
RUN chsh -s /bin/zsh

# ユーザーの切り替え
USER kashiwade

# ユーザーのホームディレクトリに移動
WORKDIR /home/kashiwade

# powerlevel10kのインストール
RUN git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ~/powerlevel10k
RUN echo 'source ~/powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc

# uv
RUN curl -LsSf https://astral.sh/uv/install.sh | sh