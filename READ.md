# Project done as part of Distributed Systems Course

## How to run the SERVER

Each server is initialized with an index and an `ip_list.txt`
```
usage: python3 server.py <id> <ip-list-file>
```

there is a file called `ip_list.txt` that has a list of IPs of the servers, the consensus majority will be calculated based on the "number of servers" (#lines) in this file. Make sure there are **no empty** lines!

example of 5-server `ip_list.txt`

```
http://127.0.0.1:5000
http://127.0.0.1:5001
http://127.0.0.1:5002
http://127.0.0.1:5003
http://127.0.0.1:5004
```

 example of running 5 servers
```
➜  python3 server.py 0 ip_list.txt
➜  python3 server.py 1 ip_list.txt
➜  python3 server.py 2 ip_list.txt
➜  python3 server.py 3 ip_list.txt
➜  python3 server.py 4 ip_list.txt
```

## How to run the CLIENT
the client can perform `GET` and `PUT` request from the command line.

- the first argument is always the `http://ip:port` of a functioning server
- the second is the `key`
- the third is optional and is a `value`
  - if the `value` **is** present the client performs a `PUT` request with key and value to the specified server
  - if the `value` **is not** present the client performs a `GET` request of the key to the specified server

```
PUT usage: python3 client.py 'address' 'key' 'value'
GET usage: python3 client.py 'address' 'key'
Format: address: http://ip:port
```

example of `PUT` key="name" , value="PESU"
```
➜  python3 client.py http://127.0.0.1:5000 name "PESU"
{'code': 'success'}
```
example of `GET` key="name" 
```
➜  python3 client.py http://127.0.0.1:5000 name 
{'code': 'success', 'payload': {'key': 'name', 'value': 'PESU'}}
