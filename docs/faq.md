# 常见问题

## 如何修改头像？

请前往 [https://cn.gravatar.com](https://cn.gravatar.com) 通过邮箱注册并设定头像，评论时，请留下相同的邮箱。

访客还可以通过输入数字 QQ 邮箱地址，使用 QQ 头像发表评论。

## 如何修改、重置管理员密码？

请前往[云开发控制台](https://console.cloud.tencent.com/tcb/database/collection/config)删除 config.ADMIN_PASS 配置项，然后前往 Twikoo 管理面板重新设置密码。

## 如何获得管理面板的私钥文件？

1. 进入[环境-登录授权](https://console.cloud.tencent.com/tcb/env/login)，点击“自定义登录”右边的“私钥下载”，下载私钥文件
2. 用文本编辑器打开私钥文件，复制全部内容
3. 点击评论窗口的“小齿轮”图标，粘贴私钥文件内容，并设置管理员密码

## 如何开启文章访问量统计？

文章访问量统计功能正在测试中，您可以在需要展示文章访问量的地方添加：

``` html
<span id="twikoo_visitors">0</span>
```

来展示访问量。暂不支持全站访问量统计。

## 如何测试 Akismet 反垃圾配置是否生效？

请填写 `viagra-test-123` 作为昵称，或填写 `akismet-guaranteed-spam@example.com` 作为邮箱，发表评论，这条评论将一定会被视为垃圾评论。

需要注意的是，由于 Akismet 服务响应速度较慢（大约 6 秒），影响用户体验，Twikoo 采取 “先放行，后检测” 的策略，垃圾评论会在发表后短暂可见。

## 免费资源如何计算？

您可以在云开发[环境总览](https://console.cloud.tencent.com/tcb/env/overview)看到资源使用情况。Twikoo 会消耗**数据库**和**云函数**两种资源，两种资源的免费用量为——

* 数据库：读 50,000 次/日，写 50,000 次/日
* 云函数：40,000 GBs/月

Twikoo 云函数的内存消耗恒定为 0.1GB，由此可计算出 Twikoo 云函数每月有长达 400,000 秒的运行时长，而免费资源的瓶颈主要在数据库日读取次数限制。建议站长关注免费资源的使用情况。

## 如何更新 Twikoo 版本？

1. **更新云函数**：登录[环境-云函数](https://console.cloud.tencent.com/tcb/scf/index)，点击 twikoo，点击函数代码，将新的云函数代码（[index.js](https://imaegoo.coding.net/public/twikoo/twikoo/git/files/dev/src/function/twikoo/index.js) 和 [package.json](https://imaegoo.coding.net/public/twikoo/twikoo/git/files/dev/src/function/twikoo/package.json) 两个文件）粘贴、点击保存并安装依赖即可。
2. **更新网站**：修改主题配置中的 Twikoo CDN 地址 `https://cdn.jsdelivr.net/npm/twikoo@x.x.x/dist/twikoo.all.min.js` 中的 `x.x.x`，使之与云函数版本号相同，然后部署网站。
