FROM node:24.12.0-bookworm-slim

# 安裝系統語系套件，並設定預設英文語系與支援中文語系
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    vim \
    curl \
    procps \
    locales && \
    echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
    echo "zh_TW.UTF-8 UTF-8" >> /etc/locale.gen && \
    echo "LANG=en_US.UTF-8" > /etc/default/locale && \
    echo "LANGUAGE=en_US:en" >> /etc/default/locale && \
    echo "LC_ALL=en_US.UTF-8" >> /etc/default/locale && \
    locale-gen && \
    rm -rf /var/lib/apt/lists/*

# 安裝系統時區套件(使用 UTC 可註解掉)
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    tzdata && \
    ln -fs /usr/share/zoneinfo/Asia/Taipei /etc/localtime && \
    dpkg-reconfigure -f noninteractive tzdata && \
    rm -rf /var/lib/apt/lists/*

# 設定系統環境變數
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US:en
ENV LC_ALL=en_US.UTF-8
ENV TZ=Asia/Taipei

# 建立專案目錄
RUN mkdir -p /source_code && \
    chown -R www-data:www-data /source_code && \
    chmod -R 755 /source_code

# 指定工作目錄
WORKDIR /source_code

CMD ["tail", "-f", "/dev/null"]
