# Lightsail Less Memory
> **Lien Chen** *2021-04-29*

When I start up database and web server, database usually starts fail. I need to start database along to make sure database start successfully.
Use command `top`, found there doesn't have swap. Use below command to add 1G swap.

```
sudo fallocate -l 1G /swapfile && sudo chmod 600 /swapfile && sudo mkswap /swapfile && sudo swapon /swapfile && sudo sed -i '$ a\/swapfile swap swap defaults 0 0' /etc/fstab
```

[Amazon lightsail instance down every day [fixed]](https://stefvanlooveren.me/blog/amazon-lightsail-instance-down-every-day-fixed)