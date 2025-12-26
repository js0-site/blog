- [x] 返回值支持 struct
- [x] rs -> volo 文件的生成
- [x] volo http 调用的后端
- [x] volo http 前端自动打包调用请求，并正确解码回调

- [ ] 邮件订阅
- [ ] contabo 数据的备份
- [ ] 如何把 contabo 的 vps 刷机为 nixos ; nixos-anywhere https://aistudio.google.com/u/2/prompts/1Mq5HN5fKubKNRoQh-qGyiCJIO7AFFK4x
- [ ] 博客的翻译
- [ ] 网站的搭建
- [ ] 发布文章到 reddit 和 hacknews 等网站的脚本
- [ ] js0-rs 项目 github 模板
- [ ] rust -> volo_grpc + js 博客文章的撰写
- [ ] 验证码的前端演示项目


- [ ] http 服务器对设备 cookie 的设置与刷新(每天刷新一次,防止永久泄露) ; cookie 设置的格式为 设备唯一码 - 第N天 - 签名
      签名 = hash(服务器私钥 + 日期 + 设备唯一码)
      如果服务器私钥不小心泄露，可以同时验证新老私钥（老私钥只验证过去签发的），过一段时间，等用户的 cookie 都刷新之后，就可以删除老私钥，切换新私钥

- [ ] 用户系统
      - [ ] FromReq 的这个 async trait
      - [ ] rs2proto 生成 rust 代码要识别出这种参数，并映射为争取的调用


- [ ] gway http - volo grpc 的网关
- [ ] js - http - volo grpc 的前端调用
- [ ] 确定从 rust 访问数据库的方案
- [ ] 基于以上方案，实现网页加上 邮件订阅、退订的按钮
- [ ] 验证码的实现
- [ ] 用户系统的开发