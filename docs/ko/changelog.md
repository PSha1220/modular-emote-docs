# 변경 내역

## 1.3.2

### 추가

- 병합 ME FX 사용 시 **오브젝트 이름 자동 변환(Auto Rename Object)** 기능을 추가했습니다.
- 빌드 시 사용할 이름을 직접 지정할 수 있는 **오브젝트 이름(Object Name)** 항목을 추가했습니다.

### 변경

- **Auto Rename Object Name** 표기를 **Auto Rename Object**로 변경했습니다.
- 아래 항목에 대해 에디터 언어 연동 번역을 추가했습니다.
  - **Auto Rename Object**
  - **Object Name**
- **Auto Rename Object**는 이제 **병합 ME FX 사용**이 켜져 있을 때만 표시됩니다.
- **Object Name** 입력란은 관련 옵션이 활성화된 경우에만 표시되도록 정리했습니다.
- VRChat SDK를 불필요하게 다운그레이드하지 않도록 VPM 패키지 의존성 범위를 조정했습니다.
- **Psha-VPM-Repository**를 통해 최신 버전을 설치할 수 있도록 레포지토리/리스팅 배포 구성을 정리했습니다.

### 개선

- **이름 불일치 경고** 표시 조건을 개선했습니다.
- **Setup VRC Emote** 실행 시 `<br>`, 줄바꿈, `<color>` 같은 표시용 태그를 제거한 뒤 오브젝트 이름에 적용하도록 개선했습니다.

### 수정

- 아래 항목과 관련된 컴파일 문제를 수정했습니다.
  - `autoRenameObjectName`
  - `objectName`
  - `GetResolvedBuildObjectName`
- 기존 프리팹 및 씬 인스턴스에서도 새 옵션이 정상 동작하도록 초기화/마이그레이션 처리를 보강했습니다.

### 유지보수

- 일반적인 릴리즈 및 배포 유지보수를 진행했습니다.
