# GMail-Architecture
GMail Architecture

### Need for separate search engine 

The email service can provide some basic search APIs like search by receiver, date etc… However, complex search queries will require a join across tables, which is expensive.

If we use a NoSQL database and dump all the denormalised email data into an email table, we can avoid joins. Even then, we would like to have an offline process to reverse index the emails. We would also like to separate the complex search operations from the CRUD operations in the email service.

Hence, it would be better to separate the two services. A drawback of this could be inconsistencies in the email service and search engine records (The search engine gets the email event after some time).

