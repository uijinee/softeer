# 데이터 크기보다 Spark Execution Memory 공간이 작을 경우

(캐싱 요청을 안했을 경우) 데이터 크기가 Spark Execution Memory보다 커도 Spark는 파티션 단위 처리와 디스크 spill 덕분에 동작은 가능하다. 다만 디스크 I/O 증가로 성능이 떨어지므로, 메모리 튜닝이나 파티션 최적화가 필요하다.

(캐싱 요청을 할 경우) Action 실행 시 연산된 파티션이 Storage Memory에 저장되지만, 공간이 부족하면 일부는 디스크에 저장되거나 날아가고(기본 정책: LRU) 필요 시 다시 계산된다.


# Optimize Local Shuffle Reader가 하는 역할

Optimize Local Shuffle Reader는 Spark AQE의 최적화 기능으로, shuffle 단계에서 데이터를 원격에서 가져오지 않고 로컬 블록을 활용해 읽도록 변환한다. 이를 통해 네트워크 I/O 비용을 줄이고 쿼리 실행 속도를 높일 수 있고, 리소스 사용 효율성도 개선된다. 특히 shuffle이 많은 작업에서 성능 향상 효과가 크다.