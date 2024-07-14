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
├── templates/
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

## 6. Forms and User Input

### Handling Forms with Flask-WTF

Flask-WTF is an extension that simplifies the integration of forms in Flask applications. It provides a way to handle form validation and rendering using WTForms.

1. **Install Flask-WTF**:
   Install Flask-WTF using `pip`:

```bash
pip install flask-wtf
```

1. **Configure Flask for CSRF Protection**:
   Flask-WTF uses CSRF tokens to protect forms from Cross-Site Request Forgery (CSRF) attacks. Configure your Flask application with a secret key for CSRF protection.

```python
from flask import Flask

app = Flask(__name__)
app.config['SECRET_KEY'] = 'your_secret_key'
```

1. **Create a Form Class**:
   Define a form class by subclassing `FlaskForm` from `flask_wtf`.

```python
from flask_wtf import FlaskForm
from wtforms import StringField, PasswordField, SubmitField
from wtforms.validators import DataRequired, Email, Length

class RegistrationForm(FlaskForm):
   username = StringField('Username', validators=[DataRequired(), Length(min=2, max=20)])
   email = StringField('Email', validators=[DataRequired(), Email()])
   password = PasswordField('Password', validators=[DataRequired(), Length(min=6)])
   submit = SubmitField('Sign Up')
```

   - **`StringField`, `PasswordField`, `SubmitField`**: Define form fields.
   - **`validators`**: Specify validation rules (e.g., `DataRequired`, `Email`, `Length`).

4. **Render the Form in a Template**:
   Create an HTML template to render the form.

```html
<!-- templates/register.html -->
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Register</title>
</head>
<body>
   <h1>Register</h1>
   <form method="POST">
	   {{ form.hidden_tag() }}
	   <p>
		   {{ form.username.label }}<br>
		   {{ form.username(size=20) }}
	   </p>
	   <p>
		   {{ form.email.label }}<br>
		   {{ form.email(size=20) }}
	   </p>
	   <p>
		   {{ form.password.label }}<br>
		   {{ form.password(size=20) }}
	   </p>
	   <p>{{ form.submit() }}</p>
   </form>
</body>
</html>
```

   - **`form.hidden_tag()`**: Renders hidden fields, including the CSRF token.
   - **`form.field`**: Renders form fields and their labels.

5. **Handle Form Submission in a View**:
   In your Flask application, handle form submission and validation.

```python
from flask import Flask, render_template, redirect, url_for, flash
from forms import RegistrationForm

app = Flask(__name__)
app.config['SECRET_KEY'] = 'your_secret_key'

@app.route('/register', methods=['GET', 'POST'])
def register():
   form = RegistrationForm()
   if form.validate_on_submit():
	   flash(f'Account created for {form.username.data}!', 'success')
	   return redirect(url_for('home'))
   return render_template('register.html', form=form)

@app.route('/')
def home():
   return 'Home Page'

if __name__ == '__main__':
   app.run(debug=True)
```

   - **`validate_on_submit()`**: Validates the form on submission.
   - **`flash()`**: Displays a success message using Flask’s flash messaging system.
   - **`redirect()` and `url_for()`**: Redirect the user after a successful form submission.

### Validating User Input

Validation ensures that the data submitted through forms meets specific criteria. Flask-WTF uses WTForms validators to validate user input.

1. **Using Validators**:
   Apply validators to form fields to enforce rules.

```python
from wtforms import StringField, PasswordField, SubmitField
from wtforms.validators import DataRequired, Email, Length

class RegistrationForm(FlaskForm):
   username = StringField('Username', validators=[DataRequired(), Length(min=2, max=20)])
   email = StringField('Email', validators=[DataRequired(), Email()])
   password = PasswordField('Password', validators=[DataRequired(), Length(min=6)])
   submit = SubmitField('Sign Up')
```

   - **`DataRequired`**: Ensures the field is not empty.
   - **`Email`**: Validates that the field contains a valid email address.
   - **`Length`**: Ensures the field value meets length requirements.

2. **Custom Validators**:
   You can create custom validators for more complex validation logic.

```python
from wtforms import ValidationError

def validate_username(form, field):
   if field.data == 'admin':
	   raise ValidationError('Username cannot be "admin".')

class RegistrationForm(FlaskForm):
   username = StringField('Username', validators=[DataRequired(), Length(min=2, max=20), validate_username])
   email = StringField('Email', validators=[DataRequired(), Email()])
   password = PasswordField('Password', validators=[DataRequired(), Length(min=6)])
   submit = SubmitField('Sign Up')
```

   - **`validate_username(form, field)`**: Custom validator function.
   - **`raise ValidationError`**: Raises a validation error if the condition is not met.

### Example: Full Application with Forms and Validation

1. **Project Structure**:
```
my_flask_app/
├── app.py
├── forms.py
├── templates/
│	└── register.html
└── requirements.txt
```

1. **forms.py**:

```python
from flask_wtf import FlaskForm
from wtforms import StringField, PasswordField, SubmitField
from wtforms.validators import DataRequired, Email, Length

class RegistrationForm(FlaskForm):
   username = StringField('Username', validators=[DataRequired(), Length(min=2, max=20)])
   email = StringField('Email', validators=[DataRequired(), Email()])
   password = PasswordField('Password', validators=[DataRequired(), Length(min=6)])
   submit = SubmitField('Sign Up')
```

3. **app.py**:

```python
from flask import Flask, render_template, redirect, url_for, flash
from forms import RegistrationForm

app = Flask(__name__)
app.config['SECRET_KEY'] = 'your_secret_key'

@app.route('/register', methods=['GET', 'POST'])
def register():
   form = RegistrationForm()
   if form.validate_on_submit():
	   flash(f'Account created for {form.username.data}!', 'success')
	   return redirect(url_for('home'))
   return render_template('register.html', form=form)

@app.route('/')
def home():
   return 'Home Page'

if __name__ == '__main__':
   app.run(debug=True)
```

1. **templates/register.html**:

```html
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Register</title>
</head>
<body>
   <h1>Register</h1>
   <form method="POST">
	   {{ form.hidden_tag() }}
	   <p>
		   {{ form.username.label }}<br>
		   {{ form.username(size=20) }}
		   {% for error in form.username.errors %}
			   <span style="color: red;">[{{ error }}]</span>
		   {% endfor %}
	   </p>
	   <p>
		   {{ form.email.label }}<br>
		   {{ form.email(size=20) }}
		   {% for error in form.email.errors %}
			   <span style="color: red;">[{{ error }}]</span>
		   {% endfor %}
	   </p>
	   <p>
		   {{ form.password.label }}<br>
		   {{ form.password(size=20) }}
		   {% for error in form.password.errors %}
			   <span style="color: red;">[{{ error }}]</span>
		   {% endfor %}
	   </p>
	   <p>{{ form.submit() }}</p>
   </form>
</body>
</html>
```

5. **requirements.txt**:

```text
Flask
Flask-WTF
```

### Summary

- **Handling Forms with Flask-WTF**:
  - Install and configure Flask-WTF.
  - Create form classes by subclassing `FlaskForm`.
  - Render forms in templates and handle form submissions in view functions.

- **Validating User Input**:
  - Use built-in validators like `DataRequired`, `Email`, and `Length`.
  - Create custom validators for complex validation logic.

## 7. Database Integration

### Setting up SQLAlchemy

SQLAlchemy is a popular SQL toolkit and Object-Relational Mapping (ORM) library for Python. Flask-SQLAlchemy is an extension that simplifies using SQLAlchemy with Flask.

1. **Install Flask-SQLAlchemy**:
Install Flask-SQLAlchemy using `pip`:

```bash
pip install flask-sqlalchemy
```

2. **Configure Flask to Use SQLAlchemy**:
In your Flask application, configure the database URI and initialize SQLAlchemy.

```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///mydatabase.db'  # For SQLite database
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

db = SQLAlchemy(app)
```

- **`SQLALCHEMY_DATABASE_URI`**: Specifies the database URL. For SQLite, it's `sqlite:///mydatabase.db`.
- **`SQLALCHEMY_TRACK_MODIFICATIONS`**: Disables a feature that signals the app every time a change is about to be made in the database, which consumes memory.

3. **Define Models**:
Define your database models by subclassing `db.Model`.

```python
class User(db.Model):
id = db.Column(db.Integer, primary_key=True)
username = db.Column(db.String(80), unique=True, nullable=False)
email = db.Column(db.String(120), unique=True, nullable=False)

def __repr__(self):
return f'<User {self.username}>'
```

- **`id`**: Primary key column.
- **`username`**: Unique and non-nullable string column.
- **`email`**: Unique and non-nullable string column.

4. **Create the Database**:
Create the database and tables by running the following commands in the Python shell:

```python
from app import db
db.create_all()
```

### Performing CRUD Operations

CRUD stands for Create, Read, Update, and Delete. Here’s how to perform these operations using Flask-SQLAlchemy.

1. **Create**:
Add a new record to the database.

```python
from app import db, User

new_user = User(username='john_doe', email='john@example.com')
db.session.add(new_user)
db.session.commit()
```

2. **Read**:
Query records from the database.

```python
# Get all users
users = User.query.all()

# Get a user by primary key
user = User.query.get(1)

# Filter users by username
user = User.query.filter_by(username='john_doe').first()
```

3. **Update**:
Modify an existing record.

```python
user = User.query.get(1)
user.email = 'john.doe@example.com'
db.session.commit()
```

4. **Delete**:
Remove a record from the database.

```python
user = User.query.get(1)
db.session.delete(user)
db.session.commit()
```

### Example: Full Application with Database Integration

1. **Project Structure**:
```
my_flask_app/
├── app.py
├── requirements.txt
└── mydatabase.db
```

2. **app.py**:

```python
from flask import Flask, request, jsonify
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///mydatabase.db'
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

db = SQLAlchemy(app)

class User(db.Model):
id = db.Column(db.Integer, primary_key=True)
username = db.Column(db.String(80), unique=True, nullable=False)
email = db.Column(db.String(120), unique=True, nullable=False)

def __repr__(self):
return f'<User {self.username}>'

@app.route('/user', methods=['POST'])
def create_user():
data = request.get_json()
new_user = User(username=data['username'], email=data['email'])
db.session.add(new_user)
db.session.commit()
return jsonify({'message': 'User created'}), 201

@app.route('/user/<int:user_id>', methods=['GET'])
def get_user(user_id):
user = User.query.get_or_404(user_id)
return jsonify({'username': user.username, 'email': user.email})

@app.route('/user/<int:user_id>', methods=['PUT'])
def update_user(user_id):
data = request.get_json()
user = User.query.get_or_404(user_id)
user.email = data.get('email', user.email)
db.session.commit()
return jsonify({'message': 'User updated'})

@app.route('/user/<int:user_id>', methods=['DELETE'])
def delete_user(user_id):
user = User.query.get_or_404(user_id)
db.session.delete(user)
db.session.commit()
return jsonify({'message': 'User deleted'})

if __name__ == '__main__':
app.run(debug=True)
```

3. **requirements.txt**:

```text
Flask
Flask-SQLAlchemy
```

4. **Create the Database**:
Run the following commands in the Python shell to create the database:

```python
from app import db
db.create_all()
```

### Summary

- **Setting up SQLAlchemy**:
  - Install and configure Flask-SQLAlchemy.
  - Define models by subclassing `db.Model`.
  - Create the database and tables.

- **Performing CRUD Operations**:
  - **Create**: Add new records using `db.session.add()` and `db.session.commit()`.
  - **Read**: Query records using `User.query` methods.
  - **Update**: Modify records and commit the changes.
  - **Delete**: Remove records and commit the changes.

## 8. API Development

### Creating RESTful APIs

Flask can be used to create [[API#REST API|RESTful API]]s by defining routes that return JSON data. Flask's built-in support for JSON makes it straightforward to handle JSON responses and requests.

### JSON Responses and Request Handling

1. **Returning JSON Responses**:
Use `jsonify` from Flask to return JSON responses.

```python
from flask import Flask, jsonify

app = Flask(__name__)

@app.route('/api/data', methods=['GET'])
def get_data():
   data = {
	   'name': 'John Doe',
	   'age': 30,
	   'city': 'New York'
   }
   return jsonify(data)

if __name__ == '__main__':
   app.run(debug=True)
```

- **`jsonify(data)`**: Converts the `data` dictionary to a JSON response.

2. **Handling JSON Requests**:
Use `request.get_json()` to parse JSON data from incoming requests.

```python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/api/data', methods=['POST'])
def create_data():
   data = request.get_json()
   return jsonify(data), 201

if __name__ == '__main__':
   app.run(debug=True)
```

- **`request.get_json()`**: Parses the JSON data from the request body.
- **`201`**: HTTP status code for resource creation.

### Using Flask-RESTful

Flask-RESTful is an extension for Flask that adds support for quickly building REST APIs. It provides tools to build RESTful APIs using class-based views.

1. **Installation**:
Install Flask-RESTful using `pip`:

```bash
pip install flask-restful
```

2. **Creating a RESTful API**:
Define resources and routes using Flask-RESTful.

```python
from flask import Flask
from flask_restful import Resource, Api

app = Flask(__name__)
api = Api(app)

class HelloWorld(Resource):
   def get(self):
	   return {'hello': 'world'}

api.add_resource(HelloWorld, '/')

if __name__ == '__main__':
   app.run(debug=True)
```

- **`Resource`**: Base class for creating RESTful resources.
- **`api.add_resource(HelloWorld, '/')`**: Adds the `HelloWorld` resource to the API at the root URL.

3. **Handling HTTP Methods**:
Define methods like `get`, `post`, `put`, and `delete` within resource classes.

```python
class Item(Resource):
   def get(self, item_id):
	   return {'item_id': item_id}

   def post(self):
	   data = request.get_json()
	   return {'data': data}, 201

   def put(self, item_id):
	   data = request.get_json()
	   return {'item_id': item_id, 'data': data}

   def delete(self, item_id):
	   return {'message': f'Item {item_id} deleted'}

api.add_resource(Item, '/item/<int:item_id>')
```

- **`get(self, item_id)`**: Handles GET requests.
- **`post(self)`**: Handles POST requests.
- **`put(self, item_id)`**: Handles PUT requests.
- **`delete(self, item_id)`**: Handles DELETE requests.

### Example: Full Application with RESTful API

1. **Project Structure**:
```
my_flask_api/
├── app.py
└── requirements.txt
```

2. **app.py**:

```python
from flask import Flask, request, jsonify
from flask_restful import Resource, Api

app = Flask(__name__)
api = Api(app)

class HelloWorld(Resource):
   def get(self):
	   return {'hello': 'world'}

class Item(Resource):
   def get(self, item_id):
	   return {'item_id': item_id}

   def post(self):
	   data = request.get_json()
	   return {'data': data}, 201

   def put(self, item_id):
	   data = request.get_json()
	   return {'item_id': item_id, 'data': data}

   def delete(self, item_id):
	   return {'message': f'Item {item_id} deleted'}

api.add_resource(HelloWorld, '/')
api.add_resource(Item, '/item/<int:item_id>')

if __name__ == '__main__':
   app.run(debug=True)
```

3. **requirements.txt**:

```text
Flask
flask-restful
```

### Summary

- **Creating RESTful APIs**: Define routes that return JSON responses and handle JSON requests using Flask's built-in functions.
- **Using Flask-RESTful**: Simplify API development by using class-based views and handling different HTTP methods in a structured way.

By following these steps, you can develop a RESTful API with Flask, leveraging the simplicity of Flask for basic JSON handling or the extended functionality of Flask-RESTful for more complex APIs.

## 9. Authentication and Authorization

### Using Flask-Login

Flask-Login is an extension that provides user session management for Flask. It handles common tasks like logging in, logging out, and remembering users' sessions.

1. **Install Flask-Login**:
   Install Flask-Login using `pip`:

```bash
pip install flask-login
```

2. **Configure Flask-Login**:
   Set up Flask-Login in your Flask application.

```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy
from flask_login import LoginManager

app = Flask(__name__)
app.config['SECRET_KEY'] = 'your_secret_key'
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///mydatabase.db'
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

db = SQLAlchemy(app)
login_manager = LoginManager(app)
login_manager.login_view = 'login'  # Redirect to login page if not authenticated
```

3. **Define User Model**:
   Your user model must implement certain properties and methods for Flask-Login to work.

```python
from flask_login import UserMixin

class User(db.Model, UserMixin):
   id = db.Column(db.Integer, primary_key=True)
   username = db.Column(db.String(80), unique=True, nullable=False)
   email = db.Column(db.String(120), unique=True, nullable=False)
   password = db.Column(db.String(60), nullable=False)

   def __repr__(self):
	   return f'<User {self.username}>'
```

4. **Load User**:
   Define a user loader function that Flask-Login will use to load a user from the user ID stored in the session.

```python
@login_manager.user_loader
def load_user(user_id):
   return User.query.get(int(user_id))
```

5. **Create Login and Register Forms**:
   Define forms for user registration and login.

```python
from flask_wtf import FlaskForm
from wtforms import StringField, PasswordField, SubmitField
from wtforms.validators import DataRequired, Email, Length

class RegistrationForm(FlaskForm):
   username = StringField('Username', validators=[DataRequired(), Length(min=2, max=20)])
   email = StringField('Email', validators=[DataRequired(), Email()])
   password = PasswordField('Password', validators=[DataRequired(), Length(min=6)])
   submit = SubmitField('Sign Up')

class LoginForm(FlaskForm):
   email = StringField('Email', validators=[DataRequired(), Email()])
   password = PasswordField('Password', validators=[DataRequired()])
   submit = SubmitField('Login')
```

1. **Handle User Registration and Login**:
   Create routes and views for user registration and login.

```python
from flask import render_template, redirect, url_for, flash, request
from flask_login import login_user, logout_user, login_required, current_user
from werkzeug.security import generate_password_hash, check_password_hash
from forms import RegistrationForm, LoginForm
from models import User  # Assuming your User model is in a models.py file

@app.route('/register', methods=['GET', 'POST'])
def register():
   form = RegistrationForm()
   if form.validate_on_submit():
	   hashed_password = generate_password_hash(form.password.data, method='sha256')
	   new_user = User(username=form.username.data, email=form.email.data, password=hashed_password)
	   db.session.add(new_user)
	   db.session.commit()
	   flash('Account created!', 'success')
	   return redirect(url_for('login'))
   return render_template('register.html', form=form)

@app.route('/login', methods=['GET', 'POST'])
def login():
   form = LoginForm()
   if form.validate_on_submit():
	   user = User.query.filter_by(email=form.email.data).first()
	   if user and check_password_hash(user.password, form.password.data):
		   login_user(user, remember=True)
		   next_page = request.args.get('next')
		   return redirect(next_page) if next_page else redirect(url_for('home'))
	   else:
		   flash('Login Unsuccessful. Please check email and password', 'danger')
   return render_template('login.html', form=form)

@app.route('/logout')
@login_required
def logout():
   logout_user()
   return redirect(url_for('home'))

@app.route('/')
@login_required
def home():
   return 'Home Page'
```

   - **`generate_password_hash()`**: Hashes the user password for storage.
   - **`check_password_hash()`**: Checks the hashed password against the user-provided password.
   - **`login_user(user, remember=True)`**: Logs in the user and remembers their session.
   - **`logout_user()`**: Logs out the user.
   - **`@login_required`**: Protects routes that require authentication.

### Protecting Routes

To protect routes so that only authenticated users can access them, use the `@login_required` decorator from Flask-Login.

1. **Protecting Routes**:
   Add the `@login_required` decorator to any route that requires authentication.

```python
from flask_login import login_required

@app.route('/dashboard')
@login_required
def dashboard():
   return 'This is the dashboard'
```

2. **Redirecting to Login Page**:
   When a user tries to access a protected route, they will be redirected to the login page. Set the `login_view` attribute in the `LoginManager` configuration to specify the login route.

```python
login_manager.login_view = 'login'
```

3. **Handling Next URL**:
   Ensure that the user is redirected back to the page they were trying to access after logging in.

```python
@app.route('/login', methods=['GET', 'POST'])
def login():
   form = LoginForm()
   if form.validate_on_submit():
	   user = User.query.filter_by(email=form.email.data).first()
	   if user and check_password_hash(user.password, form.password.data):
		   login_user(user, remember=True)
		   next_page = request.args.get('next')
		   return redirect(next_page) if next_page else redirect(url_for('home'))
	   else:
		   flash('Login Unsuccessful. Please check email and password', 'danger')
   return render_template('login.html', form=form)
```

### Example: Full Application with Authentication and Authorization

1. **Project Structure**:
```
my_flask_app/
├── app.py
├── forms.py
├── models.py
├── templates/
│   ├── register.html
│   └── login.html
└── requirements.txt
```

1. **models.py**:

```python
from flask_sqlalchemy import SQLAlchemy
from flask_login import UserMixin

db = SQLAlchemy()

class User(db.Model, UserMixin):
   id = db.Column(db.Integer, primary_key=True)
   username = db.Column(db.String(80), unique=True, nullable=False)
   email = db.Column(db.String(120), unique=True, nullable=False)
   password = db.Column(db.String(60), nullable=False)

   def __repr__(self):
	   return f'<User {self.username}>'
```

3. **forms.py**:

```python
from flask_wtf import FlaskForm
from wtforms import StringField, PasswordField, SubmitField
from wtforms.validators import DataRequired, Email, Length

class RegistrationForm(FlaskForm):
   username = StringField('Username', validators=[DataRequired(), Length(min=2, max=20)])
   email = StringField('Email', validators=[DataRequired(), Email()])
   password = PasswordField('Password', validators=[DataRequired(), Length(min=6)])
   submit = SubmitField('Sign Up')

class LoginForm(FlaskForm):
   email = StringField('Email', validators=[DataRequired(), Email()])
   password = PasswordField('Password', validators=[DataRequired()])
   submit = SubmitField('Login')
```

4. **templates/register.html**:

```html
<!DOCTYPE html>
<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Register</title>
</head>
<body>
   <h1>Register</h1>
   <form method="POST">
	   {{ form.hidden_tag() }}
	   <p>
		   {{ form.username.label }}<br>
		   {{ form.username(size=20) }}
		   {% for error in form.username.errors %}
			   <span style="color: red;">[{{ error }}]</span>
		   {% endfor %}
	   </p>
	   <p>
		   {{ form.email.label }}<br>
		   {{ form.email(size=20) }}
		   {% for error in form.email.errors %}
			   <span style="color: red;">[{{ error }}]</span>
		   {% endfor %}
	   </p>
	   <p>
		   {{ form.password.label }}<br>
		   {{ form.password(size=20) }}
		   {% for error in form.password.errors %}
			   <span style="color: red;">[{{ error }}]</span>
		   {% endfor %}
	   </p>
	   <p>{{ form.submit() }}</p>
   </form>
</body>
</html>
```

5. **templates/login.html**:

```html
<!DOCTYPE html>


<html lang="en">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <title>Login</title>
</head>
<body>
   <h1>Login</h1>
   <form method="POST">
	   {{ form.hidden_tag() }}
	   <p>
		   {{ form.email.label }}<br>
		   {{ form.email(size=20) }}
		   {% for error in form.email.errors %}
			   <span style="color: red;">[{{ error }}]</span>
		   {% endfor %}
	   </p>
	   <p>
		   {{ form.password.label }}<br>
		   {{ form.password(size=20) }}
		   {% for error in form.password.errors %}
			   <span style="color: red;">[{{ error }}]</span>
		   {% endfor %}
	   </p>
	   <p>{{ form.submit() }}</p>
   </form>
</body>
</html>
```

6. **app.py**:

```python
from flask import Flask, render_template, redirect, url_for, flash, request
from flask_sqlalchemy import SQLAlchemy
from flask_login import LoginManager, login_user, logout_user, login_required, current_user
from werkzeug.security import generate_password_hash, check_password_hash
from forms import RegistrationForm, LoginForm
from models import db, User

app = Flask(__name__)
app.config['SECRET_KEY'] = 'your_secret_key'
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///mydatabase.db'
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

db.init_app(app)
login_manager = LoginManager(app)
login_manager.login_view = 'login'

@login_manager.user_loader
def load_user(user_id):
   return User.query.get(int(user_id))

@app.route('/register', methods=['GET', 'POST'])
def register():
   form = RegistrationForm()
   if form.validate_on_submit():
	   hashed_password = generate_password_hash(form.password.data, method='sha256')
	   new_user = User(username=form.username.data, email=form.email.data, password=hashed_password)
	   db.session.add(new_user)
	   db.session.commit()
	   flash('Account created!', 'success')
	   return redirect(url_for('login'))
   return render_template('register.html', form=form)

@app.route('/login', methods=['GET', 'POST'])
def login():
   form = LoginForm()
   if form.validate_on_submit():
	   user = User.query.filter_by(email=form.email.data).first()
	   if user and check_password_hash(user.password, form.password.data):
		   login_user(user, remember=True)
		   next_page = request.args.get('next')
		   return redirect(next_page) if next_page else redirect(url_for('home'))
	   else:
		   flash('Login Unsuccessful. Please check email and password', 'danger')
   return render_template('login.html', form=form)

@app.route('/logout')
@login_required
def logout():
   logout_user()
   return redirect(url_for('home'))

@app.route('/')
@login_required
def home():
   return 'Home Page'

if __name__ == '__main__':
   with app.app_context():
	   db.create_all()
   app.run(debug=True)
```

7. **requirements.txt**:

```text
Flask
Flask-WTF
Flask-Login
Flask-SQLAlchemy
```

### Summary

- **Using Flask-Login**:
  - Install and configure Flask-Login.
  - Define a user model that implements required properties and methods.
  - Create a user loader function.
  - Define routes for user registration, login, and logout.
  - Use `login_user` to log in users and `logout_user` to log out users.

- **Protecting Routes**:
  - Use the `@login_required` decorator to protect routes.
  - Redirect unauthenticated users to the login page.
  - Handle the next URL to redirect users to their intended destination after logging in.

## 10. Blueprints and Application Structure

### Organizing the Application Using Blueprints

Flask Blueprints allow you to organize your application into smaller, reusable components, making the codebase more manageable.

1. **Creating a Blueprint**:
   Define a Blueprint in a separate module.

```python
from flask import Blueprint

main = Blueprint('main', __name__)

@main.route('/')
def home():
   return 'Home Page'

@main.route('/about')
def about():
   return 'About Page'
```

2. **Registering the Blueprint**:
   Register the Blueprint with your Flask application in the main application file.

```python
from flask import Flask
from main import main  # Import the Blueprint

app = Flask(__name__)
app.register_blueprint(main)  # Register the Blueprint

if __name__ == '__main__':
   app.run(debug=True)
```

### Recommended Project Structure

A well-organized project structure is essential for maintaining and scaling your application. Here's a recommended project structure using Blueprints:

```
my_flask_app/
├── app/
│   ├── __init__.py
│   ├── main/
│   │   ├── __init__.py
│   │   ├── routes.py
│   │   ├── templates/
│   │   │   ├── home.html
│   │   │   ├── about.html
│   │   └── static/
│   ├── auth/
│   │   ├── __init__.py
│   │   ├── routes.py
│   │   ├── templates/
│   │   │   ├── login.html
│   │   │   ├── register.html
│   │   └── static/
│   ├── models.py
│   └── forms.py
├── migrations/
├── tests/
│   ├── __init__.py
│   ├── test_main.py
│   ├── test_auth.py
├── .env
├── config.py
├── requirements.txt
└── run.py
```

### Example: Setting Up Blueprints

1. **`app/__init__.py`**:

```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy
from flask_login import LoginManager
from config import Config

db = SQLAlchemy()
login_manager = LoginManager()

def create_app():
   app = Flask(__name__)
   app.config.from_object(Config)

   db.init_app(app)
   login_manager.init_app(app)
   login_manager.login_view = 'auth.login'

   from app.main import main as main_blueprint
   app.register_blueprint(main_blueprint)

   from app.auth import auth as auth_blueprint
   app.register_blueprint(auth_blueprint, url_prefix='/auth')

   return app
```

2. **`config.py`**:

```python
import os

class Config:
   SECRET_KEY = os.environ.get('SECRET_KEY') or 'you-will-never-guess'
   SQLALCHEMY_DATABASE_URI = os.environ.get('DATABASE_URL') or 'sqlite:///site.db'
   SQLALCHEMY_TRACK_MODIFICATIONS = False
```

3. **`run.py`**:

```python
from app import create_app, db
from app.models import User

app = create_app()

if __name__ == '__main__':
   with app.app_context():
	   db.create_all()
   app.run(debug=True)
```

4. **`app/main/__init__.py`**:

```python
from flask import Blueprint

main = Blueprint('main', __name__)

from app.main import routes
```

5. **`app/main/routes.py`**:

```python
from flask import render_template
from app.main import main

@main.route('/')
def home():
   return render_template('home.html')

@main.route('/about')
def about():
   return render_template('about.html')
```

1. **`app/auth/__init__.py`**:

```python
from flask import Blueprint

auth = Blueprint('auth', __name__)

from app.auth import routes
```

1. **`app/auth/routes.py`**:

```python
from flask import render_template, redirect, url_for, flash, request
from flask_login import login_user, logout_user, login_required, current_user
from app import db
from app.auth import auth
from app.models import User
from app.auth.forms import RegistrationForm, LoginForm
from werkzeug.security import generate_password_hash, check_password_hash

@auth.route('/register', methods=['GET', 'POST'])
def register():
   form = RegistrationForm()
   if form.validate_on_submit():
	   hashed_password = generate_password_hash(form.password.data, method='sha256')
	   new_user = User(username=form.username.data, email=form.email.data, password=hashed_password)
	   db.session.add(new_user)
	   db.session.commit()
	   flash('Your account has been created!', 'success')
	   return redirect(url_for('auth.login'))
   return render_template('register.html', form=form)

@auth.route('/login', methods=['GET', 'POST'])
def login():
   form = LoginForm()
   if form.validate_on_submit():
	   user = User.query.filter_by(email=form.email.data).first()
	   if user and check_password_hash(user.password, form.password.data):
		   login_user(user, remember=True)
		   next_page = request.args.get('next')
		   return redirect(next_page) if next_page else redirect(url_for('main.home'))
	   else:
		   flash('Login Unsuccessful. Please check email and password', 'danger')
   return render_template('login.html', form=form)

@auth.route('/logout')
@login_required
def logout():
   logout_user()
   return redirect(url_for('main.home'))
```

1. **`app/models.py`**:

```python
from flask_sqlalchemy import SQLAlchemy
from flask_login import UserMixin
from app import db

class User(db.Model, UserMixin):
   id = db.Column(db.Integer, primary_key=True)
   username = db.Column(db.String(80), unique=True, nullable=False)
   email = db.Column(db.String(120), unique=True, nullable=False)
   password = db.Column(db.String(60), nullable=False)

   def __repr__(self):
	   return f'<User {self.username}>'
```

9. **`app/forms.py`**:

```python
from flask_wtf import FlaskForm
from wtforms import StringField, PasswordField, SubmitField
from wtforms.validators import DataRequired, Email, Length

class RegistrationForm(FlaskForm):
   username = StringField('Username', validators=[DataRequired(), Length(min=2, max=20)])
   email = StringField('Email', validators=[DataRequired(), Email()])
   password = PasswordField('Password', validators=[DataRequired(), Length(min=6)])
   submit = SubmitField('Sign Up')

class LoginForm(FlaskForm):
   email = StringField('Email', validators=[DataRequired(), Email()])
   password = PasswordField('Password', validators=[DataRequired()])
   submit = SubmitField('Login')
```

### Summary

- **Organizing the Application Using Blueprints**:
  - Create Blueprints in separate modules.
  - Register Blueprints in the main application file.

- **Recommended Project Structure**:
  - Use a modular structure with directories for each Blueprint (e.g., `main`, `auth`).
  - Separate templates, static files, routes, forms, and models.

- **Example Setup**:
  - Create Blueprints and define routes.
  - Register Blueprints in the application factory function (`create_app`).
  - Organize the project structure with clear separation of concerns.

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
