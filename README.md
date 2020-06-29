# django-snippets-app
## Environment:
- Python version: 3.7
- Django version: 3.0.7
- Django REST framework version: 3.11.0

## Read-Only Files:
- manage.py

## Data:
Example of a weather data JSON object:
```
{
   "id": 1,
   "title": "Test Snippet",
   "code": "Test 1 code",
   "linenos": "",
   "language": "Python",
   "style": ""
}
```

## Requirements:
The REST service must expose the /snippets/ endpoint, which allows for managing the collection of snippet records in the following way:


POST request to `/snippets/`:
- creates a new weather data record
- expects a valid weather data object as its body payload, except that it does not have an id property; you can assume that the given object is always valid
- adds the given object to the collection and assigns a unique integer id to it
- the response code is 201 and the response body is the created record, including its unique id

GET request to `/snippets/`:
- the response code is 200
- the response body is an array of matching records, ordered by their ids in increasing order

GET request to `/snippets/<id>/`:
- returns a record with the given id
- if the matching record exists, the response code is 200 and the response body is the matching object
- if there is no record in the collection with the given id, the response code is 404

DELETE request to `/snippets/<id>/`:
- deletes the record with the given id from the collection
- if matching record existed, the response code is 204
- if there was no record in the collection with the given id, the response code is 404

