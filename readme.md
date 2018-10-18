[https://gitpitch.com/TSLEFK/my-slide-gitpitch](https://gitpitch.com/TSLEFK/my-slide-gitpitch)

参考サイト
https://paiza.hatenablog.com/entry/2017/06/22/GitHub%E3%81%A0%E3%81%91%E3%81%A7%E8%B6%85%E9%AB%98%E6%A9%9F%E8%83%BD%E3%81%AA%E3%82%B9%E3%83%A9%E3%82%A4%E3%83%89%E8%B3%87%E6%96%99%E3%81%8C%E4%BD%9C%E3%82%8C%E3%82%8B%E3%80%8CGitPitch%E3%80%8D%E3%81%AE


https://gitpitch.com/docs/code-features/fenced-blocks/
https://github.com/gitpitch/gitpitch/edit/master/PITCHME.md

# GitPitch Desktop
~~i couldn't access [http://localhost:9000](http://localhost:9000). I didn't have error message, so i resigned.~~

> docker-compose up -d

> docker-compose logs

```
Attaching to test_gitpitch_1
gitpitch_1  | 2018-10-06 11:29:02,904 [info] c.g.s.DesktopService - GitPitch Desktop successfully started.
gitpitch_1  | 2018-10-06 11:29:03,421 [info] play.api.Play - Application started (Prod)
gitpitch_1  | 2018-10-06 11:29:03,681 [info] p.c.s.NettyServer - Listening for HTTP on /0.0.0.0:9000
```

if use Docker for Windows/Mac. 
> docker-machine ls

```
NAME      ACTIVE   DRIVER       STATE     URL                         SWARM   DOCKER        ERRORS
default   *        virtualbox   Running   tcp://xxx.xxx.xxx.xxx         v18.05.0-ce
```
[http://xxx.xxx.xxx.xxx:9000](http://xxx.xxx.xxx.xxx:9000)

container ssh login
> docker exec -it test_gitpitch_1 bash

