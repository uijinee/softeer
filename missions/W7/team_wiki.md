# Optimize Local Shuffle Reader가 하는 역할

Optimize Local Shuffle Reader는 Spark AQE의 최적화 기능으로, shuffle 단계에서 데이터를 원격에서 가져오지 않고 로컬 블록을 활용해 읽도록 변환한다. 이를 통해 네트워크 I/O 비용을 줄이고 쿼리 실행 속도를 높일 수 있고, 리소스 사용 효율성도 개선된다. 특히 shuffle이 많은 작업에서 성능 향상 효과가 크다.