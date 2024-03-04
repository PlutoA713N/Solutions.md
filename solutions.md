const items = [{
    name: 'Orange',
    available: true,
    contains: "Vitamin C",
}, {
    name: 'Mango',
    available: true,
    contains: "Vitamin K,Vitamin C",
}, {
    name: 'Pineapple',
    available: true,
    contains: "Vitamin A",
}, {
    name: 'Raspberry',
    available: false,
    contains: "Vitamin B, Vitamin A",

}, {
    name: 'Grapes',
    contains: "Vitamin D",
    available: false,
}];


/*

    1. Get all items that are available
    2. Get all items containing only Vitamin C.
    3. Get all items containing Vitamin A.
    4. Group items based on the Vitamins that they contain in the following format:
        {
            "Vitamin C": ["Orange", "Mango"],
            "Vitamin K": ["Mango"],
        }

        and so on for all items and all Vitamins.
    5. Sort items based on number of Vitamins they contain.

    NOTE: Do not change the name of this file

*/

const availableFruits = []
const vitamicCFruits = []
const vitaminAFruits = []


items.forEach((fruit) => {
    if(fruit.available) availableFruits.push(fruit)
})


items.forEach((fruit) => {
    if(fruit.contains.includes("Vitamin C")) vitamicCFruits.push(fruit)

})

items.forEach((fruit) => {
    if(fruit.contains.includes("Vitamin A")) vitaminAFruits.push(fruit)
})


const basket = {}

const vitamins = (string, fruit) => {
    let itemsay = string.split('')
    itemsay.forEach((vitamin) => {
        if(!basket[vitamin]) {
            basket[vitamin] = []
        }

        basket[vitamin].push(fruit);
    })
}


items.forEach((fruit) => {
    vitamins(fruit.contains, fruit.name)
})


// console.log(availableFruits, vitamicCFruits, vitaminAFruits)
// console.log(basket);


const sortFruits = items.slice().sort((fruitA, fruitB) => {
   return fruitB.contains.length - fruitA.contains.length
})

function bubbleSort(arr) {
    const len = arr.length;
  
    for (let i = 0; i < len; i++) {
      for (let j = 0; j < len - 1 - i; j++) {

        let fruit1 = arr[j].contains.split(',').length
        let fruit2 = arr[j + 1].contains.split(',').length

        console.log(fruit1, fruit2)
        // Compare adjacent elements
        if ( fruit1 > fruit2) {
          // Swap them if they are in the wrong order
          const temp = arr[j]
        //   fruit1 = fruit2;
        arr[j] = arr[j+1]
        arr[j+1] = temp
          fruit2 = temp;
        }
      }
    }
  
    return arr;
  }
  

const availableFruits2 = items.filter((fruit) => fruit.available)
const vitamicCFruits2 = items.filter((fruit) => fruit.contains.split(',').includes("Vitamin C"))
const vitamicAFruits2 = items.filter((fruit) => fruit.contains.split(',').includes("Vitamin A"))

const basket2 = items.reduce((basket, fruit) => {

    const vitamins2 = fruit.contains.split('')
    const fruit2 = fruit.name

    vitamins2.forEach((vitamin) => {
        if(!basket[vitamin]) {
            basket[vitamin] = []
        }

        basket[vitamin].push(fruit2);
    })

    return basket;

}, {})


const sortFruits2 = items.slice().sort((fruitA, fruitB) => {
   return fruitB.contains.length - fruitA.contains.length
})


function bubbleSort(arr) {
    const len = arr.length;
  
    for (let i = 0; i < len; i++) {
      for (let j = 0; j < len - 1 - i; j++) {

        let fruit1 = arr[j].contains.split(',').length
        let fruit2 = arr[j + 1].contains.split(',').length

        console.log(fruit1, fruit2)
        // Compare adjacent elements
        if ( fruit1 > fruit2) {
          // Swap them if they are in the wrong order
          const temp = arr[j]
        //   fruit1 = fruit2;
        arr[j] = arr[j+1]
        arr[j+1] = temp
          fruit2 = temp;
        }
      }
    }
  
    return arr;
  }
  

//   console.log(bubbleSort(items))
// console.log(basket2)

// console.log(vitamicAFruits2)

// console.log(availableFruits2)
// console.log(vitamicCFruits2)
