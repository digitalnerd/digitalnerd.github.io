---
layout: post
title: Docker Cheats Sheet
---
### Удалить остановленные/не используемые контейнеры/образы
Удалить все остановленные контейнеры:
```
$ sudo docker rm $( docker ps -q -f status=exited)
```

Удалить все "висящие" (не используемые) образы
```
$ sudo docker rmi $( docker images -q -f dangling=true)
```

Использовать xargs с --no-run-if-empty даже лучше, т.к. он справляется со случаем, когда нечего удалять.

Удалить все остановленные контейнеры:
```
$ sudo docker ps -q -f status=exited | xargs --no-run-if-empty docker rm
```
Удалить все "висящие" (не используемые) образы
```
$ sudo docker images -q -f dangling=true | xargs --no-run-if-empty docker rmi
```
### How to solve the issue that a Terminal screen is messed up? (usually after a resizing)
```
$ sudo docker exec -it -e COLUMNS=$COLUMNS -e LINES=$LINES -e TERM=$TERM CONTAINER bash
```
