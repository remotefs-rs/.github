# About remotefs ☁️

remotefs is a library that provides a file system structure to work with all the most popular file transfer protocols.
This is achieved through a trait called `RemoteFs` which exposes methods to operate on the remote file system.
Currently the library exposes a client for **Sftp**, **Scp**, **Ftp**, **WebDav**, **Kube** and **Aws-s3** as external libraries.

## Remote file system 💾

As mentioned earlier, this library exposes a trait called `RemoteFs`.
This trait exposes several methods to operate on a remote file system via the chosen client.

Let's briefly go over which methods are available:

- **connect**: connect to the remote host.
- **disconnect**: disconnect from the remote host.
- **is_connected**: returns whether the client is connected to the remote host.
- **append_file**: append specified buffer to the specified file.
- **append**: open a file for append and returns a stream to write to it.
- **change_dir**: change the working directory to provided path.
- **copy**: copy a file from the specified source path to the specified destination.
- **create_dir**: create a directory with the specified file mode at the specified path.
- **create_file**: create a file at a specified path with the specified content.
- **create**: create a file and returns a stream to write to it.
- **exec**: executes a shell command.
- **exists**: checks whether file at specified path exists.
- **list_dir**: get entries at the provided path.
- **mov**: move a file from the specified source path to the specified destination.
- **open_file**: open a file for reading and fill the specified buffer with the file content.
- **open**: open a file and returns a stream to read it.
- **pwd**: get working directory.
- **remove_dir_all**: remove file/directory and all of its content.
- **remove_dir**: remove directory at the specified path. It fails if it is not an empty directory.
- **remove_file**: remove file at the specified path. It fails if it is not a file.
- **setstat**: set file metadata for file at the specified path.
- **stat**: get file information of file at the specified path.
- **symlink**: create a symlink at the specified path, pointing to the specified file.
