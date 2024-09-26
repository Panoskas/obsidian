https://dev.to/sherlockcodes/pytest-with-django-rest-framework-from-zero-to-hero-8c4
https://realpython.com/pytest-python-testing/#parametrization-combining-tests
# 1.  Imports
`import json
`import pytest
`from model_bakery import baker
`from stats.models import Message
`pytestmark = pytest.mark.django_db

## 2. Create a test class and add a function for each CRUD action

`class TestMessageEndpoint:
	`endpoint = /api/messages

- get all messages
```
def test_list(self, admin_client):
	baker.make(Message)
	response = admin_client.get(self.endpoint)
	assert response.status_code == 200
	assert len(json.loads(response.content)) == 3
	assert "links" in json.loads(response.content)
	assert "meta" in json.loads(response.content)
```

- get a message by id
```

def test_retrtieve(self, admin_client):
	message = baker.make(Message)
	patch_payload = {
		"data": {"type": "message", "id": message.id}
	}
	url = f'{self.endpoint}/{message.id}'
	response = admin_client.get(url, patch_payload=patch_payload)
	assert response.status_code == 200`
```

- delete a message
```

def test_delete(self, admin_client):
	Message = baker.make(Message)
	url = f'{self.endpoint}/{message.id}'
	response = admin_client.delete(url)
	assert response.status_code == 204
```

- modify a message
```	
def test_update(self, api_admin_client):
	old_meter = baker.make(Meter)
	new_meter = baker.make(Meter)
	currency_dict = {
		'name': new_meter.name,
	}
	url = f'{self.endpoint}/{old_meter.id}
	response = api_admin_client.put(url, currency_dict)
	assert response.status_code == 200
	assert json.loads(response.content) == currency_dict
```