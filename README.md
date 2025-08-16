<!DOCTYPE html>
<html>
<head>
  <title>Student Choice Entry</title>
</head>
<body>
  <h2>Enter Student Details</h2>
  <form id="studentForm">
    <label>Name:</label>
    <input type="text" id="name" required><br><br>

    <label>Choice:</label>
    <input type="text" id="choice" required><br><br>

    <button type="submit">Submit</button>
  </form>

  <script>
    const scriptURL = "https://script.google.com/macros/s/AKfycbykTZBI11RZDRE0y-5Ds_6B0DfFsG9OkyYaYKZtFLYntSggCULGgxwWIsNZSgPa_HvNfQ/exec";

    document.getElementById("studentForm").addEventListener("submit", function(e){
      e.preventDefault();

      const name = document.getElementById("name").value;
      const choice = document.getElementById("choice").value;

      fetch(scriptURL, {
        method: 'POST',
        body: JSON.stringify({name: name, choice: choice})
      })
      .then(response => response.text())
      .then(data => {
        alert("Saved Successfully!");
        document.getElementById("studentForm").reset();
      })
      .catch(error => {
        alert("Error: " + error);
      });
    });
  </script>
</body>
</html>
