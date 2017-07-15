
### Notes on InnoDB variables

#### innodb_rollback_segments		
- MySQL Docs: [5.5](https://dev.mysql.com/doc/refman/5.5/en/innodb-parameters.html#sysvar_innodb_rollback_segments) [5.6](https://dev.mysql.com/doc/refman/5.6/en/innodb-parameters.html#sysvar_innodb_rollback_segments) [5.7](https://dev.mysql.com/doc/refman/5.7/en/innodb-parameters.html#sysvar_innodb_rollback_segments)
- 用于指定 **InnoDB rollback segments** 的数目.
- 每个rollback segment最多支持存放1023个innodb write transaction的undo log. 从MySQL 5.5开始, 一个Innodb实例最多可以有128个rollbackup segment, 因而最多支持 **(128 * 1023)** 个并发的写事务; 而在此之前(MySQL 5.1, 或者innodb 1.0), 一个Innodb实例最多只能有1个rollbackup segment.
- 从MySQL 5.7开始, innodb_rollback_segments有了更细致的变化: 其中1个必须放入system tablespace; 32个必须被保留作为temporary tablespace; 其余的(最多95个)才会被作为写事务的rollback segment.

#### innodb_undo_tablespaces
- MySQL Docs: [5.6](https://dev.mysql.com/doc/refman/5.6/en/innodb-parameters.html#sysvar_innodb_undo_tablespaces) [5.7](https://dev.mysql.com/doc/refman/5.7/en/innodb-parameters.html#sysvar_innodb_undo_tablespaces)
- 指定undo tablespace文件的数目.
- MySQL 5.6开始, Undo tablespace数据可以从system tablespace文件里分出来放入若干单独的文件: undo01, undo02, ... 这些文件的存放位置由变量[innodb_undo_directory](https://dev.mysql.com/doc/refman/5.6/en/innodb-parameters.html#sysvar_innodb_undo_directory)指定.
- innodb_undo_tablespaces一旦设定好, 就不能改了. 因此, 不妨多设置几个. innodb_rollback_segments会平均地分布在各个Undo tablespace文件上.
- innodb_undo_tablespaces的默认值为0, 这意味着undo logs存入system tablespace, 而不是放入单独的文件.
