This is all based on this blog
https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world

## Setting Up the Virtual Env
In the project directory, I ran

    virtualenv flask_env

To activate the environment, I ran

    source flask_env/bin/activate

I have added the `flask_env` folder to `.gitignore`. Need to do more research about this.

## Setting up the app
In the project directory

    mkdir app
    cd app && touch __init__.py

## Running the app
After setting up the app, I ran it with

    export FLASK_APP=flask_tutorial.py && flask run  
    # Probably should put these sorts of utility commands into a Makfile

## Loading the app into the python interpreter
In order to check that the secret_key is loaded, you can load the app into the Python environment

    from flask_tutorial import app
    app.config['SECRET_KEY']

## Templates (probably a simple solution for returning json)
Noteworthy:

- The out-of-the box template interpreter uses `{% some_pyton %}` to embed Python logic and `{{ some_variable }}` for displaying text.

## The routes file
It appears that the decorators in the routes file must immediately proceed the actual route handler.

## Models
In the user model, there is a method called `__rpr__` which appears to be a built-in Python that tells the program how to print information about the class.

In the current project, I can print this information in the Python interpreter with:

    from flask_tutorial import app # Load the app into the interpreter
    from app.models import User # Load the model into the intpreter
    u = User(username='susan', email='susan@example.com') # Instantiate a user
    u # Call the user which will be printed with the formatting designated in `__rpr__`

## Running migrations
Flask has a database schema managment plugin. It appears that these sorts of utility commands don't know about the environment or the application context right out of the box, so you have to specifiy the application before trying to run the command. So, for example:

    FLASK_APP=flask_tutorial.py flask db migrate # This appears to be for all of the calls to the `flask` utility.

For running a single migration, it looks like it has to go in two steps. First, the migration files are written, a flask command to apply the migration is run, and then the migration is run on the database. Therefore, after I wrote the "Posts" model, I ran:

    FLASK_APP=flask_tutorial.py flask db migrate -m "posts table"

and then

    FLASK_APP=flask_tutorial.py flask db migrate

## Creating an interactive shell
As discussed above, you can load the application into the Python interpreter in order to test out the app. You can also implement an interactive shell that will import the app and the models for you that behaves something like a Rails console. This is done in the application file. The command to run it is

    FLASK_APP=flask_tutorial.py flask shell
