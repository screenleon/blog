# Mongo run with Transaction
> **Lien Chen** *2020-08-19*

* To use transaction
    * Use the MongoDB driver updated for the version of your MongoDB deployment. For transactions on MongoDB 4.2 deployments (replica sets and sharded clusters), clients must use MongoDB drivers updated for MongoDB 4.2.
    * When using the drivers, each operation in the transaction must be associated with the session (i.e. pass in the session to each operation).

* Create mongo container with replicaset
    1. 新增 container: `docker run -d -p 27017:27017 --name mongo4 mongo --replSet rs0`
    2. 進入 mongo4 的 mongo shell: `docker exec -it mongo4 mongo`
    3. 輸入 `rs.initiate()` 初始化 replicaset, 即可啟用 **transaction**

[MongoDB Transaction](https://docs.mongodb.com/manual/core/transactions/)
[reference](https://stackoverflow.com/questions/27187591/deploy-mongodb-replicaset-servers-with-docker-on-different-physical-servers)