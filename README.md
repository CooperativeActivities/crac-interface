# REST API

## Endpunkte

### Login

**Request**

    POST /login

    {
      email: <string>,
      password: <string>,
    }

### Neuigkeiten

**Request**

    GET /newsfeed

**Response**

    [
      <object: task>
    ]

### Aufgabe

**Request**

    GET /task/:id

**Response**

    <object: task>

### Meine Aufgaben - Zugesagt

**Request**

    GET /tasks/joined

**Response**

  [
    <object: tasks>
  ]

### Meine Aufgaben - Gefolgt

**Request**

    GET /tasks/following

**Response**

  [
    <object: tasks>
  ]

### Aufgabe zusagen

**Request**

    PUT /tasks/:id/join

### Aufgabe absagen

**Request**

    DELETE /tasks/:id/join

### Aufgabe folgen

**Request**

    PUT /tasks/:id/follow

### Aufgabe nicht mehr folgen

**Request**

    DELETE /tasks/:id/follow

### Aufgabe kommentieren

**Request**

    POST /task/:id/comment

    {
      body: <string>,
      image: <image: base64>,
    }

### Aufgabe Kommentar löschen

    DELETE /task/:taskid/comment/:commentid

### Suche

**Request**

    GET /search?q=<searchterm>

**Response**

Array of Tasks-Proxy

    [
      {
        id: <id>,
        title: <string>,
        projectName: <string>,
        foundKeywords: [
          <string>
        ]
      }
    ]

## Projekt

**Request**

    GET /project/:id

## Organisation

**Request**

    GET /organisation/:id

### Bilder

**Requests**

    GET /image/project/:id
    GET /image/task/:id
    GET /image/comment/:id

## Daten

### Task

    {
      project: {
        id: <id>,
        name: <string>,
      },
      title: <string>,
      description: <string>,
      participants: {
        required: <int>,
        joined: [
          <object: user-proxy>
        ],
      },
      date: <string: iso date>,
      location: {
        name: <string>,
        lat: <float>,
        lng: <float>,
      },
      comments: [
        {
          id: <id>,
          body: <string>,
          bodyImage: <url>,
          user: <object: user-proxy>,
        }
      ],
      currentUser: {
        joined: <bool>,
        following: <bool>,
      },
    }

### Project

    {
      id: <id>,
      name: <string>,
      tasks: [
        <object:task>
      ],
      date: <string: iso date>,
      location: {
        name: <string>,
        lat: <float>,
        lng: <float>,
      }
    }

### Organisation

    {
      id: <id>,
      name: <string>,
      project: [
        {
          id: <id>,
          name: <string>,
        }
      ],
      location: {
        name: <string>,
        lat: <float>,
        lng: <float>,
      },
      contact: {
        phone: <string>,
        email: <string>,
      }
    }

### User Proxy

    {
      id: <id>,
      fistname: <string>,
      lastname: <string>,
    }
    
# License

       Copyright 2017 CrAc syndicate (http://www.crac.at/project-facts/partners)

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.

