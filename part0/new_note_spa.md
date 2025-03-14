```mermaid

sequenceDiagram
    participant browser
    participant server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the CSS file
    deactivate server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server
 Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{"content": "hmmm","date": "2025-03-14T16:22:53.249Z"},...]
    deactivate server

browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
Note left of server: The user adds a new note
    activate server
    server-->>browser: [{content: "hello", date: "2025-03-14T16:43:24.989Z"}]
    deactivate server
Note right of browser: The event handler rerenders the note list on the page with the new note
 
