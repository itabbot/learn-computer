# 防止 SQL 注入实践

[参考资料](https://github.com/goldbergyoni/nodebestpractices#-64-prevent-query-injection-vulnerabilities-with-ormodm-libraries) | [实践工程](https://github.com/fooins/insbiz/blob/main/src/libraries/)

做到以下三点，可以有效地避免绝大部分的 SQL 注入风险：

1. 严格校验来自外部或用户输入的数据，抛弃和拒绝不符合预期的数据，可参阅 [数据校验实践>>](./数据校验实践.md)。

2. 使用可靠的数据访问库来操作数据库，它们基本都具有针对注入攻击的内置保护。比如：[TypeORM](https://github.com/typeorm/typeorm)、[sequelize](https://github.com/sequelize/sequelize)、[mongoose](https://github.com/Automattic/mongoose)、[Knex](https://github.com/knex/knex)、[Objection.js](https://github.com/Vincit/objection.js)、[waterline](https://github.com/balderdashy/waterline)。

3. 永远不要使用 JavaScript 模板字符串或字符串连接将值拼接到查询语句中，这会使应用程序面临广泛的漏洞。
