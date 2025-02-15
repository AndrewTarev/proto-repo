1. Чтобы скомпилировать протофайл, сначало необходимо установить на компьютер приложение protobuf:
```
"MacOS"

brew install protobuf
protoc --version
```

2. Затем выполните команду из Makefile
```
gen-proto:
	protoc -I proto proto/exchange/*.proto			    # путь до файла *.proto
			--go_out=./gen/                             # куда будет скомпилирован протофайл exchange.pb.go
			--go_opt=paths=source_relative \	    # сохраняет структуру каталогов в исходных файлах(не изменять).
			--go-grpc_out=./gen/			    # куда будет скомпилирован протофайл exchange_grpc.pb.go
			--go-grpc_opt=paths=source_relative \       # сохраняет структуру каталогов в исходных файлах(не изменять).
```

3. В файле go.mod название модуля должно быть ссылкой на репо в гите:
```
module github.com/AndrewTarev/proto-repo
```

4. После каких либо изменений, не забудь проверсионировать свой код:
```
git tag v0.0.1
git push origin v0.0.1
```

5. В своем проекте установи пакет с этим репозиторием:
- `go get github.com/AndrewTarev/proto-repo`

6. Затем импортируйте в проекте сгенерированные файлы:
```
exch "github.com/AndrewTarev/proto-repo/gen/exchange"
```