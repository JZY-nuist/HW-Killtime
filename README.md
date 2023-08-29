# HW-Killtime
#### 单击事件
##### 每隔一分钟点击左键
```python
import pyautogui
import time

# 模拟单击鼠标左键
for i in range(1000):
    pyautogui.mouseDown()
    pyautogui.mouseUp()
    time.sleep(60)
```

#### 下班进度条
##### 太无聊啦！看看啥时候下班吧
```python
import time
import datetime
from rich.progress import *

# 定义起始时间和结束时间
start_time = datetime.datetime.now()
end_time = datetime.datetime(2023, 8, 29, 10, 55, 0)  # 此处需要修改为下班时间

# 计算时间差
time_diff = end_time - start_time

# 输出总秒数
total_seconds = int(time_diff.total_seconds())


progress_columns = (
    SpinnerColumn(),
    "[progress.description]{task.description}",
    BarColumn(bar_width=60, style="blue"),
    TaskProgressColumn(),
    "Elapsed:",
    TimeElapsedColumn(),
    "Remaining:",
    TimeRemainingColumn(),
)

with Progress(*progress_columns) as progress_bar:
    task = progress_bar.add_task("[blue]Working...", total=total_seconds)
    while not progress_bar.finished:
        progress_bar.update(task, advance=1)
        time.sleep(1)
```

![image](https://github.com/JZY-nuist/HW-Killtime/assets/74846298/77248762-9f3a-4a08-8092-e17c506a8341)
