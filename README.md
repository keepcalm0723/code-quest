<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Code Quest</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.1/font/bootstrap-icons.css" rel="stylesheet">
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&display=swap" rel="stylesheet">
    <style>
        /* Apply Orbitron font globally or with a class */
        body {
            font-family: 'Orbitron', sans-serif; /* Apply globally */
        }

        /* Optional: Specific class for Orbitron */
        .orbitron {
            font-family: 'Orbitron', sans-serif;
            font-weight: 400; /* Use specific weight if needed */
        }

        .brick-bg {
    background-image: url("C:\Users\akank\OneDrive\Desktop\New folder\background.png"); /* Replace with your image URL */
    background-size: cover; /* Ensures the image covers the entire screen */
    background-position: center; /* Centers the image */
    background-repeat: no-repeat; /* Prevents the image from repeating */
    background-color: #000000; /* Fallback color in case the image doesn't load */
}

    </style>
</head>
<body class="brick-bg min-h-screen">
    <div id="pages">
        <!-- Start Page -->
        <div id="startPage" class="flex flex-col items-center justify-center min-h-screen p-4">
            <div class="bg-white/90 rounded-lg shadow-xl p-8 max-w-md w-full text-center">
                <h1 class="text-4xl font-bold mb-6 text-teal-700 orbitron">Code Quest</h1>
                <p class="text-gray-600 mb-8 orbitron">Test your programming knowledge!</p>
                <button onclick="showNamePage()" class="bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 px-8 rounded-full transition duration-300 orbitron">
                    Start Quiz
                </button>
            </div>
        </div>

        <!-- Name Page -->
        <div id="namePage" class="hidden flex flex-col items-center justify-center min-h-screen p-4">
            <div class="bg-white/90 rounded-lg shadow-xl p-8 max-w-md w-full">
                <h2 class="text-3xl font-bold mb-6 text-teal-700 text-center">Enter Your Name</h2>
                <input type="text" id="userName" class="w-full p-3 border border-gray-300 rounded-lg mb-6 focus:outline-none focus:border-teal-500" placeholder="Your Name">
                <button onclick="submitName()" class="w-full bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 rounded-lg transition duration-300">
                    Continue
                </button>
            </div>
        </div>

        <!-- Language Selection Page -->
        <div id="languagePage" class="hidden flex flex-col items-center justify-center min-h-screen p-4">
            <div class="bg-white/90 rounded-lg shadow-xl p-8 max-w-md w-full">
                <h2 class="text-3xl font-bold mb-6 text-teal-700 text-center">Select Programming Language</h2>
                <div class="grid grid-cols-2 gap-4">
                    <button onclick="selectLanguage('Java')" class="bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 rounded-lg transition duration-300">Java</button>
                    <button onclick="selectLanguage('Python')" class="bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 rounded-lg transition duration-300">Python</button>
                    <button onclick="selectLanguage('C')" class="bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 rounded-lg transition duration-300">C</button>
                    <button onclick="selectLanguage('C++')" class="bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 rounded-lg transition duration-300">C++</button>
                    <button onclick="selectLanguage('SQL')" class="bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 rounded-lg transition duration-300">SQL</button>
                    <button onclick="selectLanguage('R')" class="bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 rounded-lg transition duration-300">R</button>
                    <button onclick="selectLanguage('JavaScript')" class="bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 rounded-lg transition duration-300">JavaScript</button>
                    <button onclick="selectLanguage('PHP')" class="bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 rounded-lg transition duration-300">PHP</button>
                </div>
            </div>
        </div>

        <!-- Quiz Page -->
        <div id="quizPage" class="hidden flex flex-col items-center justify-center min-h-screen p-4">
            <div class="bg-white/90 rounded-lg shadow-xl p-8 max-w-md w-full">
                <h2 class="text-3xl font-bold mb-6 text-teal-700 text-center">Quiz</h2>
                <div id="questionContainer" class="mb-6">
                    <p id="questionText" class="text-lg mb-4"></p>
                    <div id="options" class="space-y-3"></div>
                </div>
                <button onclick="nextQuestion()" class="w-full bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 rounded-lg transition duration-300">
                    Next Question
                </button>
            </div>
        </div>
    </div>

    <script>
        let currentUser = '';
        let selectedLanguage = '';
        let currentQuestion = 0;
        let score = 0;

        //questions
        const questions = {
        Java: [
        { question: "What is the main purpose of Java's 'final' keyword?", options: ["To prevent inheritance", "To declare constants", "To improve performance", "All of the above"], correct: 3 },
        { question: "Which of these is not a Java access modifier?", options: ["public", "private", "friendly", "protected"], correct: 2 },
        { question: "What is the default value of an instance variable in Java?", options: ["null", "0", "undefined", "Depends on the type"], correct: 3 },
        { question: "Which collection type should be used to maintain unique elements?", options: ["ArrayList", "LinkedList", "HashSet", "Vector"], correct: 2 },
        { question: "What is the superclass of all classes in Java?", options: ["Object", "Main", "Super", "Parent"], correct: 0 },
        { question: "Which method is used to start a thread in Java?", options: ["run()", "execute()", "start()", "begin()"], correct: 2 },
        { question: "What is a Java package?", options: ["A collection of classes", "A type of thread", "An interface", "A data structure"], correct: 0 },
        { question: "Which keyword is used to inherit a class in Java?", options: ["implements", "extends", "inherits", "super"], correct: 1 },
        { question: "What does JVM stand for?", options: ["Java Visual Machine", "Java Virtual Machine", "Java Vector Machine", "Java Version Manager"], correct: 1 },
        { question: "Which of the following is not a Java loop structure?", options: ["for", "while", "repeat", "do-while"], correct: 2 },
        { question: "What does the 'static' keyword indicate?", options: ["Method belongs to an instance", "Method belongs to the class", "Method is synchronized", "Method is final"], correct: 1 },
        { question: "What is a constructor in Java?", options: ["A class member to initialize objects", "A type of method", "A data type", "A loop"], correct: 0 },
        { question: "Which interface is used to handle collections in Java?", options: ["List", "Queue", "Collection", "Map"], correct: 2 },
        { question: "What is the size of a 'short' data type in Java?", options: ["4 bytes", "2 bytes", "1 byte", "8 bytes"], correct: 1 },
        { question: "Which exception is thrown when a thread is waiting for an object?", options: ["IOException", "InterruptedException", "RuntimeException", "NullPointerException"], correct: 1 },
        { question: "What is polymorphism in Java?", options: ["Multiple classes inheriting one class", "One method with multiple definitions", "Encapsulation of data", "A type of inheritance"], correct: 1 },
        { question: "What is a marker interface?", options: ["An interface with fields", "An interface with no methods or fields", "An interface with abstract methods", "An interface used in threading"], correct: 1 },
        { question: "Which operator is used to allocate memory for an object?", options: ["new", "malloc", "allocate", "create"], correct: 0 },
        { question: "What is the entry point of a Java program?", options: ["main()", "start()", "init()", "run()"], correct: 0 },
        { question: "Which keyword is used for garbage collection?", options: ["delete", "free", "finalize", "dispose"], correct: 2 },
    ],
    Python: [
        { question: "What is Python's primary use?", options: ["Web development", "General purpose programming", "Data analysis", "All of the above"], correct: 3 },
        { question: "Which is not a core data type in Python?", options: ["Lists", "Dictionary", "Tuple", "Array"], correct: 3 },
        { question: "What does PIP stand for?", options: ["Python Installation Package", "Pip Installs Python", "Pip Installs Packages", "Python Internal Package"], correct: 2 },
        { question: "Which of these is not a valid Python variable name?", options: ["_myvar", "my_var", "2myvar", "myVar"], correct: 2 },
        { question: "What is the correct file extension for Python files?", options: [".py", ".pyt", ".pt", ".python"], correct: 0 },
        { question: "What does the 'break' keyword do in Python?", options: ["Exits a loop", "Skips an iteration", "Ends a program", "Returns a value"], correct: 0 },
        { question: "Which function is used to get the length of a string?", options: ["size()", "len()", "count()", "length()"], correct: 1 },
        { question: "How do you create a comment in Python?", options: ["// comment", "/* comment */", "# comment", "<!-- comment -->"], correct: 2 },
        { question: "What is the result of `3**2` in Python?", options: ["5", "6", "9", "8"], correct: 2 },
        { question: "Which data structure is immutable?", options: ["List", "Set", "Tuple", "Dictionary"], correct: 2 },
        { question: "What is Python's type of a 'None' value?", options: ["null", "void", "NoneType", "NullType"], correct: 2 },
        { question: "How do you open a file in write mode?", options: ["open(filename, 'r')", "open(filename, 'w')", "open(filename, 'rw')", "open(filename, 'x')"], correct: 1 },
        { question: "What is a lambda function?", options: ["A function declared without a name", "A method in a class", "A built-in Python function", "A module"], correct: 0 },
        { question: "What is the correct way to create a dictionary?", options: ["dict = {}", "dict = []", "dict = ()", "dict = ''"], correct: 0 },
        { question: "Which module is used to generate random numbers?", options: ["math", "random", "numpy", "statistics"], correct: 1 },
        { question: "What is Python's default IDE?", options: ["Visual Studio", "Jupyter", "PyCharm", "IDLE"], correct: 3 },
        { question: "What is the output of `print(type([]))`?", options: ["list", "tuple", "<class 'list'>", "<type 'list'>"], correct: 2 },
        { question: "What does 'PEP' stand for?", options: ["Python Extension Program", "Python Enhancement Proposal", "Python Experimental Program", "Python Enrichment Proposal"], correct: 1 },
        { question: "Which method is used to remove whitespace from a string?", options: ["trim()", "strip()", "delete()", "clear()"], correct: 1 },
        { question: "What is the default argument passing method in Python?", options: ["Call by value", "Call by reference", "Call by object reference", "Call by pointer"], correct: 2 },
    ],
        C: [
    { question: "Which keyword is used to define constants in C?", options: ["const", "define", "static", "final"], correct: 1 },
    { question: "What is the output of `printf(\"%d\", 10/3);`?", options: ["3.33", "3", "10", "Error"], correct: 1 },
    { question: "Which operator is used to access members of a structure?", options: [".", "->", "::", "#"], correct: 0 },
    { question: "What does `sizeof` operator do?", options: ["Returns the size of a file", "Returns the size of a data type", "Checks memory allocation", "Calculates array length"], correct: 1 },
    { question: "Which header file is used for input and output in C?", options: ["<conio.h>", "<stdlib.h>", "<stdio.h>", "<string.h>"], correct: 2 },
    { question: "What is the default return type of a function in C?", options: ["int", "void", "char", "float"], correct: 0 },
    { question: "What is a pointer?", options: ["A variable to store memory address", "A function", "A reference to a variable", "A constant"], correct: 0 },
    { question: "What is a null pointer?", options: ["A pointer with no value", "A pointer initialized to 0", "A dangling pointer", "A pointer to an array"], correct: 1 },
    { question: "Which function is used to allocate memory dynamically?", options: ["malloc()", "memalloc()", "alloc()", "memory()"], correct: 0 },
    { question: "Which loop ensures execution of code at least once?", options: ["for", "while", "do-while", "foreach"], correct: 2 },
    { question: "What is the value of `a` after `int a=5; a=a++;`?", options: ["5", "6", "10", "Undefined"], correct: 0 },
    { question: "Which keyword is used to terminate a loop?", options: ["exit", "break", "continue", "return"], correct: 1 },
    { question: "What is a void pointer?", options: ["Pointer with no type", "Pointer to a void function", "Pointer initialized to 0", "Pointer to an array"], correct: 0 },
    { question: "What is the maximum size of an array in C?", options: ["No limit", "Depends on memory", "2^32", "10^9"], correct: 1 },
    { question: "Which of these functions can be used to compare strings?", options: ["strcmp()", "strlen()", "strcomp()", "strcat()"], correct: 0 },
    { question: "Which preprocessor directive is used for including libraries?", options: ["#library", "#define", "#include", "#header"], correct: 2 },
    { question: "What is recursion in C?", options: ["A function calling itself", "A loop", "A macro expansion", "None of the above"], correct: 0 },
    { question: "Which function is used to write formatted data to a string?", options: ["sprintf()", "printf()", "writef()", "fwrite()"], correct: 0 },
    { question: "What is the base address of an array?", options: ["Address of the first element", "Address of the last element", "Size of the array", "Address of the memory block"], correct: 0 },
    { question: "Which keyword is used to declare a structure?", options: ["struct", "structure", "object", "class"], correct: 0 },
],
        "C++": [
    { question: "What is a class in C++?", options: ["A blueprint for objects", "A variable type", "A header file", "A library"], correct: 0 },
    { question: "What does the `new` keyword do?", options: ["Allocates memory", "Defines constants", "Initializes arrays", "Defines pointers"], correct: 0 },
    { question: "Which feature of OOP is shown by function overloading?", options: ["Inheritance", "Encapsulation", "Polymorphism", "Abstraction"], correct: 2 },
    { question: "Which of these is not a fundamental data type in C++?", options: ["int", "float", "char", "string"], correct: 3 },
    { question: "What is the use of 'this' pointer?", options: ["Access base class", "Access current object", "Access global variables", "Access static members"], correct: 1 },
    { question: "Which access specifier is the default in a class?", options: ["private", "protected", "public", "static"], correct: 0 },
    { question: "What is a virtual function?", options: ["A function in the base class that can be overridden", "A function without implementation", "A static function", "A global function"], correct: 0 },
    { question: "What does STL stand for?", options: ["Standard Type Library", "Standard Template Library", "Standard Tool Library", "None of the above"], correct: 1 },
    { question: "Which operator cannot be overloaded?", options: ["+", "=", "::", "[]"], correct: 2 },
    { question: "What does the 'cout' object represent?", options: ["Input stream", "Output stream", "Control stream", "Data stream"], correct: 1 },
    { question: "Which keyword is used for exception handling?", options: ["try", "catch", "throw", "All of the above"], correct: 3 },
    { question: "What is a destructor in C++?", options: ["Function called when an object is destroyed", "Function for memory allocation", "A static method", "An overloaded function"], correct: 0 },
    { question: "Which header file is used for file handling?", options: ["<iostream>", "<fstream>", "<stdlib.h>", "<cstdio>"], correct: 1 },
    { question: "What is function overriding?", options: ["Function with the same name and parameters in base and derived class", "Function with the same name but different parameters", "A macro", "A static function"], correct: 0 },
    { question: "What does `public` inheritance mean?", options: ["Base class members become public", "Base class public members remain public", "Base class private members become protected", "None of the above"], correct: 1 },
    { question: "What is an abstract class?", options: ["A class with at least one pure virtual function", "A class without members", "A template class", "None of the above"], correct: 0 },
    { question: "What does `dynamic_cast` do?", options: ["Casts data to any type", "Casts pointers in an inheritance hierarchy", "Casts static members", "Converts objects"], correct: 1 },
    { question: "Which of the following is not a valid iterator category?", options: ["Input iterator", "Output iterator", "Container iterator", "Bidirectional iterator"], correct: 2 },
    { question: "What is the use of `typeid`?", options: ["Checks variable type at runtime", "Checks memory size", "Performs dynamic memory allocation", "None of the above"], correct: 0 },
    { question: "What is an inline function?", options: ["Function expanded at compile time", "Function with external linkage", "Virtual function", "Recursive function"], correct: 0 },
],
        SQL: [
    { question: "What does SQL stand for?", options: ["Structured Query Language", "Standard Query Language", "Sequential Query Language", "None of the above"], correct: 0 },
    { question: "Which command is used to remove rows from a table?", options: ["DELETE", "REMOVE", "TRUNCATE", "DROP"], correct: 0 },
    { question: "Which SQL keyword is used to retrieve unique values?", options: ["SELECT", "UNIQUE", "DISTINCT", "FILTER"], correct: 2 },
    { question: "Which function is used to count the number of rows in a table?", options: ["COUNT()", "SUM()", "ROW_COUNT()", "TOTAL()"], correct: 0 },
    { question: "What is a primary key?", options: ["A unique identifier for a record", "A foreign key", "A data type", "A constraint to allow duplicates"], correct: 0 },
    { question: "Which SQL clause is used to filter records?", options: ["WHERE", "HAVING", "FILTER", "GROUP BY"], correct: 0 },
    { question: "What is the default sorting order of the ORDER BY clause?", options: ["ASC", "DESC", "RANDOM", "UNSORTED"], correct: 0 },
    { question: "What does the JOIN keyword do?", options: ["Combines rows from multiple tables", "Deletes rows", "Creates a new table", "Filters rows"], correct: 0 },
    { question: "Which SQL statement is used to update data in a table?", options: ["INSERT", "UPDATE", "MODIFY", "CHANGE"], correct: 1 },
    { question: "What is a foreign key?", options: ["A key referencing another table", "A primary key", "A unique key", "None of the above"], correct: 0 },
    { question: "What is the difference between TRUNCATE and DELETE?", options: ["TRUNCATE removes all rows faster", "DELETE can use WHERE clause", "TRUNCATE resets auto-increment values", "All of the above"], correct: 3 },
    { question: "Which keyword is used to sort records?", options: ["SORT", "ORDER BY", "GROUP BY", "FILTER"], correct: 1 },
    { question: "What is the purpose of the GROUP BY clause?", options: ["Aggregates data", "Filters rows", "Sorts data", "Deletes duplicates"], correct: 0 },
    { question: "Which function is used to return the current date and time?", options: ["NOW()", "CURDATE()", "SYSDATE()", "GETDATE()"], correct: 0 },
    { question: "What is the use of the HAVING clause?", options: ["Filter groups", "Filter rows", "Sort records", "Limit rows"], correct: 0 },
    { question: "Which operator checks for a specified pattern?", options: ["LIKE", "IN", "BETWEEN", "EXISTS"], correct: 0 },
    { question: "Which statement creates a new table?", options: ["CREATE TABLE", "INSERT TABLE", "NEW TABLE", "TABLE CREATE"], correct: 0 },
    { question: "What does the LIMIT clause do?", options: ["Limits the number of rows returned", "Restricts data type sizes", "Limits column values", "Stops execution"], correct: 0 },
    { question: "What is a composite key?", options: ["A key using multiple columns", "A unique key", "A primary key", "A foreign key"], correct: 0 },
    { question: "What is the use of the ALTER TABLE command?", options: ["Modify table structure", "Delete rows", "Insert rows", "Backup data"], correct: 0 },
],
        JavaScript: [
    { question: "Which keyword declares a variable?", options: ["var", "let", "const", "All of the above"], correct: 3 },
    { question: "Which of these is not a data type in JavaScript?", options: ["undefined", "string", "float", "object"], correct: 2 },
    { question: "What is the output of `typeof null`?", options: ["null", "object", "undefined", "number"], correct: 1 },
    { question: "Which function converts a string to an integer?", options: ["parseInt()", "Number()", "toInt()", "parseString()"], correct: 0 },
    { question: "Which method adds elements to an array?", options: ["add()", "push()", "append()", "concat()"], correct: 1 },
    { question: "Which keyword is used for async functions?", options: ["async", "await", "defer", "promise"], correct: 0 },
    { question: "What is `NaN` in JavaScript?", options: ["Not a Number", "Null value", "A string", "Undefined"], correct: 0 },
    { question: "Which statement is true for `==` and `===`?", options: ["`==` checks value only", "`===` checks value and type", "Both are same", "Both check type only"], correct: 1 },
    { question: "Which method removes the last element of an array?", options: ["pop()", "remove()", "shift()", "slice()"], correct: 0 },
    { question: "Which event is triggered when a button is clicked?", options: ["onClick", "click", "mouseClick", "press"], correct: 1 },
    { question: "What is the output of `1 + '1'`?", options: ["2", "11", "Error", "undefined"], correct: 1 },
    { question: "What does `document.querySelector()` do?", options: ["Selects an HTML element", "Adds a CSS class", "Creates an element", "Deletes an element"], correct: 0 },
    { question: "Which function sets a delay?", options: ["setTimeout()", "delay()", "setInterval()", "wait()"], correct: 0 },
    { question: "What is the purpose of `JSON.stringify()`?", options: ["Convert object to string", "Convert string to JSON", "Parse JSON data", "None of the above"], correct: 0 },
    { question: "Which operator is used for exponentiation?", options: ["**", "^", "pow()", "None"], correct: 0 },
    { question: "What is the scope of a `var` variable?", options: ["Function", "Block", "Global", "File"], correct: 0 },
    { question: "Which method is used to round numbers?", options: ["round()", "Math.round()", "ceil()", "floor()"], correct: 1 },
    { question: "Which is not a looping structure?", options: ["for", "while", "do-while", "repeat-until"], correct: 3 },
    { question: "How do you declare a constant?", options: ["const", "constant", "final", "var"], correct: 0 },
    { question: "What is the output of `typeof []`?", options: ["array", "object", "list", "undefined"], correct: 1 },
],
        PHP: [
    { question: "What does PHP stand for?", options: ["Personal Home Page", "PHP: Hypertext Preprocessor", "Programming Hypertext Page", "Preprocessed Hypertext Parser"], correct: 1 },
    { question: "Which symbol is used to declare variables in PHP?", options: ["$", "#", "@", "&"], correct: 0 },
    { question: "What is the correct way to include a file in PHP?", options: ["include 'file.php';", "import 'file.php';", "require 'file.php';", "Both include and require"], correct: 3 },
    { question: "Which function is used to print output in PHP?", options: ["echo", "print", "output", "Both echo and print"], correct: 3 },
    { question: "Which of the following is a PHP superglobal?", options: ["$_GET", "$GLOBALS", "$_POST", "All of the above"], correct: 3 },
    { question: "What is the default file extension for PHP files?", options: [".html", ".php", ".ph", ".txt"], correct: 1 },
    { question: "Which operator is used for concatenation in PHP?", options: ["+", ".", "&", "||"], correct: 1 },
    { question: "Which function is used to start a session in PHP?", options: ["session_start()", "session_begin()", "start_session()", "init_session()"], correct: 0 },
    { question: "Which method is used to retrieve form data sent using POST?", options: ["$_POST", "$_GET", "$_REQUEST", "$_FORM"], correct: 0 },
    { question: "How do you define a constant in PHP?", options: ["const()", "define()", "constant()", "set()"], correct: 1 },
    { question: "Which data type does PHP support?", options: ["String", "Integer", "Boolean", "All of the above"], correct: 3 },
    { question: "Which function checks if a file exists in PHP?", options: ["file_exists()", "is_file()", "exists()", "file_check()"], correct: 0 },
    { question: "Which keyword is used to create a class in PHP?", options: ["class", "object", "define", "function"], correct: 0 },
    { question: "Which function is used to connect to a MySQL database?", options: ["mysqli_connect()", "mysql_connect()", "connect_db()", "open_mysql()"], correct: 0 },
    { question: "Which keyword ends a PHP script?", options: ["?>", "END", "</php>", "#"], correct: 0 },
    { question: "Which function is used to get the length of a string?", options: ["strlen()", "length()", "size()", "strlength()"], correct: 0 },
    { question: "Which statement is used to terminate the execution of a script?", options: ["exit()", "stop()", "terminate()", "end()"], correct: 0 },
    { question: "How do you create an array in PHP?", options: ["array()", "arr()", "createArray()", "list()"], correct: 0 },
    { question: "Which operator is used to compare both value and type?", options: ["==", "===", "!=", "!=="], correct: 1 },
    { question: "Which function is used to include the contents of another PHP file without errors?", options: ["include()", "require()", "fetch()", "insert()"], correct: 0 },
],
        R: [
    { question: "What does R primarily focus on?", options: ["Web Development", "Data Analysis", "System Programming", "Networking"], correct: 1 },
    { question: "Which function is used to read a CSV file in R?", options: ["read.csv()", "readFile()", "load.csv()", "import()"], correct: 0 },
    { question: "Which of these is not a data type in R?", options: ["Vector", "Matrix", "DataFrame", "ListView"], correct: 3 },
    { question: "What does the 'summary()' function do?", options: ["Generates data summary", "Plots graphs", "Loads a package", "Imports data"], correct: 0 },
    { question: "Which operator is used for assignment in R?", options: ["=", "<-", "->", "::"], correct: 1 },
    { question: "How do you install a package in R?", options: ["install.packages()", "load.package()", "addLibrary()", "import.package()"], correct: 0 },
    { question: "What does the `head()` function return?", options: ["First few rows", "Last few rows", "Column names", "Summary"], correct: 0 },
    { question: "Which library is used for data visualization in R?", options: ["ggplot2", "dplyr", "data.table", "tidyverse"], correct: 0 },
    { question: "What does 'NA' represent in R?", options: ["Not Applicable", "Null value", "Missing value", "None of the above"], correct: 2 },
    { question: "Which function merges datasets by a common key?", options: ["merge()", "join()", "combine()", "attach()"], correct: 0 },
    { question: "What is the class of 'TRUE' in R?", options: ["Logical", "Boolean", "Integer", "Character"], correct: 0 },
    { question: "How do you create a vector in R?", options: ["vector()", "c()", "createVector()", "v()"], correct: 1 },
    { question: "What is the output of '1:5' in R?", options: ["A vector from 1 to 5", "Matrix of size 1x5", "Sequence from 0 to 5", "Error"], correct: 0 },
    { question: "What does 'plot()' function do?", options: ["Creates graphs", "Summarizes data", "Loads a package", "None of the above"], correct: 0 },
    { question: "Which function creates a histogram in R?", options: ["hist()", "plotHist()", "ggplot()", "histo()"], correct: 0 },
    { question: "Which keyword checks for missing values?", options: ["is.na()", "missing()", "is.null()", "exists()"], correct: 0 },
    { question: "What does 'factor()' do?", options: ["Converts data into categories", "Creates a vector", "Applies math operations", "Generates plots"], correct: 0 },
    { question: "What does the function 'mean()' return?", options: ["Average of values", "Median of values", "Sum of values", "Maximum value"], correct: 0 },
    { question: "Which function binds columns together?", options: ["cbind()", "rbind()", "bindcol()", "attach()"], correct: 0 },
    { question: "What is the default index of an R array?", options: ["1", "0", "-1", "Dynamic"], correct: 0 },
],

    };


        function showNamePage() {
            document.getElementById('startPage').classList.add('hidden');
            document.getElementById('namePage').classList.remove('hidden');
        }

        function submitName() {
            const nameInput = document.getElementById('userName');
            if (nameInput.value.trim() === '') {
                alert('Please enter your name');
                return;
            }
            currentUser = nameInput.value;
            document.getElementById('namePage').classList.add('hidden');
            document.getElementById('languagePage').classList.remove('hidden');
        }

        function selectLanguage(language) {
            selectedLanguage = language;
            document.getElementById('languagePage').classList.add('hidden');
            document.getElementById('quizPage').classList.remove('hidden');
            loadQuestion();
        }

        function loadQuestion() {
            if (currentQuestion >= questions[selectedLanguage].length) {
                showResult();
                return;
            }

            const question = questions[selectedLanguage][currentQuestion];
            document.getElementById('questionText').textContent = question.question;

            const optionsContainer = document.getElementById('options');
            optionsContainer.innerHTML = '';

            question.options.forEach((option, index) => {
                const button = document.createElement('button');
                button.className = 'w-full text-left p-3 rounded-lg border border-gray-300 hover:bg-teal-50 transition duration-300';
                button.textContent = option;
                button.onclick = () => selectAnswer(index);
                optionsContainer.appendChild(button);
            });
        }

        function selectAnswer(index) {
            const question = questions[selectedLanguage][currentQuestion];
            if (index === question.correct) {
                score++;
            }
            currentQuestion++;
            loadQuestion();
        }

        function nextQuestion() {
            loadQuestion();
        }

        function showResult() {
            const quizContainer = document.getElementById('quizPage');
            quizContainer.innerHTML = `
                <div class="bg-white/90 rounded-lg shadow-xl p-8 max-w-md w-full text-center">
                    <h2 class="text-3xl font-bold mb-6 text-teal-700">Quiz Complete!</h2>
                    <p class="text-xl mb-4">Well done, ${currentUser}!</p>
                    <p class="text-2xl mb-6">Your score: ${score}/${questions[selectedLanguage].length}</p>
                    <button onclick="location.reload()" class="bg-teal-600 hover:bg-teal-700 text-white font-bold py-3 px-8 rounded-full transition duration-300">
                        Try Again
                    </button>
                </div>
            `;
        }
    </script>
</body>
</html>
