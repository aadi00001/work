# work
<!DOCTYPE html>
<html>
<head>
  <title>Most Frequent Element</title>
</head>
<body>

<h2>Find Most Frequent Element</h2>

<form id="arrayForm">
  Enter array elements (comma-separated):<br>
  <input type="text" id="arrayInput" required>
  <br><br>
  <input type="submit" value="Find">
</form>

<p id="result"></p>

<script>
  document.getElementById("arrayForm").addEventListener("submit", function(e) {
    e.preventDefault(); // Prevent form from reloading the page

    // Get and clean input
    const input = document.getElementById("arrayInput").value.trim();
    const arr = input.split(",").map(item => item.trim());

    const freq = {};
    let maxCount = 0;
    let mostFrequent;

    // Count frequencies
    for (let i = 0; i < arr.length; i++) {
      const item = arr[i];
      freq[item] = (freq[item] || 0) + 1;

      if (freq[item] > maxCount) {
        maxCount = freq[item];
        mostFrequent = item;
      }
    }

    // Show result
    document.getElementById("result").innerText =
      Most frequent element: ${mostFrequent} (appears ${maxCount} times);
  });
</script>

</body>
</html>


3: this is program 3


<form method="POST" action="">
    Name: <input name="name" required><br><br>
    Email: <input name="email" type="email" required><br><br>
    Couurse: <input name="course" type="text" required><br><br>
    <input type="submit" value="Add Employee">

</form>
<center><?php
$conn=mysqli_connect("localhost","root","");
$sql="CREATE DATABASE IF NOT EXISTS testdb";
if($conn->query( $sql ) === false) {
    echo"Error";
}
$conn->select_db("testdb");
$table="
CREATE TABLE IF NOT EXISTS employees (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL,
    course VARCHAR(100) NOT NULL
)";
if($conn->query( $table ) === false) {
    echo "no table";
}

if ($_SERVER["REQUEST_METHOD"]==="POST"){
    $stmt= $conn->prepare("INSERT INTO EMPLOYEES (name,email,course) VALUES(?,?,?)");
    $stmt->bind_param("sss", $_POST['name'],$_POST['email'],$_POST['course']);
    if($stmt->execute()) {
        echo"<p style='color:green'>Done</p>";
    }
    $stmt->close();
}
$result = $conn->query("SELECT * FROM employees");
while($row = $result->fetch_assoc()) {
    echo $row["name"]." ".$row["course"]."<br>";
}

?>

</center>


Code:1
<!DOCTYPE html>
<html>
<head>
<title>Most Frequent Element</title>
</head>
<body>

<h2>Find Most Frequent Element</h2>

<form id="arrayForm">
Enter array elements (comma-separated):<br>
<input type="text" id="arrayInput" required>
<br><br>
<input type="submit" value="Find">
</form>

<p id="result"></p>

<script>
document.getElementById("arrayForm").addEventListener("submit", function(e) {
e.preventDefault(); // Prevent form from reloading the page

// Get and clean input
const input = document.getElementById("arrayInput").value.trim();
const arr = input.split(",").map(item => item.trim());

const freq = {};
let maxCount = 0;
let mostFrequent;

// Count frequencies
for (let i = 0; i < arr.length; i++) {
const item = arr[i];
freq[item] = (freq[item] || 0) + 1;

if (freq[item] > maxCount) {
maxCount = freq[item];
mostFrequent = item;
}
}

// Show result
document.getElementById("result").innerText =
Most frequent element: ${mostFrequent} (appears ${maxCount} times);
});
</script>

</body>
</html>
