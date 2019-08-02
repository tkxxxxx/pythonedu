# クラスメソッドと関数の違いは？

## クラスメソッドは関数とそれほど大きな違いは無いと言えます。 ですが、以下の違いがあります。

* 第一引数でクラスが取得できる
* クラスの中にあるので、クラスをインポートすれば使える。

よく使われる例としては、そのクラスを作るメソッドを書くことです。 以下の例ではクラス Item と、Itemの情報をあるAPIから取得して返す retrieve_from_api というクラスメソッドを実装しています。


```python
class Item:
    def __init__(self, id, name):
        self.id = id
        self.name = name

    @classmethod
    def retrieve_from_api(cls, id):
        res = requests.get(f"https://api.example.com/items/{id}")
        data = res.json()
        return cls(id, data["name"])  
```

もちろんクラスメソッドを使わずに、以下のように関数でも書けます。

```python
class Item:
    def __init__(self, id, name):
        self.id = id
        self.name = name


def retrieve_item(id):
    res = requests.get(f"https://api.example.com/items/{id}")
    data = res.json()
    return Item(id, data["name"])
```

このようにクラスメソッドと関数はそれほど大きな違いはありません。 ですが、 import Item としたときにまとめてインポートできるかどうかの違い（クラスの中でまとめて管理できるかどうかの違い）が大きいです。
