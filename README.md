# docker file content

FROM UBUNTU
sudo docker run -it ubuntu bash
apt-get update
apt-get install -y python3 python3-pip
pip install flask
#create and copy app source code to /opt/app.py
ENTRYPOINT FLASK_APP=app.py flask run --host=0.0.0.0

-----------------------------------------------------------------

Source Code below
import os
from flask import Flask
app = Flask(__name__)

@app.route("/")
def main():
    return "Welcome!"

@app.route('/how are you')
def hello():
    return 'I am good, how about you?'

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=8080)
