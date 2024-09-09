sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of server: Server processes the new note and stores it
    server-->>browser: 201 Created
    deactivate server

    Note right of browser: The browser receives confirmation and can update the UI accordingly.
