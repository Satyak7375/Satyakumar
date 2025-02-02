// Java
//A
import java.util.Random;

public class ShuffleArray {
    public static void main(String[] args) {
        // Create an array with values (1, 2, 3, 4, 5, 6, 7)
        int[] arr = {1, 2, 3, 4, 5, 6, 7};

        // Shuffle the array
        shuffleArray(arr);

        // Print shuffled array
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }

    public static void shuffleArray(int[] arr) {
        Random random = new Random();
        for (int i = 0; i < arr.length; i++) {
            // Generate a random index between i and arr.length-1
            int j = random.nextInt(arr.length - i) + i;

            // Swap arr[i] and arr[j]
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }
}




// B

import java.util.Scanner;

public class RomanToInteger {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input a Roman numeral
        System.out.println("Enter a Roman numeral: ");
        String roman = scanner.nextLine();

        // Convert the Roman numeral to an integer
        int result = romanToInt(roman);

        // Output the result
        System.out.println("The integer value is: " + result);
    }

    public static int romanToInt(String roman) {
        int result = 0;
        int prevValue = 0;
        
        // Process each character from right to left
        for (int i = roman.length() - 1; i >= 0; i--) {
            char currentChar = roman.charAt(i);
            int currentValue = romanCharToInt(currentChar);

            // If the current value is less than the previous value, subtract it; otherwise, add it
            if (currentValue < prevValue) {
                result -= currentValue;
            } else {
                result += currentValue;
            }
            prevValue = currentValue;
        }
        
        return result;
    }

    public static int romanCharToInt(char c) {
        switch (c) {
            case 'I': return 1;
            case 'V': return 5;
            case 'X': return 10;
            case 'L': return 50;
            case 'C': return 100;
            case 'D': return 500;
            case 'M': return 1000;
            default: return 0;
        }
    }
}


// C

import java.util.Scanner;

public class PangramCheck {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Input a sentence
        System.out.println("Enter a sentence: ");
        String sentence = scanner.nextLine();

        // Check if the sentence is a pangram
        boolean isPangram = isPangram(sentence);

        // Output the result
        if (isPangram) {
            System.out.println("The sentence is a pangram.");
        } else {
            System.out.println("The sentence is not a pangram.");
        }
    }

    public static boolean isPangram(String sentence) {
        boolean[] letters = new boolean[26]; // Array to track presence of each letter
        
        // Convert the sentence to lowercase for uniformity
        sentence = sentence.toLowerCase();

        // Traverse through the sentence and mark the letters
        for (char c : sentence.toCharArray()) {
            if (c >= 'a' && c <= 'z') {
                letters[c - 'a'] = true;
            }
        }

        // Check if all letters are present
        for (boolean letter : letters) {
            if (!letter) {
                return false;
            }
        }

        return true;
    }
}


// Javascript

// A

function reverseWordsInSentence(sentence) {
    
    let words = sentence.split(' ');
    let reversedWords = words.map(word => word.split('').reverse().join(''));
    return reversedWords.join(' ');
}

let sentence = "This is a sunny day";
let reversedSentence = reverseWordsInSentence(sentence);
console.log(reversedSentence);  // Output: "sihT si a ynnus yad"


// B

function sortDescending(arr) {
    let n = arr.length;
    
    for (let i = 0; i < n - 1; i++) {
        for (let j = 0; j < n - i - 1; j++) {
            if (arr[j] < arr[j + 1]) {
                // Swap the elements if they are in the wrong order
                let temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    return arr;
}

let arr = [5, 2, 8, 1, 3];
let sortedArray = sortDescending(arr);
console.log(sortedArray);  // Output: [8, 5, 3, 2, 1]

// Html

// A

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Basic Calculator</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #ccc;
        }
        .calculator {
            width: 250px;
            background: #222;
            border-radius: 10px;
            overflow: hidden;
        }
        .display {
            background: #fff;
            padding: 10px;
            text-align: right;
            font-size: 1.5em;
        }
        .buttons {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 5px;
            padding: 10px;
        }
        button {
            padding: 15px;
            font-size: 1.2em;
            border: none;
            cursor: pointer;
        }
        .operator {
            background: #666;
            color: white;
        }
        .clear {
            background: teal;
            color: white;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <div class="display" id="display">0</div>
        <div class="buttons">
            <button onclick="clearDisplay()" class="clear">AC</button>
            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button onclick="appendToDisplay('+')" class="operator">+</button>
            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button onclick="appendToDisplay('-')" class="operator">-</button>
            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button onclick="appendToDisplay('*')" class="operator">×</button>
            <button onclick="appendToDisplay('0')">0</button>
            <button onclick="appendToDisplay('.')">.</button>
            <button onclick="calculate()">=</button>
            <button onclick="appendToDisplay('/')" class="operator">÷</button>
        </div>
    </div>

    <script>
        function appendToDisplay(value) {
            let display = document.getElementById('display');
            if (display.innerText === '0' && value !== '.') {
                display.innerText = value;
            } else {
                display.innerText += value;
            }
        }

        function clearDisplay() {
            document.getElementById('display').innerText = '0';
        }

        function calculate() {
            let display = document.getElementById('display');
            try {
                display.innerText = eval(display.innerText);
            } catch {
                display.innerText = 'Error';
            }
        }
    </script>
</body>
</html>


// B

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Survey Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 10px gray;
            width: 300px;
        }
        label {
            display: block;
            margin-top: 10px;
        }
        input, select {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
        }
        .buttons {
            margin-top: 15px;
            display: flex;
            justify-content: space-between;
        }
        button {
            padding: 10px;
            border: none;
            background: teal;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background: darkcyan;
        }
    </style>
</head>
<body>
    <div class="container">
        <h2>Customer Survey Form</h2>
        <form id="surveyForm">
            <label>First Name:<input type="text" id="firstName" required></label>
            <label>Last Name:<input type="text" id="lastName" required></label>
            <label>Date of Birth:<input type="date" id="dob" required></label>
            <label>Country:
                <select id="country" required>
                    <option value="">Select</option>
                    <option value="USA">USA</option>
                    <option value="Canada">Canada</option>
                    <option value="UK">UK</option>
                    <option value="India">India</option>
                </select>
            </label>
            <label>Gender:
                <input type="checkbox" name="gender" value="Male"> Male
                <input type="checkbox" name="gender" value="Female"> Female
            </label>
            <label>Profession:<input type="text" id="profession" required></label>
            <label>Email:<input type="email" id="email" required></label>
            <label>Mobile Number:<input type="tel" id="mobile" required></label>
            <div class="buttons">
                <button type="button" onclick="submitForm()">Submit</button>
                <button type="reset">Reset</button>
            </div>
        </form>
    </div>

    <script>
        function submitForm() {
            let firstName = document.getElementById('firstName').value;
            let lastName = document.getElementById('lastName').value;
            let dob = document.getElementById('dob').value;
            let country = document.getElementById('country').value;
            let genderElements = document.getElementsByName('gender');
            let gender = [];
            for (let g of genderElements) {
                if (g.checked) {
                    gender.push(g.value);
                }
            }
            let profession = document.getElementById('profession').value;
            let email = document.getElementById('email').value;
            let mobile = document.getElementById('mobile').value;
            
            if (!firstName || !lastName || !dob || !country || gender.length === 0 || !profession || !email || !mobile) {
                alert('Please fill all fields correctly.');
                return;
            }
            
            let message = `Name: ${firstName} ${lastName}\nDOB: ${dob}\nCountry: ${country}\nGender: ${gender.join(', ')}\nProfession: ${profession}\nEmail: ${email}\nMobile: ${mobile}`;
            alert(message);
            document.getElementById('surveyForm').reset();
        }
    </script>
</body>
</html>




