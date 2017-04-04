# ebooktools

A few things to make ebooks easier to make.

## What's Inside

Subject to change:

- pandoc
- calibre (for ebook-convert)
- epubcheck

## How it Works

At the moment I'm stringing together the build steps using a bash script. Here's what my docker-compose.yml looks like ATM:

version: '2'

```yaml
services: 
  build:
    container_name: ebooktools
    build: ./ebooktools
    image: garyritchie/ebooktools
    volumes: 
      - ./build:/build 
      - ./src:/src
      - ./build.sh:/build.sh
    working_dir: /
    entrypoint: /bin/bash
    command: build.sh
```
so I can then do: `docker-compose run build`
