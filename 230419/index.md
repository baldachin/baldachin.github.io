# [Original] 艰难的 chatGPT 体验


在 chatGPT 刚刚火起来不久自己就注册了帐号并且开始尝试使用，但一直没有购买 plus 服务也就没有直接体验过传说中的 chatGPT 4 服务。因为有帐号也就同时获得了几个可用的 key 可以在一些第三方工具里通过 key 实现调用 API 使用的目的。之后又遇到 API 地址被限制的问题，根据网上教程在 cloudflare 上创建了反向代理才终于能够正常使用。

前些天重装了工作电脑把之前折腾的很多环境都清理掉了，于是又要重新折腾这些东西，这才发现自己无论如何都登录不到 chatGPT 的服务网站，从提示来看是自己的代理地址被屏蔽了。又试过自己在服务器搭建的代理服务依然无法访问，不知道什么时候代理地址也被屏蔽了。还好自己手边还有之前折腾的 key 和 API 可以用，但访问不了网站就没法折腾  chatGPT 4 了。

这两天想要把之前不大健全的代码完善重构一下，当然要试试通过各种人工智能帮助自己工作。也试着下载了各种智能辅助编程的工具，有一些效果还可以但总是差那么一点意思，完全没有网上别人用 chatGPT 4 的效果那么惊艳，原来因为自己用的是 3.5 就有这么大的差距。

于是自己收集整理自己可以用到的各种 chatGPT 途径：

- 各种 chatGPT 中转网站，可以体验基本使用但都是 chatGPT 3.5 的接口，和手边没什么不同。其实现在可以免费使用 3.5 接口的途径已经有很多了，没什么特别使用这些第三方服务的理由。
- Poe ，Quora 正规军的 GPT 服务，集成了包含 chatGPT 3 和 4 和 Claude 等众多不同模型服务，多数模型均可免费使用，其中 chatGPT 4 和 Claude+ 还提供了每日的限额试用，但无法付费购买服务。
- New Bing 微软智能辅助，据说也是 chatGPT 4 的底层，但实际结果和 Poe 中的 chatGPT 有巨大落差，相信是为了适配浏览器搜索而做了简化的特定模型，基本无法满足开发辅助工作。
- Monica 浏览器插件，可以使用类似 chatGPT 的会话服务，早期使用 chatGPT 3.5 现在已经不再使用但没有告知实际使用模型，综合水平接近 chatGPT 3.5，开发辅助效果一般。
- Cursor 代码编辑器，免费使用 chatGPT 3.5 辅助开发，受限于 chatGPT 3.5 的代码生成能力只可以辅助参考还无法完全生成。
- 第三方 chatGPT 4 中转网站，付费充值获得点数，问答扣除。

Poe 中 chatGPT 4 服务每天只有一条免费使用限额，随便试试还行要拿来做事还远远不够。试着充值第三方服务之后体验了传说中的 chatGPT 4 的代码生成，真的相比 3.5 版本有了质的变化，应该可以直接产生相对复杂的直接可用的代码，唯一的缺点是费用消耗非常快。

在考察过程中自己还尝试了询问一些关于佛教法理的问题，chatGPT 4 和 Claude+ 都有令人惊艳的表现，其他几种模型相对差距还比较大。最后再吐槽一下百度的文心一言，回答完全就是瞎编，最搞笑是问了两个不同的佛教核心名词居然给出几乎完全一样的回答。
