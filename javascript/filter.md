# Filter

Today I learned how to use ```filter()``` method.

> The filter() method creates an array filled with all array elements that pass a test (provided as a function).


## Simple number array example

```javascript
const ages = [32, 33, 16, 40];
const adults = ages.filter((age) => {return age >= 18});
```
adults:
```[32, 33, 40]```

## Object example

```javascript
const guests = [
    {name: 'Gabriel', vip: true, age: 22},
    {name: 'Anton', vip: false, age: 23},
    {name: 'Will', vip: true, age: 16},
];

const vips = guests.filter((guest) => {return guest.vip});
const adultVips = guests.filter((guest) => {return (guest.vip && guest.age >=18)});
```

vips:

```0: {name: "Gabriel", vip: true, age: 22}```

```1: {name: "Will", vip: true, age: 16}```

adultVips:

```0: {name: "Gabriel", vip: true, age: 22}```

---