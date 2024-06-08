# baccarat_gambler

## Run ##

### 執行 <h3> 

```
python main.py 
```

執行main.py


![image](https://github.com/jerryshih1106/baccarat_gambler/assets/66662065/717a2439-25a1-4042-b190-d5ff013776a4)



## working level ##

### Methodology <h3>

新增算牌的公式：

```
## ---- python/method/NEW_METHOD.py ----
from ..base.base_baccarat import BaseBaccaratGambler

class NEW_METHODOLOGY(BaseBaccaratGambler):
    def __init__(self):
        super().__init__()
        ...
    def start(self):
        ...
```


### Error Except: <h3>

如果有想要添加的 except:

```
## ---- python/except_handler.py ----
class YOUR_EXCEPTION_NAME(Exception):
    def __init__(self, message):
        self.message = f"YOUR REMINE: {message}"
```
大寫地方改成自定義 exception


```
## ---- python/except_handler.py ----
def except_decorator(func):
    def wrapper(*args, **kargs):
        try:
            return func(*args, **kargs)
        except IllegalInputError as e:
            print(f"{e.__class__.__name__}: {e.message}")
            print("維持上一把的 desicion......")
        except MethodChooseError as e:
            print(f"{e.__class__.__name__}: {e.message}")
            exit()
        except YOUR_EXCEPTION as e:
            ...
        except Exception as e:
            print(f"Error: {e}")
    return wrapper
```
將自定義的 exception 以及發生後程式的後續處理寫入 decorator 中
