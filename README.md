# Client-Server File Retrieval System

## Overview
In this client-server project, a client can request a file or a set of files from the server. The server searches for the file/s in its file directory rooted at its ~ and returns the file/files requested to the client (or an appropriate message otherwise). Multiple clients can connect to the serverw from different machines and can request file/s as per the commands listed in section 2.

## Components
- **Server (serverw24):** Listens for client requests and processes them.
- **Mirror Servers (mirror1, mirror2):** Additional servers to handle client requests in a distributed manner.
- **Client (clientw24):** Sends commands to the server to request files.

## Running the Project
1. **Server Setup:** Run the `serverw24` and two mirror servers (`mirror1`, `mirror2`) on separate machines/terminals.
2. **Client Connection:** Clients (`clientw24`) can connect to any of the servers to request files.
3. **Command Syntax:** Clients can use various commands to request files, such as `dirlist`, `w24fn`, `w24fz`, `w24ft`, `w24fdb`, `w24fda`, and `quitc`.

## Client Commands
- `dirlist -a`: Returns a list of subdirectories/folders.
- `dirlist -t`: Returns a list of subdirectories/folders in the order of creation.
- `w24fn filename`: Returns file information (size, date created, permissions) for a specific filename.
- `w24fz size1 size2`: Returns a compressed file containing files within a specified size range.
- `w24ft <extension list>`: Returns a compressed file containing files with specified extensions.
- `w24fdb date`: Returns files created before a specified date.
- `w24fda date`: Returns files created after a specified date.
- `quitc`: Terminates the client process.

## Alternating Server Usage
- First 3 connections are handled by `serverw24`.
- Next 3 connections (4-6) are handled by `mirror1`.
- Next 3 connections (7-9) are handled by `mirror2`.
- Remaining connections are alternated between `serverw24`, `mirror1`, and `mirror2`.

## File Storage
- Files returned by the server are stored in a folder named `w24project` in the client's home directory.
