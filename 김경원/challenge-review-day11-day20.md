# 지난 10일 나의 목표는?!
- [x] 폭염 속에서 잘 살아남아 매일 1 commit 달성
- [x] 게임 로직 구현 (기반은 다 다졌으니 이제 재미난거 해보자)

# 10일 돌아보면 잘한 점
- 폭염과 출근 속에서 살아남아 매일 커밋을 해냈다.
- 머릿속에 그리고 있던 기본 기능들을 구현하는 방법을 거의 다 학습했다.
- 단순히 기능을 완성하는 데에서 그치지 않고 최적화 면에서 더 좋은 방법을 계속 모색하며 만들었다. 배운 게 많았다.

# 10일 돌아보며 아쉬운 점
- 매일매일 커밋 성공 하는데에만 포커스를 두느라 실제 작업량은 많지 않았다. 잔디 색깔이 저번 10일에 비해 맹탕이다.
- 목표한 기능을 모두 구현하지는 못했다.

# 10일 동안 공부한 내용
현재 진행 프로젝트: WinAPI로 지뢰찾기 만들기
실제 목표: C++ 공부

- WinAPI 
  - 펜, 브러쉬를 교체해가며 그래픽 요소 그리기 (모양, 텍스트 등)
    - CreateSolidBrush, CreatePen, CreateFont 등의 함수로 브러쉬 생성
    - SelectBrush() 함수의 인자로 생성한 브러쉬를 전달해서 선택하기
    - SelectBrush를 호출하면 현재 사용하는 브러쉬를 반환하므로 기존에 사용하던 브러쉬 백업이 필요하면 활용하기
    - 다 사용한 브러쉬는 DeleteObject()로 해제해주기

- C++
  - 포인터, 참조 타입을 매개변수로 쓰기 좋을 때
    - 포인터 타입
      - NULL로 초기화가 필요할 때
      - 동적 메모리 관리가 필요할 때
      - 상속 관계 등 다형성을 활용할 때
    - 참조 타입
      - 값 복사를 방지하고 싶을 때 (STL 컨테이너 등 크기가 큰 값 주고받을 때 쓰기 좋음)
      - 전달 받은 값을 함수 내에서 직접 변경하고 싶을 때

  - STL활용: vector 컨테이너 멋지게 사용하기
    - 벡터가 현재 가지고 있는 값의 양과 실제 용량은 다른 값이다. 전자는 size(), 후자는 capacity()
    - reserve()로 용량을 미리 정의해두고 값을 넣으면 성능을 개선시킬 수 있음 (물론 용량이 딱 정해졌을 때만)
    - clear(), resize(): size는 0이 되지만 capacity는 그대로
    - swap(): capacity도 바꿀 수 있다.

  - STL활용: 난수 멋지게 생성하기
    - std::uniform_int_distribution 으로 균등 분포 난수 생성
    - 생성한 난수를 unordered_set에 넣어주며 중복 난수를 방지하기

  - const 활용:
    - 클래스 멤버 함수 뒤에 붙이기: 해당 함수 내에서 클래스 멤버를 수정하지 않겠다고 보장
    - 매개변수로 사용하기: 전달받은 값을 함수 내에서 수정하지 않겠다고 보장 
    적절한 const 사용으로 개발자의 의도를 파악하기 쉬운 코드를 작성할 수 있다.
  
# 앞으로 10일 동안 나의 목표는?!
- [ ] 지뢰는 다 뿌렸으니 찾기를 본격적으로 시작하기
- [ ] 하루 내에 작업이 완료되는 보장이 없더라도 복잡한 작업 무작정 시도해보기