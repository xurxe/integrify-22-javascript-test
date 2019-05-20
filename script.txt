/* 1. Create a function which solve quadratic equation ax2 + bx + c = 0. A quadratic equation may have one, two or no solution. The function should return a set of the solution/s.

console.log(solveQuadratic()); //Set(1) {0}
console.log(solveQuadratic(1, 4, 4)); //Set(1) {-2}
console.log(solveQuadratic(1, -1, -2)); //{2, -1}
console.log(solveQuadratic(1, 7, 12));//Set(2) {-3, -4}
console.log(solveQuadratic(1, 0, -4));//{2, -2}
console.log(solveQuadratic(1, -1, 0)); //{1, 0} */

function solveQuadratic(a, b, c) {

    // calculate both solutions
    const x1 = (-b + (b**2 - 4*a*c)**0.5) / 2*a;
    const x2 = (-b - (b**2 - 4*a*c)**0.5) / 2*a;

    // create new set with unique values (it won't add the solution if it's NaN)
    const set = new Set([x1, x2])

    console.log(set);
    return set;
};

solveQuadratic(); // note: I didn't make it so that it would return instead of NaN when no values are passed (as in the example); this is because returning 0 here would mean that the number 0 is one of the solutions to the equation(which would be incorrect, because there was no equation to solve)
solveQuadratic(1, 4, 4);
solveQuadratic(1, -1, -2);
solveQuadratic(1, 7, 12);
solveQuadratic(1, 0, -4);
solveQuadratic(1, -1, 0);



/* 2. Create a function called isPrime which check if a number is prime or not.

console.log(isPrime(0)); // false
console.log(isPrime(1)); // false
console.log(isPrime(2)); // true
console.log(isPrime(3)); // true
console.log(isPrime(5));// true */

function isPrime(number) {

    // if not a number, not an integer, or below 2: not prime
    if (
        typeof number !== 'number'
        || !Number.isInteger(number)
        || number < 2
    ) {
        console.log(false)
        return false;
    }

    // otherwise...
    else {

        // loop through the divisors (starting at 2, and up until half the number)
        for (let divisor = 2; divisor < Math.ceil((number + 1) / 2); divisor++) {

            // if any of the divisors is a factor, the number is not prime
            if (number % divisor === 0) {
                console.log(false);
                return false;
            };
        };

        // if the loop ran its course without returning, the number is prime
        console.log(true);
        return true;
    };
};

isPrime(0);
isPrime(1);
isPrime(2);
isPrime(3);
isPrime(5);



/* 3. Write a function rangeOfPrimes. It takes two parameters, a starting number and an ending number . The function returns an object with properties primes and count. The primes value is an array of prime numbers and count value is the number of prime numbers in the array. See example:

console.log(rangeOfPrimes(2, 11));
//{primes:[2, 3, 5, 7, 11], count:5}
console.log(rangeOfPrimes(50, 60));
//{primes:[53, 59], count:2}
console.log(rangeOfPrimes(95, 107));
//{primes:[97, 101, 103, 107], count:4} */

function rangeOfPrimes(first, last) {

    if (typeof first !== 'number') {
        console.log(null, `'${first} is not a number.`)
        return null;
    }

    else if (typeof last !== 'number') {
        console.log(null, `'${last} is not a number.`)
        return null;
    };

    // declare empty array for prime numbers
    let primes = [];

    // loop through the range
    for (let number = first; number < last + 1; number++) {

        // all numbers have at least one factor (themselves)
        let factors = 1;

        // loop through the divisors of the number, starting at 1 and ending at half the number. Examples:
        // If number = 1, the loop doesn't run
        // If number = 2, the loop runs once (for divisor 1)
        // If number = 6, the loop runs three times (for divisors 1, 2, and 3)
        // If number = 7, the loop runs three times (for divisors 1, 2, and 3)
        for (let divisor = 1; divisor < Math.ceil((number + 1) / 2); divisor++) {

            // when the remainder is zero, the divisor is a factor, so update the tally
            if (number % divisor === 0) {
                factors++
            };
        };

        // if the number has exactly two factors (1 and itself), it is prime
        if (factors === 2) {
            primes.push(number)
        };
    };

    console.log({primes: primes, count: primes.length});
    return {primes: primes, count: primes.length};
};

rangeOfPrimes(2, 11);
rangeOfPrimes(50, 60);
rangeOfPrimes(95, 107);



/* 4. Create a function called isEmpty which check if the parameter is empty. If the parameter is empty, it returns true else it returns false.

isEmpty('') // true
isEmpty(' ') // false
isEmpty('Asabeneh') // false
isEmpty([]) // true
isEmpty(['HTML', 'CSS', 'JS']) // false;
isEmpty({}) //true
isEmpty({name:'Asabeneh', age:200}) // false */

function isEmpty(value){

    // numbers and booleans
    if (typeof value === 'number' || typeof value === 'boolean') {
        console.log(false);
        return false;
    }

    // undefined and null
    else if (value === undefined || value === null) {
        console.log(true);
        return true;
    }

    // strings and arrays
    else if (value.length === 0) {
        console.log(true);
        return true;
    }

    // objects
    else if (Object.entries(value).length === 0) {
        console.log(true);
        return true;
    }

    else {
        console.log(false);
        return false;
    };
};

isEmpty('');
isEmpty(' ');
isEmpty('Asabeneh');
isEmpty([]);
isEmpty(['HTML', 'CSS', 'JS']);
isEmpty({});
isEmpty({name:'Asabeneh', age:200});



/* 5.

a. Create a function called reverse which take a parameter and it returns the reverse of the parameter. Don't use the built in reverse method.
reverse('cat'); // tac
reverse('123'); // 321 */

function reverse(input) {
    // if not string, convert to string
    if (typeof input !== 'string') {
        input = input.toString();
    }

    // split string into array
    array = input.split('')

    // declare empty array
    let reversedArray = [];

    // push the characters backwards
    for (let i = 0; i < array.length; i++) {
        reversedArray.unshift(array[i])
    };

    // join array into string
    reversedString = reversedArray.join('');

    console.log(reversedString);
    return reversedString;
};

reverse('cat');
reverse('123');



/* b. Create a function called isPalindrome which check if a parameter is a palindrome or not.

console.log(isPalindrome('Anna'));//true
console.log(isPalindrome(121));//true
console.log(isPalindrome('Noon'));//true
console.log(isPalindrome('Asa '));//true
console.log(isPalindrome('Asab'));//false
console.log(isPalindrome('cat'));//false */

function isPalindrome(input) {

    // if not string, convert to string
    if (typeof input !== 'string') {
        input = input.toString();
    }

    // transform string to lowercase, and remove punctuation, whitespace, and linebreaks
    string = input.toLowerCase().replace(/[,;.:…(){}\[\]\^\`¡!¿?"“”'‘’\/\\+\-%=@#$&\*~_\r\n ]/g,"");

    // split string into array
    array = string.split('')

    // declare empty array
    let reversedArray = [];

    // push the characters backwards
    for (let i = 0; i < array.length; i++) {
        reversedArray.unshift(array[i])
    };

    // join array into string
    reversedString = reversedArray.join('');

    // if the string is equal to the reversed string, it's a palindrome
    if (string === reversedString) {
        return true;
    }

    else {
        return false;
    };
};

console.log(isPalindrome('Anna'));
console.log(isPalindrome(121));
console.log(isPalindrome('Noon'));
console.log(isPalindrome('Asa '));
console.log(isPalindrome('Asab'));
console.log(isPalindrome('cat'));



/* 6. Create a function called countPalindrowWords which counts the number of palindrome words in the palindoromeWords array or in any array. */

const palindromeWords = [
    'Anna',
    'Asa',
    'Civic',
    'common',
    'Kayak',
    'Level',
    'Madam',
    'Mom',
    'Noon ',
    'Rotor',
    'Sagas',
    'Solar',
    'Stats',
    'Tenet ',
    'Wow'
];

const palindromeWords2 = [
    'Anna',
    'Asa',
    'Civic',
];

const palindromeWords3 = [
    'Annai',
    'Asai',
    'Civici',
];

function countPalindromeWords(array) {

    // inititalize count
    let count = 0;

    // loop through array
    for (let i = 0; i < array.length; i++) {

        // use function isPalindrome; if true, update count
        if (isPalindrome(array[i])) {
            count++
        }
    }

    return count;
};

console.log(countPalindromeWords(palindromeWords));
console.log(countPalindromeWords(palindromeWords2));
console.log(countPalindromeWords(palindromeWords3));



/* 7. Count the number of palindrome words in the following sentence. */ 

const sentence = `He met his mom at noon and she was watching an epsoide of the begninging of her Solos. Her tenet helped her to level up her stats. After that H went to kayak driving Civic Honda.`

function countPalindromeWordsInSentence(sentence) {

    // split sentence into array
    const array = sentence.split(' ');

    // use countPalindromeWords
    const number = countPalindromeWords(array);

    // return count
    console.log(number);
    return number;
};

countPalindromeWordsInSentence(sentence);



/* Questions 8, 9 and 10 are based on the following two arrays: users and products */

const users = [
    {
        _id: 'ab12ex',
        username: 'Alex',
        email: 'alex@alex.com',
        password: '123123',
        createdAt:'17/05/2019 9:00 AM',
        isLoggedIn: false
    },
    {
        _id: 'fg12cy',
        username: 'Asab',
        email: 'asab@asab.com',
        password: '123456',
        createdAt:'17/05/2019 9:30 AM',
        isLoggedIn: true
    },
    {
        _id: 'zwf8md',
        username: 'Brook',
        email: 'brook@brook.com',
        password: '123111',
        createdAt:'17/05/2019 9:45 AM',
        isLoggedIn: true
    },
    {
        _id: 'eefamr',
        username: 'Martha',
        email: 'martha@martha.com',
        password: '123222',
        createdAt:'17/05/2019 9:50 AM',
        isLoggedIn: false
    },
    {
        _id: 'ghderc',
        username: 'Thomas',
        email: 'thomas@thomas.com',
        password: '123333',
        createdAt:'17/05/2019 10:00 AM',
        isLoggedIn: false
    }
];

const products = [
    {
        _id: 'eedfcf',
        name: 'mobile phone',
        description: 'Huawei Honor',
        price:200,
        Rating: [{ userId: 'fg12cy', rating: 5 }, { userId: 'zwf8md', rating: 4.5 }],
        likes: []
    },
    {
        _id: 'aegfal',
        name: 'Laptop',
        description: 'MacPro: System Darwin',
        price:2500,
        Rating: [],
        likes: ['fg12cy']
    },
    {
        _id: 'hedfcg',
        name: 'TV',
        description: 'Smart TV:Procaster',
        price:400,
        Rating: [{userId: 'fg12cy', rating:5}],
        likes: ['fg12cy']
    }
];



/* 8. Imagine you are getting the above users collection from a MongoDB database.

a. Create a function called signUp which allows user to add to the collection. If user exists, inform the user that he has already an account.

b. Create a function called signIn which allows user to sign in to the application */

function generateRandomAlphanumericId(length) {

    // declare character set
    const characters = '0123456789abcdefghijklmnopqrstuvwxyz'

    // declare empty string 
    let string = '';

    // run loop length times
    for (let i = 0; i < length; i++) {
        // pick a random index from the character set
        let j = Math.floor(Math.random() * characters.length);

        // add the character at that index to the string
        string += characters[j]
    }

    return string;
};

function signUp(array, username, email, password) {

    // loop through the array
    for (let i = 0; i < array.length; i++) {

        // if the username at index i matches the username passed...
        if (array[i].username === username) {
            console.log('There‘s already an account with that username.')
            return;
        }

        // otherwise, if the email at index i matches the email passed...
        else if (array[i].email === email) {
            console.log('There‘s already an account with that email.')
            return;
        };
    };

    // if the loop ran its course without returning, add new user
    newUser = {
        _id: generateRandomAlphanumericId(6),
        username: username,
        email: email,
        password: password,
        createdAt: new Date().toLocaleString('en-US', {day: '2-digit', month: '2-digit', year: 'numeric', hour: '2-digit', minute: '2-digit'}),
        isLoggedIn: true,
    };

    // push new user to array
    array.push(newUser);

    console.log('You created a new account.', newUser)
    return newUser;
};

signUp(users, 'Xurxe', 'xurxe@xurxe.com', 'abcd');
signUp(users, 'Alex', 'alex@alex.com', 'abcd');
signUp(users, 'Alexander', 'alex@alex.com', 'abcd');



function signIn(array, username, email, password) {

    // loop through the array
    for (let i = 0; i < array.length; i++) {

        // if you find a matching user, who is not logged in...
        if (
            array[i].username === username
            && array[i].email === email
            && array[i].password === password
            && array[i].isLoggedIn === false
        ) {
            // log in
            array[i].isLoggedIn = true;

            console.log('You just signed in!', array[i])
            return;
        }

        // otherwise, if you find a marching user who is logged in...
        else if (
            array[i].username === username
            && array[i].email === email
            && array[i].password === password
            && array[i].isLoggedIn === true
        ) {
            console.log('You‘re already signed in.', array[i])
            return;
        }
    };

    // if the loop ran its course without returning...
    console.log('Couldn‘t sign in.')
    return;
};

signIn(users, 'Alex', 'alex@alex.com', '123123');
signIn(users, 'Brook', 'brook@brook.com', '123111');
signIn(users, 'Asab', 'asab@asab.com', '123123');



/* 9. The products array has three elements and each of them has six properties.

a. Create a function called rateProduct which rates the product

b. Create a function called averageRating which calculate the average rating of a product */

function rateProduct(array, productId, userId, rating) {
    
    // loop through the array
    for (let i = 0; i < array.length; i++) {

        // if you find a product with a matching id...
        if (array[i]._id === productId) {

            // loop through the ratings
            for (let j = 0; j < array[i].Rating.length; j++) {

                // if you find a matching user id
                if (array[i].Rating[j].userId === userId) {

                    // update the rating
                    array[i].Rating[j].rating = rating;
                    
                    console.log('Rating updated', array[i].Rating)
                    return array[i].Rating;
                };
            };

            // if you looped through the ratings without finding a matching user id, add new rating
            array[i].Rating.push(
                {userId: userId, rating: rating}
            );
                                
            console.log('Rating added', array[i].Rating)
            return array[i].Rating;
        };
    };

    // if you looped through the array without finding a matching product id, the product doesn't exist
    console.log('That product doesn‘t exist.')
    return;
};

rateProduct(products, 'eedfcf', '5po8vw', 5);
rateProduct(products, 'hedfcg', 'fg12cy', 4);
rateProduct(products, 'banana', 'fg12cy', 4);



function averageRating(array, productId) {

    // loop through the array
    for (let i = 0; i < array.length; i++) {

        // if you find a product with a matching id...
        if (array[i]._id === productId) {

            // if the length is 0...
            if (array[i].Rating.length === 0) {

                console.log('No ratings yet.')
                return null;
            };

            // otherwise...

            // initialize sum
            let sum = 0;

            // loop through the ratings, adding them to the sum
            for (let j = 0; j < array[i].Rating.length; j++) {
                sum += array[i].Rating[j].rating;
            };

            // divide by the length to find the average
            let average = sum / array[i].Rating.length;

            console.log('Average rating', average)
            return average;
        };
    };

    // if you looped through the array without returning...
    console.log('That product doesn‘t exist.')
    return;
};

averageRating(products, 'aegfal');
averageRating(products, 'eedfcf');
averageRating(products, 'banana');



/* 10. Create a function called likeProduct. This function will helps to like to the product if it is not liked and remove like if it was liked. */

function likeProduct(array, productId, userId) {

    // loop through the array
    for (let i = 0; i < array.length; i++) {
        
        // if you find a product with a matching id...
        if (array[i]._id === productId) {

            // if the length is 0...
            if (array[i].likes.length === 0) {

                // add like
                array[i].likes.push(userId)

                console.log('Like added', array[i].likes)
                return array[i].likes;
            };

            // otherwise...

            // loop through likes
            for (let j = 0; j < array[i].likes.length; j++) {

                // if you find a matching user id...
                if (array[i].likes[j] === userId) {

                    // remove like
                    array[i].likes.splice(j, 1);

                    console.log('Like removed', array[i].likes)
                    return array[i].likes;
                }

                // otherwise, add the like
                else {
                    array[i].likes.push(userId)

                    console.log('Like added', array[i].likes)
                    return array[i].likes;
                };
            };
        };
    };

    console.log('That product doesn‘t exist.')
    return;
};

likeProduct(products, 'eedfcf', 'eefamr');
likeProduct(products, 'aegfal', 'fg12cy');
likeProduct(products, 'banana', 'fg12cy');