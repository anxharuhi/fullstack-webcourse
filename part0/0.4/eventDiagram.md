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
    Server->>Browser: STATUS: 304 Not modified
    Note left of Server: STATUS 304 tells the browser that it has not been modified since last request of said resource.
    Note left of Server: Basically use the cache copy and don't download it again, saving bandwith and reducing load times.
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
