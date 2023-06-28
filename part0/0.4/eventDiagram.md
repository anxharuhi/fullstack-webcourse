```mermaid
sequenceDiagram
    participant Browser
    participant Server

    Note right of Browser: User inputs a new note and presses "Save"
    Browser-->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate Server
    Server->>Browser: STATUS: 302 Found
    Note left of Server: STATUS 302 tells the browser that it is trying to access to a resource that has been moved.
    Note left of Server: Commonly used to redirect the browser to a specific URL.
    Browser-->>Server: GET: /exampleapp/notes
    Server->>Browser: HTML Document
    deactivate Server

    Browser-->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Server
    Server->>Browser: STATUS: 304 Not Modified
    deactivate Server

    Browser-->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate Server
    Server->>Browser: STATUS: 304 Not Modified
    deactivate Server

    Browser-->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server->>Browser: STATUS: 200 OK
    deactivate Server
