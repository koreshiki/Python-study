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



### 内包表記

次のsquares, suqres2の2つのリストの内容は同じになる

```python
squares = []
for x in range(10):
    squares.append(x**2)
    
squares2 = [x**2 for x in range(10)]
```



### その他関数

#### count

そのリストに引数で与えた値が何個含まれるかを返す

```python
mylist = [1,2,3,4,1,2]

mylist.count(1) # 2
```

#### reverse

リストの順番を返す

```python
mylist.reverse()

mylist # 2,1,4,3,2,1
```

#### sort

ソートする 

```python
mylist.sort() #昇順ソート
mylist # 1,1,2,2,3,4

mylist.sort(reverse=True) # 降順ソート
mylist # 4,3,2,2,1,1
```



## タプル Tupple

```python
tup = (1,2,3)
tup = 1,2,3
# 要素が1つの場合
tup = (1,)

# 要素の変更は出来ない
tup[0] = 10 # TypeError!!
```



## 集合 Set

```python
myset = {'apple', 'orange', 'banana', 'apple'}

# 集合には順序がなく、重複も排除される
myset # 'apple','orange','banana'

'orange' in myset # True
'pear' in myset # False

# 空集合
empty = set()
```

### 集合の演算

```python
a = {1,2,3,5,6}
b = {2,4,6}

# 集合の和
a | b # {1,2,3,4,5,6}

# 集合の差
a - b # {1,3,5}

# 集合の積
a & b # {2,6}

# 排他 いずれにしかないものを求める
a ^ b # {1,3,4,5}
```



## 辞書 Dictonary

キー(Key)と値(Value)の組をもつデータ

```python
mydict = {'one':1, 'two':2, 'three':3}

# 追加
mydict['four'] = 4
mydict # {'one':1, 'two':2, 'three':3, 'four':4}

# 削除
del mydict['three']
mydict # {'one':1, 'two':2, 'four':4}

# キーだけを取り出す
list(mydict.keys()) # ['one', 'two', 'four']
# 値だけを取り出す
list(mydict.values) # [1,2,4]
# キー、値を取り出す
list(mydict.items()) # {'one':1, 'two':2, 'four':4}

# ある要素が含まれるか
'two' in mydict # True
'three' in mydict # False
```



## 関数 Function

### 関数の定義

```python
def function():
    """documentation""" #関数の説明などを表記 省略可
    procedure           #具体的な手続き
    return              #戻り値 省略可
```

documentationにはその関数の説明、具体的には引数にどのような値が入り何を返すか、関数がどのようなものかなどを記述すると良い

returnは無くてもよい(その場合Javaで言うところのvoid関数みたいな振る舞いとなる)

#### documentationの参照

```python
print(sample.__doc__)
```

#### アノテーション

引数や戻り値の型を注記することが出来る

```python
def sample(name:str, age:int) -> str:
    ~~~~

print(sample.__annotations__) # sample関数アノテーションを表示    
```



#### 関数例(returnなし)

```python
def hello(person):
    """say hello to person""""
    print('hello', person)

 hello('alice') # hello alice
```

#### 関数例(returnあり)

```python
def twice(n):
    """return 2*n"""
    return 2*n

twice(10) # 20
```

### デフォルト引数

```python
def hello(person='alice'):
	print('hello', person)

hello('bob')
```

#### キーワードを指定する

```python
def create_table(database='test', table='sample'):
    print('create table', test, '.', sample, ";")
    
create_table() # create table test.sample;
create_table(percona) # create table percona.sample;
create_table(table=sample2) # create table test.sample2;
```

#### リスト・辞書を引数として渡す(可変長引数)

```python
def func_list(*arguments):
    for arg in arguments:
        print(arg," ")
	print()       

numlist = list(range(10)) # 0~9までの整数を含むリストを作成する
func_list(*numlist) # 0,1,2,3,4,5,6,7,8,9
```



デフォルト引数に変素を指定する場合は、その関数の定義時の値が使われる

```python
i = 1
def sample(arg = i):
    print(arg)

i = 2
sample() # 1
```

### ラムダ式(無名関数)

```python
lambda 引数 : 戻り値
```

次の関数とlambda式はどちらもx^xを返す

```python
def power(x):
    return x**x

lambda x : x**x
```

用途としてはsortなど行うとき、関数を定義するレベルではないが特殊な動きをさせた問いときなど？
