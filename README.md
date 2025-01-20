# PHP
# Web Technology using PHP Lab

## 1. Registration Form Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form Example</title>
</head>
<body>
    <h1>Registration Form</h1>
    <form action="/submit-form" method="post">
        <fieldset>
            <legend>Personal Information</legend>
            <label for="name">Name:</label>
            <input type="text" id="name" name="name" placeholder="Enter your full name" required><br><br>
            
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" placeholder="Enter your email" required><br><br>
            
            <label for="phone">Phone:</label>
            <input type="text" id="phone" name="phone" placeholder="123-456-7890" 
                pattern="\d{3}-\d{3}-\d{4}" title="Phone number must be in the format 123-456-7890" required><br><br>
            
            <label for="password">Password:</label>
            <input type="password" id="password" name="password" placeholder="Enter your password" required><br><br>
            
            <label for="dob">Date of Birth:</label>
            <input type="date" id="dob" name="dob" required><br><br>
        </fieldset>
        
        <fieldset>
            <legend>Preferences</legend>
            <label for="quantity">Number of items:</label>
            <input type="number" id="quantity" name="quantity" min="1" max="10" required><br><br>
            
            <label>
                <input type="checkbox" id="terms" name="terms" required> I agree to the terms and conditions
            </label><br><br>
            
            <p>Gender:</p>
            <label><input type="radio" name="gender" value="male" required> Male</label>
            <label><input type="radio" name="gender" value="female" required> Female</label>
            <label><input type="radio" name="gender" value="other" required> Other</label><br><br>
        </fieldset>
        
        <button type="submit">Submit</button>
    </form>
</body>
</html>
```
```php
##2.Create an HTML form with fields for name, email, and age. Write a PHP script to process the form using the POST method and display the submitted data.
<!DOCTYPE html>
<html>
<head>
    <title>User Information Form</title>
</head>
<body>

    <h2>User Information</h2>

    <form action="process_form.php" method="post">
        <label for="name">Name:</label><br>
        <input type="text" id="name" name="name" required><br><br>

        <label for="email">Email:</label><br>
        <input type="email" id="email" name="email" required><br><br>

        <label for="age">Age:</label><br>
        <input type="number" id="age" name="age" required><br><br>

        <button type="submit" name="submit">Submit</button> 
    </form>

</body>
</html>
### process_form.php
<?php
if (isset($_POST["submit"])) { // Check if the form was submitted
    // Retrieve form data
    $name = $_POST["name"];
    $email = $_POST["email"];
    $age = $_POST["age"];

    // Display submitted data
    echo "<h2>Submitted Data:</h2>";
    echo "<p>Name: " . $name . "</p>";
    echo "<p>Email: " . $email . "</p>";
    echo "<p>Age: " . $age . "</p>";
}
?>
```

```php
##3. Write a PHP script to print numbers from 1 to 10 using a for loop
<?php
for ($i = 1; $i <= 10; $i++) {
    echo "$i<br>";
}
?>


```
```php
4. Write a script to calculate the factorial of a number using a while loop.
<?php
// Get the input from the user
$num = 5; // You can replace this with user input, e.g., $_POST['number'] or $_GET['number']

// Initialize variables
$factorial = 1;
$i = 1;

// Ensure the number is non-negative
if ($num < 0) {
    echo "Factorial is not defined for negative numbers.";
} elseif ($num == 0 || $num == 1) {
    echo "The factorial of $num is 1.";
} else {
    // Calculate factorial using a while loop
    while ($i <= $num) {
        $factorial *= $i;
        $i++;
    }
    echo "The factorial of $num is $factorial.";
}
?>
```
```php
##5.Iterate through an associative array of country names and their capitals and display them.
<?php
$countries = [
    "India" => "New Delhi",
    "USA" => "Washington D.C.",
    "France" => "Paris",
    "Japan" => "Tokyo"
];

foreach ($countries as $country => $capital) {
    echo "The capital of $country is $capital<br>";
}
?>

```
```php
##6. Write a PHP function to:
##• Calculate the square of a number
##• Reverse a string.

<?php
function square($number) {
    return $number * $number;
}

function reverseString($string) {
    return strrev($string);
}

echo "Square of 4: " . square(4) . "<br>";
echo "Reversed string of 'hello': " . reverseString("hello");
?>

```
```php
##7. Create a PHP script that:
#• Defines a function to check whether a given string is a palindrome.
#• Calls the function and displays the result.

<?php
function isPalindrome($string) {
    // $reversed = strrev($string);
    // Remove spaces and convert to lowercase for case-insensitive check
  $cleanStr = strtolower(str_replace(" ", "", $string));
  $reversed = strrev($cleanStr); 

    return $cleanStr === $reversed;
}

$string = "r a r";
echo "$string is " . (isPalindrome($string) ? "a palindrome" : "not a palindrome");
?>

```
```php
#8.Create a PHP script to:
#• Define an indexed array of numbers and print the sum of its elements.
#• Create an associative array with keys as subjects and values as marks. Print thesubject with the highest marks.

<?php

// 1. Sum of elements in an indexed array

$numbers = array(10, 20, 30, 40, 50);
$sum = 0;

foreach ($numbers as $number) {
    $sum += $number;
}

echo "Sum of elements in the array: " . $sum . "<br>";


// 2. Subject with the highest marks

$marks = array(
    "Math" => 90,
    "Science" => 85,
    "English" => 95,
    "History" => 80
);

$highestMarks = 0;
$highestSubject = "";

foreach ($marks as $subject => $mark) {
    if ($mark > $highestMarks) {
        $highestMarks = $mark;
        $highestSubject = $subject;
    }
}

echo "Subject with the highest marks: " . $highestSubject . " (" . $highestMarks . " marks)";

```
```php
##9. Create a registration form with fields for username, email, and password. 
##•Add PHP validation to check if the fields are not empty and the email is valid.
#• Hash the password before storing it.
#• Add a dropdown (select) field withmultiple options (e.g., favourite programming languages). Write a PHP script to handle multiple selected values.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Registration Form</title>
</head>
<body>
    <form action="register.php" method="POST">
        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required><br><br>

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br><br>

        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required><br><br>

        <label for="languages">Favourite Programming Languages:</label>
        <select id="languages" name="languages[]" multiple required>
            <option value="Python">Python</option>
            <option value="JavaScript">JavaScript</option>
            <option value="Java">Java</option>
            <option value="C++">C++</option>
            <option value="Ruby">Ruby</option>
        </select><br><br>

        <input type="submit" value="Register" name="submit">
    </form>
</body>
</html>

###register.php
<?php
if (isset($_POST["submit"])) {
    // Collect and validate form data
    $username = !empty($_POST['username']) ? trim($_POST['username']) : null;
    $email = !empty($_POST['email']) && filter_var($_POST['email'], FILTER_VALIDATE_EMAIL) ? trim($_POST['email']) : null;
    $password = !empty($_POST['password']) ? trim($_POST['password']) : null;
    $languages = !empty($_POST['languages']) ? $_POST['languages'] : null;

    if ($username && $email && $password && $languages) {
        // Hash the password
        $hashed_password = password_hash($password, PASSWORD_DEFAULT);

        // Process selected languages
        $selected_languages = implode(", ", $languages);

        // Dummy code to show the data (You should store it in a database)
        echo "Username: $username<br>";
        echo "Email: $email<br>";
        echo "Hashed Password: $hashed_password<br>";
        echo "Favourite Programming Languages: $selected_languages<br>";
    } else {
        echo "All fields are required and the email must be valid.";
    }
}
?>
```
```php
##10.Create an HTML form with:
##• A file input field to allow users to upload an image. Write a PHP script to handle file uploads:
##• Check the file type (allowonly images like .jpg, .png, .gif). 
##• Check the file size (e.g., limit to 2MB).
##• Save the uploaded file to a uploads/ directory on the server.
 ##• Display a success or error message after the upload.

 //create a uploads folder

##index.php
 <! DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Image Upload</title>
</head>
<body>
<form action="upload.php" method="post" enctype="multipart/form-data">
<label for="image">Upload Image :</label>
<input type="file" id="image" name="image" required><br><br>
<input type="submit" value="submit" name="submit">
</form>
</body>
</html>

##upload.php
<?php
if (isset($_POST['submit']) && isset($_FILES['image'])) {
    $file = $_FILES['image'];
    $allowedTypes = ['image/jpeg', 'image/png', 'image/gif'];
    $maxSize = 2 * 1024 * 1024;

    if (!in_array($file['type'], $allowedTypes)) {
        echo "Only JPG, PNG, and GIF files are allowed.";
        exit;
    }

    if ($file['size'] > $maxSize) {
        echo "File size exceeds the 2MB limit.";
        exit;
    }

    $uploadDir = 'uploads/';
    $filePath = $uploadDir . basename($file['name']);

    if (move_uploaded_file($file['tmp_name'], $filePath)) {
        echo "File uploaded successfully!";
    } else {
        echo "Failed to upload file.";
    }
}
?>

```

```php
##11.Write a PHP script to connect to a MySQL database using MySQLi or PDO


<?php
$servername = "localhost";  // Change to your database server
$username = "root";  // Change to your database username
$password = "";  // Change to your database password
$dbname = "db_name";  // Change to your database name

// Create connection
$conn = mysqli_connect($servername, $username, $password, $dbname);

// Check connection
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}
echo "Connected successfully using MySQLi (Procedural)";
?>


//pdo method
<?php
$servername = "localhost";  // Change to your database server
$username = "root";  // Change to your database username
$password = "";  // Change to your database password
$dbname = "db_name";  // Change to your database name

try {
    $conn = new PDO("mysql:host=$servername;dbname=$dbname", $username, $password);
    // Set the PDO error mode to exception
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    echo "Connected successfully using PDO";
} catch(PDOException $e) {
    echo "Connection failed: " . $e->getMessage();
}
?>

```

```php
##12.Create a complete PHP CRUD application with the following features: 
##• Add a form to insert new records into the database.
 ##• Display all records in an HTML table. 
##• Include "Edit" and "Delete" buttons for each row.

CREATE DATABASE crud_db;
USE crud_db;
CREATE TABLE records (
 id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
 name VARCHAR(30) NOT NULL,
 email VARCHAR(50)

);

##db.php
<?php
$servername = "localhost";  // Change to your database server
$username = "root";  // Change to your database username
$password = "";  // Change to your database password
$dbname = "crud_db";  // Change to your database name

// Create connection
$conn = mysqli_connect($servername, $username, $password, $dbname);

// Check connection
if (!$conn) {
    die("Connection failed: " . mysqli_connect_error());
}
?>


##index.php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CRUD Application</title>
</head>
<body>
    <h2>Add New Record</h2>
    <form action="insert.php" method="POST">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required><br><br>
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br><br>
        <input type="submit" value="Add Record">
    </form>
    <br>
    <h2>All Records</h2>
    <table border="1">
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Email</th>
            <th>Action</th>
        </tr>
        <?php
       
        include_once 'db.php';
        $result = mysqli_query($conn, "SELECT * FROM records");
        while ($row = mysqli_fetch_assoc($result)) {
            echo "<tr>
                    <td>{$row['id']}</td>
                    <td>{$row['name']}</td>
                    <td>{$row['email']}</td>
                    <td>
                        <a href='edit.php?id={$row['id']}'>Edit</a>
                        <a href='delete.php?id={$row['id']}'>Delete</a>
                    </td>
                </tr>";
        }
        ?>
    </table>
</body>
</html>

##insert.php
<?php
include_once 'db.php';

if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $name = $_POST['name'];
    $email = $_POST['email'];

    $sql = "INSERT INTO records (name, email) VALUES ('$name', '$email')";
    if (mysqli_query($conn, $sql)) {
        echo "New record created successfully";
    } else {
        echo "Error: " . $sql . "<br>" . mysqli_error($conn);
    }

    mysqli_close($conn);
    header('Location: index.php');
    exit;
}
?>

##edit.php
<?php
include_once 'db.php';

if (isset($_GET['id'])) {
    $id = $_GET['id'];
    $result = mysqli_query($conn, "SELECT * FROM records WHERE id=$id");
    $row = mysqli_fetch_assoc($result);
}
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $id = $_POST['id'];
    $name = $_POST['name'];
    $email = $_POST['email'];

    $sql = "UPDATE records SET name='$name', email='$email' WHERE id=$id";
    if (mysqli_query($conn, $sql)) {
        echo "Record updated successfully";
    } else {
        echo "Error: " . $sql . "<br>" . mysqli_error($conn);
    }

    mysqli_close($conn);
    header('Location: index.php');
    exit;
}
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Edit Record</title>
</head>
<body>
    <h2>Edit Record</h2>
    <form action="edit.php" method="POST">
        <input type="hidden" name="id" value="<?php echo $row['id']; ?>">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" value="<?php echo $row['name']; ?>" required><br><br>
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" value="<?php echo $row['email']; ?>" required><br><br>
        <input type="submit" value="Update Record">
    </form>
</body>
</html>

##delete.php
<?php
include_once 'db.php';

if (isset($_GET['id'])) {
    $id = $_GET['id'];

    $sql = "DELETE FROM records WHERE id=$id";
    if (mysqli_query($conn, $sql)) {
        echo "Record deleted successfully";
    } else {
        echo "Error: " . $sql . "<br>" . mysqli_error($conn);
    }

    mysqli_close($conn);
    header('Location: index.php');
    exit;
}
?>

```

```php
##13. Create an HTML form with fields for Name, Email, Password, and Age.Validate the following using jQuery: 
##• Name: Must not be empty. 
##• Email: Must have a valid format (e.g., example@domain.com). 
##• Password: Must be at least 8 characters long. 
##• Age: Must be a number greater than 0.

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form Validation</title>
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <script>
        $(document).ready(function () {
            $("form").submit(function (event) {
                let isValid = true;

                // Validate Name
                const name = $("#name").val();
                if (name.trim() === "") {
                    alert("Name must not be empty.");
                    isValid = false;
                }

                // Validate Email
                const email = $("#email").val();
                const emailPattern = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,6}$/;
                if (!emailPattern.test(email)) {
                    alert("Email must have a valid format.");
                    isValid = false;
                }

                // Validate Password
                const password = $("#password").val();
                if (password.length < 8) {
                    alert("Password must be at least 8 characters long.");
                    isValid = false;
                }

                // Validate Age
                const age = $("#age").val();
                if (isNaN(age) || age <= 0) {
                    alert("Age must be a number greater than 0.");
                    isValid = false;
                }

                if (isValid) {
                    alert("Form submitted successfully!");
                } else {
                    event.preventDefault(); // Prevent form submission if validation fails
                }
            });
        });
    </script>
</head>
<body>
    <h2>Registration Form</h2>
    <form method="POST" action="submit_form.php">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required><br><br>

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br><br>

        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required><br><br>

        <label for="age">Age:</label>
        <input type="number" id="age" name="age" required><br><br>

        <input type="submit" value="Register">
    </form>
</body>
</html>

```
