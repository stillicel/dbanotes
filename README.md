
# Notes on InnoDB variables

## innodb_rollback_segments		
- MySQL Docs: [5.5](https://dev.mysql.com/doc/refman/5.5/en/innodb-parameters.html#sysvar_innodb_rollback_segments) [5.6](https://dev.mysql.com/doc/refman/5.6/en/innodb-parameters.html#sysvar_innodb_rollback_segments) [5.7](https://dev.mysql.com/doc/refman/5.7/en/innodb-parameters.html#sysvar_innodb_rollback_segments)
- 用于指定 **InnoDB rollback segments** 的数目.
- 每个rollback segment最多支持存放1023个innodb write transaction的undo log. 从MySQL 5.5开始, 一个Innodb实例最多可以有128个rollbackup segment, 因而最多支持 **(128 * 1023)** 个并发的写事务; 而在此之前一个Innodb实例最多只能有1个rollbackup segment.
