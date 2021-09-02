# ShareIt! - Shared Editor

###### This repository contains the university project carried out for the _System and Device Programming_ course at the _Politecnico of Turin_.
-------------------------


<details open="open">
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#about-shareit">About ShareIt!</a></li>
    <li><a href="#requirements">Requirements</a></li>
    <li><a href="#features">Features</a></li>
    <li><a href="#the-team">The Team</a></li>
  </ol>
</details>
 
  
## About ShareIt!

The availability of broadband connections and the need to work in a team without
necessarily requiring the co-presence of the actors in the same physical space pushes towards
the creation of increasingly effective support systems for cooperative work. Eg,
Google provides the Docs suite, through which it is possible to edit, so
cooperative and distributed, documents of various kinds and in
able to scale even large numbers of contemporary users: this solution is based on
a set of centralized servers that manage traffic to and from individual clients and put
the logic necessary to guarantee the correctness of the concurrent operations is in place.

_ShareIt! _ Is a cooperative text editing system that allows one or more users to edit the content of a document at the same time, ensuring that different insertion or modification operations, performed by users at the same time, produce the same effects, regardless of the 'order in which they are performed on the different systems in use (** commutativity **) and that repeated cancellations lead to the same result (** idempotence **).
  
## Requirements

1. The system consists of **two independent modules**, the client and the server.

2. The **server** consists of a constantly active process, capable of accepting,
through the network, connections from clients. The server, on the inside, keeps
a set of documents that can be edited collaboratively by clients.
These documents are stored on the server's file system, so as not to lose their
content in case of accidental interruption of the process. Rescue operations
they are performed automatically and do not require any explicit request from the part
of clients.

3. The **clients** are discontinuous processes (they can be started and ended in
independent, according to the will of the user), performed within computers
networked with the server. The clients offer a graphical interface through which
a user can ask the server to edit one of the active documents or ask to
create a new one, assign it a unique name. When the required document comes
open, the client offers a typical editor interface that allows you to edit the
document. If two or more clients edit the document at the same time, the
server ensures that the operations performed generate, in each client, a
consistent representation. Individual clients show the number and identity of users
that are editing the current document and highlight the cursor position
of the different users within the document. The client can highlight the entered text
by different users using different colors.

4. When starting a client, the user must **authenticate** to the
server using appropriate credentials (username, password). For each user, the
server maintains a profile (nickname, icon, ...) that can be changed by the user
through your client.


## Features
  
- **Export to PDF**:
The client can produce a PDF version of the current document and save it in its own file
system.

- **Cut|Copy|Paste keyboard shortcuts**:
The editor provides cut-copy-paste operations which are made available both via keyboard shortcuts and
graphical interface.

- **Invito a collaborare**:
A client can send _out-of-band_ (E.g., e-mail,
chat), a unique URI of a document. By copying and pasting that URI into their own
client, the recipients of the invitation link can access and edit the document.


## The Team

- [@AbakusW](github.com/AbakusW): client/server side [CRDT](https://en.wikipedia.org/wiki/Conflict-free_replicated_data_type) algorithm implementation
- [@cleidetomaselli](github.com/cleidetomaselli): UI, db
- [@EnnioRiccobene](github.com/EnnioRiccobene): application protocol
- [@gmberton](github.com/gmberton): client/server logic

