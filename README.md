# Fastdeb
## Description
`fastdeb` CLI tool is intended for fast creation of `.deb` packages for Ubuntu and 
other Debian-based operating systems. 
## Installation
First, download fastdeb `.deb` package from [Releases](https://github.com/osintegrator/fastdeb/releases) page.
Then you can install `fastdeb` with this command:
```bash
sudo apt install -y /path/to/fastdeb_<version>.deb
``` 
## Usage
There are 5 mandatory parameters for fastdeb: 

- `-p` or `--path` - path to script or binary which you want to pack into `.deb` package
- `-n` or `--name` - desired name of package
- `-v` or `--version` - package version
- `-m` or `--maintainer` - maintainer email (could be fake email)
- `-d` or `--description` - description of your software.

There is one optional parameter as well:

- `-a` or `--architecture` - architecture of your software which you pack into `.deb` package. 

By default it has value `all`, this is appropriate for all scripts. 

Example command:
```bash
fastdeb -p fastdeb -n fastdeb -v 1.0.1 -m kostya@osintegrator.com -d "Fastdeb - CLI tool for deb packages creation"
```

Output of this command would be such:
```
INFO     2021-04-26 17:05:28,354 Successfully created the directory /tmp/tmpsad5hynh/fastdeb_1.0.1/DEBIAN
INFO     2021-04-26 17:05:28,354 Successfully created the directory /tmp/tmpsad5hynh/fastdeb_1.0.1/usr/bin/
INFO     2021-04-26 17:05:28,354 Control file was successfully created at /tmp/tmpsad5hynh/fastdeb_1.0.1/DEBIAN/control!
INFO     2021-04-26 17:05:28,354 Binary file fastdeb was successfully copied to /tmp/tmpsad5hynh/fastdeb_1.0.1/usr/bin/!
dpkg-deb: building package 'fastdeb' in '/tmp/tmpsad5hynh/fastdeb_1.0.1.deb'.
INFO     2021-04-26 17:05:28,368 Deb package fastdeb_1.0.1.deb.deb was successfully created!!!
```

The result of running such command would be `.deb` file in this format:
```
<name>_<version>.deb
```
In case of abovementioned commnad:
```
fastdeb_1.0.1.deb
```

The resulting `.deb` file will be placed in directory from which `fastdeb` command was called.
If I call it say from `/home/username` directory, it will be placed on path: `/home/username/fastdeb_1.0.1.deb`