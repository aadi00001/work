<!DOCTYPE html>
<html>
<head><title>Upload and Delete One File</title></head>
<body>

<h2>Upload a File</h2>

<form method="post" enctype="multipart/form-data">
    <input type="file" name="fileToUpload" required>
    <input type="submit" name="upload" value="Upload">
</form>

<?php
$folder = "uploads/";
if (!is_dir($folder)) mkdir($folder);

// Handle file upload
if (isset($_POST['upload']) && isset($_FILES['fileToUpload'])) {
    $filename = basename($_FILES['fileToUpload']['name']);
    $target = $folder . $filename;
    $type = strtolower(pathinfo($target, PATHINFO_EXTENSION));
    $size = $_FILES['fileToUpload']['size'];

    if ($size < 500000 && in_array($type, ['jpg', 'png', 'txt', 'pdf'])) {
        if (move_uploaded_file($_FILES["fileToUpload"]["tmp_name"], $target)) {
            echo "<p style='color:green;'>File uploaded: $filename</p>";
            echo "<form method='post'>
                    <input type='hidden' name='deleteFile' value='$filename'>
                    <input type='submit' value='Delete File'>
                  </form>";
        } else {
            echo "<p style='color:red;'>Upload failed.</p>";
        }
    } else {
        echo "<p style='color:red;'>Invalid file! Only JPG, PNG, TXT, PDF under 500KB allowed.</p>";
    }
}

// Handle delete
if (isset($_POST['deleteFile'])) {
    $file = $folder . basename($_POST['deleteFile']);
    if (file_exists($file)) {
        unlink($file);
        echo "<p style='color:blue;'>File deleted successfully.</p>";
    } else {
        echo "<p style='color:red;'>File not found.</p>";
    }
}
?>

</body>
</html>
