# About remotefs ☁️

remotefs is a library that provides a file system structure to work with all the most popular file transfer protocols.
This is achieved through a trait called `RemoteFs` (and its async counterpart `AsyncRemoteFs`, behind the `async` feature) which exposes methods to operate on a remote file system using **absolute paths only**: there is no working-directory concept, every call addresses a path on the remote host directly.
Currently the library exposes a client for **Ssh** (Sftp/Scp), **Ftp**, **WebDav**, **Kube**, **Aws-s3**, **Smb**, **Gcs** and an in-**memory** backend for testing, each as an external crate, plus an [omni](https://github.com/remotefs-rs/remotefs-rs-omni) crate that wraps every implementation behind a single client and a [FUSE/Dokany driver](https://github.com/remotefs-rs/remotefs-rs-fuse) to mount a remote file system on your OS.

## Remote file system 💾

As mentioned earlier, this library exposes a trait called `RemoteFs`.
This trait exposes several methods to operate on a remote file system via the chosen client.

Let's briefly go over which methods are available:

- **connect**: connect to the remote host.
- **disconnect**: disconnect from the remote host.
- **is_connected**: returns whether the client is connected to the remote host.
- **capabilities**: returns which optional operations the client supports.
- **list_dir**: get entries at the provided path.
- **stat**: get file information of file at the specified path.
- **exists**: checks whether file at specified path exists.
- **set_metadata**: set file metadata for file at the specified path.
- **create_dir**: create a directory, with an optional file mode, at the specified path.
- **remove_file**: remove file at the specified path. It fails if it is not a file.
- **remove_dir**: remove directory at the specified path. It fails if it is not an empty directory.
- **remove_dir_all**: remove file/directory and all of its content, recursively.
- **rename**: rename/move a file from the specified source path to the specified destination.
- **copy**: copy a file from the specified source path to the specified destination.
- **symlink**: create a symlink at the specified path, pointing to the specified file.
- **open**: open a file for reading, with the given `ReadOptions`, and return a stream to read it.
- **create**: create a file for writing, with the given `WriteOptions`, and return a stream to write to it.
- **append**: open a file for append, with the given `WriteOptions`, and return a stream to write to it.
- **read_file**: open a file for reading and fill the specified buffer with the file content.
- **write_file**: create a file at a specified path with the specified content.
- **append_file**: append specified buffer to the specified file.
- **exec**: executes a shell command, returning its `ExecOutput`.
