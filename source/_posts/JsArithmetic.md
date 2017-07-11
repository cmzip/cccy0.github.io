---
title: JsArithmetic
date: 2017-07-11 11:06:50
categories: JavaScript
---
*前几天学习了在Js里面实现的几个经典算法.*
***
# 判断闰年
```
<script language="javascript">
var str=prompt("请输入一个年份","");
var year=parseInt(str);
if(isNaN(year))
    {
    	alert("年份必须数值！");
    }
else{
	if(year%100==0)
    {
		if(year%400==0)
            {
			    document.write(year+"&nbsp"+"is leap year!");
            }
		else
            {
				document.write(year+"&nbsp"+"isnot leap year!");
			}
    }
	else if(year%4==0)
        {
			document.write(year+"&nbsp"+"is leap year!");
        }
		else
            {
			    document.write(year+"&nbsp"+"isnot leap year!");
            }
    }                  
</script>
```
# 输出乘法表
```
<script language="JavaScript">
    var i,j;
    for(i=1;i<10;i++){
        for(j=1;j<=i;j++){
            document.write(j+"*"+i+"="+i*j);
            if(i*j<10){
                document.write("&nbsp;&nbsp;");
            }
            document.write("&nbsp;&nbsp;");
        }
        document.write("<br/>");
    }
  </script>
```
# 输出100以内的第几个素数
```
<script language="JavaScript">
      var k=0;
      for(var i=2;i<=100;i++)
        {
          var flag=0;
          for(var j=2;j<i;j++){
              if(i%j==0)
                {
                    flag=1;
                    break;
                }      
          }
          if(flag==0){
              k++;
          }
          if(k==10){
              document.write("100以内的第10个素数是: "+i);
              break;
            }   
        }
   </script>

```
# 构造对象(函数+原型)
```
<script>
   function Person(name,age,gender){
	   this.name=name;
	   this.age=age;
	   this.gender=gender;};
   Person.prototype.country="China";
   Person.prototype.show=function(){
	   document.write("name:"+this.name+"<br/>");
	   document.write("age:"+this.age+"<br/>");
	   document.write("gender:"+this.gender+"<br/>");
	   document.write("country:"+this.country+"<br/>"); }
   var person=new Person("cccy0",3,"male");
   person.show();
</script>
```

