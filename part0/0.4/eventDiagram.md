```mermaid
sequenceDiagram
    participant Browser
    participant Server

    Note right of Browser: User inputs a new note and presses "Save"
        Browser-->Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
        activate Server
        Server->>Browser: STATUS: 302 Found
        Browser-->Server: GET: /exampleapp/notes
        Server->>Browser: HTML Document
        deactivate Server

    
