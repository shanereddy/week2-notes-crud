# Notes CRUD API
## Description
This is a CRUD(Create/Read/Update/Delete) API for managing notes which uses a database as a backend. We use FastAPI for the API and Sqlite for the database.

On app startup, a new database file is created with no records.

## Get Started
### Create virtual environment
`python3 -m venv .venv`

### Install Packages
`python3 -m pip install -r requirements.txt`

### Run the API
`uvicorn main:app --reload`

## Testing endpoints
You can use Postman to test the endpoints

### Test the API is running
```
Method: GET
URL: http://127.0.0.1:8000/
```
Expected Response:
```
Status Code: 200
```

### Get all notes
```
Method: GET
URL: http://127.0.0.1:8000/notes
```
Expected Response:
```
Status Code: 200
Body: All notes
```

### Create a note
```
Method: POST
URL: http://127.0.0.1:8000/notes
Body:
{
  "title": "Postman note",
  "text": "I created this note using Postman."
}
```
Expected Response:
```
Status Code: 201
Body: Your new note
```

### Read the note you just created
Replace `[id]` with the id of the note you created.

```
Method: GET
URL: http://127.0.0.1:8000/notes/[id]
```
Expected Response:
```
Status Code: 200
Body: The single note with the id you specified
```

### Update the note you just created
```
Method: PATCH
URL: http://127.0.0.1:8000/notes/[id]
Body:
{
  "title": "I updated this note title only!"
}
```

Expected Response:
```
Status Code: 200
Body: Your existing note with updated title
```

### Delete the note
Replace `[id]` with the id of the note you created.

```
Method: DELETE
URL: http://127.0.0.1:8000/notes/[id]
```
Expected Response:
```
Status Code: 200
Body:
{
    "message": "Note deleted"
}
```

### Read a note that doesn't exist
```
Method: GET
URL: http://127.0.0.1:8000/notes/999
```
Expected Response:
```
Status Code: 404
Body:
{
    "detail": "Note not found"
}
```