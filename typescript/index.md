/*
const range = (from: number, to: number): number[] => from < to ? [from, ...range(from + 1, to)] : []

const fold = <T>(array: T[], callback: (result: T, val: T) => T, initValue: T) => {
    let result: T = initValue
    for (let i = 0; i < array.length; i++) {
        const value = array[i]
        result = callback(result, value)
    }
    return result
}

const filter = <T>(array: T[], callback: (value: T, index?: number) => boolean): T[] => {
    let result: T[] = []
    for (let index: number = 0; index < array.length; index++) {
        const value = array[index]
        if (callback(value, index))
            result = [...result, value]
    }
    return result
}

const map = <T, Q>(array: T[], callback: (value: T, index?: number) => Q): Q[] => {
    let result: Q[] = []
    for (let index = 0; index < array.length; index++) {
        const value = array[index]
        result = [...result, callback(value, index)]
    }
    return result
}

let numbers: number[] = range(1, 100 + 1)
let result = fold(map(numbers, value => value * value), (result, value) => result + value, 0)
console.log(result)
*/

import { readFile } from "fs";
import { resolve } from "path";
import { values } from "ramda";

// number and boolean behave in a deep copy way
/*
let original = 1
let copied = original
copied += 2
console.log(original, copied) // 1 3
*/

// Object and Arrays behave in a shallow copy way
/*
const originalArray = [5, 3, 9, 7]
const shallowCopiedArray = originalArray
shallowCopiedArray[0] = 0
console.log(originalArray, shallowCopiedArray) // [ 0, 3, 9, 7 ] [ 0, 3, 9, 7 ]
*/

// Spread Operator and Deep copy
// Spread Operator behave in a shallow copy way and The original arrangement remains unchanged
/*
const oArray = [1, 2, 3, 4]
const deepCopiedArray = [...oArray]
deepCopiedArray[0] = 0
console.log(oArray, deepCopiedArray) // [ 1, 2, 3, 4 ] [ 0, 2, 3, 4 ]
*/

// Implement the sort method of an array as a pure function
// The pureSort function maintains the contents of the input array with a readonly type
/*
const pureSort = <T>(array: readonly T[]): T[] => {
    let deepCopied = [...array]
    return deepCopied.sort()
}

let beforeSort = [6, 2, 9, 0]
const afterSort = pureSort(beforeSort)
console.log(beforeSort, afterSort) // [ 6, 2, 9, 0 ] [ 0, 2, 6, 9 ]
*/

// Variable number function
// Do not compromise the contents of the parameters, so use readonly

/*
const mergeArray = <T>(...arrays: readonly T[][]): T[] => {
    let result: T[] = []
    for (let index = 0; index < arrays.length; index++) {
        const array: T[] = arrays[index]
        result = [...result, ...array]
    }
    return result
}

const mergedArray1: string[] = mergeArray(['Hello'], ['World'])
console.log(mergedArray1) // [ 'Hello', 'World' ]

const mergedArray2: number[] = mergeArray([1], [2, 3], [4, 5, 6], [7, 8, 9, 10])
console.log(mergedArray2) // [1, 2, 3, 4,  5, 6, 7, 8, 9, 10]
*/

// Tuple

// There is no tuple in js. Therefore, any type arrangement is declared.
// let tuple: any[] = ['hello world', 100, true]

// but any[] type is disables the function of the type script, so it is usesd as follows.
// const array: number[] = [1, 2, 3, 4]
// const tuple: [boolean, string] = [true, 'hello world']

// Repeater and generator
// Set downlevelIteration entry to true in tsconfig.json

// Repeater Characteristics
// Provide a method named next
// The next method returns an object with two properties: value and done

// const createRangeIterable = (from: number, to: number) => {
//     let currentValue = from
//     return {
//         next() {
//             const value = currentValue < to ? currentValue++ : undefined
//             const done = value == undefined
//             return { value, done }
//         }
//     }
// }

// const iterator = createRangeIterable(1, 3 + 1)
// while (true) {
//     const { value, done } = iterator.next()
//     if (done) break
//     console.log(value) // 1 2 3
// }

// Why use iterator?
// The range function consumes more memory to pre-generate a value before it is required.
// const range = (from, to)=>from < to ? [from, ...range(from+1,to)]:[]

// Iterable<T> and Iterator<T> Interface

// class xxx implements Iterable<T>{}
// [Symbol.iterator](): Iteator<T>{}

// class StringIterable implements Iterable<string>{
//     constructor(private strings: string[] = [], private curretIndex: number = 0) { }
//     [Symbol.iterator](): Iterator<string> {
//         const that = this
//         let currentIndex = that.curretIndex, length = that.strings.length

//         const iterator: Iterator<string> = {
//             next(): { value: string, done: boolean } {
//                 const value = currentIndex < length ? that.strings[currentIndex++] : undefined
//                 const done = value == undefined
//                 return { value, done }
//             }
//         }
//         return iterator
//     }
// }

// for (let value of new StringIterable(['hello', 'world', '!']))
//     console.log(value) // hello world !

// yield
// The field must be used within function*
// function* keyword are called generators

// function* generator() {
//     console.log('genertor started...')
//     let value = 1
//     while (value < 4)
//         yield value++
//     console.log('genertor finished...')
// }

// for (let value of generator())
//     console.log(value) 
//     // genertor started...
//     // 1
//     // 2
//     // 3
//     // genertor finished...

// setInterval function and Similarity of generator
// The way the generator works is called semicolutin
// Semicolutin, like the TS, is a single thread that makes behavior look like multiple threads.
// const intervalID = setInterval(callback, Cycle)

// Promise and async/await 

// Synchronize Way
// const buffer = readFileSync('data')

// Asynchronous Way
// readFile('data',callback()=>{}) 

// Use Promise and async/await 
// const readFilePromise = (filename: string): Promise<string> =>
// new Promise<string>((resolve,reject)=>{
//     readFile(filename,callback()=>{

//     })
// })

// (async ()=>{
//     const content = await readFilePromise('data')
// })

// single thread and asynchronous API
// JS,TS is work single thread so should not use synchronous API

// Promises
// const Variable : Promise<T> = new Promise<T>(callback)
// new Promise<T>((
//     resolve:(sucessValue:T)=>void,
//     reject:(any)=>void
// )=>{

// })

// Promise.all method (All conditions satisfied)
// all(promise object array : Promise[]):Promise<array of values or any>

// Promise.race method (Any conditions satisfied)
// race(promise object array : Promise[]):Promise<Type of value for the object that was first resolved>

// async and await Characteristics
// Available like a normal function
// Available as Promise object
// The function can return a value

// Principles and Applications of Functional Combinations

// high-order-function
// A function expression is a kind of value
// The function when one function returns another

// type FirstOrderFunc<T, R> = (T) => R
// type SecondOrderFunc<T, R> = (T) => FirstOrderFunc<T, R>
// type ThirdOrderFunc<T, R> = (T) => SecondOrderFunc<T, R>

// const add: ThirdOrderFunc<number, number> =
//     (x: number): SecondOrderFunc<number, number> =>
//         (y: number): FirstOrderFunc<number, number> =>
//             (z: number): number => x + y + z

// console.log(add(1)(2)(3)) // 6

// Closure
// Closure is a persistence scope
// Closer functionality is essential to implement higher order functions

// const makeNames = (): () => string => {
//     const names = ['Jack', 'Jane', 'Smith']
//     let index = 0
//     return (): string => {
//         if (index == names.length)
//             index = 0
//         return names[index++]
//     }
// }

// const makeName: () => string = makeNames()
// console.log([1, 2, 3, 4, 5, 6].map(n => makeName())) // [ 'Jack', 'Jane', 'Smith', 'Jack', 'Jane', 'Smith' ]

// composition function 
// combine functions that implement small functions several times to produce more meaningful functions
// It looks like a synthetic function

// const f = <T>(x: T): string => `f(${x})`
// const g = <T>(x: T): string => `g(${x})`
// const h = <T>(x: T): string => `h(${x})`
// y= h(h(f(x)))

// const compose = <T, R>(...functions: readonly Function[]): Function => (x: T): (T) => R => {
//     const deepCopiedFunctions = [...functions]
//     return deepCopiedFunctions.reverse().reduce((value, func) => func(value), x)
// }
// const composedFGH = compose(h, g, f)
// console.log(composedFGH('x')) // h(g(f(x)))

// pipe function 
// no reverse
// const f = <T>(x: T): string => `f(${x})`
// const g = <T>(x: T): string => `g(${x})`
// const h = <T>(x: T): string => `h(${x})`

// const pipe = <T, R>(...functions: readonly Function[]): Function => (x: T): (T) => R => {     
//     return deepCopiedFunctions.reduce((value, func) => func(value), x)
// }

// const piped = pipe(f,g,h)
// console.log(piped('x')) // h(g(f(x)))

// f function Signature: (number)=>string
// g function Signature: (string)=>string[]
// h function Signature: (string[])=>number

/// Lamda Library

// Lamda Package
// import * as R from 'ramda'

// R.range function
// R.range(min,max)

// import * as R from "ramda"

// console.log(R.range(1, 9 + 1))

// R.tap Debugging function
// R.tap(callback)(array)
// Understand how the values change step by step

// import * as R from "ramda"

// const numbers: number[] = R.range(1, 9 + 1)
// R.tap(n => console.log(n))(numbers) // [1,2,3,4,5,6,7,8,9]

// R.pipe function
// import * as R from 'ramda'

// const array: number[] = R.range(1, 10)
// R.pipe(R.tap(n => console.log(n)))(array)

// auto curry
// Can be used as a normal function or higher order function
