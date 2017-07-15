
### Notes on InnoDB variables

#### innodb_rollback_segments		
- MySQL Docs: [5.5](https://dev.mysql.com/doc/refman/5.5/en/innodb-parameters.html#sysvar_innodb_rollback_segments) [5.6](https://dev.mysql.com/doc/refman/5.6/en/innodb-parameters.html#sysvar_innodb_rollback_segments) [5.7](https://dev.mysql.com/doc/refman/5.7/en/innodb-parameters.html#sysvar_innodb_rollback_segments)
- 用于指定 **InnoDB rollback segments** 的数目.
- 每个rollback segment最多支持存放1023个innodb write transaction的undo log. 从MySQL 5.5开始, 一个Innodb实例最多可以有128个rollbackup segment, 因而最多支持 **(128 * 1023)** 个并发的写事务; 而在此之前(MySQL 5.1, 或者innodb 1.0), 一个Innodb实例最多只能有1个rollbackup segment.
- 从MySQL 5.7开始, innodb_rollback_segments有了更细致的变化.具体参考文档.

#### innodb_undo_tablespaces
- MySQL Docs: [5.6](https://dev.mysql.com/doc/refman/5.6/en/innodb-parameters.html#sysvar_innodb_undo_tablespaces) [5.7](https://dev.mysql.com/doc/refman/5.7/en/innodb-parameters.html#sysvar_innodb_undo_tablespaces)
- 指定undo tablespace的数目.
- MySQL 5.6开始, Undo tablespaces可以从system tablespace上分出来放到若干到单独的文件上: undo01, undo02, ...
