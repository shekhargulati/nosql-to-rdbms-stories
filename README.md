# NoSQL to RDBMS Stories
This repository contains list of publicly available stories where decision to NoSQL databases proved costly. Many organisations went the route of using NoSQL datastore like MongoDB, Cassandra, etc. as their primary data storage solution to take advantage of their perceived benefits. Many times this shift to NoSQL databases has proved costly and wrong. Internet is full of such sad stories. Some of these stories are mentioned below. Please note that some of the posts are old so databases might have improved and fixed their problems.

1. Don't use MongoDB - [Link](http://pastebin.com/raw/FD3xe6Jt) - The issues mentioned in this post are following. 
   * MongoDB issues writes in unsafe ways by default in order to win benchmarks
   * MongoDB can loose data in many startling ways
   * MongoDB sharing doesn't work that well under load
   * MongoDB actually deleted the entire dataset

2. Goodbye MongoDB, Hello PostgreSQL - [Link](https://developer.olery.com/blog/goodbye-mongodb-hello-postgresql/) - The key issues related to MongoDB outlines in this post are:
   * MongoDB went in near total lockdown when they tried to reinsert a million documents. This resulted in degraded performance for several hours
   * MongoDB does not give any indication when things go wrong
   * The lack of schema in the database often means implicit schema in your application. This means data consistency  becomes problem of the application not database

3. Why you should never use MongoDB -  [Link](http://www.sarahmei.com/blog/2013/11/11/why-you-should-never-use-mongodb/) - The post talks about how denormalised data leads to data duplication which makes updating data difficult. If you normalise data in MongoDB, then you end up doing joins in your application code. Two main points mentioned in the post are:
   *  Whether you’re duplicating critical data (ugh), or using references and doing joins in your application code (double ugh), when you have links between documents, you’ve outgrown MongoDB. When the MongoDB folks say “documents,” in many ways, they mean things you can print out on a piece of paper and hold. A document may have internal structure — headings and subheadings and paragraphs and footers — but it doesn’t link to other documents. It’s a self-contained piece of semi-structured data.
   *  MongoDB’s ideal use case is even narrower than our television data. The only thing it’s good at is storing arbitrary pieces of JSON. “Arbitrary,” in this context, means that you don’t care at all what’s inside that JSON. You don’t even look. There is no schema, not even an implicit schema, as there was in our TV show data. Each document is just a blob whose interior you make absolutely no assumptions about.

4. Our journey from Graph Databases to PostgreSQL - [Link](http://engineering.hipolabs.com/graphdb-to-postgresql/) - The problems outlined in this post are:
   * Application logic was getting more complicated every day, Neo4J is great, but it gets slower with complicated queries and increased data scale
   * As our database grew, Neo4j started getting slower and slower with no clear path for scaling or optimization

5. RethinkDB versus PostgreSQL: my personal experience - [Link](http://blog.sagemath.com/2017/02/09/rethinkdb-vs-postgres.html) - This post outlines why SageMath moved from RethinkDB to PostgreSQL
   * Bugs in automatic failover 
   * Everything was a battle; even trying to do backups was really painful, and eventually we gave up on making proper full consistent backups (instead, backing up only the really important tables via complete JSON dumps). We also had a lot of issues with disk usage.
   * The total disk space usage was an order of magnitude less (800GB versus 80GB) – some of our tables had a lot of TEXT fields, and PostgreSQL automatically compresses those, which was a huge win.

6. Why Shippable Moved from NoSQL MongoDB to PostgreSQL - [Link](http://blog.shippable.com/why-we-moved-from-nosql-mongodb-to-postgressql) - The post outlines following major issues with MongoDB:

   * MongoDB lacked tooling to handle large databases. In Shippable case, database was around 4TB.
   * MongoDB took hours to reboot
   * Schemaless forces developers to handle schema in their code. This makes code ugly and unmanageable

7. DynamoDB to Postges. Why and How. - [Link](https://containership.engineering/dynamodb-to-postgres-why-and-how-aa891681af4d) - The post outlines following reasons why they ditched DynamoDB:

   * Unless you’re only getting data by its primary key, or have very few queries to run on the data itself (and you know these from the start!) Dynamo does not allow your application to grow

   * There is no way to have the data returned sorted by anything other than the originally defined range (aka sort) key

8. Bye Bye MySQL & MongoDB. Guten Tag PostgreSQL - [Link](https://www.userlike.com/en/blog/bye-by-mysql-and-mongodb-guten-tag-postgresql) - Reasons for moving away from MongoDB as mentioned in the post are:

   * MongoDB consumes absurd amount of memory over time. Since PostgreSQL added JSON support a while ago, we decided to switch over, the biggest upside being one service less to maintain.



> You will notice that there are more posts criticising MongoDB than any other NoSQL database. I think this has to do with the fact that most people considered MongoDB as replacement for RDBMS. MongoDB ease of use and simple concepts made it easy for developers to adopt it without spending a lot of time grokking its details. Most other NoSQL database were used along with RDBMS so they were not in the critical path.

In last couple of years, developers have again started to embrace relational databases. Even NoSQL databases like MongoDB recently (Feb 2018) added [support for multi-document ACID transactions](https://www.mongodb.com/blog/post/multi-document-transactions-in-mongodb). Not only MongoDB, there are distributed databases like [YugaByte](https://blog.yugabyte.com/yes-we-can-distributed-acid-transactions-with-high-performance/), [NuoDB](https://www.nuodb.com/blog/acid-instrumental-move-saas), and [VoltDB](https://www.voltdb.com/product/features-benefits/acid-transactions/) that also support ACID transactions.

 