# bcdown

[Bilibili漫画](manga.bilibili.com/)下载器，written in [Rust](rust-lang.org/)

这个项目用来接替[之前的python版](https://github.com/lihe07/bilibili-manga-downloader)

## 特性

1. 异步高性能

   网络相关操作使用了基于`tokio`的`reqwests`，较多线程版有较大的性能提升

2. 更加灵活的登录

   工具支持 **扫码登录** 及 **SESSDATA登录** 两种登录方式，且能保存登录结果，无需每次重复登录

3. 更完善的缓存功能

   工具会缓存更多的内容以减少网络请求，缓存地址可配置，默认选取用户的*文档*文件夹

4. 更灵活的导出

   支持分话导出和合并导出，会自动添加Kindle等阅读器可识别的书签

## 使用方法

工具共有如下几个命令：

- `bcdown info ` - 显示配置信息，缓存大小，登录状态

  使用示例：

  - `bcdown info`

    ```
    ℹ 加载配置文件：D:\Documents\bcdown/config.toml
    ℹ 登录信息有效！
    ℹ 用户名：[数据删除]
    ℹ 漫币余额：[数据删除]
    ℹ 缓存目录：D:\Documents\bcdown/cache
    ℹ 缓存目录大小：137 MB
    ℹ 默认下载目录：D:\Download
    ```

- `bcdown login`  - 登录B漫账号，通过二维码或者sessdata

  使用示例：

  - `bcdown login -s [数据删除]` 通过sessdata登录

    ```
    ℹ 加载配置文件：D:\Documents\bcdown/config.toml
    ℹ 登录信息有效！
    ℹ 用户名：[数据删除]
    ℹ 漫币余额：[数据删除]
    ```

  - `bcdown login -q` 通过扫描二维码登录

    ```
    ℹ 加载配置文件：D:\Documents\bcdown/config.toml
        ▀ ██▀▀▀▄  ▀ ▄▄ █▄ ▀▄▄ ▀█▀█▄▀▄ ██▀▀█▄
          ▀▀ ▄▀ ▀   █ ▀ ▄ ▄▄▄▄▀▄█▀▀██ █ ▄█▀▀█
           █ █▀█▄▄▀██▄  ▄▀▄▄▄▄▀▄▀▀▀▀█▀▀█▀ ▀▀▀
         █▄█▀█▀██ ▄   ██▄ █▄ ██ ▄ ▄▀█▄ ██▀ ██
        █▀ ▀▄▀▀█▀  █▀▄█▄ ▀█▄▄▄▀█▀▀▀ ▄▀▀▄▀ █▄
         █   █▀█  █▄█  █▄   █▄▄ ▄▀ ██▄█▄  ▀▀█
        ▄ ▄▄▀▄▀ █▄▄▄ ▄▄▀▄██▄█▄▀█▀▀▀▀▄█▀ ▀█▀
        █▀█   ▀▀▄███▀█▄▀█ ▀ ▀▄▀▄█ ██ ████▀ █▀
        ▄▄ █  ▀ █▄▄▀█▀█ ▄█▄▄▄ ▄▄▄█▀▀▄█▀█▀ █▀▀
        █ ▄▄▀▄▀▄██▀ █ █▀ ▀  ▀▄█▄▀ ▄██▄▀█  ▀██
        ▀ ▀▀▀ ▀ ▄▀▄▄▀ ▀▀ █▄██▄▀▄▀▀▀ █▀▀▀██▀▀
        █▀▀▀▀▀█ ▄▀   █▀██▀▀▄█▄▀ ▄ ▀ █ ▀ █▄▀█▀
        █ ███ █ █  ▄▄▄█▀▄▄▀█▀ ▄█▄█▀▀███▀█▄▀▀▄
        █ ▀▀▀ █ ▀ ▀▀▀▄ ▀█ █  ██▄█ ▀▀▄▀  ▄  ▀█
        ▀▀▀▀▀▀▀ ▀▀▀    ▀▀▀▀▀    ▀▀▀▀ ▀▀ ▀ ▀▀▀
    
    
    ✔ 二维码已生成，请扫描二维码登录
    ℹ 如果显示错误，请手动访问：[链接省略]
    ⠇ 等待确认...
    ```

    > **备注**：建议在现代的终端中执行，如*Windows Terminal*等

- `bcdown clear` - 清空缓存文件夹
- `bcdown search [链接或ID]` - 搜索某个漫画，列出它的全部章节
- `bcdown list` - 列出缓存中的漫画
- `bcdown fetch [链接或ID] <--from [从哪话开始]> <--to [到哪话结束]>` - 将一个漫画下载到本地
- `bcdown export [链接或ID] <--from [从哪话开始]> <--to [到哪话结束]> <-s 不合并pdf> <--output [输出位置]>`  - 导出一个本地漫画

## 构建，编译，安装

和大部分rust crates一样，只需clone该存储库，之后执行`cargo build --release` 即可本地构建

> **备注**：鉴于依赖项`printpdf`的特性，只有在添加`--release`标签后，工具才会对PDF执行压缩

如果只是普通用户，可以下载编译好的可执行文件：[Releases](https://github.com/lihe07/bilibili_comics_downloader/releases)

## 联系方式

我的QQ：*3525904273*