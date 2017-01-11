# MarkDown Usage [参考](http://www.jianshu.com/p/q81RER)
- #  标题, #,##,###....
- -  "."
- 1. "1."
- ![] 链接
- > 引用
- ··· 代码
-  表格
   | Tables        | Are           | Cool  |
   | ------------- |:-------------:| -----:|
   | col 3 is      | right-aligned | $1600 |
   | col 2 is      | centered      |   $12 |
   | zebra stripes | are neat      |    $1 |
   
# React

## key name define

('@'+appName+':'+keyName)

```
let STORAGE_KEY = '@ChaojihaoyiApp:zip';
```

## read AsyncStorage
```
AsyncStorage.getItem(STORAGE_KEY)
    .then((value)=> {
        if (value != null) {
            console.log("local value=" + value);
            } else {
                console.log("local value is null");
            }
    })
    .catch((error)=>console.log('AsyncStorage error:' + error.message))
    .done();
```
## write AsyncStorage
```
let value = "aaa";
AsyncStorage.setItem(STORAGE_KEY, value)
    .then(()=>console.log('Save storage value=' + value))
    .catch((error)=>console.log('AsyncStorage error:' + error.message))
    .done();
```


## AsyncStorage Util
```
class Util {
    static async saveCache(key, value) {
        try {
            await AsyncStorage.setItem(key, value);
        } catch (error) {
            console.warn(error);
        }
    }

    static async getCache(key) {
        try {
            let value = await AsyncStorage.getItem(key);
            return value;
        }
        catch (error) {
            console.warn(error);
            return null;
        }
    }
}
```  
## AsyncStorage Util usage
```
async componentDidMount() {
    let key = "aaaa";
    await Util.saveCache(key, "1111");
    let value =await Util.getCache(key);
}
```
