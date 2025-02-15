```
gen-proto:
	protoc -I proto proto/exchange/*.proto								   # # путь до файла *.proto
			--go_out=./gen/                                                # куда будет скомпилирован протофайл exchange.pb.go
			--go_opt=paths=source_relative \							   # сохраняет структуру каталогов в исходных файлах.
			--go-grpc_out=./gen/										   # куда будет скомпилирован протофайл exchange_grpc.pb.go
			--go-grpc_opt=paths=source_relative \
			./proto/exchange/*.proto		
```