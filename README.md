# 2026 Life OS

我的 2026 个人成长与运动档案。

在线查看：https://945279157-netizen.github.io/2026-life-os/

## 怎么加训练记录

直接在网页上加，不用改代码。

打开链接，点右下角的「＋ 记录训练」，或者点日历里的某一天再点「在这天加一次训练」，填完保存。日历、训练记录、数据统计、类型分布、PR、年度总结、月报会同时更新。

保存后数据先存在你这台设备上，页面顶部会出现「有还没同步的修改」。点「同步到 GitHub」，数据就写回仓库里的 `data.json`，GitHub Pages 大约一分钟后重新发布，之后手机、电脑、任何人打开链接看到的都是同一份。

第一次用需要在「记录 / 同步」页面填一个 GitHub Token：

1. 打开 https://github.com/settings/personal-access-tokens/new
2. Repository access 只勾选 `2026-life-os` 这一个仓库
3. Permissions → Repository permissions → Contents 设为 **Read and write**
4. 生成后把 token 粘进页面里点「保存设置」

Token 只存在这台设备的浏览器本机存储里，不会写进仓库，也不会发给 GitHub 以外的任何地方。换设备要重新填一次。公用电脑用完点「清除本机 Token」。

不想用 Token 也可以：在「记录 / 同步」页点「导出 data.json」，把文件上传替换仓库里的同名文件，效果一样。

## 数据结构

数据都在仓库根目录的 `data.json`：

```json
{
  "updatedAt": "2026-08-11T00:00:00.000Z",
  "extraMonths": ["2026-07"],
  "workouts": [
    {
      "id": "w-20260810-1",
      "date": "2026-08-10",
      "type": "strength",
      "name": "背部力量",
      "duration": "58:51",
      "distance": null,
      "calories": 215,
      "load": 3,
      "avgHr": 93,
      "status": "completed"
    }
  ],
  "body": [],
  "goals": []
}
```

- `type`：`run` / `strength` / `fight` / `mixed` / `endurance` / `aerobic` / `complete` / `basic`
- `status`：`completed` 已完成 / `planned` 计划
- 可选字段：`maxHr`、`pace`、`best`、`climb`、`detail`
- 同一天有几条就写几条，一天多练会在日历里全部展开
- `body`：身体数据 `{date, weight, fat, note}`，填了体脂率后目标卡会自动显示当前值
- `goals`：月度目标 `{month, metric, target, current, note}`
- `extraMonths`：想让某个还没有数据的月份出现在筛选里，加进这个数组

`index.html` 里还留了一份同样的数据作为兜底，只在 `data.json` 读不到的时候使用（比如把 html 单独下载到本地打开）。正常情况下以 `data.json` 为准。
