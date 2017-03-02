##[2D array-DS](https://www.hackerrank.com/challenges/2d-array)

```javascript
function main() {
    var arr = [];
    for(arr_i = 0; arr_i < 6; arr_i++){
       arr[arr_i] = readLine().split(' ');
       arr[arr_i] = arr[arr_i].map(Number);
    }
    var sumArr=[];
    for(var i=0; i<arr.length-2; i++){
        for(var j=0; j<arr.length-2; j++){
            //첫째줄
            var firstLine=arr[i][j]+arr[i][j+1]+arr[i][j+2];
            var secondLine=arr[i+1][j+1];
            var thirdLine=arr[i+2][j]+arr[i+2][j+1]+arr[i+2][j+2];
            var sum=firstLine+secondLine+thirdLine;
            sumArr.push(sum);
        }
    }
    sumArr.sort(function(a,b){return b-a});
    console.log(sumArr[0]);
}

```
***
