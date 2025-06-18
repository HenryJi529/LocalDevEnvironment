FROM mono:6.12.0
LABEL maintainer="jeep.jipu@gmail.com" version="1.0"
WORKDIR /root

RUN cat /etc/apt/sources.list
RUN sed -i 's|http://deb.debian.org|http://archive.debian.org|g' /etc/apt/sources.list && \
    sed -i 's|http://security.debian.org|http://archive.debian.org/debian-security|g' /etc/apt/sources.list && \
    apt-get update && \
    apt-get upgrade -y

# 安装必要工具
RUN apt-get install -y unzip vim wget tmux

## 时区
RUN export DEBIAN_FRONTEND=noninteractive && apt-get install -y tzdata >/dev/null
RUN ln -fs /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN dpkg-reconfigure -f noninteractive tzdata

# 安装TShock
RUN wget https://github.com/Pryaxis/TShock/releases/download/v5.2.4/TShock-5.2.4-for-Terraria-1.4.4.9-linux-arm64-Release.zip -O /root/tshock.zip
RUN unzip tshock.zip -d /root/TShock/ && rm tshock.zip && cd ./TShock && tar xf TShock* && rm *.tar

# 解决路径无法访问问题
RUN mkdir -p /root/.local/share/Terraria
RUN chmod 777 /root/.local/share/Terraria

# 安装.NET
# RUN /root/TShock/TShock.Installer
RUN echo "export DOTNET_ROOT=/root/TShock/dotnet" >> /etc/bash.bashrc

EXPOSE 7777
