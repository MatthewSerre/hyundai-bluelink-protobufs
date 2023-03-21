# Hyundai Bluelink Protobufs

A repository for proto files containing definitions for the communication contracts between clients and services.

## Getting Started

* [Install Go](https://go.dev/doc/install)
* [Install the Buf CLI](https://buf.build/docs/installation/)

## Usage

Packages from this repository can be imported in Go projects. For example:

```
import (
    authv1 "github.com/MatthewSerre/hyundai-bluelink-protobufs/gen/go/protos/authentication/v1"
)
```

The protobuf definitions can be used to generate code for any supported language. The code can be used both client- and server-side to ensure the data transmitted between them conforms to a strict contract that specifies the required data types. For example:

The generated Go code contains an interface which accepts an `AuthenticationRequest`

```
type AuthenticationRequest struct {
	state         protoimpl.MessageState
	sizeCache     protoimpl.SizeCache
	unknownFields protoimpl.UnknownFields

	Username string `protobuf:"bytes,1,opt,name=username,proto3" json:"username,omitempty"`
	Password string `protobuf:"bytes,2,opt,name=password,proto3" json:"password,omitempty"`
	Pin      string `protobuf:"bytes,3,opt,name=pin,proto3" json:"pin,omitempty"`
}
```

and returns an `AuthenticationResponse`.

```
type AuthenticationResponse struct {
	state         protoimpl.MessageState
	sizeCache     protoimpl.SizeCache
	unknownFields protoimpl.UnknownFields

	Username  string `protobuf:"bytes,1,opt,name=username,proto3" json:"username,omitempty"`
	Pin       string `protobuf:"bytes,2,opt,name=pin,proto3" json:"pin,omitempty"`
	JwtToken  string `protobuf:"bytes,3,opt,name=jwt_token,json=jwtToken,proto3" json:"jwt_token,omitempty"`
	JwtExpiry int64  `protobuf:"varint,4,opt,name=jwt_expiry,json=jwtExpiry,proto3" json:"jwt_expiry,omitempty"`
}
```

The generated types can be used to format the data in the request and response, which ensures whatever code is written to handle the data on either the client- or server-side can rely on the specified data being present in the expected type.

## Contributing

Create an issue and/or a pull request and I will take a look.

***

This project is not affiliated with Hyundai in any way. Credit to [TaiPhamD](https://github.com/TaiPhamD) and his `bluelink_go` project [link](https://github.com/TaiPhamD/bluelink_go) for inspiration and some code snippets.