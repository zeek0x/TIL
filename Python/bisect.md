# bisect モジュール

二分探索処理を提供するモジュール

```python3
>>> bisect.bisect_left([1,1,2,2,3,3,4,4,5,5], 3)
4
>>> bisect.bisect_right([1,1,2,2,3,3,4,4,5,5], 3)
6
>>> bisect.bisect_right([1,1,2,2,3,3,4,4,5,5], 1000)
10
>>> bisect.bisect_right([1,1,2,2,3,3,4,4,5,5], -1)
0
```

# Link

https://docs.python.org/ja/3/library/bisect.html
