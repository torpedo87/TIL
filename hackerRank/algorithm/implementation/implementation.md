##[mini-max sum](https://www.hackerrank.com/challenges/mini-max-sum)

```javascript
function main() {
  var a_temp = readLine().split(' ');
  var a = parseInt(a_temp[0]);
  var b = parseInt(a_temp[1]);
  var c = parseInt(a_temp[2]);
  var d = parseInt(a_temp[3]);
  var e = parseInt(a_temp[4]);
  var sortedArr=a_temp.sort(function(a, b){return a - b});

  var max=0;
  for(var i=1; i<sortedArr.length; i++){
      max+= sortedArr[i]*1;
  }
  var min=0;
  for(var i=0; i<sortedArr.length-1; i++){
     min+=sortedArr[i]*1;
  }
  console.log(min, max);
}

```
***
