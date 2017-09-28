<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
      <br>
      <li><a href="http://vuejs-templates.github.io/webpack/" target="_blank">Docs for This Template</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    // ConstLetEs6()
    // AnalysisEs6()
    // SetWeakSet()
    // ArrowheadEs6()
    // ClassEs6()
   
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  created(){
    outerDta(this.msg)
  },
  methods:{
    
  }
}

let outerDta = (data =>{
  console.log("你好"+data)
})



function ConstLetEs6(){
  const b = 10; // 不可改变
  let a = 3;  //可改变
  {
    a = 5; //子作用域
  }
  alert('a' + a)
  alert('b' + b)
}

function AnalysisEs6(){
//   1.数组解构
  // let [a, b, c,d] = ["aa", "bb", 77,88];  
  // alert(b) //bb
  // let [a,b,[c,d],e] =["aa",'bb',[33,44],55]; //嵌套数组解构 
  // alert(c) //33
  // let [a,b,,e] =["aa",'bb',[33,44],55]; //空缺变量 
  // alert(e) //55
  // let [a,b,,e,f] =["aa",'bb',[33,44],55]; //多余变量 
  // alert(f) //undefined
  // let [a,b,,e,f='hello'] =["aa",'bb',[33,44],55]; //  默认值
  // alert(f) //hello
//   2.对象解构 
  // let obj=new Object(); 
  // obj={uid:121,uname:'张三'}; 
      // let {uid:id,uname:name}=obj; //顺序改变无影响 
      // alert(name); //张三
      // 小括号： 
      // let uid,uname; 
      // ({uid,uname} = obj); //必须有小括号，否则{}就会被解读为语句块 
      // alert(uname); //张三
// 3.字符串解构 
  // let [a, b, c, d] ="倚天屠龙"; 
  // console.log('a' + a,'b' + b,'c' + c,'d' + d); //a倚 b天 c屠 d龙
// 4.函数参数解构 
    // let obj=new Object(); 
    // obj={uid:121,uname:'张三'}; 
    // function analysis({uid,uname}){ 
    //     alert(uid); //121
    //     alert(uname); //张三
    // } 
    // analysis(obj); 
  //-------以下也正确 
    //  let obj={uid:121,uname:'张三'}; 
    //   function analysis({uname}){ 
    //     alert(uname); 
    //   } 
    //   analysis(obj); 
      
}
//Symbol是ES6新增的一种值类型数据，表示一种绝不重复的值
function SymbolEs6(){   //   用来区分两个形同的东西
  let s1 = Symbol(33); 
  let s2 = Symbol(33); 
  alert(s1.toString()); 
  alert(s1==s2);
}      
//Set和WeakSet 数据结构是ES6新增。   
function SetWeakSet(){

  /*
  // var set = new Set([1, 2, 3, 4, 2, 8, 4]); //两个2   
  // for (var elem of set) {   
  //   console.log(elem)   // 去掉重复
  // }   
//-----------循环用add添加赋值-----------------------   
    var set = new Set();   
    // [1, 2, 3, 4, 2, 8, 4].map(function (elem) {   
    //   set.add(elem);   
    // })   
    [1, 2, 3, 4, 2, 8, 4].map((elem)=>{   
      set.add(elem);   
    }) 
    for (let elem of set) { //for...of遍历   
      console.log(elem)   
    }   

//------扩展运算符--------------   
  var set = new Set([1, 2, 3, 4, 2, 8, 4]);   
  console.log(set)  //  obj对象
  var arr = [...set];//   扩展运算符（…）内部使用for…of循环, 对象转换成数组 相同的 输出一个
  console.log(arr);   //  [1, 2, 3, 4, 8]

//------清空、删除----------   
  var set = new Set([1, 2, 3, 4, 2, 8, 4]);   
  set.clear(); //清空   
  set.delete(8); //删除  只删除一条数据   
  var arr = [...set];    
  console.log(arr);   //空的
//------遍历键值------------   
  var set = new Set([1, 2, 3, 4, 2, 8, 4]);   

  set.forEach(function (value, key) {   
      console.log(value+'='+key);   //1=1 2=2 3=3 4=4 8=8   从输出结果可以看出，键和键值是相同的。   
    })   

//-----判断set中是否含有----   
    var set = new Set([1, 2, 3, 4, 2, 8, 4]);   
        console.log(set.has(8));   //true

//----遍历值--------   
    var set = new Set([1, 2, 3, 4, 2, 8, 4]);   
        // values  把 set 的值 赋给 setIter  转换成另一中 obj
    let setIter = set.values();   
      for(let val of setIter) {   
        console.log(val);   //1 2 3 4 8
      }   
    //----数量---------   
    console.log(set.size);  //5

    //---------------map 循环的的方法------------------------------   
    let set = new Set([1, 2, 3]);   
    set = new Set([...set].map(x => x * 2));   
    var arr = [...set];   
    console.log(arr);   // 返回Set结构：{2, 4, 6}
   
// WeakSet 的用法
    var weakset = new WeakSet();   
      let aObj = {a:'aa'};
      //声明变量的方法   
      let bObj = new String("你好");   
      let cObj = new Number(8);   
      weakset.add(aObj);   
      weakset.add(bObj);   
      weakset.add(cObj);   
    console.log(weakset.has(bObj)); //true 
    //---删除-----   
    weakset.delete(aObj);   
    bObj=null;      //把对象删除，weakset中的对象也没了   
    console.log(weakset.has(bObj)); //weakset不能取值，也不能显示，只用来表示是否有重复的对象    false
*/
    
}
// 箭头函数
    function ArrowheadEs6(){
      /*
      //1.单参数
        // function cheng(a=3){
        //   console.log(a*a)
        //     return a*a;
        // }
        //  函数名 参数  执行的方法 
        let cheng= (a=3)=>a*a;
        console.log(cheng(9));    //  81
      //2.多参数
        // function add(a,b){
        //     return a+b;
        // }
        let add = (a,b)=>a+b;   // 默认返回值
        console.log(add(3,9));  // 12
      //3.无返回值
        // function add(a,b){
        //     console.log(a+b);
        // }
        //  函数名 参数      执行的方法 (默认弹出)
        let add = (a,b)=>{console.log(a+b)   //12
        }; 
        console.log(add(3,9)); //undefined
      //4.多行
        // function add(a,b){
        //     console.log(a+b);
        //     return a+b;
        // }
        // let add = (a,b)=>{
        //     console.log(a+b); //   12
        //     return a+b;
        // };
        // console.log(add(3,9)); // 12
      
//2.如果箭头表达式仅仅就是简化了函数的命名，我们为什么要改变原来的习惯而去使用它呢？
  //箭头函数内部没有constructor方法，也没有prototype，所以不支持new操作。但是它对this的处理与一般的普通函数不一样。箭头函数的 this 始终指向函数定义时的this，而非执行时。
        // var o = {
        //       x : 1,
        //       func : function() { console.log(this.x) },
        //       test : function() {
        //   进入有 setTimeout 里时  要保存this  才能解决  问题
        //           setTimeout(function() {
        //               alert(this); //this指针转为全局
        //               this.func();
        //           }, 1000);
        //       }
        //   };
        //   o.test();  // TypeError : this.func is not a function

        //----改为箭头函数
        var o = {
            x : 1,
            func : function() { console.log(this.x) },
            test : function() {
                setTimeout(() => { this.func() }, 100);
            }
        };
        o.test();    //这回this就指向o了
        o.func();    //这回this就指向o了
      */
        }
// class 函数

 function ClassEs6(){
   /*
  //      之前写的 es5 的面向对象的方法
      //   function Person(name, age, job){
      //     this.name = name;  
      //     this.age = age;  
      //     this.job = job;
      //     this.friends = ['Shelby','Court'];  
      //   }
      //   Person.prototype.sayName = function () {
      //     console.log(this.friends);  //["Shelby", "Court"]
      //   };
      // let person1 = new Person('张三',26,'司机');  
      //       person1.sayName()


  // 1.  创建构造函数
      // es6 的书写方法
    class Person {  
        constructor(name, age, job) {  
          this.name = name;  
          this.age = age;  
          this.job = job;  
          this.friends = ['Shelby','Court'];  
        }  
        sayName () {  
          console.log(this.friends);  //["Shelby", "Court"]
        }  
      }  
      //new 构造函数 
      let person = new Person('张三',26,'司机');  
      person.sayName();  

    //2.静态方法：  
      class Point {  
          constructor(x, y) {  
              this.x = x;  
              this.y = y;  
          }  
          static distance(a, b) {  
              const dx = a.x - b.x;  
              const dy = a.y - b.y;  
              return Math.sqrt(dx*dx + dy*dy);  
          }  
      }  
        
      const p1 = new Point(5, 5);  
      const p2 = new Point(10, 10);  
        
      console.log(Point.distance(p1, p2));  //7.0710678118654755
*/
//4.继承:
      class Animal {   
          constructor(name) {  
              this.name = name;  
            }  
        
            speak() {  
              console.log(this.name + ' makes a noise.');  
            }  
          }  
        //extends 继承 Animal 同名 的时候 会调用后者
        class Dog extends Animal {  
          speak() {  
            console.log(this.name + ' barks 同名');  
          }
          speakq() {  
            console.log(this.name + ' barks 不同名');  
          }  
        }  
        let dog = new Dog('旺财');  
        let animal = new Animal('旺财');  
        dog.speakq();    //旺财 barks.
        dog.speak();    //旺财 makes a noise.
        animal.speak()  //旺财 makes a noise.



 }


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
