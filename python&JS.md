## Why sometime we need to treat mutable types as immutable?

```python
marks = [100, 80, 75]
marks[1] = 60
marks.append(50)
marks.pop()
```

```python
dailyCheckInTimeMonday = {'Vinay': 9.15, 'Himanshu': 9.30, 'Bhargav': 9.45}
print('Monday: ',dailyCheckInTimeMonday)
print()
dailyCheckInTimeTuesday = dailyCheckInTimeMonday
dailyCheckInTimeTuesday['Vinay'] = 8.0
print('Monday: ',dailyCheckInTimeMonday)
print('Tuesday: ',dailyCheckInTimeTuesday)
```

# PYTHON

## LIST

### 1. mylist.SORT() VS SORTED(mylist)

```python
mylist = [3, 1, 4]
mylist_copy = mylist
print(id(mylist), id(mylist_copy))

mylist.sort()
print(id(mylist), id(mylist_copy))

mylist = sorted(mylist_copy)
print(id(mylist), id(mylist_copy))
```

### 2. mylist.COPY() VS mylist_copy = mylist

```python
fruits = ['Mango', 'Apple', 'Grapes']
fruits_copy1 = fruits
fruits_copy2 = fruits.copy()
print('Fruits:', id(fruits))
print('Fruits (Copy 1):', id(fruits_copy1))
print('Fruits (Copy 2):', id(fruits_copy2))
```

### 3. LIST SLICING AND LIST COMPREHENSION

```python
names = ['Ram', 'Shyam', 'Ghanshyam']
print(id(names),'\n', names)
print(id(names[:]),'\n', names[:])
print(id([name for name in names]),'\n', [name for name in names])
```

### 4. APPEND and EXTEND VS CONCATINATION

```python
state_codes = ['UK','UP', 'HP']
state_codes_copy = state_codes

print('Original: ', id(state_codes))

state_codes.append('DL')
print('Append: ', id(state_codes))

state_codes.extend(['KL', 'TN'])
print('Extend: ', id(state_codes))

state_codes = state_codes + ['PN']
print('Concat: ', id(state_codes))
```

### 5. REVERSE() VS REVERSED()

```python
dailyPushUps = [50, 40, 100, 80]
dailyPushUps_Copy = dailyPushUps
print('Original: ', id(dailyPushUps))

dailyPushUps.reverse()
print('Reverse: ', id(dailyPushUps))

dailyPushUps = list(reversed(dailyPushUps))
print('Reversed: ', id(dailyPushUps))
```

## DICTIONARY

### 1. mydict.COPY() VS mydict_copy = mydict

```python
fruitsQuantity = {'Mango': 5, 'Apple': 2, 'Banana':12}
fruitsQuantity_copy1 = fruitsQuantity
fruitsQuantity_copy2 = fruitsQuantity.copy()
print('Fruits:', id(fruitsQuantity))
print('Fruits (Copy 1):', id(fruitsQuantity_copy1))
print('Fruits (Copy 2):', id(fruitsQuantity_copy2))
```

### 2. Dictionary Comprehension

```python
studentMarks = {'Vinay': 100, 'Himani': 80, 'Harsh': 85}
print(id(studentMarks),'\n', studentMarks)
print(id(dict(studentMarks.items())),'\n', dict(studentMarks.items()))
print(id({student:marks for student,marks in studentMarks.items()}),'\n', {student:marks for student,marks in studentMarks.items()})
```

### 3. mydict.clear() vs mydict = {}

```python
studentMarks = {'Vinay': 100, 'Himani': 80, 'Harsh': 85}
studentMarksCopy = studentMarks
print('Original: ', id(studentMarks))

studentMarksCopy = dict()
print('dict(): ', id(studentMarksCopy))

studentMarks.clear()
print('Clear: ', id(studentMarks))
```

## SET

### 1. CLEAR() VS ASSIGNING AN EMPTY SET

```python
cities = {'Mumbai', 'Delhi', 'Chennai'}
cities_copy = cities
print('Original: ', id(cities))

cities_copy = set()
print('set(): ', id(cities_copy))

cities.clear()
print('Clear: ', id(cities))
```

### 2. ADD VS UNION

```python
actors = {'Tiger Shroff', 'Shahrukh Khan', 'Vicky Kaushal'}
actors_Copy = actors
print('Original: ', id(actors))

actors.add('Ranbir Kapoor')
print('.add(): ', id(actors))

actors = actors.union({'Akshay Kumar'})
print('.union(): ', id(actors))
```

### 3. UPDATE VS UNION

```python
actors = {'Tiger Shroff', 'Shahrukh Khan', 'Vicky Kaushal'}
actors_Copy = actors
print('Original: ', id(actors))

actors.update({'Ranbir Kapoor'})
print('.update(): ', id(actors))

actors = actors.union({'Akshay Kumar'})
print('.union(): ', id(actors))
```

### 4. INTERSECTION_UPDATE VS INTERSECTION

```python
actors = {'Tiger Shroff', 'Shahrukh Khan', 'Vicky Kaushal'}
actors_Copy = actors
print('Original: ', id(actors))

actors_Copy = actors_Copy.intersection({'Akshay Kumar', 'Tiger Shroff'})
print('.intersection(): ', id(actors_Copy))

actors.intersection_update({'Ranbir Kapoor', 'Tiger Shroff'})
print('.intersection_update(): ', id(actors))
```

### 5. COPY() VS DIRECT ASSIGNMENT

```python
fruits = {'Mango', 'Apple', 'Grapes'}
fruits_copy1 = fruits
fruits_copy2 = fruits.copy()
print('Fruits:', id(fruits))
print('Fruits (Copy 1):', id(fruits_copy1))
print('Fruits (Copy 2):', id(fruits_copy2))

```

| **Type**       | **Memory Modification Methods**                                      | **Memory Address Change Methods**                                                    |
| -------------- | -------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **List**       | **mylist.sort()**- (modifies the mylistay in place)                  | **sorted(mylist)**- (creates a new sorted mylistay)                                  |
|                | **mylist.copy()**- (creates a shallow copy in place)                 | **new_mylist = mylist**- (assigns a new reference to the same mylistay)              |
|                | **mylist.reverse()**- (reverses the mylistay in place)               | **new_mylist = list(reversed(mylist))**- (creates a new reversed mylistay)           |
| **Dictionary** | **dict_obj.clear()**- (removes all keys in place)                    | **d = {}**- (assigns a new empty dictionary)                                         |
|                | **d.copy()**- (creates a shallow copy in place)                      | **d_copy1 = d**- (assigns a new reference to the same dictionary)                    |
|                | **d_copy1 = {k:v for k,v in d.items()}**- (creates a new dictionary) | **d_copy1 = {k:v for k,v in d.items()}**- (creates a new dictionary)                 |
| **Set**        | **set_obj.clear()**- (clears the set in place)                       | **set_obj = set()**- (assigns a new empty set)                                       |
|                | **set_obj.update()**- (updates set in place)                         | **new_set = set_obj.union(new_set)**- (creates a new set with added elements)        |
|                | **set_obj.intersection_update()**- (modifies the set)                | **new_set = set_obj.intersection(other_set)**- (creates a new set from intersection) |
|                | **set_obj.add()**- (adds elements in place)                          | **new_set = set_obj.copy()**- (creates a new copy of the set)                        |
|                | **set_obj.pop()**- (removes an arbitrary element in place)           | **new_set = {x for x in set_obj if x != 2}**- (creates a new set by filtering)       |

# JAVASCRIPT

## ARRAY

### 1. ARRAY.push() vs ARRAY.concat()

```js
let state_codes = ["UK", "UP", "HP"];
let state_codes_copy = state_codes;

console.log("Original: ", state_codes);

state_codes.push("DL");
console.log("Push: ", state_codes);

state_codes = state_codes.concat(["PN"]);
console.log("Concat: ", state_codes);
```

### 2. SLICE() VS SPLICE()

```js
let names = ["Ram", "Shyam", "Ghanshyam", "Vinay", "Rohit", "Yogesh"];
let names_copy = names;
console.log("Original names: ", names);
let slicedNames = names.slice(0, 4);
console.log("Original names: ", names);
let splicedNames = names.splice(0, 4);
console.log("Original names: ", names);
```

### 3. ARRAY.reverse() vs ARRAY.slice().reverse()

```js
let dailyPushUps = [50, 40, 100, 80];
let dailyPushUps_Copy = dailyPushUps;
console.log("Original: ", dailyPushUps);
dailyPushUps.reverse();
console.log(".reverse(): ", dailyPushUps);
let sliceReversed = dailyPushUps.slice().reverse();
console.log(".slice.reverse(): ", dailyPushUps);
```

### 4. ARRAY.map() vs ARRAY.forEach

```js
let dailyPushUps = [50, 40, 100, 80];
let dailyPushUps_Copy = dailyPushUps;

let doubledPushUps = dailyPushUps.map((pushUps) => pushUps * 2);
console.log("Original: ", dailyPushUps);
console.log("Map: ", doubledPushUps);
console.log();

dailyPushUps.forEach((value, index, dailyPushUps) => {
  dailyPushUps[index] = value * 2;
});
console.log("Original: ", dailyPushUps);
console.log("forEach: ", dailyPushUps);
```

### 5. ARR.shift() VS ARR.slice(1)

```js
let dailyPushUps = [50, 40, 100, 80];
let dailyPushUps_Copy = dailyPushUps;

let pushupSlice = dailyPushUps.slice(1);
console.log("Original: ", dailyPushUps);
console.log("Sliced: ", pushupSlice);
console.log();

dailyPushUps.shift();
console.log("Shift: ", dailyPushUps);
```

## OBJECT

### myobj_copy = myobj VS Object.assign()

```js
let fruitsQuantity = { Mango: 5, Apple: 2, Banana: 12 };
let fruitsQuantity_copy1 = fruitsQuantity;
fruitsQuantity_copy1.Apple = 4;

let fruitsQuantity_copy2 = Object.assign({}, fruitsQuantity);
fruitsQuantity_copy1.Mango = 14;

console.log("Fruits:", fruitsQuantity);
console.log("Fruits (Copy 1):", fruitsQuantity_copy1);
console.log("Fruits (Copy 2):", fruitsQuantity_copy2);
```

| **Type**    | **Memory Modification Methods**                  | **Memory Address Change Methods**                                     |
| ----------- | ------------------------------------------------ | --------------------------------------------------------------------- |
| **Arrays**  | **arr.push()**- (modifies the array in place)    | **arr.concat()**- (creates a new array)                               |
|             | **arr.reverse()**- (modifies the array in place) | **arr.slice().reverse()**- (creates a new reversed array)             |
|             | **arr.shift()**- (modifies the array in place)   | **arr.slice(1)**- (creates a new array with sliced elements)          |
|             | **arr.splice()**- (modifies the array in place)  | **arr.slice()**- (creates a new array with sliced elements)           |
|             | **arr.forEach()**- (modifies the array in place) | **arr.map()**- (creates a new array)                                  |
| **Objects** | **Object.assign()**- (creates a shallow copy)    | **Direct Assignment**- (assigns the reference of the original object) |

```

```
