# Booking service contracts

This Go module contains the versioned Protobuf contracts and their generated Go
and gRPC code. The schema source is `proto/meeting_rooms.proto`; generated
packages are published from `gen/go`.

## Generate Go code

Run from the repository root with `protoc`, `protoc-gen-go`, and
`protoc-gen-go-grpc` available on `PATH`:

```sh
protoc -I proto proto/meeting_rooms.proto --go_out=./gen/go --go_opt=paths=source_relative --go-grpc_out=./gen/go --go-grpc_opt=paths=source_relative
```

Commit the schema and generated code together. Before consuming a release from
another Go module, create and push a semantic-version Git tag, for example
`v0.1.0`. Consumers can then pin that contract version with:

```sh
go get github.com/shagalinD/booking-service-proto@v0.1.0
```
