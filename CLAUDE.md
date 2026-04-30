# CLAUDE.md — NeuralTactics

이 파일은 Claude가 매 대화에서 자동으로 참고하는 프로젝트 가이드다.

## 프로젝트 문서

- [NeuralTactics.md](NeuralTactics.md) — 프로젝트 전체 설계, AI 아키텍처, 학습 파이프라인, 구현 순서

## 프로젝트 한 줄 요약

Python으로 전술 전투 시뮬레이션을 구현하고, EGNN 기반 Soldier AI와 Commander AI를 모방 학습 → 유전 알고리즘 + 강화학습 순으로 훈련하는 기술 검증 프로젝트.

## 코드 구조 원칙

```
NeuralTactics/
├── common/        # 공용 유틸리티, 데이터 구조, 설정
├── neural/        # 신경망 (모델, 학습, 추론) — game 레이어에 의존하지 않음
└── game/
    ├── core/      # 게임 규칙·엔티티 — 엔진 종속성 없음
    ├── simulation/ # 순수 계산, 렌더링 없음
    └── interface/ # Pygame 시각화, 입력 — 플래그로 on/off 가능
```

- `game/` 레이어는 추후 언리얼 엔진 등 상용 엔진으로 교체 가능하도록 설계
- `neural/`은 표준 텐서/배열 인터페이스만 사용, 게임 레이어와 분리 유지
- Pygame 인터페이스는 항상 비활성화 가능하도록 구현

## 현재 구현 단계

구현 순서 1단계: 게임 기획 및 기본 게임 환경 구현 중

## 코드 스타일

- **줄바꿈:** CRLF (`\r\n`) — LF 사용 금지

## 주요 기술 결정

- **신경망:** EGNN (이동·회피) + CNN/MLP (스킬·진형 판단) Hybrid
- **학습:** Behavioral Cloning (Phase 1) → Genetic Algorithm + RL (Phase 2)
- **시각화:** Pygame (선택적)
- **언리얼 연동:** 현재 범위 밖 — 향후 확장 계획
