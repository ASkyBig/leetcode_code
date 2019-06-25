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
今天学到一个新知识：字符串可以当数组来取值。
```
"abc"[2] // 'c'
```
获取字符串的某个字符有两种方法。 
1、第一种是使用 charAt 方法：
`return 'cat'.charAt(1); // returns "a"`
2、另一种 (在ECMAScript 5中有所介绍) 是把字符串当作一个类似数组的对象，其中的每个字符对应一个数值索引：
`return 'cat'[1]; // returns "a"`
但是有一个注意点：使用括号访问字符串不可以对其进行删除或添加，因为字符串对应未知的属性并不是可读或配置的。

[来自 MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String)
