# docker
## Задание 1 - Docker CLI
1. Загрузите образ `busybox` последней версии
   ```
        vagrant@testing:~$ sudo docker pull busybox
    Using default tag: latest
    latest: Pulling from library/busybox
    3f4d90098f5b: Pull complete
    Digest: sha256:3fbc632167424a6d997e74f52b878d7cc478225cffac6bc977eedfe51c7f4e79
    Status: Downloaded newer image for busybox:latest
    docker.io/library/busybox:latest

   ```
1. Запустите новый контейнер `busybox` с командой `ping` сайта `netology.ru`, и количеством пингов 7, поименуйте контейнер `pinger`
      ```
          vagrant@testing:~$ sudo docker run --name pinger busybox ping -c 7 netology.ru
        PING netology.ru (188.114.99.224): 56 data bytes
        64 bytes from 188.114.99.224: seq=0 ttl=53 time=1085.283 ms
        64 bytes from 188.114.99.224: seq=1 ttl=53 time=90.531 ms
        64 bytes from 188.114.99.224: seq=2 ttl=53 time=6.783 ms
        64 bytes from 188.114.99.224: seq=3 ttl=53 time=9.029 ms
        64 bytes from 188.114.99.224: seq=4 ttl=53 time=5.515 ms
        64 bytes from 188.114.99.224: seq=5 ttl=53 time=7.656 ms
         64 bytes from 188.114.99.224: seq=6 ttl=53 time=8.533 ms

        --- netology.ru ping statistics ---
          7 packets transmitted, 7 packets received, 0% packet loss
         round-trip min/avg/max = 5.515/173.332/1085.283 ms

      ```
1. Выведите на список всех контейнеров - запущенных и остановленных
   ```
        vagrant@testing:~$ sudo docker ps -a
    CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS                          PORTS     NAMES
    32edcf7f92f9   busybox   "ping -c 7 netology.…"   2 minutes ago   Exited (0) About a minute ago             pinger

   ```
1. Выведите на экран логи контейнера с именем `pinger`
      ```
        vagrant@testing:~$ sudo docker logs pinger
          PING netology.ru (188.114.99.224): 56 data bytes
          64 bytes from 188.114.99.224: seq=0 ttl=53 time=1085.283 ms
          64 bytes from 188.114.99.224: seq=1 ttl=53 time=90.531 ms
          64 bytes from 188.114.99.224: seq=2 ttl=53 time=6.783 ms
          64 bytes from 188.114.99.224: seq=3 ttl=53 time=9.029 ms
          64 bytes from 188.114.99.224: seq=4 ttl=53 time=5.515 ms
          64 bytes from 188.114.99.224: seq=5 ttl=53 time=7.656 ms
          64 bytes from 188.114.99.224: seq=6 ttl=53 time=8.533 ms

           --- netology.ru ping statistics ---
            7 packets transmitted, 7 packets received, 0% packet loss
              round-trip min/avg/max = 5.515/173.332/1085.283 ms

      ```
1. Запустите второй раз контейнера с именем `pinger`
   ```
        vagrant@testing:~$ sudo docker start -a pinger
     PING netology.ru (188.114.98.224): 56 data bytes
     64 bytes from 188.114.98.224: seq=0 ttl=53 time=6.299 ms
     64 bytes from 188.114.98.224: seq=1 ttl=53 time=6.631 ms
     64 bytes from 188.114.98.224: seq=2 ttl=53 time=8.756 ms
     64 bytes from 188.114.98.224: seq=3 ttl=53 time=8.975 ms
     64 bytes from 188.114.98.224: seq=4 ttl=53 time=8.312 ms
     64 bytes from 188.114.98.224: seq=5 ttl=53 time=7.480 ms
     64 bytes from 188.114.98.224: seq=6 ttl=53 time=8.400 ms

      --- netology.ru ping statistics ---
      7 packets transmitted, 7 packets received, 0% packet loss
      round-trip min/avg/max = 6.299/7.836/8.975 ms

   ```
1. Выведите на список всех контейнеров - запущенных и остановленных
   ```
      vagrant@testing:~$ sudo docker ps -a
      CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS                     PORTS     NAMES
      32edcf7f92f9   busybox   "ping -c 7 netology.…"   7 minutes ago   Exited (0) 2 minutes ago             pinger

   ```
1. Выведите на экран логи контейнера с именем `pinger`
   ```
      vagrant@testing:~$ sudo docker logs pinger
     PING netology.ru (188.114.99.224): 56 data bytes
     64 bytes from 188.114.99.224: seq=0 ttl=53 time=1085.283 ms
     64 bytes from 188.114.99.224: seq=1 ttl=53 time=90.531 ms
     64 bytes from 188.114.99.224: seq=2 ttl=53 time=6.783 ms
     64 bytes from 188.114.99.224: seq=3 ttl=53 time=9.029 ms
     64 bytes from 188.114.99.224: seq=4 ttl=53 time=5.515 ms
     64 bytes from 188.114.99.224: seq=5 ttl=53 time=7.656 ms
     64 bytes from 188.114.99.224: seq=6 ttl=53 time=8.533 ms

     --- netology.ru ping statistics ---
    7 packets transmitted, 7 packets received, 0% packet loss
    round-trip min/avg/max = 5.515/173.332/1085.283 ms
    PING netology.ru (188.114.98.224): 56 data bytes
    64 bytes from 188.114.98.224: seq=0 ttl=53 time=6.299 ms
    64 bytes from 188.114.98.224: seq=1 ttl=53 time=6.631 ms
    64 bytes from 188.114.98.224: seq=2 ttl=53 time=8.756 ms
    64 bytes from 188.114.98.224: seq=3 ttl=53 time=8.975 ms
    64 bytes from 188.114.98.224: seq=4 ttl=53 time=8.312 ms
    64 bytes from 188.114.98.224: seq=5 ttl=53 time=7.480 ms
    64 bytes from 188.114.98.224: seq=6 ttl=53 time=8.400 ms

     --- netology.ru ping statistics ---
     7 packets transmitted, 7 packets received, 0% packet loss
     round-trip min/avg/max = 6.299/7.836/8.975 ms

   ```
1. Определите по логам общее количество запусков команды `ping` и какое общее количество отправленых запросов

   ```
     vagrant@testing:~$ sudo docker logs pinger | grep "PING netology.ru" | wc -l
     2

   ```
1. Удалите контейнер с именем `pinger`   
```
 vagrant@testing:~$ sudo docker stop pinger
 pinger
 vagrant@testing:~$ sudo docker rm pinger
 pinger

```
1. Удалите образ `busybox`
   ```
      vagrant@testing:~$ sudo docker rmi busybox
   Untagged: busybox:latest
   Untagged: busybox@sha256:3fbc632167424a6d997e74f52b878d7cc478225cffac6bc977eedfe51c7f4e79
   Deleted: sha256:a416a98b71e224a31ee99cff8e16063554498227d2b696152a9c3e0aa65e5824
   Deleted: sha256:3d24ee258efc3bfe4066a1a9fb83febf6dc0b1548dfe896161533668281c9f4f

   ```
