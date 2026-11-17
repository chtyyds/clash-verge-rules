# Clash Verge Rev 地区分流配置

由 nextin-rules 地区版适配，面向较新的 Clash Verge Rev / Mihomo，保留40个策略组及原网站分流。原Nextin仓库不变。

## 首次使用

1. 下载 https://raw.githubusercontent.com/chtyyds/clash-verge-rules/main/config.yaml 。
2. 在电脑文本编辑器中打开，找到 proxy-providers → airport → url，将 https://example.com/REPLACE_WITH_YOUR_CLASH_SUBSCRIPTION 替换为机场的 Clash / Mihomo 格式订阅地址。保留双引号可避免特殊字符问题。不要把真实地址提交到这个公开仓库。
3. 在 Clash Verge Rev 的订阅/配置页面，新建“本地”配置并导入修改后的文件，启用该配置。这里是完整配置，不是另一个节点订阅；客户端里已有的其他订阅不会自动注入本文件。
4. 使用规则模式，打开系统代理；需要接管游戏等不遵循系统代理的程序时，再在客户端设置中启用服务模式和TUN。端口7897可能由客户端设置覆盖。TUN和DNS接管需设备实测。
5. 若节点无法下载，先确认订阅地址和格式正确。订阅默认经DIRECT下载；若直连无法访问，需使用可用网络完成首次下载。

## 更新

机场节点、anti-AD及国内域名/IP库配置为每24小时更新。每5分钟健康检查，延迟容差100ms，懒检测降低闲置组后台负担。仓库config.yaml自身更新不会自动合并到你的本地文件；需要重新下载并在本地填回订阅地址，或自行合并变更。不要直接刷新远程模板覆盖本地密钥。

## 节点分组

香港HK、日本JP、美国US、新加坡SG、台湾TW、韩国KR、阿根廷AR、土耳其TR、马来西亚MY。每个地区分为“地区节点”“地区1.5倍率”“地区直连”，均为自动测速。普通组排除后两类；直连组严格按地区代码+数字分类，如HK 011、JP 001、SG 012。“地区直连”仍是代理节点，不是DIRECT，不能验证实际线路和计费。1.5组按名称标记分类，无标记无法识别。空组拒绝连接，不跨地区回退。

## 网站分流

保留AI服务、YouTube、Netflix、TikTok、其他流媒体、Steam、Apple服务、微软服务及广告与追踪。国内网站/国内IP直连，漏网流量进入节点选择；Apple/微软默认DIRECT，广告默认REJECT。测速不代表AI可用、流媒体解锁或实际带宽。

## 验证与来源

已通过Mihomo v1.19.34配置解析（用本地模拟节点集合验证），分流规则和策略组与源地区版一致。未使用你的机场节点进行连通实测。
规则来源：MetaCubeX/meta-rules-dat；广告追踪：privacy-protection-tools/anti-AD。域名拦截不能清除全部广告。
