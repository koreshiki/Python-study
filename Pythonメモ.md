# Pythonメモ

## リスト List

### Listの定義

```python
numlist = [1,2,3]
charlist = ['a', 'b', 'c']
emptylist = []

# 入れ子も可能
lists = [numlist,charlist] # [[1,2,3],['a','b','c']]
```

### Listの参照

```python
mylist = [1,2,3,4,5,6,7,8,9,10]
mylist # mylist内の全ての要素

mylist[0] # 1 mylistの先頭の要素
mylist[-1] # 10 mylistの最後尾の要素

# スライスを使った参照
mylist[1:4] # [1]~[3]の要素 [4]は含まれない
mylist[8:] # [8]から最後の要素まで
mylist[:3] # 先頭の要素から[3]まで
mylist[:] # 元のリストのコピー

```

### Tips:range関数を使ったリストの作成

```python
# 1~10000の整数を要素として持つリストを作成
mylist = list(range(1,10001))

# 1~10000の偶数を要素として持つリストを作成
evenlist = list(range(2,10001,2))
```

range関数を上手く使えば様々なリストを柔軟に、迅速に作成できる

### 追加・削除する

```python
mylist = [1,2,3]
mylist # (1,2,3)

# 最後尾に追加
mylist.append(4)
mylist # (1,2,3,4)

# インデックスを指定して追加
mylist.insert(2,-1)
mylist # (1,2,-1,3,4)

# インデックスを指定して削除
mylist.pop(1)
mylist # (1,-1,3,4)

# 要素を指定して削除
mylist.remove(3)
mylist # (1,-1,4)
```



## 関数 Function

### 関数の定義

```python
def function():
    """documentation""" #関数の説明などを表記 省略可
    procedure           #具体的な手続き
    return              #戻り値 省略可
```

returnは無くてもよい(その場合Javaで言うところのvoid関数みたいな振る舞いとなる)

関数例(returnなし)

```python
def hello(person):
    """say hello to person""""
    print('hello', person)

 hello('alice') # hello alice
```

関数例(returnあり)

```python
def twice(n):
    """return 2*n"""
    return 2*n

twice(10) # 20
```



