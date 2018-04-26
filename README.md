## Load the environment

     source flask_env/bin/activate

## Load the application in the Python shell

    FLASK_APP=flask_tutorial.py flask shell
    from flask import current_app
    from app import create_app
    app = create_app()
    app.app_context().push()
    current_app.config['SQLALCHEMY_DATABASE_URI']
