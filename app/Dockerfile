FROM golang:1.19-alpine

WORKDIR /go/src
COPY ./app/src .

RUN apk upgrade --update && apk --no-cache add git

RUN go get -u github.com/cosmtrek/air && go build -o /go/bin/air github.com/cosmtrek/air

RUN apk add --update gcc musl-dev \ 
&& go get gorm.io/driver/sqlite  \ 
&& go get gorm.io/gorm

RUN go get golang.org/x/oauth2/google \ 
&& go get golang.org/x/oauth2/google  \ 
&& go get -u google.golang.org/api/oauth2/v2

RUN go get github.com/joho/godotenv

CMD ["air", "-c", ".air.toml"]
