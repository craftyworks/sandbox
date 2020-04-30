## @Scheduled

### fixedRate 와 fixedDelay 의 차이

#### fixedDelay

> `fixedDelay` 는 작업이 완료된 이후 다음 작업이 시작되기 까지의 지연을 준다. 따라서 중복되서 실행되지 않음을 보장할 수 있다.

#### fixedRate

> `fixedRate` 는 설정된 `n` 밀리 세컨드마다 예약된 작업을 실행한다. 이전에 실행된 작업의 종료 여부등을 체크하지 않는다. 따라서 중복 실행될 수 있다.

### initialDelay

> `fixedDelay` 와 `fixedRate` 가 설정된 작업은 Application 이 Boot 되면 바로 시작하고 본다. `initialDelay` 를 설정하면 최초 시작되는 작업을 지연시킬 수 있다.

### cron

> 아래 순서대로 설정한다. 6개다.

* 초
* 분
* 시
* 일
* 월
* 요일 : 1-7 또는 SUN-SAT

> `*` (all value) vs `?` (no specific value)

`?` 는 일과 요일 필그에만 설정 가능하다. 아무리 설명을 바도 이해를 못하겠다. 둘의 차이가 뭔지... 게다가 Spring Scheduled Cron 식에선 둘이 차이 없이 동작한다.

```java
  @Scheduled(cron = "0 */1 12-13 * * *")

  @Scheduled(cron = "0 */1 12-13 ? * ?")
```

> `/` Increment 연산자? 초기값과 증분을 지정한다.

* `0/5` 를 `분` 으로 설정하면 0분, 5분, 10분... 
* `0/5` 는 `*/5` 와 같다.

> 하나의 메소드에 여러개의 @Scheduled 를 지정할 수 있다.

```java
  /* 22시 ~ 06시 */
  @Scheduled(cron = "0 */5 22,23 * * ?")
  @Scheduled(cron = "0 */5 0-6 * * ?")
  private void test() {
    logger.info("Triggered");
  }
```

> Refereces

* http://www.quartz-scheduler.org/documentation/quartz-2.3.0/tutorials/crontrigger.html
* https://riptutorial.com/spring/example/21209/cron-expression





