# Warmup
##[staircase](https://www.hackerrank.com/challenges/staircase)

```javascript
function main() {
    var n = parseInt(readLine());
    var result = ""
    //i=1...n
    //한줄 =공백(n-i)+#(i);
    //띄우기 i=1...n-1
    for(var i=1; i<n; i++){
        for(var j=n-i-1; j>=0; j--){
            result+=" "
        }
        for(var k=0; k<i; k++){
            result+="#"
        }
      result+="\n"  
    }
    for(var l=0; l<n; l++){
        result+="#"
    }

    console.log(result);

}

```
***
