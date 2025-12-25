<figure markdown>
  ![Hero](images/hero.png){ width="720" }
</figure>

# Modular Emote

**Modular Emote**는 애니메이션을 쉽게 아바타에 도입하기 위한 방법에서 고안한  
VRChat SDK3 Avatar용 **NDMF 기반 Non-destructive 애니메이션 패치 도구**입니다.

## 특징

- **원본 AnimatorController 애셋을 수정하지 않고**,  
  NDMF의 **VirtualAnimatorController 레벨에서만** 그래프를 병합합니다.
- **비파괴(Non-destructive)** 원칙을 지켜, 원본 메뉴/컨트롤러 애셋을 직접 변경하지 않습니다.
- 빌드 파이프라인(NDMF)에서 **가상 컨트롤러를 수정**해 최종 결과만 반영합니다.
