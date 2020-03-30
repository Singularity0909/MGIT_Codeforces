# 数据可视化 山威 ACM 校集训队 Codefoces rating

### [展示页面](https://www.macrohard.cn/codeforces)  [代码仓库](https://github.com/Singularity0909/MGIT_Codeforces)

最近在B站偶遇[【数据可视化】Codeforces历史TOP10](https://www.bilibili.com/video/av43450831/)，觉得甚是有趣，于是有了给我们校队造一份可视化 rating 的想法。

UP 主的项目基于 GitHub 上的一个热门项目 [Historical-ranking-data-visualization-based-on-d3.js](https://github.com/Jannchie/Historical-ranking-data-visualization-based-on-d3.js)，它能够将历史数据排名转化为动态柱状图图表，后者又基于 [D3](https://github.com/d3/d3)。

D3js: Data-Driven Documents 是一个可以基于数据来操作文档的 JavaScript 库。可以帮助你使用 HTML, CSS, SVG 以及 Canvas 来展示数据。D3 遵循现有的 Web 标准，可以不需要其他任何框架独立运行在现代浏览器中，它结合强大的可视化组件来驱动 DOM 操作。

D3 作为一个强大的数据可视化函数库效果拔群，衍生出了许多优秀实用的轮子，以上动态柱状图图表便是一个典范。

言归正传。首先我们需要获取校队成员在 Codefoces 的历史参赛情况，主要包括比赛编号、时间、rating 前后变化。我们可以通过 Python 爬虫获取这些信息，但 Codefoces 已经提供了一个便捷的接口（参考 [API 文档](https://codeforces.com/apiHelp)）美滋滋。

在此之前我们先准备好两份名单，分别是 `handles.json` 和 `names.json`。

```json
// handles.json
[
    "handle1",
    "handle2",
    "handle3",
    "// ..."
]
```

```json
// names.json
{
    "handle1": "name1",
    "handle2": "name2",
    "handle3": "name3",
    "//": "..."
}
```

接着通过 Python requests 方法从 API 筛选信息写入初步数据文件 `data.josn`。

再整合 `names.json` 中的姓名映射将 `data.json` 转化为最终数据文件 `data.csv` 以便 D3 解析。

至此所有有效数据已经到手，最后配置动态图表。改造 Web 页面及调参，略。大功告成。

![](https://cdn.jsdelivr.net/gh/singularity0909/cdn/img/screenshot/codeforces.gif)