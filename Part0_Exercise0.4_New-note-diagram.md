sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes request
    activate server
    server-->>browser: HTML document (server responds with HTTP status code 302 Found)
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css 
    activate server
    server-->>browser: main.css (fetching the style sheet)
    (server responds with HTTP status code 304 Not Modified)
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: main.js (the JavaScript code) 
    (server responds with HTTP status code 304 Not Modified)
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [...,
  {
    "content": "moi moi",
    "date": "2024-08-18T12:31:50.737Z"
  },... ]

    (server responds with HTTP status code 200 OK)
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes