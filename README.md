# GitHub Action 自动编译 padavan 和 openWrt

## [openwrt 单独参数及功能说明](/openwrt/readme.md)

## [padavan 单独参数及功能说明](/padavan/readme.md)


### 监听文件 `push` 编译（默认编译，需要其他方式，打开注释修改或自己添加就好）

- 选择按log文件默认的原因
  1. 方便查看管理
  2. 防止多次的push多次编译
  3. 防止不是自己点击 star 之后 Actions 还是会有显示

- 编译模板 yml 里面也有例子

```yml
push:                     # push 操作
  branches:               # 分支
    - master              # 主分支
  # paths:                # 路径
  #   - padavan/*         # 监听padavan目录下所有文件的push操作
  paths:                  # 路径
    - logs/k2.md          # 监听logs目录下 k2.md 的push操作 (默认)
```

### 星标 `star` 编译

- yml文件打开注释点击 **star** (星标开始全部编译)；依赖这句判断是仓库持有者点击:`github.event.repository.owner.id == github.event.sender.id`

```yml
watch:                     # 监视操作
    types: started         # 点击 star 之后,可以写数组形式，具体可以参考官方文档
```

### 定时 `schedule` 编译

- 定时编译方法 [GitHub 官方文档](https://help.github.com/en/actions/reference/events-that-trigger-workflows#scheduled-events-schedule)
- 编译模板 yml 文件中有个每天北京时间凌晨 3 点编译的例子

```yml
schedule:                 # 时间表
  - cron: "0 19 * * *"    # 每天国际时间 19 点，北京时间 3 点执行(北京+8)
```

## 目录说明

```json
  |-- .editorconfig     # 编辑规范
  |-- .github           # GitHub 工作目录
  |   |-- workfloms     # 存放 Action 的 YML文件
  |-- openwrt           # openwrt 有关
  |   |-- backups       # openwrt 文件备份 以及 openwrt 编译模板
  |   |-- public.sh      # 公共的修改执行文件
  |-- padavan           # padavan 有关
  |   |-- backups       # padanvan文件备份 以及 padavan 编译模板
  |   |-- public.sh     # 公共的修改执行文件
  |-- screenshots       # 效果目录
```

## [编译结果欣赏图](./screenshots/readme.md)

## Action 常用参数说明

> - name 自动构建的名字
> - on 触发条件
>
>   - schedule:                 # 时间表
>     - cron: '0 19 \* \* \*'   # 每天国际时间 19 点，北京时间凌晨 3 点执行(北京+8)
>   - watch                     # 监视
>     - type: started           # 类型：点击了星标
>
> - env 环境变量
> - jobs 任务
> - build 工作的 id
> - run-on 工作运行的环境平台
> - if 工作运行的判断
> - steps 包含一系列任务步骤
>   - name 子任务名
>   - user 使用官方的一些库完成一些操作
>   - run 运行脚本
>   - id 运行 id

## 参考项目或文章

- [Github Action 官方 Help](https://help.github.com/cn/actions/)

- [Github Action 官方仓库](https://github.com/actions)

- [openwrt 源码](https://github.com/coolsnowwolf/lede) © coolsnowwolf

- [openwrt 构建参考](https://github.com/P3TERX/Actions-OpenWrt) © P3TERX

- [openwrt 构建参考](https://github.com/ljk4160/GDOCK) © ljk4160

- [openwrt 主题](https://github.com/sypopo/luci-theme-argon-mc) © sypopo

- [openwrt-OpenClash](https://github.com/vernesong/OpenClash) © vernesong

- [openwrt-packages 包](https://github.com/Lienol/openwrt-package) © Lienol

- [adguardhome 插件](https://github.com/rufengsuixing/luci-app-adguardhome) © rufengsuixing

- [Hello Word 插件](https://github.com/jerrykuku/luci-app-vssr) © jerrykuku

- [Hello Word 插件修复冲突版](https://github.com/Leo-Jo-My/luci-app-vssr-plus) © Leo-Jo-My

- [OpenAppFilter 插件](https://github.com/destan19/OpenAppFilter) © destan19

- [openwrt 插件配置参考恩山](https://www.right.com.cn/forum/thread-344825-1-1.html) © xtwz

- [padavan 源码](https://github.com/chongshengB/rt-n56u) © chongshengB

- [padavan 构建参考](https://github.com/chongshengB/Padavan-build) © chongshengB

