#base images
FROM golang:1.22-alpine AS builder

#setup the workdir
WORKDIR /usr/src/app

#copy source code
COPY . .

#download the dependencies
RUN go mod download

#build the dependencies

RUN go build -o product-catlog ./

# ###############


FROM alpine AS release

WORKDIR /usr/src/app/

COPY ./products/ ./products/
COPY --from=builder /usr/src/app/product-catlog/ ./

ENV PRODUCT_CATALOG_PORT 8087

ENTRYPOINT ["./product-catlog"]