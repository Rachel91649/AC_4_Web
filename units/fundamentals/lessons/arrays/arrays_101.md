# Arrays

## Goals 
* Understand how to create an array, and why you'd want to. 
* Know basic array propery length.
* Know how to index / key into an array.
* Know how to change the value of an element in an array if given the index. 
* Know how to add and remove elements in an array. 
** push, pop, unshift, and shift 
* Know basic built-in array methods.
* Know what a multidimensional array is and how to index / key into it.


## Lesson

An array provides a convenient way to store a collection of __things__. Say we want to keep the numbers `2`, `3`, `5`, `7`, and `11` - all in one place. 
Instead of creating five separate variables we can create an array to store all these values. 
To create an array, we use the `[` and `]` brackets, and in between put whatever values we need separated by commas.
We call also call new on the Array class and pass in the elements desired. 

```js
let arr = [2, 3, 5, 7, 11]

// OR 

let arr = new Array(2, 3, 5, 7, 11)
```


Arrays can be accessed like strings. They also have indexes and a `length` property.

![array](../assets/array_elements.jpg)

We can put any type of variables as elements of an array. We can even mix different types in a single array or put an array itself as one
of the elements.

```js
let animals = ['cat', 'dog', 'raccoon']
let mixedArray = [2, 5, 'zebra', ["Can", "you", "believe", "it"]]
```
However it is **BEST** practice to use the same data type across all elements in the array.

We access the first element of the array by using index `0`, and the last by using index `array.length - 1`

```js
let animals = ['cat', 'dog', 'racoon', 'giraffe']

// this will print 'cat'
console.log(animals[0])

// this will print 'giraffe'
console.log(animals[animals.length -1])
```

## Adding, Removing and Modifying Elements

Unlike with strings, we can modify array elements:

```js
let animals = ['cat', 'dog', 'racoon', 'giraffe']
// changing the second element to 'zebra'
animals[1] = 'zebra'
console.log(animals)
// => [ 'cat', 'zebra', 'racoon', 'giraffe' ]
```

### Push

We can add elements to the end of an array by using the `push` method

```js
let numbers = [2, 4, 6]
// adding the number 8
numbers.push(8)
// now numbers will be: [2, 4, 6, 8]
// you can also add mulitipe elements by adding more elements to push. 
numbers.push(10, 12, 14)
// now numbers will be: [2, 4, 6, 8, 10, 12, 14]
```

### Pop
We can remove an element from the end of an array by using the `pop` method:

```js
let numbers = [2, 4, 6]
// removing the last element in the  array
numbers.pop()
// now array will be: [2, 4]
```

### Unshift

To add an element to the beginning of the array use the method: `unshift`. 
```js 
let numbers = [3, 5]
numbers.unshift(1)
// numbers is now: [1, 3, 5]
```

### Shift

To remove an element from the beginning of the array use the method: `shift`. 
```js 
let numbers = [3, 5]
numbers.shift()
// numbers is now: [5]
```
**Helpful trick**
Sometimes it can be hard to remember which methods do what. Here's a helpful trick. Push and pop are fairly easy. Pushing into the array, and poppiing off. Now with shift and unshift try and remember that unshift is like push but at the beginning. You can __tell__ they are similar because they both have the letter 'u' in them. The ones with the 'u' add to the array, the other two are removing. 

## Built-In Methods

### Slice
Arrays have a `slice` method that works by taking a slice of the array. The method takes in two arguments. The first is the starting index (inclusive), the second argument is the ending index (exclusive). 
```js
let arr = [4, 6, 8, 10, 12]
// getting [6, 8, 10]. arr will still be the same.
let sliceOfArr = arr.slice(1, 4)
```
### Splice
Let's talk about `splice`. This method takes a starting index as an argument and removes all array elements starting from that index.

```js
let arr = ['dog', 'cat', 'mouse']
arr.splice(1)
// arr contains ['dog']
```

We can specify a *delete count* as  a second argument:

```js
let arr = ['dog', 'cat', 'mouse']
arr.splice(1, 1)
// arr contains ['dog', 'mouse']
```

Any additional arguments to `splice` (after the first two) will be inserted into the array in place of the deleted ones.

```js
let arr = ['dog', 'cat', 'mouse', 'giraffe']
// removing 'cat' and 'mouse' and inserting 'fish'
arr.splice(1, 2, 'fish')
// arr contains ['dog', 'fish', 'giraffe']
```

`splice` **returns** an array containing the elements that were removed. The modification happens on the array that the method was called from.


### Join: Array --> String

Arrays can be converted to strings by using the `join` method. This method does not change the array, 
instead it **returns** a string. The string will contain the array element separated by a comma. We can also pass a separator as argument to `join`.

```js
let animals = ['cat', 'dog', 'llama']

console.log(animals.join())
// will log: 'cat,dog,llama'

console.log(animals.join(''))
// will log: 'catdogllama'

console.log(animals.join(' '))
// will log: 'cat dog llama'

console.log(animals.join('$'))
// will log: 'cat$dog$llama'
```

### Split: String --> Array

Strings can be converted to arrays, by using the `split` method. This method will separate the string based on the **separator** provided as an argument. For example, if our string is `'hello world'` and we provide a single space as an argument, we will get an array with two elements: `'hello'` and `'world'`:

```js
let str = 'hello world'
let arr = str.split(' ')
// arr will be ['hello', 'world']
```

If we provide an empty string as an argument to `split`, we will get an array with as many elements as there are characters in the string.

```js
let str = 'hello'
let arr = str.split('')
// arr will be: ['h','e','l','l','o']
```


## Array Equality Test

When we were dealing with strings and numbers, we could compare them by simply using the `===` operator. With arrays this will not work as expected:

```js
let arr1 = [2, 3, 4]
let arr2 = [2, 3, 4]
console.log(arr1 === arr2)
// will log: false
```

### Array Variables as References

Each array is like a container. In JavaScript,  even if two containers hold the same values, they are still not considered equal to each other. These containers are located somewhere in the computer's memory. A variable defined as an array holds the address in which the array is located. This means that if we have a variable `firstArr` and set another variable `secondArr` to be equal to `firstArr`, they will both have the address for the same array. When we modify either `firstArr` or `secondArr`, the same array will be modified.

```js
let firstArr = ['cat', 'dog', 'mouse']
let secondArr = firstArr
secondArr[0] = 'giraffe'
// firstArr[0] will also be 'giraffe'
console.log(firstArr[0])
```

The only case in which an equality test returns `true` for two array variables, is if the two variables hold the address of the same array.

```js
let arr1 = [1,  2, 3]
let arr2 = arr1
// equality test for arr1 and arr2 will return true
console.log(arr1 === arr2)
```

For now, if you'd like to compare arrays convert them to strings and then compare them. **Note** this will not always be 100% effective. 
For more information on the best way to compare [arrays](https://stackoverflow.com/questions/7837456/how-to-compare-arrays-in-javascript)

### Multidimensional Array
Multidimensional arrays are arrays that contain arrays as their elements. 
If an array is filled with arrays it is considered to be 2 dimensional (also often referred to as a matrix). 
If those arrays that are filling the array are also filled with arrays it becomes a 3 dimensional array or mulidimensional. 
Typically it is **BAD** practice to go further than 2 dimensional arrays. 

#### Indexing into Multidimensional Arrays
The indexing pattern of using brackets `[]` with the desired index remains the same. However, if you want to access elements in an array within an array, we must then index again into that. 

```js
let matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
]

console.log(matrix[0]) // => [1, 2, 3]
console.log(matrix[0][0]) // => 1 
console.log(matrix[0][1]) // => 2 
console.log(matrix[2][2]) // => 9 
```
