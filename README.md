# Student Management System APIs

A simple Flask REST API for managing student records stored in MongoDB. The project is provided as a Jupyter Notebook and demonstrates create, read, update, and delete operations.

## Features

- Create a student/user record
- Find a record by its custom `id`
- Update an existing record
- Delete a record
- JSON responses with appropriate HTTP status codes

## Technologies

- Python 3
- Flask
- PyMongo
- MongoDB
- Jupyter Notebook

## Project structure

```text
Students_Management_System_APIs_MongoDB.ipynb
README.md
requirements.txt
```

## Setup

1. Install Python 3 and MongoDB Atlas (or a local MongoDB server).
2. Clone this repository:

   ```bash
   git clone https://github.com/Saqib17Ishfaq/Student_Management_System_APIs_MongoDB.git
   cd Student_Management_System_APIs_MongoDB
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Open `Students_Management_System_APIs_MongoDB.ipynb` in Jupyter Notebook or JupyterLab.
5. Set your MongoDB URI in the `MONGODB_URI` environment variable before running the connection cell. Do not commit credentials or secrets to GitHub. Create the `Student_Management_System` database and `Students_Data` collection, or let MongoDB create them on the first insert.
6. Run the notebook cells in order and start the Flask server from the final cell.

The API runs at `http://127.0.0.1:5000` by default.

## API reference

### Create a student

`POST /create-user`

Example request:

```json
{
  "id": "STU-001",
  "name": "Ali Khan",
  "age": 20,
  "department": "Computer Science"
}
```

Example response (`201 Created`):

```json
{
  "message": "User created successfully",
  "inserted_id": "..."
}
```

### Get a student

`GET /get-user?id=STU-001`

Returns the matching document with its MongoDB `_id` converted to a string.

### Update a student

`PUT /update-user`

Send a JSON body containing the existing `id` and the fields to update:

```json
{
  "id": "STU-001",
  "department": "Data Science"
}
```

### Delete a student

`DELETE /delete-user?id=STU-001`

Returns `404 Not Found` when no record matches the supplied ID.

## Error responses

- `400 Bad Request` when the required `id` is missing
- `404 Not Found` when a student record does not exist
- `201 Created` after a successful insert
- `200 OK` after a successful read or update
- `204 No Content` after a successful delete

## Notes

- The notebook currently uses Flask's development server and `debug=True`; use a production WSGI server for deployment.
- The custom `id` field should be unique for reliable student lookups.
- Keep MongoDB credentials in environment variables or another secret manager rather than in source code.
- Windows PowerShell example: `$env:MONGODB_URI = "mongodb+srv://<username>:<password>@<cluster>/?retryWrites=true&w=majority"`

## License

This project is available for learning and educational use.
