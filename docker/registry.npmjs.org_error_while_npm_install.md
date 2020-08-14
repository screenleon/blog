# registry.npmjs.org Error While Npm Install
> **Lien Chen** *2020-07-28*

Can't not run the npm install. Docker's DNS can't fetch the website.`/etc/docker/daemon.json` add below data and restart.
```json=
{
    "dns": ["10.0.0.2", "8.8.8.8"]
}
```