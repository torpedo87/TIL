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
##[divisible sum pairs](https://www.hackerrank.com/challenges/divisible-sum-pairs)

```javascript
function main() {
    var n_temp = readLine().split(' ');
    var n = parseInt(n_temp[0]);
    var k = parseInt(n_temp[1]);
    a = readLine().split(' ');
    a = a.map(Number);
    var result=0;
    for(var i=0; i<n; i++){
        for(var j=i+1; j<n; j++){
            if((a[i]+a[j])%k==0){
                result+=1;
            }
        }
    }
    console.log(result);
}

```
***

##[camelcase](https://www.hackerrank.com/challenges/camelcase)

```javascript
function main() {
    var s = readLine();
    var upperNum=0;
    for(var i=0; i<s.length; i++){
        if(s[i] === s[i].toUpperCase()){
            upperNum+=1;
        }
    }
    console.log(upperNum+1);
}

```
***

##[bon appetit](https://www.hackerrank.com/challenges/bon-appetit)

```javascript
function main(input) {
    //Enter your code here
    var n_temp = readLine().split(' ');
    var n = parseInt(n_temp[0]);
    var k = parseInt(n_temp[1]);
    cost = readLine().split(' ');
    cost = cost.map(Number);
    charge = readLine().split(' ');
    charge = parseInt(charge[0]);
    var totalCost=0;
    for(var i=0; i<n; i++){
        totalCost+=cost[i]
    }
    //console.log(totalCost);
    var shareCost=(totalCost - cost[k])/2;
    //console.log(shareCost);
    if(charge===shareCost){
        console.log("Bon Appetit");
    }else{
        console.log(charge-shareCost);
    }
}

process.stdin.resume();
process.stdin.setEncoding('ascii');

var input_stdin = "";
var input_stdin_array = "";
var input_currentline = 0;

process.stdin.on('data', function (data) {
    input_stdin += data;
});

process.stdin.on('end', function () {
    input_stdin_array = input_stdin.split("\n");
    main();    
});

function readLine() {
    return input_stdin_array[input_currentline++];
}
```
***

##[the hurdle race](https://www.hackerrank.com/challenges/the-hurdle-race)

```javascript
function main() {
    var n_temp = readLine().split(' ');
    var n = parseInt(n_temp[0]);
    var k = parseInt(n_temp[1]);
    height = readLine().split(' ');
    height = height.map(Number);
    // your code goes here
    var maxHeight = height.sort(function(a,b){return b-a})[0];
    if(maxHeight>k){
        console.log(maxHeight-k);
    }else{
        console.log(0);
    }
}

```
***
