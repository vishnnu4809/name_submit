<?php
// Enable error reporting
ini_set('display_errors', 1);
ini_set('display_startup_errors', 1);
error_reporting(E_ALL);

// Database connection details
$host = 'database-1.cj8y2qswas7c.ap-south-1.rds.amazonaws.com';  // Replace with your RDS endpoint
$username = 'admin';  // RDS database username
$password = 'redhat_123';  // RDS database password
$database = 'vishnu';         // Your database name
$port = 3306;                 // MySQL port

// Test MySQL connection
$conn = new mysqli($host, $username, $password, $database, $port);

// Check if the connection was successful
if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
} else {
    echo "Connected successfully to MySQL!<br>";
}

// Get the submitted name from the form
$name = $_POST['name'] ?? '';

// Only proceed if a name is submitted
if (!empty($name)) {
    echo "Name: $name<br>";
    
    // SQL query to insert the name into the 'users' table
    $sql = "INSERT INTO users (name) VALUES (?)";

    // Prepare and bind the statement
    $stmt = $conn->prepare($sql);
    
    // Check if the prepare statement failed
    if ($stmt === false) {
        die("Prepare failed: " . $conn->error);
    }

    $stmt->bind_param("s", $name);

    // Execute the query
    if ($stmt->execute()) {
        echo "Name submitted successfully!";
    } else {
        echo "Error: " . $stmt->error;
    }

    // Close the statement
    $stmt->close();
} else {
    echo "No name submitted!";
}

// Close the connection
$conn->close();
?>

