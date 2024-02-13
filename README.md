# Install Hugo

```
sudo apt install hugo
```

# Build

```
hugo server --minify --theme hugo-book
```

# Run

```
<web browser> http://localhost:1313
```


docker run -p 8080:8080 \
  -v ${PWD}:/src \
  razonyang/hugo \
  hugo server --bind 0.0.0.0 -p 8080
  