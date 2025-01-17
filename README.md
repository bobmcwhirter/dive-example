# Dive 

A hacky example rust application that finds java processes running in containers,
dives into them and analyzes their jar files

# Steps
1. Install Rust

   ```
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   ```

2. Install musl-gcc and gmake
    ```
    sudo dnf install -y musl-gcc make
    ```

3. Install x86_64-unknown-linux-musl target
    ```
    rustup target install x86_64-unknown-linux-musl
    ```

4. Build
    ```
    $ make
    cargo build --release --target x86_64-unknown-linux-musl
    Finished release [optimized] target(s) in 9.25s
    ```

5. Run some containers
    ```
    podman run -d --rm docker.io/library/tomcat:9.0
    podman run -d --rm docker.io/library/jetty
    ```

6. Run (Warning becomes root)
    ```
    $ make run
    ```