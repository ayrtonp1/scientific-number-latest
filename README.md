<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Scientific Number Checker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 50px;
            background-image: url('your-image-file.jpg'); /* Change to your image file */
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
        }
        .menu-bar {
            display: flex;
            justify-content: center;
            border: 1px solid black;
            width: fit-content;
            margin: 0 auto;
            background: rgba(255, 255, 255, 0.8); /* Adding slight transparency for visibility */
        }
        .menu-item {
            padding: 10px;
            border: 1px solid black;
            font-weight: bold;
            cursor: pointer;
        }
        input { padding: 5px; margin: 10px; }
        button { padding: 5px 10px; cursor: pointer; }
        #message { font-weight: bold; margin-top: 10px; }
    </style>
</head>
<body>
    <div class="menu-bar">
        <div class="menu-item" onclick="saveAsPDF()">File</div>
        <div class="menu-item" onclick="clearInput()">Edit</div>
        <div class="menu-item" onclick="checkNumber()">Run</div>
        <div class="menu-item" onclick="showAbout()">About us</div>
    </div>
    
    <h2>Scientific Number Format Checker</h2>
    <input type="text" id="inputString" placeholder="Enter a number">
    <p id="message"></p>

    <script>
        function checkNumber() {
            const input = document.getElementById("inputString").value.trim();
            const scientificNumberPattern = /^-?\d+(\.\d+)?(e[+-]?\d+)?$/i;
            
            if (scientificNumberPattern.test(input)) {
                document.getElementById("message").innerText = "Yes, it is a number";
            } else {
                document.getElementById("message").innerText = "No, it is not a number";
            }
        }
        
        function clearInput() {
            document.getElementById("inputString").value = "";
            document.getElementById("message").innerText = "";
        }
        
        function showAbout() {
            alert("This tool verifies if a given input is a valid scientific number format. A scientific number consists of a coefficient and an exponent, such as 1.23e+10 or -4.56e-3.");
        }
        
        function saveAsPDF() {
            const { jsPDF } = window.jspdf;
            const doc = new jsPDF();
            const message = document.getElementById("message").innerText;
            
            if (message) {
                doc.text(`Scientific Number Validation Result:\n${message}`, 10, 10);
                doc.save("ScientificNumberResult.pdf");
            } else {
                alert("Please run the check first before saving.");
            }
        }
    </script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
</body>
</html>
