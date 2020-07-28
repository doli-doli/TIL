# CSS
- <head> 부분에 사용
- <style type="text/css"> </style>
  
## 사용예제
~~~
<style type="text/css">
  div {
      width: 800px;
      margin: auto;
      text-align: center;
   }
   table {
      width: 800px;
      border-collapse: collapse;      
   }
   
   td, th {
      border : 1px solid #4169e1;
      padding: 10px;
   }
   thead { 
      background-color: #6991e1;
      color: white;
   
   }
   th:nth-of-type(1) {
      width:80px;
   }
   th:nth-of-type(2) {
      width:200px;
   }
   th:nth-of-type(3) {
      width:300px;
   }
   th:nth-of-type(4) {
      width:200px;
   }
</style>
~~~
