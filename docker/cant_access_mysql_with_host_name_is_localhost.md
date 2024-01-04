# Can't access mysql with host name is localhost
> **Lien Chen** *2020-08-06*

* Ensure that MySQL is running either via Docker or on localhost.
* You cant access mysql by user@localhost.
* Create user with user@% to connect. 
P.S. It might make some security issue, should make sure to use.

[reference](https://stackoverflow.com/questions/10823854/using-for-host-when-creating-a-mysql-user)