# CFW Mihomo Patch

适用于 Clash for Windows v0.20.39 的“延寿”补丁，添加对 Mihomo 核心的支持，解决核心替换后的配置目录、版本显示、日志解析和服务模式兼容问题。

## 主要改动

1. 将 `mihomo-windows-amd64-v1.19.27` 的可执行文件重命名为 `clash-win64.exe`，替换原核心文件。
2. 将 `clash-core-service.exe` 内置公钥替换为自签公钥，并使用自签私钥生成 `clash-win64.exe.sign`，替换原签名文件。
3. 修改核心启动参数，强制使用 CFW 配置目录 `~/.config/clash`，而非 `~/.config/mihomo`，确保配置文件正确加载。
4. 修改 UI 渲染逻辑，兼容 Mihomo 核心字段，使界面能够正确显示当前 Mihomo 版本信息，而非 `Unknown`。
5. 修改日志解析模块，使 Mihomo 输出的实时与历史日志在 UI 中正确显示，避免乱码或标签丢失。

## 注意事项

1. 有些代理服务商会拒绝向 CFW 下发配置，需要解包 `app.asar`，修改 `main.js` 中的 `userAgent`，然后打包替换。
2. 建议在修补前备份 `clash-win64.exe`、`clash-win64.exe.sign`、`clash-core-service.exe` 和 `app.asar` 四个文件。
3. 本补丁仅针对 CFW v0.20.39 测试，其他版本可能需要自行适配。
4. 本补丁仅用于兼容性修复与学习研究，请自行承担使用风险。

## 参考资料

1. [CFW 无缝移植 Mihomo 核心指南](https://fufu.blog/t/166/)
2. [自签 CFW 的服务模式核心](https://www.nodeseek.com/post-342248-1)
3. [修改 CFW 的 User-Agent](https://www.nodeseek.com/post-432302-1)
