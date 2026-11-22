# Chronograf for TOS 7

Chronograf 是 InfluxData 的时序数据可视化工具。此包使用 Docker 官方镜像，在 x86_64 和 aarch64 TNAS 上提供 Chronograf 1.11.7。查看数据需要一台可从 NAS 访问的 InfluxDB；配置告警还需要 Kapacitor。[上游项目](https://github.com/influxdata/chronograf) · [官方镜像](https://hub.docker.com/_/chronograf)

## 首次连接

1. 启动 TOS 的 Docker Engine 和 Chronograf。在 TOS 桌面点击 Chronograf，或在可信网络中打开 `http://<NAS-IP>:18888/`。默认入口使用 HTTP，能访问此端口的人可以打开管理界面。
2. 在连接向导中填写 InfluxDB 的地址和访问凭据。例如，InfluxDB 在同一台 NAS 上发布了 8086 端口时，连接地址可填 `http://<NAS-IP>:8086`。容器中的 `localhost` 指向 Chronograf 容器自身。
3. 连接成功后，打开 **Data Explorer** 查询指标，或在 **Dashboards** 创建仪表板。[连接 InfluxDB 和 Kapacitor](https://docs.influxdata.com/chronograf/v1/administration/creating-connections/)

## 数据与备份

Chronograf 以 UID/GID `1000:1000` 运行，容器内的数据文件为 `/var/lib/chronograf/chronograf-v1.db`。在 TOS Docker 管理器中可查看挂载到 `/var/lib/chronograf` 的宿主目录。该目录须允许 UID 1000 写入；备份前先停止应用，再复制数据目录，并限制备份的读取权限。连接设置和仪表板保存在这里，时序数据由已连接的 InfluxDB 管理。

安装包和 SHA-256 校验文件随本仓库的 Release 发布。Chronograf 遵循 GNU AGPL-3.0-or-later，本仓库中的安装说明、打包元数据和自绘图标由 Lu Yifei 维护。[安装包](https://github.com/LuYifei-TOS-Apps/tos-chronograf/releases) · [Chronograf 许可证](https://github.com/influxdata/chronograf/blob/1.11.7/LICENSE)
