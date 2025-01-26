# proyecto-final
Proyecto final de programacion avanzada
Quadra/
├── app/
│   ├── __init__.py
│   ├── routes.py
│   ├── models.py
├── venv/
├── requirements.txt
├── README.md
├── .gitignore

Flask==2.0.1
SQLAlchemy==1.4.22
python -m venv venv
venv\Scripts\activate
source venv/bin/activate
pip install Flask SQLAlchemy
Flask==2.0.1
SQLAlchemy==1.4.22
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///quadra.db'
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False
db = SQLAlchemy(app)

from app import routes
from app import db

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(80), unique=True, nullable=False)
    email = db.Column(db.String(120), unique=True, nullable=False)
    password = db.Column(db.String(120), nullable=False)

    def __repr__(self):
        return f'<User {self.username}>'

class FoodStall(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(100), nullable=False)
    location = db.Column(db.String(200), nullable=False)
    description = db.Column(db.Text, nullable=False)
    image = db.Column(db.String(300), nullable=True)

    def __repr__(self):
        return f'<FoodStall {self.name}>'
        from app import app

@app.route('/')
def home():
    return "Welcome to Quadra!"

@app.route('/login')
def login():
    return "Login Page"

@app.route('/register')
def register():
    return "Register Page"
from app import app

if __name__ == '__main__':
    app.run(debug=True)
python run.py

