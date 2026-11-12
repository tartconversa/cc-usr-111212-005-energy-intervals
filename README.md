# 异步功率表的能量积分与缺测界

本项目保存虚构台架测量表及Python读取工具。当前工具加载文件并检查输入，不执行统计检验、求解、配准或分析。所有仪器、试件、对象与人工标签均为合成。

## 字段与单位

time_seconds以共同实验起点计，signed_power为瞬时功率；重复戳必须内容一致。meters以不可拆的[start,end)区间计净能量，不是瞬时读数。

material-index.json记录全部输入内容哈希；fixtures保存原始资料与配置，计算输出可放.workspace-output，原始资料不应被覆盖。

## 运行已有读取器

Python 3.11以上，标准库即可，不需安装第三方依赖。

    python -m src.energy_reader fixtures/power.csv
    python -m compileall -q src tests
    python -m unittest discover -s tests -v

## 固定容器

    docker build -t energy-intervals:local .
    docker run --rm energy-intervals:local

容器镜像以完整digest固定，默认仅检查输入契约；实现新增分析功能所需依赖由开发者明确登记。
