# IoT·Edge 확장 로드맵 (Planned)

LAMP는 금융 전용 솔루션이 아닌, 실시간 서비스 및 외부 장치 연결을 수용하는 범용 마이크로서비스 플랫폼을 지향합니다. **MQTT와 BLE Bridge는 추가할 예정인 확장 기능이며, 이 문서 작성 시점에 구현·출시·호환성을 검증하지 않았습니다.**

## 활용 구상

- IoT 센서 수집 및 상태 모니터링
- 산업 장치/설비와 중앙 서비스 사이의 이벤트 전달
- Edge에서의 로컬 데이터 처리와 중앙 서비스 연계
- MQTT Broker 및 BLE 장치와 기존 서비스·플러그인의 연동

## 단계적 계획 (순서만 제안, 날짜 약속 아님)

| 단계 | 범위 | 검증 관문 | 상태 |
|---|---|---|---|
| P0 | Bridge 계약, 메시지 매핑, 인증·관측성 정의 | 공개 API/스키마 설계 검토 | Planned |
| P1 | MQTT Bridge 프로토타입 | Topic/QoS, 재접속, 중복/순서 처리 시험 | Planned |
| P2 | BLE Bridge 프로토타입 | GATT, 페어링/권한, 연결·스캔 회복 시험 | Planned |
| P3 | Edge 운영 통합 | 오프라인 버퍼링, 재동기화, 장치 격리, 배포 시험 | Planned |

## 현재 제한

LAMP Core가 MQTT Broker나 BLE 스택을 기본 제공한다고 해석하면 안 됩니다. 장치 인증, 저장 후 재전송, QoS 보장, BLE 게이트웨이 호환성은 설계 및 실증을 거쳐야 합니다.

[Protocol Bridge 아키텍처](../architecture/protocol-bridges.md) · [개발 원칙](../developer/bridge-development.md)
