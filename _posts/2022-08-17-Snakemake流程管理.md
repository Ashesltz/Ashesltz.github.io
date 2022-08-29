---
layout: post
title: Snakemake流程管理
tags: software
stickie: false
---

**Snakemake 工作流是通过在 Snakefile 中指定规则来定义的**。规则通过指定如何从**输入**文件集创建**输出文件**集，将**工作流分解为小步骤**（例如，单个工具的应用）。Snakemake通过匹配文件名自动确定规则之间的**依赖关系**。

> Snakemake 的rule all 需要输入一个列表，这个列表包括所有的步骤会产生的文件（也就是output）。实际上，Snakemake的工作机制是先通过 shell 产生 output 文件，再检查这些 output 文件是否在指定的目录下存在，确认存在后再执行下一个 rule 。这个检查过程就是通过寻找rule all 下的input 列表完成的。

> 如果rule间没有依赖的话，rule all里面没有写所有的output的话，只会执行和rule all相关的rule。

> 最后，在新建一个snakemake项目时，都先用conda create -n 项目名 python=版本号创建一个全局环境，用于安装一些常用的软件，例如bwa、samtools、seqkit等。然后用如下命令将环境导出成yaml文件

> conda env export -n 项目名 -f environment.yaml

> 以后再部署的时候，只需要conda env create -f environment.yaml