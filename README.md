<p align="center">
 <img width="500" src="https://user-images.githubusercontent.com/92259277/190894050-ba6b293d-c3b0-4679-86aa-61622a4dafde.png">
 <h1 align="center">CodersHQ Backend</h1>
</p>

<h2>:memo: Table Of Contents</h2>
<ol>
  <li>Introduction</li>
  <li>Project Parts</li>
  <ol>
    <li>Backend</li>
    <li>Database</li>
    <li>API Gateway</li>
  </ol>
</ol>

<h2>💻Introduction</h2>
A backend is the server-side of a website/system. It is responsible for storing and arranging data for the frontend to display. It is the part of the system that cannot be seen or interacted directly by the end users. The functions that are developed by the backend developers are accessed indirectly by the users through the frontend application. The common activities that come under backend are creating libraries, handling logic of the system, writing APIs. 

<h2>⚙️Project Parts</h2>
This project will be split into 3 different parts:
<ul>
    <li>Schemas</li>
    <li>Database</li>
    <li>API Gateway</li>
</ul>

These 3 parts are crucial for the working of a proper backend. The team must ensure that these 3 parts are able to communicate between each other flawlessly and in cluterless manner.

<h3>👨‍💻Schemas</h3>
The CHQ Backend will be responsible for connecting the users to the database. Also they will be responsible for the authentication between the frontend and the API. It is responsible for the creation of schemas that will be used by the database. It is only right to see the backend as a central nervous system.

<h4>What are some of the schemas that will be fed onto the database models?</h4>

```python
from pydantic import BaseModel

class User(BaseModel):
    username: str
    password: str
    bio: str
    date_of_birth: str
    age: int
    profession: str
    ...

class Company(BaseModel):
    name: str
    field: str
    website: str
    ...

class Bounties(BaseModel):
    company: Company
    challenge: str
    bounty: str
    deadline_day: int
    priority: str
    ...

class Event(BaseModel):
    title: str
    image: str
    date_time: str
    duration: int
    short_description: str
    event_location: str
    ...
```
This should give an idea on how the schemas are expected to be. In reality the schemas will be be split into an abstract base classes, a class with the data related to action and a main class. For example, if the user is being made, there will be a `UserCreate` schema, and when the user data is being shown, the `User` schema will be used, both of which will inherit from the [ABC](https://www.educative.io/answers/what-is-the-abstract-base-class-in-python) `UserBase` which will have the information not present in both the other classes.

<h2>📙Database</h2>
For the database, we will be using an ORM library (possibly <a href="https://www.sqlalchemy.org/"><code>SQLAlchemy</code></a>) with the postgres driver to connect onto our <a href="https://www.postgresql.org/">PostgreSQL</a> mdatabase, which will store and provide the data related to the schemas we define. 

<h2>🔗API Gateway</h2>
The CHQ Backend will also be responsible for creating and designing the API gateway that will be a center point of communication between the CHQ Interfaces(<a href="https://github.com/Coders-HQ/CLI">CLI</a> and <a href="https://github.com/Coders-HQ/Admin">Admin</a>) and the <a href="https://github.com/Coders-HQ/Bounty">CHQ Bounty</a>. It is preferred to make a <a href"https://restfulapi.net/">REST API</a> following all the REST principles. This API must also be flexible, meaning that it must be easy to add or remove code/modules. It must also be user friendly since it will be used by 3 different system with, possibly, an entirely different people.
