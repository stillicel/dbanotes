
# Notes on InnoDB variables

## innodb_rollback_segments		
- MySQL Docs: [5.5](https://dev.mysql.com/doc/refman/5.5/en/innodb-parameters.html#sysvar_innodb_rollback_segments) [5.6](https://dev.mysql.com/doc/refman/5.6/en/innodb-parameters.html#sysvar_innodb_rollback_segments) [5.7](https://dev.mysql.com/doc/refman/5.7/en/innodb-parameters.html#sysvar_innodb_rollback_segments)
- Defines the number of **rollback segments** used by InnoDB.
- 从MySQL 5.5开始, 每个rollback segment最多支持存放1023个innodb write transaction的undo log. 因此一个Innodb实例的并发事务上限数目是**(128 * 1023)**.
