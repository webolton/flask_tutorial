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



