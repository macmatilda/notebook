# React AsyncStorage Usage

## key name define

('@'+appName+':'+keyName)

eg:

let STORAGE_KEY = '@ChaojihaoyiApp:zip';

## read
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
## write
```
        let value = "aaa";
        AsyncStorage.setItem(STORAGE_KEY, value)
            .then(()=>console.log('Save storage value=' + value))
            .catch((error)=>console.log('AsyncStorage error:' + error.message))
            .done();
```
