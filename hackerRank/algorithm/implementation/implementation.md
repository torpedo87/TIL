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

##[grading students](https://www.hackerrank.com/challenges/grading)

```javascript
function main() {
    var n = parseInt(readLine());
    //console.log(n);
    for(var i = 0; i < n; i++){
        var grade = parseInt(readLine());
        // your code goes here
        if(grade<38){
            grade=grade;
        }else if((5-grade%5)<3){
            grade=(grade-grade%5)+5;
        }
        console.log(grade);
    }

}

```
***
