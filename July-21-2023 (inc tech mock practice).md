Yesterday, I did code war problems and reviewed transposing strings.

📖 Currently, I am learning/working on reviewing JavaScript Alogrithims and Data Structures.

Complete the function using the rules below to modify the object passed to the function.

Your function must always return the entire records object.
If value is an empty string, delete the given prop property from the album.
If prop isn't tracks and value isn't an empty string, assign the value to that album's prop.
If prop is tracks and value isn't an empty string, you need to update the album's tracks array. First, if the album does not have a tracks property, assign it an empty array. Then add the value as the last item in the album's tracks array.

```
function updateRecords(records, id, prop, value) {
  // Access target album in record collection
  const album = records[id];
  // Update the album
  if (value === "") {
    delete album[prop];
  } else if (prop !== "tracks") {
    album[prop] = value;
  } else {
    album["tracks"] = album["tracks"] || [];
    album["tracks"].push(value);
  }
  // Return the full collection
  return records;
}
```
Iterate with JavaScript For Loops
You can run the same code multiple times by using a loop.

The most common type of JavaScript loop is called a for loop because it runs for a specific number of times.

For loops are declared with three optional expressions separated by semicolons:

for (a; b; c), where a is the initialization statement, b is the condition statement, and c is the final expression.

The initialization statement is executed one time only before the loop starts. It is typically used to define and setup your loop variable.

The condition statement is evaluated at the beginning of every loop iteration and will continue as long as it evaluates to true. When the condition is false at the start of the iteration, the loop will stop executing. This means if the condition starts as false, your loop will never execute.

The final expression is executed at the end of each loop iteration, prior to the next condition check and is usually used to increment or decrement your loop counter.

In the following example we initialize with i = 0 and iterate while our condition i < 5 is true. We'll increment i by 1 in each loop iteration with i++ as our final expression.
```
const ourArray = [];

for (let i = 0; i < 5; i++) {
ourArray.push(i);
}
ourArray will now have the value [0, 1, 2, 3, 4].
```
Iterate Odd Numbers With a For Loop
For loops don't have to iterate one at a time. By changing our final-expression, we can count by even numbers.

We'll start at i = 0 and loop while i < 10. We'll increment i by 2 each loop with i += 2.
```
const ourArray = [];

for (let i = 0; i < 10; i += 2) {
  ourArray.push(i);
}
ourArray will now contain [0, 2, 4, 6, 8].
```
Let's change our initialization so we can count by odd numbers.

Declare and initialize a variable total to 0. Use a for loop to add the value of each element of the myArr array to total.
```
// Setup
const myArr = [2, 3, 4, 5, 6];

// Only change code below this line
let total = 0;
for (let i = 0 ; i < myArr.length ; i++){
  total +=myArr[i]
```
}🎯 My goal is to work on the JavaScript Algorithims and Data Structures on FreeCodeCamp by today
and mock technical algorithims.

Here are the Mock Technical Algorithim questions and my solutions.

 Leap Years (Easy to get used to TDD)
 * 
 * As a user, I want to know if a year is a leap year, So that I can plan for 
 * an extra day on February 29th during those years.
 * 
 * Acceptance Criteria:
 * 
 * - All years divisible by 400 ARE leap years (so, for example, 2000 was indeed a leap year),
 * - All years divisible by 100 but not by 400 are NOT leap years 
 *   (so, for example, 1700, 1800, and 1900 were NOT leap years, NOR will 2100 be a leap year),
 * - All years divisible by 4 but not by 100 ARE leap years (e.g., 2008, 2012, 2016),
 * - All years not divisible by 4 are NOT leap years (e.g. 2017, 2018, 2019).
```
const leapYear = (years) => {
  if (years % 400 === 0) {
    return `leap year`;
  } else if (years % 100 === 0) {
    return `not a leap year`;
  } else if (years % 4 === 0) {
    return `leap year`;
  } else {
    return `not a leap year`;
  }
};
```
 String Calculator
 * 
 * You are building an educational website and want to create a simple 
 * calculator for students to use. The calculator will only allow addition 
 * and subtraction of non-negative integers.
 * 
 * Given an expression string using the "+" and "-" operators like 
 * "5+16-2", write a function to find the total.
 * 
 * Sample input/output:
 * calculate("6+9-12")  => 3
 * calculate("1+2-3+4-5+6-7") => -2
 * calculate("100+200+300") => 600
 * calculate("1-2-3-0") => -4
 * calculate("255") => 255
 * calculate("0-1-2-3") => -6

 */
 We use parseFloat to convert the string values to numbers before performing the addition.
 ```
 const total = (str) => {
  return str.split(/[+\-]/).reduce((a, b) => parseFloat(a) + parseFloat(b));
};
```
Write a function which takes a ROT13 encoded string as input and returns a decoded string.
charCode: This is the ASCII code of the uppercase letter that we want to decode (e.g., 'A' has an ASCII code of 65, 'B' has an ASCII code of 66, and so on).

charCode - 65: We subtract 65 from the character's ASCII code. This step is done to bring the range of characters from 'A' to 'Z' into the range 0 to 25.

charCode - 65 - 13: We subtract 13 from the result of step 2. This step is the core of the ROT13 decoding algorithm. Subtracting 13 effectively reverses the ROT13 encryption process.

charCode - 65 - 13 + 26: After step 3, we add 26 to handle any negative values that might result. This is because we want to ensure that the result stays within the range of 0 to 25.

(charCode - 65 - 13 + 26) % 26: Taking the modulo 26 of the result in step 4 ensures that the value wraps around in the range of 0 to 25. For example, if the result is 30, taking modulo 26 will give us 4, which corresponds to the letter 'E'.

(charCode - 65 - 13 + 26) % 26 + 65: Finally, we add 65 to the result in step 5. This brings the range of characters back to the ASCII code values of 'A' to 'Z'.

By performing these steps, we can correctly decode a ROT13 encoded uppercase letter back to its original letter. The same process can be applied to decode the entire ROT13 encoded string.
```
const rot13 = (message) => {
  return message
    .split("")
    .map((char) => {
      const charCode = char.charCodeAt(0);

      if (char >= "A" && char <= "Z") {
        const decodedCharCode = ((charCode - 65 - 13 + 26) % 26) + 65;
        return String.fromCharCode(decodedCharCode);
      } else {
        return char;
      }
    })
    .join("");
};
```
