# queryForObject deprecated
> **Lien Chen** *2021-03-23*

When try using queryForObject to select one line data
Using `queryForObject(String sql, @Nullable Object[] args, RowMapper<T> rowMapper)` it show deprecated.
[In this document](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/jdbc/core/JdbcOperations.html#queryForObject-java.lang.String-org.springframework.jdbc.core.RowMapper-java.lang.Object...-), we know it is prefer to use `queryForObject(String sql, RowMapper<T> rowMapper, Object[] args)`

[reference_stackoverflow](https://stackoverflow.com/questions/65301011/jdbctemplate-queryforobject-and-query-is-deprecated-in-spring-what-should-i)
[reference_spring_document](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/jdbc/core/JdbcOperations.html#queryForObject-java.lang.String-org.springframework.jdbc.core.RowMapper-java.lang.Object...-)