# 50 Core & Logic Questions — Arrays, Objects, Strings

Each question includes a hidden answer using collapsible `<details>` blocks.

---

# 🔷 Arrays (1–18)

---

## **1. What is the output and why?**
```js
const arr = [1,2,3];
arr[5] = 9;
console.log(arr.length, arr);
```
<details><summary><b>Answer</b></summary>
Length becomes **6** because index 5 is assigned.  
Empty slots remain as **empty × 2**.  
Output: `6 [1,2,3, empty × 2, 9]`
</details>

---

## **2. Remove duplicates from an array without using Set**
```js
const unique = arr.filter((v,i)=> arr.indexOf(v) === i);
```
<details><summary><b>Answer</b></summary>
Using filter + indexOf ensures first occurrence is kept.
</details>

---

## **3. Flatten nested array without flat()**
```js
const flat = (a)=> 
  a.reduce((acc,v)=> Array.isArray(v) ? acc.concat(flat(v)) : acc.concat(v), []);
```
<details><summary><b>Answer</b></summary>
Recursive reduce + concat.
</details>

---

## **4. Spread vs reference mutation**
<details><summary><b>Answer</b></summary>
Spread (`[...]`) makes a **shallow copy**; direct assignment keeps reference.
</details>

---

## **5. Why is `[10,5,2,20].sort()` wrong?**
<details><summary><b>Answer</b></summary>
Default sort is **lexicographical**.  
Should use: `sort((a,b)=>a-b)`
</details>

---

## **6. Merge two sorted arrays in O(n)**
<details><summary><b>Answer</b></summary>
Use **two-pointer** merge (like merge sort).
</details>

---

## **7. Rotate array right by k**
```js
k %= arr.length;
const rotated = [...arr.slice(-k), ...arr.slice(0,-k)];
```
<details><summary><b>Answer</b></summary>
Use slicing with modulo.
</details>

---

## **8. Find missing number from 1..n**
<details><summary><b>Answer</b></summary>
Use sum formula:  
`n*(n+1)/2 - actualSum`
</details>

---

## **9. First repeating element**
<details><summary><b>Answer</b></summary>
Use Set → first value seen twice.
</details>

---

## **10. Two-sum in O(n)**
<details><summary><b>Answer</b></summary>
Use Map storing complements.
</details>

---

## **11. Count frequency**
```js
arr.reduce((m,v)=> (m[v]=(m[v]||0)+1, m), {})
```
<details><summary><b>Answer</b></summary>
Classic reduce-based frequency map.
</details>

---

## **12. Remove falsy values**
```js
arr.filter(Boolean)
```
<details><summary><b>Answer</b></summary>
Boolean removes: 0, '', false, null, undefined, NaN.
</details>

---

## **13. Chunk array**
<details><summary><b>Answer</b></summary>

```js
for (let i=0;i<arr.length;i+=size)
  chunks.push(arr.slice(i,i+size));
```
</details>

---

## **14. Intersection efficiently**
<details><summary><b>Answer</b></summary>

```js
const set2 = new Set(arr2);
const inter = arr1.filter(v => set2.has(v));
```
</details>

---

## **15. Stable sort by property**
<details><summary><b>Answer</b></summary>
Use `.sort((a,b)=> a.key - b.key)`
</details>

---

## **16. Kadane’s max subarray**
<details><summary><b>Answer</b></summary>
Track `maxEnding` and `maxSoFar` in one pass.
</details>

---

## **17. Longest subarray with equal 0s & 1s**
<details><summary><b>Answer</b></summary>
Convert 0→-1, find longest subarray with **sum = 0** using Map.
</details>

---

## **18. Debounce + throttle**
<details><summary><b>Answer</b></summary>
Debounce delays execution; throttle limits execution per time window.
</details>

---

# 🟩 Objects (19–34)

---

## **19. Shallow vs deep clone**
<details><summary><b>Answer</b></summary>
Shallow copy references; deep clone copies recursively.
</details>

---

## **20. Object.assign vs spread**
<details><summary><b>Answer</b></summary>
Both shallow copy, but spread doesn't copy getters/setters.
</details>

---

## **21. Group by key**
```js
arr.reduce((g,o)=> ((g[o[key]] ??= []).push(o), g), {})
```
<details><summary><b>Answer</b></summary>
Use reduce + grouping logic.
</details>

---

## **22. Merge objects combining same keys into arrays**
<details><summary><b>Answer</b></summary>
For each key, push values into result arrays.
</details>

---

## **23. Check if empty object**
```js
Object.keys(obj).length === 0
```
<details><summary><b>Answer</b></summary>
Keys length check.
</details>

---

## **24. keys vs getOwnPropertyNames vs for-in**
<details><summary><b>Answer</b></summary>

- `Object.keys` → enumerable own props  
- `getOwnPropertyNames` → all own props  
- `for-in` → enumerable + prototype  
</details>

---

## **25. Object.freeze**
<details><summary><b>Answer</b></summary>
Prevents mutation but only at first level.
</details>

---

## **26. deepGet / deepSet**
<details><summary><b>Answer</b></summary>
Split path (“a.b.c”) and walk recursively.
</details>

---

## **27. Remove property immutably**
```js
const {x, ...rest} = obj;
```
<details><summary><b>Answer</b></summary>
Use object rest.
</details>

---

## **28. Convert {key: [values]} to array of objects**
<details><summary><b>Answer</b></summary>
Map keys and values into objects.
</details>

---

## **29. hasOwnProperty vs in**
<details><summary><b>Answer</b></summary>

- `in` → checks prototype chain  
- `hasOwnProperty` → own props only  
</details>

---

## **30. Keys ordered by frequency**
<details><summary><b>Answer</b></summary>
Build frequency map → sort entries.
</details>

---

## **31. Unique objects by id but keep last occurrence**
<details><summary><b>Answer</b></summary>
Use Map, last assignment wins.
</details>

---

## **32. Object.create(null)**
<details><summary><b>Answer</b></summary>
Creates object with **no prototype** — pure dictionary.
</details>

---

## **33. Memoization with WeakMap**
<details><summary><b>Answer</b></summary>
WeakMap auto-garbage-collects unused keys → perfect for caching objects.
</details>

---

## **34. Deep equality**
<details><summary><b>Answer</b></summary>
Compare types, lengths, and recursively values.
</details>

---

# 🟥 Strings (35–50)

---

## **35. Reverse string**
```js
str.split('').reverse().join('')
```
<details><summary><b>Answer</b></summary>
Classic reverse.
</details>

---

## **36. Palindrome ignoring punctuation**
<details><summary><b>Answer</b></summary>
Clean via regex → compare with reverse.
</details>

---

## **37. Character frequency**
```js
[...str].reduce((m,c)=> (m[c]=(m[c]||0)+1, m), {})
```
<details><summary><b>Answer</b></summary>
Reduce-based char map.
</details>

---

## **38. Anagram check**
<details><summary><b>Answer</b></summary>
Sort strings or compare frequency objects.
</details>

---

## **39. First non-repeating character**
<details><summary><b>Answer</b></summary>
Build frequency → first with freq 1.
</details>

---

## **40. Remove duplicate characters**
```js
[...new Set(str)].join('')
```
<details><summary><b>Answer</b></summary>
Set removes duplicates.
</details>

---

## **41. Longest common prefix**
<details><summary><b>Answer</b></summary>
Compare characters across all strings.
</details>

---

## **42. Longest substring with k distinct chars**
<details><summary><b>Answer</b></summary>
Sliding window + Map tracking counts.
</details>

---

## **43. Longest palindromic substring**
<details><summary><b>Answer</b></summary>
Expand around each index as center.
</details>

---

## **44. Title Case**
```js
str.toLowerCase().replace(/\b\w/g,c=>c.toUpperCase())
```
<details><summary><b>Answer</b></summary>
Regex-based capitalization.
</details>

---

## **45. Slugify**
```js
str.toLowerCase().replace(/\s+/g,'-').replace(/[^\w-]/g,'')
```
<details><summary><b>Answer</b></summary>
Convert to URL-friendly format.
</details>

---

## **46. Balanced parentheses**
<details><summary><b>Answer</b></summary>
Use stack to match opening/closing pairs.
</details>

---

## **47. Substring search**
<details><summary><b>Answer</b></summary>
Use naive O(n*m) or KMP algorithm.
</details>

---

## **48. Escape HTML**
<details><summary><b>Answer</b></summary>
Replace `& < > " '` with HTML entities.
</details>

---

## **49. Compress string (Run-length encoding)**
<details><summary><b>Answer</b></summary>
Count consecutive chars → build compressed string.
</details>

---

## **50. Sliding-window anagram search**
<details><summary><b>Answer</b></summary>
Compare window + target frequency sliding over string.
</details>

