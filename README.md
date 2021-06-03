
import React from "react";
import "./styles.css";

export default function App() {
  const [todos, setTodos] = React.useState([]);
import random
random.randint(1,1000)
print("random")

  return (
    <div className="App">
      <h1>random.py</h1>
      {todos.length ?
        <div>
          {todos.map((todo, index) => <p key={index}>{todo}</p>)}
        </div>
      :
        <p>random.</p>
      }
    </div>
  );
}

import os
import uuid
from dotenv import load_dotenv
from flask import Flask
from flask_cors import CORS
from twilio.jwt.access_token import AccessToken
from twilio.jwt.access_token.grants import SyncGrant

load_dotenv()
app = Flask(__name__)
CORS(app)


@app.route('/token', methods=['POST'])

def token():
    token = AccessToken(os.environ['TWILIO_ACCOUNT_SID'],
                        os.environ['TWILIO_API_KEY_SID'],
                        os.environ['TWILIO_API_KEY_SECRET'],
                        grants=[SyncGrant(os.environ['TWILIO_SYNC_SERVICE_SID'])],
                        identity=uuid.uuid4().hex)
    return {'token': token.to_jwt().decode()}
