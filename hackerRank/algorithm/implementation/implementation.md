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

##[apple and orange](https://www.hackerrank.com/challenges/apple-and-orange)

```javascript
function main() {
    var s_temp = readLine().split(' ');
    var s = parseInt(s_temp[0]);
    var t = parseInt(s_temp[1]);
    var a_temp = readLine().split(' ');
    var a = parseInt(a_temp[0]);
    var b = parseInt(a_temp[1]);
    var m_temp = readLine().split(' ');
    var m = parseInt(m_temp[0]);
    var n = parseInt(m_temp[1]);
    apple = readLine().split(' ');
    apple = apple.map(Number);
    orange = readLine().split(' ');
    orange = orange.map(Number);
    var appleNum=0;
    for(var i=0; i<m; i++){
        if(a+apple[i]>=s && a+apple[i]<=t){
            appleNum+=1;
        }
    }
    var orangeNum=0;
    for(var i=0; i<n; i++){
        if(b+orange[i]>=s && b+orange[i]<=t){
            orangeNum+=1;
        }
    }
    console.log(appleNum);
    console.log(orangeNum);
}


```
***

##[kangaroo](https://www.hackerrank.com/challenges/kangaroo)

```javascript
function main() {
    var x1_temp = readLine().split(' ');
    var x1 = parseInt(x1_temp[0]);
    var v1 = parseInt(x1_temp[1]);
    var x2 = parseInt(x1_temp[2]);
    var v2 = parseInt(x1_temp[3]);
    var n = (x2-x1)/(v1-v2);
    if(Number.isInteger(n) && n>0){
        console.log("YES");
    }else{
        console.log("NO");
    }
}

```
***
