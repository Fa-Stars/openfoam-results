# OpenFOAM / DeepFlame 最终结果

私有研究数据仓库。最终时刻 **59.516958444840895 微秒**，目录 `5.9517e-05`。

## 下载

在右侧 **Releases** 中打开 `paperB-mist-final-20261107`，下载 `paperB_mist-final-59.516958us-20261107.tar.gz` 和 `SHA256SUMS.txt`。需要先登录获授权的 GitHub 账号。首次下载请接受协作邀请。

本次分享包含：24 个分区的最终气相场与液滴、完整网格及配置、化学机理、最终日志和退出码，以及合并各重启段的峰值压力轨迹 PNG、NPZ 和 CSV。**不包含全部历史时刻，无法制作完整时间动画。**

## 校验和打开

Windows PowerShell 使用 `Get-FileHash .\paperB_mist-final-59.516958us-20261107.tar.gz -Algorithm SHA256`，与 `SHA256SUMS.txt` 比较。

解压后用 ParaView 打开 `paperB_mist_final/case.foam`，选择 OpenFOAM reader 的 **Decomposed Case**，保留全部 24 个 processor 目录。选中最终时间并选择 p/T/pMax 等字段。

归档中的 README.md 提供完整说明，manifest.json 给出每个选中源文件的 SHA-256 校验值。

## 数据边界

算例共 3,035,760 网格、24 个分区；最终保存 2,695 个计算液滴，求解器正常退出（退出码 0）。

峰值轨迹图是逐时间步累计的历史峰值，已合并 2、2.5、10 微秒重启端点与最终段。最终原始 pMax 会因程序重启重置，不能单独代替完整传播轨迹。

20—90 mm 分段平均波速约 1.787 km/s、分段 CV 2.16%。结果支持持续且近似稳定的胞格传播，严格统计稳定性尚未充分验证。

本仓库提供后处理数据；没有自动启动求解器的脚本，也不包含完整 DeepFlame 运行环境。
