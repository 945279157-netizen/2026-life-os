# 2026 Life OS

我的 2026 个人成长与运动档案。

在线查看：https://945279157-netizen.github.io/2026-life-os/

## 怎么更新数据

所有训练数据集中在 `index.html` 里的 `workoutData` 数组，加一条记录，日历、训练记录、数据统计、筛选和月报会一起更新。

```js
{
  date: "2026-08-10",     // 日期
  type: "strength",       // run / strength / fight / mixed / endurance / aerobic / complete / basic
  name: "背部力量",
  duration: "58:51",
  distance: null,         // 公里，跑步类填写
  calories: 215,
  load: 3,                // 训练负荷 TL，可选
  avgHr: 93,              // 平均心率，可选
  status: "completed"     // completed 已完成 / planned 计划
}
```

同一天有几条就写几条，一天多练会在日历里全部展开。

- 身体数据：`bodyData`，格式 `{date, weight, fat, note}`
- 月度目标：`goalData`，格式 `{month, metric, target, current, note}`
- 想让某个还没数据的月份出现在筛选里：加进 `EXTRA_MONTHS`
