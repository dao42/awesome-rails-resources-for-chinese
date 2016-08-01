# Ruby on Rails 在中文圈子的特别资源收集

众多周知, 在中文圈子里 Rails 的很多资源是被 GFW 的, 或者非常慢. 经历长期的积累, 作者收集了一些比较好的替代或一些较好的实践. 以期帮忙中文圈子的 Railser 节省一些无谓的耗时.

## Gem source

[Ruby gems 中文源](https://gems.ruby-china.org/)


```shell
$ gem -v
# 2.6.3 ( 建议 >= 2.6 )
$ gem sources --add https://gems.ruby-china.org/ --remove https://rubygems.org/
```

推荐指数: 5星

推荐说明: [RubyGems](https://rubygems.org) 是最常用的安装 `gems` 的托管服务, 但由于布署在 `AWS` 上, 基本上从 15 年开始就一直不通. 强烈建议切换.

缺点: 唯一的缺点是, 如果写自己的 ruby gems 后会导致无法 `gem push` 到官方源上. 对大部分人无影响.


## Bundler Mirror

```shell
$ bundle config mirror.https://rubygems.org https://gems.ruby-china.org
```

推荐指数: 5星

推荐说明: [Bundler] 是 Ruby 社区管理项目依赖的标配工具, 它有自己的源读取方法, 利用 `Gemfile` 头部声明的源进行安装. 这种方式的好处是你无须调整任何 `Gemfile` 的配置, 就能利用到 `gems.ruby-china.org` 的源. 非常的方便, 很适合于跨国协作.

缺点: 无缺点

## rbenv plugin

[rbenv-china-mirror](https://github.com/AndorChen/rbenv-china-mirror)

```shell
$ git clone https://github.com/andorchen/rbenv-china-mirror.git ~/.rbenv/plugins/rbenv-china-mirror
```

推荐指数: 4星

推荐说明: [rbenv] 安装 Ruby 的时候默认指定的是 [caches.ruby-lang.org], 在中国也是很慢的, 你只需要简单执行以上命令, 即可切换至 [ruby.taobao.org] 的 Ruby installer 源. 经过我的尝试, 下载时间从过去的 30 分钟下降至 5 秒. 快了300多倍. 绝对是节省时间的好工具.

缺点: 目前好像对 rbenv 的版本有依赖, 建议使用 rbenv 的新版本.

--------------------

# 命令行翻墙指南

不推荐使用 http_proxy 环境变量的方式来翻墙. 因为有许多命令会忽略这个环境变量, 或根本不支持 http 方式的翻墙.

经作者长期实践, 推荐以下工具:

## polipo

[polipo](https://github.com/jech/polipo)

一个非常成熟的将 sock5 代理转换为 http 代理的工具.

推荐指数: 4星

推荐说明: 非常实用的工具

## proxychains-ng

[proxychains-ng](https://github.com/rofl0r/proxychains-ng)

现在是第 4 代.

```shell
# Usage
# Before: gem install rails
proxychains4 gem install rails
```

一个可以 hook 任何命令将其网络请求全部转到 sock 或 http 代理通道的命令行工具.

推荐指数: 5星

推荐说明: 不是每一个命令都遵守网络代理规范, 但 proxychains4 做到了.

