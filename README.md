# Rust 标准库中文版


这是翻译 [Rust 库](https://github.com/rust-lang/rust/tree/master/library) 的地方， 相关源代码来自于 <https://github.com/rust-lang/rust>。

如果您不会说英语，那么拥有使用中文的文档至关重要，即使您会说英语，使用母语也仍然能让您感到愉快。Rust 标准库是高质量的，不管是新手还是老手，都可以从中受益。市面上有很多的 Rust 教程，然而，想要成为 Rust 高手，那么阅读核心库和标准库的源码则是必要的手段。

该仓库包含了 `rust-src` 组件的所有源代码文件，并对其所有的源代码进行翻译。主要包括对 Rust 核心库的翻译，Rust 标准库的翻译，以及其他一些资源。该仓库使用 [`Cmtor`](#) (我写的效率工具) 程序并借助 `JSON` 文件来完成翻译的所有工作，当 Rust 更新时，将尽可能为其生成中文翻译。




## 下载翻译好的 Rust 文档

每次在构建新的中文文档时，会修复之前构建结果中存在的问题，为了尽可能的保证翻译的准确性，本仓库只提供最新版本的构建。最新的构建结果会放在 [`dist`](./dist) 目录下，您可以手动跳转到该文件夹，下载最新的构建结果。




## 使用 Rust 中文文档

> - 在使用中文文档时，请注意版本号，中文文档版本和 Rust 版本号必须要保持一致。
> - 必须使用 `stable` 版本，不要使用 `beta` 和 `nightly` 版本。
> - 在翻译后的源代码中，一些文档的底部会存在一定量的内容为空的注释行，其实这是有意为之，请不要擅自修改和删除。如果您删除了它，就会导致 `source-map` 失效，当 `source-map` 失效后，在调试源代码时就会出现执行位置和源代码位置不一致的严重问题。



如果您是刚开始使用 Rust，那么请确保 Rust 已经安装好，并且可以正常工作。在 Rust 安装成功后，您还应该通过 `rustup component add rust-src` 命令来安装 `rust-src` 组件。当安装 `rust-src` 组件之后，请按照以下步骤进行操作：

1. 在终端执行：`rustup default stable` 来切换到 `stable` 版本，并确保 `stable` 的版本与中文版文档所对应的版本一致
2. 在终端执行 `rustup show`，然后在输出中找到 `rustup home` 所对应的路径，然后将其在资源管理器中打开
3. 打开 `toolchains` 的文件夹，在该文件夹下，找到您当前所使用的 Rust 工具链并将其打开，例如，在 `Windows` 平台上对应的是 `stable-x86_64-pc-windows-msvc` 文件夹
4. 然后打开 `lib/rustlib/src/rust` 目录，这个目录下的文件夹就是 Rust 标准库源代码所在的位置
5. 将 `lib/rustlib/src/rust/library` 文件夹下的所有内容保存一份副本
6. 下载本仓库对应的中文文档源文件，将其重命名为 `library` 并放置到 `lib/rustlib/src/rust` 文件夹下
7. 请确保您已经在 IDE 中安装 Rust 相关插件，例如，`vscode` 需要安装：[rust-analyzer](https://marketplace.visualstudio.com/items?itemName=matklad.rust-analyzer)
8. 重新启动 `IDE` 工具，中文文档的智能提示开始工作
9. 愉快的编码！



## 离线 HTML 文档

该中文翻译为源码级翻译，现在您可以轻松的构建离线的 HTML 文档供自己阅读。在构建离线 HTML 文档之前，您需要了解一些 Git 操作知识以及 Rust 构建流程。在这里，仅提供 HTML 离线文档的构建命令。

有关构建离线文档的更多信息，请参见：[构建离线 HTML 文档](./BuildHtml.md)



## Gitee 国内镜像

为了方便国内朋友的下载和访问，Github 上的 [rust-library-i18n](https://github.com/wtklbm/rust-library-i18n) 仓库已同步到了 Gitee，项目地址为: <https://gitee.com/wtklbm/rust-library-chinese>，其中 [rust-library-chinese](https://gitee.com/wtklbm/rust-library-chinese) 仅为镜像仓库，如果您想找到我，请在 [Github](https://github.com/wtklbm) 上进行留言。




## NOTE

该翻译底层基于机器翻译，但优于纯机器翻译，它只会翻译该翻译的地方，并能够保证所翻译的文档和英文文档是完全同步的，不会产生文档脱节的情况。

**请注意**，本仓库所提供的翻译只是在提供一种方便，并不能完全取代官方文档，也没有任何在内容上的绝对保证。如果您有任何问题，请以官方文档为准。有任何难以决绝的地方，请阅读文档和其文档所关联的标准库源代码。众所周知，在使用机器翻译处理技术文档时，仍然有待提升的空间，因为其技术文档的高度专业性，使用机器翻译就会不可避免的存在漏翻、多翻、错翻等诸多问题，该仓库基于机器翻译，也就意味着人工校对是不可或缺的步骤，所以每次在添加新的翻译时，都会或多或少的参与粗略校对。因为其待校对的内容已达 33 万多条语句，有好几百万字符，并且要翻译的内容以每一个版本 1000 条语句的速度增加，每更新一版都要花费一天的时间进行粗略校对。翻译是一个体力活，没有太多技术含量，且枯燥乏味，在没有其他长期贡献者参与的情况下，在未来某个时间 (几天或者几个月)，迫于压力，该项目可能会也可能不会再次更新，恕不另行通知。

一个人的时间和精力是有限的，有缺漏不对，翻译不好的地方，请海涵。该翻译的效果谈不上通顺易懂，主要以明白大意为主，要想完全掌握基础和底层，还需要我们更多的熟悉和探索，更多的敲和练，也希望能通过中文翻译打开一个新的窗口，我们一起探索更多可能性，把 Rust 写的又快又好。

非常欢迎您直接提交 PR 来改进翻译。



## Others

### `crm`

`crm` 是一个镜像源管理工具，内置了 5 种 Rust 国内镜像源，并提供了测速功能，更换镜像源特别方便。

- [从 Github 访问](https://github.com/wtklbm/crm)
- [从 Gitee 访问](https://gitee.com/wtklbm/crm)




## License

MIT OR Apache-2.0
