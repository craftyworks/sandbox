
## Pattern

### Local

```yml
logging:
  pattern:
    console: "%clr(%d{yyyy-MM-dd HH:mm:ss.SSS}){magenta} %highlight(${LOG_LEVEL_PATTERN:-%5p}) | %cyan(%40.40logger{40}.%-15.15method) %green([%4.4L]) %m%n"
```

### Prod

```yml
logging:
  pattern:
    console: "%d{yyyy-MM-dd HH:mm:ss.SSS} ${LOG_LEVEL_PATTERN:-%5p} | %40.40logger{40}.%-15.15method [%4.4L] %m%n"
```
