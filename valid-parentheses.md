给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

```
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    if (s === '') {
        return true;
    }
    if (s.length % 2 != 0) {
        return false;
    }
    
    let tempArr = [];
    
    for (let i = 0; i < s.length; i++) {
       if (s.charAt(i) === '(' || s.charAt(i) === '[' || s.charAt(i) === '{') {
           tempArr.push(s.charAt(i));
       } else if (s.charAt(i) === ')' && tempArr[tempArr.length - 1] === '(' || s.charAt(i) === ']' && tempArr[tempArr.length - 1] === '[' || s.charAt(i) === '}' && tempArr[tempArr.length - 1] === '{') {
              tempArr.pop();
          } 
    }
    
    if (tempArr.length === 0) {
        return true;
    } else {
        return false;
    }
};
```
