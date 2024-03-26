# Date

```javascript
    let myDate = new Date();
```

```javascript
    console.log(myDate.getTime());
```
Output : `Returns the stored time value in milliseconds since midnight, January 1, 1970 UTC`

```javascript
    console.log(typeof myDate);
```
Output : `object`

```javascript
    console.log(myDate.toString());
```
Output : `Tue Mar 26 2024 16:02:06 GMT+0530 (India Standard Time)`

```javascript
    console.log(myDate.toDateString());
```
Output : `Tue Mar 26 2024`

```javascript
    console.log(myDate.toLocaleDateString());
```
Output : `26/3/2024`

```javascript
    console.log(myDate.toLocaleString());
```
Output : `26/3/2024, 4:04:25 pm`

```javascript
    const option1 = {
    weekday: "long",
    year: "numeric",
    month: "long",
    day: "numeric",
    };

    console.log(myDate.toLocaleString("default", option1)); //Tuesday, 26 March, 2024

    const option2 = {
    weekday: "short",
    year: "2-digit",
    month: "short",
    day: "2-digit",
    };

    console.log(myDate.toLocaleString("default", option2)); //Tue, 26 Mar, 24

    const option3 = {
    weekday: "narrow",
    year: "numeric",
    month: "narrow",
    day: "numeric",
    };

    console.log(myDate.toLocaleString("default", option3)); //T, 26 M, 2024
```

```javascript
    console.log(myDate.toLocaleTimeString());
```
Output : `4:05:04 pm`

# Personalized Date

```javascript
    //yyyy-mm-dd
    let myDate = new Date("2002-06-19");
    console.log(myDate.toDateString());
```
Output : `Wed Jun 19 2002`

```javascript
    //(year , month [ 0 based ] , day)
    let myDate = new Date(2002, 5, 19);
    console.log(myDate.toDateString());
```
Output : `Wed Jun 19 2002`

# Time

```javascript
    let date = Date.now();

    //1711464265814 (i.e in milliseconds)
    console.log(date);

    //1711464265 (i.e in seconds)
    let dateInSec = Math.floor(date / 1000);
    console.log(dateInSec);
```

# Clock

```javascript
    let hours = myDate.getHours().toString().padStart(2, 0);
    let mins = myDate.getMinutes().toString().padStart(2, 0);
    let secs = myDate.getSeconds().toString().padStart(2, 0);

    //postfix (i.e AM or PM)
    let postFix = hours > 12 ? "PM" : "AM";

    //converting hours into 12 hour clock format
    hours = hours % 12;

    //replacing 00 with 12
    hours = hours == 0 ? 12 : hours;

    let clock = `${hours} : ${mins} : ${secs} ${postFix}`;
    console.log(clock);
```