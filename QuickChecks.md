_Sampled Values_ are delivered on port **48001**.
_Synchrophasors_ are delivered on port **48003**.

*Kill old tasks using UDP Port 48001

`sudo fuser -k 48001/udp`

*See what's on UDP Port 48001 using netcat

`nc -l -u 48001`

-l listen, -u UDP
