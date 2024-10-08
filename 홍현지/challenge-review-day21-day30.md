# 지난 10일 나의 목표는?!
- [ ] 매일 1 commit 달성
- [ ] 알고리즘 문제 2문제 풀기
- [ ] CUDA 4장 진도 완료하기

# 10일 돌아보면 잘한 점
- 개강하면 많이 놓칠 줄 알았는데 다행히 생각보다 잘 참여했다
- CUDA 진도를 많이 나갔다

# 10일 돌아보며 아쉬운 점
- 커밋을 놓친 날이 있었다
- 알고리즘 문제를 1문제 밖에 풀지못했다

# 10일 동안 공부한 내용
- 스레드 인덱싱의 필요성
 - 스레드 레이아웃 설정으로 1024번째 계산까지는 올바르게 계산되지만 1025번째부터 올바르게 이루어지지 못한다
 => 1024개가 한 개의 블록이 가질 수 있는 최대 스레드 수다
 - 인덱싱을 올바르게 하지 않으면 한 블록 이상으로는 잘못된 인덱싱이 이루어지기 때문에 각 스레드가 속한 블록 번호를 고려해 담당한 데이터 번호를 지정해야한다
 => 스레드 인덱싱
 - 스레드 레이아웃 시 사용되지 않는 위치는 불필요한 계산이 이루어지지 않도록 예외처리를 한다 
- 스레드 레이아웃과 인덱싱
  - 메모리 속 배열은 벡터의 형태로 저장되므로 이러한 형태를 고려하여 인덱싱을 해주면 된다
  - 스레드의 전역 번호(스레드마다 하나의 데이터를 담당하는 경우)를 만들어 해당 위치를 계산하는 방식이 있다
    - 이러한 방식은 1차원 형태의 데이터를 다룰 때 주로 사용된다
  - 2차원 형태의 테이터를 다룰 때에는 스레드 번호 매칭시 X-차원과 y-차원 번호를 행과 열 중 어느 것에 대응할 지 결정해야함
  - 데이터의 형태에 따라 그에 맞는 스레드 레이아웃 및 인덱싱 방안을 고려하여 코드를 구성해야한다
- CUDA 실행모델
  - 엔디비아 GPU 주요 아키텍처 : 스트리밍 프로세서(SM), CUDA 코어
  - 그리드 -> GPU
    - 하나의 그리드는 한 GPU에서 실행된다
  - 스레드 블록 -> SM
    - 스레드 블록을 처리하는 단위는 SM이다
    - 스레드 블록은 SM에 균등하게 분배되어 처리된다
  - 워프 & 스레드 -> SM 속의 CUDA 코어
    - 스레드는 각각 CUDA 코어 하나에서 처리된다
    - 워프는 하나의 명령어에 움직인다
  - 무비용 문맥 교환
    - CPU와는 달리 GPU는 블록 내 스레드들이 SM의 레지스터 파잉을 나누어서 사용하기 때문에 문맥 교환 시 레지스터 값이 유지되어 부하 없이 문맥 교환이 가능하다
  - 워프 분기
    - 스레드들은 독립적으로 움직일 수 있으나 워프들은 한 명령어에 같이 움직이는 것이 제일 효율적이다
    - 이로 인해 분기문이 있을 시 프로그램 성능을 크게 떨어뜨릴 수 있다
  - 메모리 접근 대기 시간 숨기기 전략
    - 메모리 접근 시 코어가 일을 하지 못하므로 GPU는 한 스레드가 메모리를 대기하는 동안 다른 스레드가 CUDA 코어를 사용하게 해 메모리 접근 시간으로 인한 지연을 숨긴다
    - 이러한 특성은 GPU의 무비용 문맥 교환 특성에 의해 가능하다
  - 스레드 수
    - 데이터 접근이 잦은 알고리즘 : 스레드 수를 늘리기
    - 계산 집약적 알고리즘 : 많은 스레드는 악영향을 줄 수 있음
    => 각 상황에 맞추어 스레드 수를 튜닝하는 것이 중요
- CUDA 기반 행렬 곱셈 프로그램
  - 스켈레톤 코드를 제공받고 그 안의 내용을 채워보았다
  - 헷갈리는 개념을 많이 정리할 수 있었다
  

# 앞으로 10일 동안 나의 목표는?!
- [ ] 매일 1 commit 달성
- [ ] 알고리즘 문제 2문제 풀기
- [ ] CUDA 8장까지 진도 완료하기
