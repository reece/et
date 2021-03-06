# et
Sending and receiving arbitrary data via UDP


This package implements a lightweight, pure-Python client and server
pair that sends and receives simple Python structures via UDP.  The original motivation is to
enable a package to send "phone home" messages.

The default encoding is zlib-compressed json. (pickle is not used out
of security concerns
[[example](https://www.smartfile.com/blog/python-pickle-security-problems-and-solutions/)].)



# Example

```
make devready
```

In one shell, type:

```
$ python et/server.py
INFO:__main__:Listening on localhost:2233
```

In another shell, type:

```
$ python ./et/client.py 
```
(There is no output from the client)

In the server window, you should see messages like: 

```
INFO:__main__:Received 4 bytes from ('127.0.0.1', 47750) in format 1

INFO:__main__:Received 12 bytes from ('127.0.0.1', 59498) in format 2

INFO:__main__:Received 18 bytes from ('127.0.0.1', 42396) in format 1
{'test': 'data'}
INFO:__main__:Received 26 bytes from ('127.0.0.1', 42598) in format 2
{'test': 'data'}
INFO:__main__:Received 122 bytes from ('127.0.0.1', 57842) in format 1
{'version': '1.2.3rc4', 'sys.version_info': [3, 5, 2, 'final', 0], 'sys.platform': 'linux', 'local_ip': '172.18.20.148'}
INFO:__main__:Received 108 bytes from ('127.0.0.1', 44319) in format 2
{'version': '1.2.3rc4', 'sys.version_info': [3, 5, 2, 'final', 0], 'sys.platform': 'linux', 'local_ip': '172.18.20.148'}
```

Format 1 is json; format 2 is compressed json.
