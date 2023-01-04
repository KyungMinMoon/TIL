# app.py

from flask import Flask, request
import random
from utils import send_message
import requests

app = Flask('hi')  # 클래스 초기화

@app.route('/', methods=['POST'])  # @ = decorator
def home():
    # request 서버로서 내가 받은 요청 => server
    data = request.json
    input_message = data['message']['text']
    sender_id = (data['message']['from']['id'])


    if input_message == '안녕':
         send_message('안녕하세요', sender_id)
    elif input_message == '로또':
        lotto = random.sample(range(1, 46),6)
        send_message(lotto, sender_id)
    else:
        send_message('안녕 또는 로또 중에 하나를 골라 입력하세요', sender_id)

    return 'Hello Server!'



    send_message(message, sender_id)
    send_url = f'https://api.telegram.org/bot{token}/sendMessage?chat_id={chat_id}&text={out_message}'
    requests.get(url)
    return 'Hello Server!'

def send_message(msg, sender_id):
    token = '5333713413:AAEyYZkdGPps3H-LVAFLG4dbg3aZiwAfQ1I'
    url = f'https://api.telegram.org/bot{token}/sendMessage?chat_id={sender_id}&text={msg}'
    requests.get(url)


@app.route('/lotto')
def test():
    return OK




    ---
# utils

    import requests
import random

token = '5333713413:AAEyYZkdGPps3H-LVAFLG4dbg3aZiwAfQ1I'
me = '5581631026'

def send_message(msg, sender_id):
    token = '5333713413:AAEyYZkdGPps3H-LVAFLG4dbg3aZiwAfQ1I'
    url = f'https://api.telegram.org/bot{token}/sendMessage?chat_id={sender_id}&text={msg}'
    requests.get(url)


# send_message('안녕', '5581631026')


'https://api.telegram.org/bot5333713413:AAEyYZkdGPps3H-LVAFLG4dbg3aZiwAfQ1I/setWebhook?url=Kyungmin.pythonanywhere.com'