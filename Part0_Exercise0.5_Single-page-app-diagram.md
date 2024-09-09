sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    Note right of server: Server checks if the resource has changed
    server-->>browser: 304 Not Modified
    deactivate server

    Note right of browser: The browser uses the cached version of the resource
