# Modular Emote Transition Settings

`ModularEmoteTransitionSettings`는 **ME Action 템플릿**에서  
“StartState → 템플릿 엔트리” 구간의 전이(Transition) 설정을 **빌드 시점에 재구성**하기 위한 `StateMachineBehaviour`입니다.

ME Action 템플릿의 특정 스테이트(예: `[ME] StartState Transition Settings`)에 이 Behaviour를 붙여두면,
Pass가 이를 감지해 **Exit Time / Duration / Offset / Interruption / 추가 조건**을
Behaviour의 값 기준으로 다시 구성합니다.

---

## 사용 방법(요약)

1. ME Action 템플릿의 “전이 설정용 스테이트”에 `ModularEmoteTransitionSettings`를 추가합니다.
2. 아래 **Transition Settings** 값을 원하는 규칙으로 설정합니다.
3. 필요하면 **Additional Conditions**에 추가 필터 조건을 넣습니다.

> 참고  
> `VRCEmote == slotIndex` 조건은 시스템이 자동으로 처리합니다.  
> 따라서 Additional Conditions에는 “추가로 걸고 싶은 조건”만 넣는 용도로 사용하세요.

---

## Transition Settings

- **Interruption Source**  
  인터럽트(중단) 판정의 기준이 되는 쪽을 지정합니다.  
  `None / Source / Destination / SourceThenDestination / DestinationThenSource`

- **Has Exit Time**  
  활성화하면 Exit Time(0~1)을 사용합니다.

- **Exit Time (0~1)**  
  Has Exit Time이 켜져 있을 때 적용되는 종료 시점(정규화 값)입니다.

- **Transition Duration**  
  전이 지속 시간입니다.  
  `Fixed Duration` 설정에 따라 “초” 또는 “정규화 시간”으로 해석됩니다.

- **Transition Offset (0~1)**  
  대상 애니메이션의 시작 오프셋(정규화 값)입니다.

- **Fixed Duration**  
  켜져 있으면 Transition Duration을 **초 단위**로 해석합니다.  
  꺼져 있으면 **정규화 시간(Normalized)** 으로 해석합니다.

- **Ordered Interruption**  
  인터럽트 평가 순서를 보장할지 여부입니다.

---

## Additional Conditions

`conditions`는 전이에 추가로 붙일 **추가 조건 배열**입니다.

- 기본 `VRCEmote == slotIndex` 조건은 자동 처리됩니다.
- 여기에는 예를 들어 `IsSeated`, 커스텀 모드 파라미터 등 **추가 필터**만 넣는 것을 권장합니다.

### 지원 타입

- Bool
- Int
- Float
- Trigger

### Int/Float 비교 모드

- Greater
- Equal
- Less
- NotEqual

---

## 참조 사이트

- <a href="https://docs.unity3d.com/Manual/class-Transition.html" target="_blank" rel="noopener noreferrer">Unity Doc (Animation transitions) </a>