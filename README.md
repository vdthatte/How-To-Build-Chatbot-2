# How To Build Chatbot - Part 2

Part two of How To Build a Chatbot on Facebook

Install Wit Ai using this [Link](https://github.com/wit-ai/pywit)

```python
from wit import Wit
```


```python

def send(request, response):
    print('Sending to user...', response['text'])
def my_action(request):
    print('Received from user...', request['text'])

actions = {
    'send': send,
    'my_action': my_action,
}



client = Wit(access_token="YOUR_CLIENT_ACCESS_TOKEN", actions=actions)

```

```python
def wit_bit(message_text, sender_id):
	resp = client.message(message_text)

	if(resp["entities"] != {}):
		if(resp["entities"]["intent"][0]["value"] == "greetings"):
			print("Hey! How can I help you?")
			send_message(sender_id, "Hey! How can I help you?")

		else:
			print("I'm to dumb to understand complex sentences.")
			send_message(sender_id, "I'm dumb sometimes. Maybe start by saying Hello?")
	else:
		print("I'm to dumb to understand complex sentences.")
		send_message(sender_id, "I'm dumb sometimes. Maybe start by saying Hello?")
```

