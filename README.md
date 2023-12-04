# Panduza Documentation

## Clone

```
git clone 
git submodule --init
git submodule update --recursive
```

## Build

Using docker

```
docker run --rm -p 1313:1313 -v $(pwd):/src klakegg/hugo:0.107.0-ext-alpine server
```

## Run

```
<web browser> http://localhost:1313
```


