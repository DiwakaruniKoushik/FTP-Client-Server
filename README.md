# FTP Client and Server

This project implements a File Transfer Protocol (FTP) Client and Server with features adhering to the specifications in RFC 959. The project supports file transfer commands, authentication, logging, error handling, and more.

## Features

### 1. Support for `get` Command
The `get` command allows the client to download files from the server. It corresponds to the `RETR` command as defined in RFC 959.

### 2. Support for `put` Command
The `put` command enables the client to upload files to the server. It corresponds to the `STOR` command as defined in RFC 959.

### 3. Support for `list` Command
The `list` command provides a directory listing from the server. It corresponds to the `LIST` command as defined in RFC 959.

### 4. Error Handling Mechanism
Error handling is implemented using standardized status codes as defined in RFC 959. Examples include:
- **550**: File not found or access denied.
- **530**: Authentication failure.

### 5. Authentication
The client and server implement user authentication using the `USER` and `PASS` commands as specified in RFC 959.

### 6. Logging
Logging functionality is included to:
- Debug errors.
- Keep track of executed commands.

### 7. Rename
The `rename` functionality allows renaming files on the server. It corresponds to:
- `RNFR`: Rename from.
- `RNTO`: Rename to.

### 8. Support for `delete` Command
The `delete` command enables clients to delete a specified file on the server. Command syntax:
```plaintext
DELE <filename>
```

### 9. File Access Prevention
File access prevention ensures unauthorized users cannot access, modify, or delete files. The server enforces permissions and ownership checks, returning errors like **550 Permission denied**.

### 10. Data Transfer Types
FTP supports:
- **ASCII (TYPE A)** for text files.
- **Binary (TYPE I)** for non-text files.

Clients must set the transfer type before executing commands like `RETR` or `STOR`, ensuring proper file format handling during transfers.

## Requirements

### Client Requirements
- Ability to send commands (`get`, `put`, `list`, `rename`, `delete`, etc.) to the server.
- Receive responses and files from the server.

### Server Requirements
- Handle and respond to client commands as per FTP standards.
- Authenticate users and ensure secure access to files.
- Log activities for monitoring and debugging.
- Implement error handling and provide appropriate status codes.

## Usage

### Running the Server
To start the server, run the following command:
```bash
./ftp_server
```

### Running the Client
To start the client, run:
```bash
./ftp_client
```

### Example Commands
- Download a file:
  ```plaintext
  get <filename>
  ```
- Upload a file:
  ```plaintext
  put <filename>
  ```
- List directory contents:
  ```plaintext
  list
  ```
- Rename a file:
  ```plaintext
  rename <old_filename> <new_filename>
  ```
- Delete a file:
  ```plaintext
  delete <filename>
  ```

## Error Codes
- **550**: File not found or access denied.
- **530**: Authentication failure.

## References
- [RFC 959 - File Transfer Protocol (FTP)](https://www.rfc-editor.org/rfc/rfc959.html)
