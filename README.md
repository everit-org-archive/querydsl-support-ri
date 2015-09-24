# querydsl-support-ri

Reference implementation of [querydsl-support-api][1].

## Usage with Java 7

```
return querydslSupport.execute(new QuerydslCallable<Long>() {
     @Override
     public Long call(Connection connection, Configuration configuration) throws SQLException {
        QResource qResource = new QResource("qResource");
        SQLInsertClause insertClause = new SQLInsertClause(connection, configuration, qResource);
        return insertClause.executeWithKey(qResource.resourceId);
    }
});
```

## Usage with Java 8

```
return querydslSupport.execute((connection, configuration) -> {
    QResource qResource = new QResource("qResource");
    SQLInsertClause insertClause = new SQLInsertClause(connection, configuration, qResource);
    return insertClause.executeWithKey(qResource.resourceId);
});
```

[1]: https://github.com/everit-org/querydsl-support-api