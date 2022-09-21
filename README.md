<p align="center">
    <picture>
        <source media="(prefers-color-scheme: dark)" srcset="https://www.arsal.xyz/CHQAssets/CHQLogo.png">
        <img alt="White CHQ logo in dark mode and dark CHQ logo in light mode" src="https://www.arsal.xyz/CHQAssets/CHQLogoYellow.png" width=500px>
    </picture>
    <h1 align="center">CodersHQ Backend</h1>
</p>

<p align="center">
 <a href="LICENSE.md" target="_blank"><img width="80" src="https://img.shields.io/badge/License-MIT-red.svg"></a>
 <a href="https://discord.gg/X3vZZxK3KQ" target="_blank"><img width="80" src="https://img.shields.io/badge/Discord-%237289DA.svg?style=for-the-badge&logo=discord&logoColor=white"></a>
</p>

<h2>📝Table of Contents</h2>

<ol>
    <a href='#intro'><li>Introduction</li>
    <a href='#parts'><li>Project Parts</li>
    <ol>
        <a href='#backend'><li>Backend</li></a>
        <a href='#schemas'><li>Schemas</li></a>
        <a href='#db'><li>Database (including database models)</li></a>
        <a href='#api'><li>API Gateway</li></a>
    </ol>
</ol>

<h2 id='intro'>💻Introduction</h2>

A backend is the server-side of a website/system. It is responsible for storing and arranging data for the frontend to display. It is the part of the system that cannot be seen or interacted directly by the end users. The functions that are developed by the backend developers are accessed indirectly by the users through the frontend application. The common activities that come under backend are creating libraries, handling logic of the system, writing APIs and database management.

<h2 id='parts'>⚙️Project Parts</h2>

This project will be split into 4 different parts:

<ul>
    <a href='#backend'><li>Backend</li></a>
    <a href='#schemas'><li>Schemas</li></a>
    <a href='#db'><li>Database</li></a>
    <a href='#api'><li>API Gateway</li></a>
</ul>

These 4 parts are crucial for the working of a proper backend. The team must ensure that these 4 parts are able to communicate between each other flawlessly and in clutter-less manner.

<h2 id='backend'>🧑‍💻Backend</h2>

The CHQ Backend will be responsible for connecting the users to the database. Also they will be responsible for the authentication between the frontend and the API. It is responsible for the creation of schemas that will be used by the database. It is only right to see the backend as a central nervous system.


<h2 id='schemas'>📖Schemas</h2>
Schemas are <em>like</em> the blueprint of the database tables. The data taken from the user (frontend) and database will be validated against this schema which will ensure clean data to pass through.

<h3>What are some of the schemas that will be fed onto the database?</h3>

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

This should give an idea on how the schemas are expected to be*. In reality the schemas will be split into an abstract base classes, a class with the data related to action and a main class. For example, if the user is being made, there will be a `UserCreate` schema, and when the user data is being shown, the `User` schema will be used, both of which will inherit from the [ABC](https://www.educative.io/answers/what-is-the-abstract-base-class-in-python) `UserBase` which will have the information not present in both the other classes.


<h2 id='db'>📙Database</h2>

For the database connectivity, we will be using an ORM library (possibly [`SQLAlchemy`](https://www.sqlalchemy.org/)) with the postgres driver to connect onto our [PostgreSQL](https://www.postgresql.org/) database, which will store and provide the data related to the schemas we define. We create models that are similar to the schemas to store data in the database. The data we fetch from the database will be validated against the schema that we define and will be fed onto the frontend.


<h2 id='api'>🔗API Gateway</h2>

The CHQ Backend will also be responsible for creating and designing the API gateway that will be a center point of communication between the CHQ Interfaces([CLI](https://github.com/Coders-HQ/CLI) and [Admin](https://github.com/Coders-HQ/Admin)) and the [CHQ Bounty](https://github.com/Coders-HQ/Bounty). It is preferred to make a [REST API](https://restfulapi.net/) following all the REST principles. This API must also be flexible, meaning that it must be easy to add or remove code/modules. It must be inter-compatible since it will be used by 3 different systems with, possibly, an entirely different people.
        
<h6>*These are the initial schemas. As the projects grows we may need to add more and tune a few things. For now we can start here and improve with time.</h6>
