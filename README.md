Javascript高级部分面试题

1．	请写出程序在以下三种场景下被触发的Value值:
function MAN() {};
        MAN.prototype = {
        value: "linkxiao",
        wakeUp: function(event) {
           console.log(this.value);//请分别写出value的值
        }
 };

var man=new MAN;//实例化

var button = document.getElementById('btn1');
    button.addEventListener(//第一种场景下被触发
        "click",
        man.wakeUp,
        false
    );

var button = document.getElementById('btn2');
    button.addEventListener(//第二种场景下被触发
        "click",
        function() {
            MAN.prototype.wakeUp.apply(man, arguments);
        },
        false
    );

var button = document.getElementById('btn3');
    button.value="[‘eileen’]";
    button.addEventListener(//第三种场景下被触发
        "click",
        function() {
            var value=this.value;
            MAN.prototype.wakeUp.apply(this, arguments);
        },
        false
);



2．	请输出程序在以下四种场景下的结果
var name = 'Linkxiao';
var obj = {
    name: 'John',
    prop: {
      name: 'Eileen',
      setName: function() {
         return this.name;
      }
   }
};

console.log(obj.prop.setName());//请输出结果

var getName = obj.prop.setName;

console.log(getName());//请输出结果

console.log(getName.call(obj))//请输出结果

console.log(getName.call(obj.prop))//请输出结果



3．	请写出下面程序的运算结果
(function() {
   var a = b = 5;
})();
console.log(a);//undefiend
console.log(b);//5


4．	请写出下面程序的运算结果
function LinkXiao(){
　　　　var n=999;
　　　　this.Add=function(){
           n+=1
       }
　　　　return function(){
　　　　　　return n;
　　　　}
　　}
　　var result=LinkXiao();
    　  console.log(result());
    　　console.log(Add());  
    　　console.log(result());

5．	高效实现以下数组除重: var data=[0,1,2,3,4,5,5,6,2,1,7];


6．	请写出一个小算法提取100以内的质数(即:除了1和自身外不能被任何数整除的数)；


7．	写一个验证手机号的正则表达式
