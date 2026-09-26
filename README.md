# Mihomo 广告域名规则

本仓库只存放可公开的广告域名规则，不放 ShellCrash 配置、订阅链接或节点信息。

## 文件

- `rules/ads.yaml`：供 Mihomo HTTP 规则提供者读取的域名列表。

## 添加域名

在 `payload` 下每行添加一条，缩进两个空格，并以 `- ` 开头：

```yaml
payload:
  - ads.example.com
  - '+.tracker.example.org'
```

- `ads.example.com` 仅匹配这个完整域名。
- `+.tracker.example.org` 匹配该域名及其所有子域名。此写法范围更广，应在确认需要时使用。
- 不要写 `https://`、路径、端口、IP 地址或 `DOMAIN-SUFFIX,` 等规则前缀。
- 新增条目前先确认它确实用于广告或跟踪；有疑问时先用完整域名。

当前列表为空，不会拦截任何域名。添加首条真实域名并提交后，Mihomo 会按本地模板配置的间隔更新。

## 误拦截

如果一条规则没有必要，直接从 `rules/ads.yaml` 删除它并提交。如果需要保留较宽的拦截规则，可在路由器的本地模板中、广告 `RULE-SET` 之前加入更精确的放行规则，例如 `DOMAIN,login.example.org,DIRECT`。放行规则无需公开到本仓库。
