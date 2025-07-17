# Ximalaya.bundle - 喜马拉雅 Plex 有声书代理插件

## 概述

这是一个升级版的 Plex 有声书代理插件，用于从喜马拉雅 FM 获取有声书元数据。本插件已经更新以适配最新的喜马拉雅 API 接口。

## 升级内容

### API 接口更新

1. **搜索接口更新**
   - 专辑搜索: `https://www.ximalaya.com/revision/search?core=album&kw=`
   - 艺术家搜索: `https://www.ximalaya.com/revision/search?core=user&kw=`

2. **音轨获取接口更新**
   - 新接口: `http://mobwsa.ximalaya.com/mobile/playlist/album/page?albumId=`
   - 支持分页获取，提高数据完整性

### 响应格式适配

1. **统一错误处理**
   - 更新为新的响应格式检查 (`ret` 字段)
   - 改进错误日志记录

2. **数据结构适配**
   - 搜索结果路径: `response['data']['result']['response']['docs']`
   - 音轨数据路径: `response['data']['list']`

### 功能改进

1. **HTTP 请求头优化**
   - 更新 User-Agent 为现代浏览器标识
   - 添加必要的请求头以提高兼容性
   - 设置合适的 Referer 和 Origin

2. **分页支持**
   - `GetTracks` 函数支持自动分页获取所有音轨
   - 避免因单页限制导致的数据不完整

3. **错误处理增强**
   - 添加详细的错误日志
   - 改进异常处理机制
   - 添加 `ValidatePrefs` 函数

## 安装方法

1. 将整个 `Ximalaya.bundle` 文件夹复制到 Plex Media Server 的插件目录
2. 重启 Plex Media Server
3. 在 Plex 设置中启用该代理插件

## 使用说明

1. 在 Plex 中创建音乐库
2. 选择 "Ximalaya" 作为代理
3. 插件将自动从喜马拉雅 FM 获取有声书元数据

## 技术参考

本次升级参考了以下项目的架构和实现：

- **Audnexus.bundle**: Plex 代理插件的最佳实践
- **Abs-Ximalaya**: 喜马拉雅 API 的现代化应用
- **喜马拉雅 API 文档**: 最新的接口规范

## 注意事项

1. 确保网络连接正常，能够访问喜马拉雅 FM
2. 插件会缓存数据以提高性能，如需刷新可清除 Plex 缓存
3. 如遇到问题，请检查 Plex 日志文件中的错误信息

## 更新历史

- **v2.0**: 全面升级 API 接口，适配最新喜马拉雅 API
- **v1.x**: 原始版本（已失效）
