## JSON-Server: How would you create the cheapest REST API in 5 minutes?

## Who are you?
- A Product owner, a Software engineer who is preparing for a demo or a POC (proof of concept), and all you want is to prove your idea with the minimum cost in terms of time and development effort.
- A Front-end developer or a mobile developer expecting to consume an API in order to continue your development process.
- A Backend developer in the middle of a design process or a brainstorming phase for the next REST API project.
- or maybe just a nerd playing around with new technologies and you need a REST API.

If you're one of the above, then here is the magic solution that would enable you to create a **FAKE API**, don't worry it's not totally Fake because it can handle all the CRUD operations that you'd require, along with filtering, sorting, routing and more.
feel free to explore their repo mentioned below.

The magic solution is called [JSON-Server](https://github.com/typicode/json-server).

> If you already know what is that, please feel free to skip reading.

## Pre-requisites
- [Node.js](https://nodejs.org/en/).
- Basic Knoweldge about JSON.
- Text-Editor (give [vscode](https://code.visualstudio.com/) a try)
- Command-line. (powershell or bash)

## Exploring The JSON-Server
As the creators have already mentioned 
> Get a full fake REST API with zero coding in less than 30 seconds

And they don't lie BTW, I tried it myself while playing around with React, and all I wanted is a Rest API to continue with my weekend project. so I'll push the discussion a bit forward by discussing the pros and cons.

### Pros
- Accelerate the development process, by temporarily breaking the dependency between your Backend team and consumers (whether it's a mobile application or a web application, ...)
- A perfect choice for a quick demo with a tiny timeframe or blueprinting a design for your new API.
- Easy to create, all you need is to describe how your API would look-like.
- Exponentially reduce the time and effort required for creating a fully-fledged REST API that you'd throw away within weeks.

### Cons
- Don't ever use it in a production environment. it has a certain use-case and scope with one mission to achieve (faking a REST API)
- It's not intended for scalability.

## How to Install & Create?
Assuming that you have the pre-requisites, open your command line and follow up (as mentioned by the creators).

1. Install `json-server` globally on your machine
```powershell
npm install -g json-server
```
2. Create a file (anywhere) and call it `db.json` just for a matter of convention.
```powershell
touch db.json
```
3. Describe your API, for example:
```
{
  "posts": [
    { "id": 1, "title": "json-server", "author": "typicode" }
  ],
  "comments": [
    { "id": 1, "body": "some comment", "postId": 1 }
  ],
  "profile": { "name": "typicode" }
}
```
4. Run your JSON server 
```
json-server --watch db.json
```

Note: the `db.json` file is your actual description of the API, you can always update it to change the schema.

### Manipulating your REST API
Once you are done with describing your REST API, you'll have the basic HTTP-Methods in hand, defined by the default route that you can try yourself with Postman for example:
```http
GET    /posts
GET    /posts/1
POST   /posts
PUT    /posts/1
PATCH  /posts/1
DELETE /posts/1
```

## Real-life Example
Speaking of a more complex example, here is a use case that I used to experiment with the utility.

My use-case was mainly about a home library tracker or library manager, whatever you'd call it.

### Entities
- **User** a user can create multiple libraries depending on his needs, it could also be an author on our system.
- **Library** a library can have multiple shelves
- **Shelf** a shelf would contain multiple books, along with tags.
- **tags** a tag is the keyword used to categorise books and later filter all shelves that are assigned a specific tag.
- **book** the core item that we want to track

### JSON Description for Entities
1. User Definition
```json
"users": [
    {
      "id": 1,
      "name": "mohamed halawa",
      "username": "thecodingcod",
      "biography": "A Stoic by mind, Software engineer the rest of the day",
      "imageUrl": "https://avatars.githubusercontent.com/u/27898642?v=4",
      "Created": "14-05-2022",
      "isAuthor": false
    },
    {
      "id": 1,
      "name": "Alain de botton",
      "username": "alaindebotton",
      "biography": "Alain de Botton is a writer and television producer who lives in London and aims to make philosophy relevant to everyday life.",
      "imageUrl": "https://images.gr-assets.com/authors/1189753902p5/13199.jpg",
      "Created": "14-05-2022",
      "isAuthor": true
    }
  ]
```
2. Library Definition
```json
"libraries": [
    {
      "id": 1,
      "name": "Home Library",
      "description": "Shelves at my home library"
    }
  ]
```
3. Shelf Definition
```json
"shelves": [
    {
      "id": 1,
      "name": "philosophy",
      "tags": [
        1
      ],
      "owner": 1
    }
  ]
```

4. Tags Definition
```json
"tags": [
    {
      "id": 1,
      "name": "philosophy",
      "createdBy": 1,
      "created": "14-05-2022"
    }
  ]
```
5. Books Definition
```json
"books": [
    {
      "id": 1,
      "title": "Consolation Of Philosophy",
      "subtitle": "How philosophy could help in life",
      "description": "Alain de Botton's The Consolations of Philosophy takes the discipline of logic and the mind back to its roots. Drawing inspiration from six of the finest minds in history - Socrates, Epicurus, Seneca, Montaigne, Schopenhauer and Nietzsche - he addresses lack of money, the pain of love, inadequacy, anxiety and conformity. De Botton's book led one critic to call philosophy 'the new rock and roll'",
      "isbn13": "9789776483545",
      "pages": 320,
      "released": "January, 2000",
      "language": "Arabic",
      "imageUrl": "https://i.gr-assets.com/images/S/compressed.photo.goodreads.com/books/1448130674l/27872336._SX318_.jpg",
      "created": "14-05-2022",
      "volumeId": -1,
      "authorId": 1,
      "shelfId": 1,
      "tags": [
        1
      ]
    }
]
```

Finally, you should combine all of the entities within a single JSON object, then you'd also run the JSON Server.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652729907306/5kk5QLIFl.png align="left")

## CRUD Operations
For this, I've used [postman](https://www.postman.com/), and for the sake of keeping this article short, I'll just show a sample of how you can add data to an existing collection/entity.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652729864174/A_LIYnpI3.png align="left")

And you'd notice that the collection has been successfully updated, as shown below. also if you checked the `db.json` you'll find that it has been updated as well.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1652729993818/iKxbRp_3A.png align="left")

