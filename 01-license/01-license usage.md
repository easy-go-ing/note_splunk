### Daily total by GB

```python
index="_internal" source="*metrics.log" per_index_thruput | eval GB=kb/(1024*1024) | timechart span=1d sum(GB) | convert ctime(_time) as timestamp
```



### Highest-usage indexes

```python
index="_internal" source="*metrics.log" per_index_thruput | eval GB=kb/(1024*1024) | stats sum(GB) as total by series date_mday | sort total | fields + date_mday,series,total | reverse
```

