# Description
The route guide server and client demonstrate how to use grpc go libraries to
perform unary, client streaming, server streaming and full duplex RPCs.

# CHANGES:

The example has been modified to perform mutual authentication between the client and the server.
# -------

Please refer to [gRPC Basics: Go] (http://www.grpc.io/docs/tutorials/basic/go.html) for more information.

See the definition of the route guide service in proto/route_guide.proto.

# Run the sample code
To compile and run the server, assuming you are in the root of the route_guide
folder, i.e., .../examples/route_guide/, simply:

```sh
$ go run server/server.go
```

Likewise, to run the client:

```sh
$ go run client/client.go
```

# Optional command line flags
The server and client both take optional command line flags. For example, the
client and server run without TLS by default. To enable TLS:

```sh
$ go run server/server.go -tls=true
```

and

```sh
$ go run client/client.go -tls=true
```

# Optional resources
Generate self-signed client and server certs for testing.
```sh
$ openssl genrsa -out ca-key.pem 2048;
$ openssl req -new -x509 -nodes -days 1000 -key ca-key.pem -out ca-cert.pem;
$ openssl req -newkey rsa:2048 -days 1000 -nodes -keyout server-key.pem -out server-req.pem;
$ openssl x509 -req -in server-req.pem -days 1000 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out server-cert.pem;
$ openssl req -newkey rsa:2048 -days 1000 -nodes -keyout client-key.pem -out client-req.pem;
$ openssl x509 -req -in client-req.pem -days 1000 -CA ca-cert.pem -CAkey ca-key.pem -set_serial 01 -out client-cert.pem;
```sh

SSL/TLS mutual authentication:
Link: https://github.com/grpc/grpc-go/issues/403
