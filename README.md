# Baccarat Gambler


## Run ##

### 執行 <h3> 

```
python main.py 
```

執行main.py

### 執行 <h3> 

1. 選擇方法, 若不填為預設： 高階算排法
2. 輸入閒家上把牌，只接受撲克牌上有的數字以及英文. eg：Ａ j 12
3. 輸入莊家牌
4. 贏錢


![image](https://github.com/jerryshih1106/baccarat_gambler/assets/66662065/717a2439-25a1-4042-b190-d5ff013776a4)



## Ｗorking Ｌevel ##

### Methodology <h3>

新增算牌的公式：

```
## ---- python/method/YOUR_METHOD.py ----

from ..base.base_baccarat import BaseBaccaratGambler

class YOUR_METHOD(BaseBaccaratGambler):
    def __init__(self):
        super().__init__()
        ...
    def start(self):
        ...
```

![image](https://github.com/jerryshih1106/baccarat_gambler/assets/66662065/c3ddf09e-b247-46ee-8c54-772b24bf77bd)


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
