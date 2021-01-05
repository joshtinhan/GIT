# 區塊級作用域宣告
不存在變數提升，在變數宣告之前，此變數是不可使用的，並非只是undefined。
- let
- const
```JavaScript
    const teacher = {
        name:"Jake",
        age:25
    };
    //對物件進行修改沒問題
    teacher.name = "Lucy";
    teacher.age = "24";
    //直接修改常數的指向則會出錯
    const teacher = {
        name:"Lucy",
        age:24
    };
```
# 解構
- 陣列解構設定值
```JavaScript
    let students = ['Jake','Lucy','Benson','July'];
    //完全解構
    let [a,b,c,d] = students;
    console.log(a+" "+b+" "+c+" "+d)//Jake Lucy Benson July
    //不完全解構
    let [e,f,g] = students;
    console.log(e+" "+f+" "+g); //Jake Lucy Benson
    //只要最後一個
    let [,,,h] = students;
    console.log(h) //July
    //分析陣列中的第1個值，並將餘值放入另一個陣列
    let [i,...j] = students;
    console.log(i+" "+j) //Jake [Lucy,Benson,July]
    //溢位的變數被設定值為undefined
    let [k,l,m,n,o] = students;
    console.log(k+" "+l+" "+m+" "+n+" "+o); //Jake Lucy Benson July undefined
    //解構設定值的巢狀結構
    let array = [1,2,[5,6,7]];
    let [p,g,[r,s,t]] = array;
    console.log(""+p+q+r+s+t);//12567
```
- 物件解構設定值
```JavaScript
    let teacher = {
        name:"Jake",
        age:25,
        teaching:function(){
            console.log("teaching...");
        }
    };
    let {name:name,age:age} = teacher;
    //簡寫如下
    let (name,age,teaching) = teacher;
    console.log(name+" "+age); //Jake 25
    teaching();//teaching...
```
- 解構巢狀結構
```JavaScript
    let teacher = {
        name:"Jake",
        age:25,
        students:[{
            name:"Lucy",
            age:24
        },
        {
            name:"July",
            age:26
        }],
        teaching:function(){
            console.log("teaching...");
        }
    }
    let {students:[{name:name1},{name:name2}]} = teacher;
    console.log(name1+" "+name2); //Lucy July
```
- 解構應用： 交換兩個變數的值，不需要中間變數
```JavaScript
    let v1=10;
    let v2=11;
    [v1,v2] = [v2,v1];
    console.log(v1); //11
    console.log(v2); //10
```
# 箭頭函數
- 傳統函數寫法
```JavaScript
    function exp(a){
        return a*a;
    }
    let res = exp(5);
    console.log(res); //25
```
- 箭頭函數語法
```JavaScript
    let f = (a)=>{
        return a*a;
    }
    let res = f(5);
    console.log(res); //25
    //只有一個參數可以更簡化
    let f = a=>a*a;
    let res = f(5);
    console.log(res) //25
```
- 如果箭頭函數本體只有一行程式碼，且傳回的是物件，需要將物件包裹在小括號內，因為大括號預設會被解釋為程式區塊
```JavaScript
    let func = ({name,age})=>console.log(name,age);
    func({name:"Jake",age:25}); //Jake 25
```
- 箭頭函數中this的固定
```JavaScript
    function foo(){
        this.name = "foo";
        this.inline = ()=>{
            console.log(this.name);
        };
        this.outline = function(){
            console.log(this.name);
        }
    }
    //見this固定成為foo函數物件本身，無論呼叫方如何修改，this的指向都不變
    let obj = new foo();
    obj.inline(); //foo
    obj.inline.call({name:"Jake"}); //foo
    obj.outline(); //foo
    obj.outline.call({name:"Jake"}); //Jake
```
- 解析箭頭函數的this
不能將箭頭函數作為建置函數來使用，即不能使用**new**關鍵字來呼叫箭頭函數
**notice**: 定義的全域物件中箭頭函數的this之所以指向全域物件，是因為物件可以視為是全域物件呼叫**Object**建置函數建立的，
這個函數中的this當然指向其呼叫方全域物件，因此箭頭函數中的this固定成了全域物件。
```JavaScript
    function foo(){
        let _this = this;
        this.name = "foo";
        this.inline = ()=>{
            console.log(_this.name);
        }
        this.outline = function(){
            console.log(this.name);
        }
    }
```
# Set與Map資料結構
- Set集合結構
允許儲存任意類型資料的**唯一**值
```JavaScript
    //建立Set集合
    let set = new Set([1,2,3,4,4,2]);
    console.log(set); //Set {1,2,3,4}
    console.log(set.size); //4
    //向集合中插入元素
    set.add();
    //刪除元素
    set.delete();
    //刪除集合中所有元素
    set.clear()
```
```JavaScript
    let set = new Set();
    set.add('Jake');
    set.add('Lucy');
    console.log(set.entries());//SetIterator{['Jake','Jake'],['Lucy','Lucy']}
    set.forEach((element)=>{
        console.log(element);
    },set);
    /*將印出 
    Jake
    Lucy
    */
    for(item of set){ //物件屬性檢查用for-in;Set元素的檢查是用for-of
        console.log(item);
    }
    /*將印出
    Jake
    Lucy
    */
    console.log(set.has("Jake")); //true
    console.log(set.keys()); //SetIterator {'Jake','Lucy'}
    console.log(set.values()); //SetIterator {'Jake','Lucy'}
```