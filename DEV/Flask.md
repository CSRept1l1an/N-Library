#Dev 
1. İntroduction
2. Installation
3. Basic Setup

## 1. Introduction

### Brief Overview of Flask

Flask is a lightweight web framework for Python that is designed to be simple and flexible. It is part of the micro-framework category, meaning it does not come with many built-in features like database abstraction layers, form validation, or authentication, which are provided by more extensive frameworks such as Django. Instead, Flask gives developers the tools to add these features as needed, providing the freedom to choose the components that suit their application best.

Flask was created by Armin Ronacher as part of the Pallets project and is based on the Werkzeug WSGI toolkit and the Jinja2 template engine. Its minimalist approach makes it a popular choice for developing small to medium-sized web applications and APIs.

### Key Features and Benefits

1. **Simplicity and Minimalism**:
   - Flask's core design is simple and easy to understand, making it ideal for developers who prefer a straightforward approach to web development.
   - The framework provides just the essentials, enabling developers to build applications quickly without unnecessary complexity.

2. **Flexibility**:
   - Flask does not impose any dependencies beyond the necessary ones, allowing developers to structure their projects as they see fit.
   - This flexibility extends to choosing libraries and tools for tasks like database interactions, form handling, and authentication.

3. **Modular and Scalable**:
   - Despite its minimalistic nature, Flask can be scaled to support larger applications through its modular design.
   - Extensions are available to add functionality, such as Flask-SQLAlchemy for database integration, Flask-WTF for form handling, and Flask-Login for authentication.

4. **Built-in Development Server and Debugger**:
   - Flask includes a built-in development server and debugger, which simplifies the process of testing and debugging applications during development.
   - The debugger provides detailed error reports and an interactive console for troubleshooting.

5. **RESTful Request Dispatching**:
   - Flask's routing system is simple yet powerful, making it easy to map URLs to Python functions and create RESTful APIs.
   - The `@app.route` decorator allows developers to define routes in a clear and concise manner.

6. **Jinja2 Templating**:
   - Flask uses the Jinja2 template engine, which supports template inheritance and allows for the creation of reusable templates.
   - Jinja2's syntax is similar to Python, making it easy for developers to write and maintain templates.

7. **Extensive Documentation and Community Support**:
   - Flask has comprehensive and well-organized documentation, which is valuable for both beginners and experienced developers.
   - A large and active community contributes to a wealth of third-party extensions, tutorials, and support resources.

8. **Testing Capabilities**:
   - Flask applications can be easily tested using tools like unittest or pytest.
   - The framework supports test-driven development (TDD) by providing utilities for creating test clients and handling requests and responses.

## 2. Installation

### Installing Flask

To get started with Flask, you'll need to install it using Python's package manager, `pip`. It's recommended to set up a virtual environment to manage your project's dependencies.

### Setting up a Virtual Environment

A virtual environment is a self-contained directory that contains a Python installation for a particular version of Python, plus a number of additional packages. Using virtual environments is a good practice to avoid conflicts between dependencies in different projects.

1. **Install `virtualenv` (if you haven't already)**:
```bash
pip install virtualenv
```

2. **Create a virtual environment**:
Navigate to your project directory and create a virtual environment. For example:
```bash
virtualenv venv
```
This will create a directory named `venv` containing the virtual environment.

3. **Activate the virtual environment**:

- **On Windows**:
```bash
venv\Scripts\activate
```

- **On macOS and Linux**:
```bash
source venv/bin/activate
```

Once activated, your command prompt will change to indicate that you are now working inside the virtual environment.

4. **Install Flask**:
With the virtual environment activated, install Flask using `pip`:
```bash
pip install Flask
```

You can verify the installation by running:
```bash
python -m flask --version
```

### Example Installation Process

Here’s a step-by-step example of setting up a virtual environment and installing Flask:

1. **Open your terminal or command prompt**.
2. **Navigate to your project directory**:
```bash
cd path/to/your/project
```

3. **Create a virtual environment**:
```bash
virtualenv venv
```

4. **Activate the virtual environment**:

- **On Windows**:
```bash
venv\Scripts\activate
```

- **On macOS and Linux**:
```bash
source venv/bin/activate
```

5. **Install Flask**:
```bash
pip install Flask
```

6. **Verify the installation**:
```bash
python -m flask --version
```

### Deactivating the Virtual Environment

When you’re done working in the virtual environment, you can deactivate it by simply running:
```bash
deactivate
```

### Summary

Setting up a virtual environment and installing Flask involves the following steps:
1. Install `virtualenv` if it's not already installed.
2. Create a virtual environment in your project directory.
3. Activate the virtual environment.
4. Install Flask within the virtual environment.
5. Deactivate the virtual environment when you're done.

## 3. Basic Setup

### Creating a Basic Flask Application

1. **Create a Project Directory**:
Navigate to your project directory or create a new one:
```bash
mkdir my_flask_app
cd my_flask_app
```

2. **Set Up a Virtual Environment**:
Create and activate a virtual environment (if not already done):
```bash
virtualenv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```

3. **Install Flask**:
Install Flask within the virtual environment:
```bash
pip install Flask
```

4. **Create the Application File**:
In your project directory, create a file named `app.py` and open it in your text editor. Add the following code to create a basic Flask application:
```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
return 'Hello, World!'

if __name__ == '__main__':
app.run(debug=True)
```

### Explanation:
- **`from flask import Flask`**: Imports the Flask class from the Flask module.
- **`app = Flask(__name__)`**: Creates an instance of the Flask class.
- **`@app.route('/')`**: A decorator that binds a function to the URL path `/`.
- **`def hello_world()`**: A view function that returns the string 'Hello, World!' when the root URL is accessed.
- **`app.run(debug=True)`**: Starts the Flask application with debugging enabled, which is useful for development.

### Running the Flask Application

1. **Activate the Virtual Environment** (if not already activated):
```bash
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
```

2. **Run the Application**:
In the terminal, navigate to the directory containing `app.py` and run the application using:
```bash
python app.py
```

3. **Access the Application**:
Once the application is running, you will see output indicating that the Flask development server is running, typically on `http://127.0.0.1:5000/`. Open a web browser and navigate to this URL to see the message "Hello, World!".

### Example Output:
```plaintext
* Serving Flask app 'app'
* Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment.
Use a production WSGI server instead.
* Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
* Restarting with stat
* Debugger is active!
* Debugger PIN: xxx-xxx-xxx
```

### Summary

To create and run a basic Flask application:
1. Set up a project directory and virtual environment.
2. Install Flask in the virtual environment.
3. Create a basic `app.py` file with the Flask application code.
4. Run the application using `python app.py`.
5. Access the running application in a web browser at `http://127.0.0.1:5000/`.

This process sets up a simple Flask application that can be the foundation for more complex web development projects.

## 4. Routing

### Defining Routes

In Flask, routing refers to mapping URLs to functions. These functions, also known as view functions, are executed when their associated URL is accessed.

#### Basic Route Definition

To define a route, use the `@app.route` decorator. Here’s an example:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return 'This is the home page.'

@app.route('/about')
def about():
    return 'This is the about page.'

if __name__ == '__main__':
    app.run(debug=True)
```

- **`@app.route('/')`**: Binds the `home` function to the root URL (`/`).
- **`@app.route('/about')`**: Binds the `about` function to the `/about` URL.

#### Dynamic Routes

Flask allows for dynamic routes where parts of the URL can act as parameters to functions. Here’s an example:

```python
@app.route('/user/<username>')
def show_user_profile(username):
    return f'User: {username}'

@app.route('/post/<int:post_id>')
def show_post(post_id):
    return f'Post ID: {post_id}'
```

- **`<username>`**: Captures a string and passes it to the `show_user_profile` function.
- **`<int:post_id>`**: Captures an integer and passes it to the `show_post` function.

### HTTP Methods (GET, POST, etc.)

By default, routes respond to `GET` requests. However, you can specify the methods a route should respond to using the `methods` parameter in the `@app.route` decorator.

#### Handling GET and POST Requests

Here’s an example of a route that handles both `GET` and `POST` requests:

```python
from flask import request

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        username = request.form['username']
        return f'Logged in as {username}'
    return '''
        <form method="post">
            <p><input type="text" name="username">
            <p><input type="submit" value="Login">
        </form>
    '''
```

- **`methods=['GET', 'POST']`**: Specifies that the `login` route can handle both `GET` and `POST` requests.
- **`request.method`**: Checks the HTTP method used for the request.
- **`request.form`**: Accesses form data sent in a `POST` request.

#### Other HTTP Methods

Flask supports other HTTP methods like `PUT`, `DELETE`, and `PATCH`. Here’s an example using these methods:

```python
@app.route('/item', methods=['POST'])
def create_item():
    return 'Item created'

@app.route('/item/<int:item_id>', methods=['PUT'])
def update_item(item_id):
    return f'Item {item_id} updated'

@app.route('/item/<int:item_id>', methods=['DELETE'])
def delete_item(item_id):
    return f'Item {item_id} deleted'
```

- **`POST`**: Typically used for creating resources.
- **`PUT`**: Used for updating existing resources.
- **`DELETE`**: Used for deleting resources.

### Example: Full Application with Routes and Methods

```python
from flask import Flask, request

app = Flask(__name__)

@app.route('/')
def home():
    return 'Home Page'

@app.route('/user/<username>')
def show_user_profile(username):
    return f'User: {username}'

@app.route('/post/<int:post_id>')
def show_post(post_id):
    return f'Post ID: {post_id}'

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        username = request.form['username']
        return f'Logged in as {username}'
    return '''
        <form method="post">
            <p><input type="text" name="username">
            <p><input type="submit" value="Login">
        </form>
    '''

@app.route('/item', methods=['POST'])
def create_item():
    return 'Item created'

@app.route('/item/<int:item_id>', methods=['PUT'])
def update_item(item_id):
    return f'Item {item_id} updated'

@app.route('/item/<int:item_id>', methods=['DELETE'])
def delete_item(item_id):
    return f'Item {item_id} deleted'

if __name__ == '__main__':
    app.run(debug=True)
```

### Summary

- **Defining Routes**: Use the `@app.route` decorator to bind URLs to view functions.
- **Dynamic Routes**: Capture parts of the URL as parameters.
- **HTTP Methods**: Use the `methods` parameter to specify which HTTP methods a route should handle, such as `GET`, `POST`, `PUT`, and `DELETE`.

## 5. Templates

### Setting up Jinja2 Templates

Flask uses the Jinja2 template engine to render HTML templates. This allows you to create dynamic web pages by embedding [[DEV/Programming/Python|Python]]-like expressions within HTML.

1. **Create a Templates Directory**:
Flask looks for templates in the `templates` directory by default. Create this directory in your project root.

```bash
mkdir templates
```

2. **Create a Template File**:
Create an HTML file within the `templates` directory. For example, create a file named `index.html`:

```html
<!-- templates/index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>{{ title }}</title>
</head>
<body>
   <h1>{{ heading }}</h1>
   <p>{{ message }}</p>
</body>
</html>
```

- **`{{ title }}`**: A placeholder for dynamic content passed from the Flask view.
- **`{{ heading }}`** and **`{{ message }}`**: Additional placeholders for dynamic content.

### Rendering Templates

To render a template from a Flask view function, use the `render_template` function provided by Flask.

1. **Import `render_template`**:
Ensure you import `render_template` from Flask:

```python
from flask import Flask, render_template
```

2. **Render the Template in a View Function**:
Use `render_template` to render the HTML template and pass any dynamic content as keyword arguments:

```python
app = Flask(__name__)

@app.route('/')
def home():
return render_template('index.html', title='Home Page', heading='Welcome!', message='This is the home page.')

if __name__ == '__main__':
app.run(debug=True)
```

- **`render_template('index.html', title='Home Page', heading='Welcome!', message='This is the home page.')`**:
- Renders the `index.html` template.
- Passes dynamic content to the template using keyword arguments.

### Example: Full Application with Templates

Here’s a complete example demonstrating how to set up and render templates in a Flask application:

1. **Project Structure**:
```
my_flask_app/
├── app.py
└── templates/
└── index.html
```

2. **app.py**:

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def home():
return render_template('index.html', title='Home Page', heading='Welcome!', message='This is the home page.')

@app.route('/about')
def about():
return render_template('index.html', title='About', heading='About Us', message='This is the about page.')

if __name__ == '__main__':
app.run(debug=True)
```

3. **templates/index.html**:

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>{{ title }}</title>
</head>
<body>
	<h1>{{ heading }}</h1>
	<p>{{ message }}</p>
</body>
</html>
```

### Summary

- **Setting up Jinja2 Templates**:
  - Create a `templates` directory in your project.
  - Add HTML files in the `templates` directory with placeholders for dynamic content using Jinja2 syntax (`{{ }}`).

- **Rendering Templates**:
  - Import `render_template` from Flask.
  - Use `render_template` in view functions to render HTML templates and pass dynamic content as keyword arguments.

By following these steps, you can create dynamic web pages with Flask, rendering content based on the data passed from your view functions.

### 6. Forms and User Input
- Handling forms with Flask-WTF
- Validating user input

## 7. Database Integration
- Setting up SQLAlchemy
- Performing CRUD operations

### 8. API Development

- Creating RESTful APIs
- JSON responses and request handling
- Using Flask-RESTful
## 9. Authentication and Authorization
- Using Flask-Login
- Protecting routes

## 10. Blueprints and Application Structure
- Organizing the application using Blueprints
- Recommended project structure

## 11. Error Handling
- Custom error pages

## 12. Testing
- Writing unit tests for Flask applications

## 13. Deployment
- Deploying with Gunicorn
- Setting up for Heroku

## 14. Useful Extensions
- List and brief description of useful Flask extensions

## 15. Additional Resources
### Documentation
- https://flask.palletsprojects.com/en/3.0.x/

### Tutorials
- https://realpython.com/flask-project/
- https://realpython.com/flask-database/
- https://realpython.com/flask-logging-messages/
