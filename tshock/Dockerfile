FROM mono:latest
LABEL maintainer="jeep.jipu@gmail.com" version="1.0"
WORKDIR /root

RUN sed -i 's|http://deb.debian.org|https://mirrors.aliyun.com|g' /etc/apt/sources.list && \
    sed -i 's|http://security.debian.org|https://mirrors.aliyun.com/debian-security|g' /etc/apt/sources.list && \
    apt-get update && \
    apt-get upgrade -y

# 安装必要工具
RUN apt-get install -y unzip vim wget tmux

## 时区
RUN export DEBIAN_FRONTEND=noninteractive && apt-get install -y tzdata >/dev/null
RUN ln -fs /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN dpkg-reconfigure -f noninteractive tzdata

# 安装tshock
RUN wget https://github.com/Pryaxis/TShock/releases/download/v5.2.1/TShock-5.2.1-for-Terraria-1.4.4.9-linux-arm64-Release.zip -O /root/tshock.zip
RUN unzip tshock.zip -d /root/TShock/ && rm tshock.zip && cd ./TShock && tar xf TShock* && rm *.tar

# 解决路径无法访问问题
RUN mkdir -p /root/.local/share/Terraria
RUN chmod 777 /root/.local/share/Terraria

# COPY tshock/start.sh /start.sh
EXPOSE 7777
