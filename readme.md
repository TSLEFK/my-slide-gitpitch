[https://gitpitch.com/TSLEFK/my-slide-gitpitch](https://gitpitch.com/TSLEFK/my-slide-gitpitch)


# GitPitch Desktop
~~i couldn't access [http://localhost:9000](http://localhost:9000). I didn't have error message, so i resigned.~~

Only this command. You can see GitPitch.
> docker-compose up -d


... if you have error(store/gitpitch/desktop:pro not found: does not exist or no pull access), plz read the rest.

docker compose has this line.
```yaml 
    image: store/gitpitch/desktop:pro
```
plz register GitPitch Pro(First month may be free trial).
Docker Store : [GitPitch Pro](https://store.docker.com/images/gitpitch-pro)  

> docker login

you type your Username and Password.  
After you'll get "Login Succeeded". Retry compose up.

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

