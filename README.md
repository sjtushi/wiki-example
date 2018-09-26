# [实验楼](https://www.shiyanlou.com)技术教程示例仓库

所有配置文件统一使用 [YAML](http://yaml.org/spec/1.2/spec.html) 格式。
所有文件 **必须** 使用 UTF-8 编码。

## 目录结构

目录结构如下：

```bash
├── README.md
├── books
│   ├── README.md
│   ├── external-book1-meta.yaml
│   ├── internal-book1-meta.yaml
│   └── internal-book2-meta.yaml
├── index_config.yaml
└── internal
    ├── README.md
    ├── book1
    │   ├── README.md
    │   ├── SUMMARY.md
    │   ├── chapter1.md
    │   └── chapter2.md
    └── book2
        ├── README.md
        └── SUMMARY.md
```

核心目录（文件）如下：

* [index_config.yaml](./index_config.yaml) 技术教程首页配置示例；
* `books` 目录包含所有技术教程配置文件；
* `internal` 目录包含所有内部技术教程的具体内容；

## 教程配置文件

所有技术教程都必须包含配置文件，且必须位于 `books` 目录下。系统在处理技术教程时，会先从 `books` 目录读取技术教程配置文件，然后再从相应的 Git 仓库中同步技术教程具体内容。

没有配置文件的教程将不会进行同步。

[教程示例配置](books/internal-book1-meta.yaml)。

## 内部教程与外部教程

实验楼自己维护的内部教程内容将存储在 `internal` 目录中，`internal` 目录的每一个子目录对应一个教程。

外部教程内容将存储在其他仓库中。

不管是内部教程还是外部教程，都应在 `books` 目录中都应该有相应的配置文件。

## 教程目录

每一个教程包含：

* 配置文件，位于实验楼 wiki 仓库的 `books` 目录下；
* 内容目录，可能位于实验楼 wiki 仓库的 `internal` 目录下，或者是在教程作者的仓库中；

其中内容目录结构示例如下：

```bash
├── README.md
├── SUMMARY.md
├── chapter1.md 
└── chapter2.md
```

其中几个比较关键的文件：

* [README.md](internal/book1/README.md) 可以包含一些介绍信息；
* [SUMMARY.md](internal/book1/SUMMARY.md) 指定了教程同步到系统时，应包含的内容章节信息，[示例](./internal/book1/SUMMARY.md)；

系统从 Github 同步技术教程时，将自动从 `SUMMARY.md` 文件中解析出所有的章节文件，并读取其内容存储到数据库中。同时由于需要在技术教程详情页面展示教程的所有目录，系统在读取章节内容时也会从总解析出 H2 和 H3 菜单（H1 菜单是章节名称）。

## 同步

* 定时同步
* Webhook 同步