##### 读取

```python
import pandas as pd

dtypes = {"id": "int64", "value": "float32", "flag": "category"} # 预设类型

df = pd.read_csv("文件.csv",
                 engine="pyarrow",     # 多线程解析, 提高 I/O 速度
                 dtype=dtypes,         # 强制指定列的数据类型
                 parse_dates=["time"], # 读取时将某些列转换为 datetime64[ns] 类型
                 encoding="gbk")       # 在中文 Windows 环境下, CSV 常用 GBK 编码;
                                       # 若用默认 utf-8 可能报错 UnicodeDecodeError.
```

##### 写入

```python
df.to_csv("输出.csv", index=False, encoding="utf-8-sig")  # 推荐UTF-8-SIG, Excel打开不会乱码
```

