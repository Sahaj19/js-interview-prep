# break keyword
- Used to exit the loop completely when a certain condition is met.

```javascript
for (let i = 1; i <= 10; i++) {
  if (i === 5) {
    console.log("5 Detected");
    break;
  }
  console.log(i);
}
```

### Output
```javascript
1
2
3
4
5 Detected
```

# continue keyword
- Useful for skipping certain iterations based on a condition without terminating the loop entirely.

```javascript
for (let i = 0; i <= 10; i++) {
  if (i === 5) {
    console.log("5 Detected");
    continue;
  }
  console.log(i);
}
```

### Output
```javascript
0
1
2
3
4
5 Detected
6
7
8
9
10  
```