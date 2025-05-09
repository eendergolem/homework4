# homework4
homework4
<!DOCTYPE html>
<html lang="uk">
<head>
  <meta charset="UTF-8">
  <title>Форма з валідацією</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 30px;
      background-color: #f4f4f4;
    }

    form {
      background-color: #fff;
      padding: 20px;
      max-width: 400px;
      border-radius: 10px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }

    label {
      display: block;
      margin-top: 15px;
    }

    input {
      width: 100%;
      padding: 10px;
      margin-top: 5px;
      border: 1px solid #ccc;
      border-radius: 5px;
    }

    .error {
      color: red;
      font-size: 0.9em;
    }

    button {
      margin-top: 20px;
      padding: 10px 20px;
      background-color: #28a745;
      border: none;
      color: white;
      border-radius: 5px;
      cursor: pointer;
    }

    button:hover {
      background-color: #218838;
    }
  </style>
</head>
<body>

  <form id="myForm">
    <label>
      Ім'я:
      <input type="text" id="name" name="name">
      <div class="error" id="nameError"></div>
    </label>

    <label>
      Email:
      <input type="email" id="email" name="email">
      <div class="error" id="emailError"></div>
    </label>

    <label>
      Вік:
      <input type="number" id="age" name="age">
      <div class="error" id="ageError"></div>
    </label>

    <button type="submit">Submit</button>
  </form>

  <script>
    document.getElementById("myForm").addEventListener("submit", function(event) {
      event.preventDefault();

      // Очищення попередніх помилок
      document.getElementById("nameError").textContent = "";
      document.getElementById("emailError").textContent = "";
      document.getElementById("ageError").textContent = "";

      let valid = true;
      const name = document.getElementById("name").value.trim();
      const email = document.getElementById("email").value.trim();
      const age = parseInt(document.getElementById("age").value.trim(), 10);

      if (name === "") {
        document.getElementById("nameError").textContent = "Ім'я обов'язкове.";
        valid = false;
      }

      if (!email.includes("@")) {
        document.getElementById("emailError").textContent = "Email повинен містити '@'.";
        valid = false;
      }

      if (isNaN(age) || age <= 0) {
        document.getElementById("ageError").textContent = "Вік повинен бути числом більше нуля.";
        valid = false;
      }

      if (valid) {
        alert("Form submitted!");
        // Можна надіслати форму, наприклад: this.submit();
      }
    });
  </script>

</body>
</html>
