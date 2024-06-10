## Flask Registration Form

This repository contains a simple Flask web application that provides a registration form for users to fill out. Upon submission, it displays a confirmation page with the entered details.

### Features

- **Flask Web Application:** Uses the Flask framework to create a web server.
- **HTML Templates:** Utilizes HTML templates for rendering the registration form and confirmation page.
- **Form Handling:** Handles form submission and displays submitted data on a confirmation page.

### Prerequisites

- **Flask Library:** Ensure you have Flask installed. You can install it using pip:
  ```sh
  pip3 install flask
  ```

### Usage

1. **Setup Flask Application:**
   Create the following file structure:
   ```
   /project-directory
   ├── app.py
   ├── templates
   │   ├── register.html
   │   └── confirm.html
   ```

2. **Create HTML Templates:**

   **`register.html`:**
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Register</title>
   </head>
   <body>
       <h2>Registration Form</h2>
       <form action="/confirmation" method="post">
           <label for="name">Name:</label>
           <input type="text" id="name" name="name"><br><br>
           <label for="city">City:</label>
           <input type="text" id="city" name="city"><br><br>
           <label for="phone">Phone Number:</label>
           <input type="text" id="phone" name="phone number"><br><br>
           <input type="submit" value="Submit">
       </form>
   </body>
   </html>
   ```

   **`confirm.html`:**
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Confirmation</title>
   </head>
   <body>
       <h2>Confirmation Page</h2>
       <p>Name: {{ name }}</p>
       <p>City: {{ city }}</p>
       <p>Phone Number: {{ phonenumber }}</p>
   </body>
   </html>
   ```

3. **Run the Flask Application:**
   Execute the Flask application using Python:
   ```sh
   python3 app.py
   ```

4. **Access the Application:**
   Open a web browser and navigate to `http://127.0.0.1:5000/` to view the registration form.

### Example Code

```python
# IMPORTING
from flask import Flask, render_template, request

# INTERACTION
web = Flask(__name__)

# MAPPING
@web.route('/')
@web.route('/register')
def home():
    return render_template('register.html')

@web.route("/confirmation", methods=['POST', 'GET'])
def register():
    if request.method == "POST":
        n = request.form.get('name')
        c = request.form.get('city')
        p = request.form.get('phone number')
        return render_template('confirm.html', name=n, city=c, phonenumber=p)

# MAIN
if __name__ == "__main__":
    web.run(debug=True)  # debug=True enables auto-refresh for code changes
```

### Notes

- **Debug Mode:** The application runs in debug mode (`debug=True`), which provides detailed error messages and automatically restarts the server on code changes.
- **HTML Form:** The form uses the `POST` method to securely send data to the server.

### Contributing

Feel free to fork this repository and submit pull requests. For major changes, please open an issue first to discuss what you would like to change.

### License

This project is licensed under the MIT License. See the LICENSE file for details.
