# TASKS

## 日历


```dataview
CALENDAR file.ctime
```

## 今天任务
```dataview
CALENDAR begin
FROM #类型/日记
```

```dataview
TASK
FROM "0001-日记"
WHERE date(file.name)=date(today) and !completed
```

## 全部任务

```dataview
TASK
WHERE !completed and !contains(file.path,"0001-日记")
```