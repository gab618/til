# Map

Today I learned how to use ```map()``` method.

> The map() method creates a new array populated with the results of calling a provided function on every element in the calling array.


## Simple number array example

```javascript
const fahrenheit = [0, 32, 45, 46, 47, 91, 93, 121];
const celsius = fahrenheit.map((item) => {
    return Math.round((item - 32) * 5 / 9);
});
```
celsius:
```[-18, 0, 7, 8, 8, 33, 34, 49]```

## Object example

```javascript
const guests = [
    {name: 'GaBrIeL', vip: true, age: 22},
    {name: 'anton', vip: false, age: 23},
    {name: 'wiLL', vip: true, age: 16},
];

const upperCaseGuests = guests.map((guest) => {
    return Object.assign(guest, {
        name: guest.name.toUpperCase()
    });
});
```

upperCaseGuests:

```0: {name: "GABRIEL", vip: true, age: 22}```

```1: {name: "ANTON", vip: false, age: 23}```

```2: {name: "WILL", vip: true, age: 16}```

---