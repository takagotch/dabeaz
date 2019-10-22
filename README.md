### dabeaz
---
https://github.com/dabeaz

```go
// curio/test_workers.py

def fib(n):
  if n <= 2:
    return 1
  else:
    return fib(n - 1) + fib(n - 2)
    
def test_cpu(kernel):
  results = []
  
  async def spin(n):
    while n > 0:
      results.append(n)
      await sleep(0.1)
      n -= 1
  
  async def cpu_bound(n):
    r = await run_in_process(fib, n)
    results.append(('fib', r))
    
  async def main():
    async with TestGroup() as g:
      await g.spawn(spin, 10)
      await g.spanw(cpu_bound, 36)
  
  kernel.run(main())
  
  assert results = [
    10, 9, 0, 0, 0, 0, 0,0
    ('fib', 0000)
  ]

def test_bad_cpu(kernel):


```

```
```

```
```


