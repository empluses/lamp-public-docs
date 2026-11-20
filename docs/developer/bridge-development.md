# Bridge 서비스 개발 원칙 (설계 초안)

> **Planned:** 현 시점에 개발자가 사용할 수 있는 MQTT/BLE Bridge SDK, 함수 서명 또는 공개 예제를 보증하지 않습니다. 아래는 구현 전에 합의할 개발 계약입니다.

## 서비스 경계

Bridge는 외부 프로토콜 연결 및 어댑터의 수명을 관리하는 독립 서비스입니다. LAMP Core는 기존 요청 처리·라우팅·플러그인 실행·운영 모델을 유지합니다. 서비스 경계와 배포 단위는 실제 부하 및 Edge 환경을 검토 후 확정합니다.

## 권장 작업 흐름

1. 프로토콜과 역할 결정: MQTT Subscriber/Publisher, BLE Central 등의 요구를 명세합니다.
2. 장치 식별자, 이벤트 타입, 버전, 메시지 최대 크기와 오류 코드를 정의합니다.
3. 입력 이벤트를 검증하고 공통 계약으로 정규화하는 Mapper를 설계합니다.
4. LAMP 라우팅/서비스 Hook과 연결하는 경계를 정의합니다. 기존 코어 API를 검토하기 전 임의의 함수 서명을 공개하지 않습니다.
5. 인증·인가·비밀정보 격리, 재접속·백프레셔·버퍼 상한을 정의합니다.
6. 중복 이벤트, 역순 도착, 부분 장애, 재기동 이후 복구를 시험합니다.
7. 모의 Broker/가상 장치와 실제 Edge 하드웨어의 결과를 구분해 기록합니다.

## 프로토콜별 체크리스트

| 항목 | MQTT Bridge | BLE Bridge |
|---|---|---|
| 연결 | Broker TLS, 세션 재접속 | Adapter/GATT 연결, 페어링 |
| 데이터 | Topic·QoS·Payload 매핑 | Service/Characteristic·Notification 매핑 |
| 흐름 제어 | 수신 burst, QoS ACK, 재전송 | MTU·notification rate, 연결 끊김 |
| 보안 | Broker credential 분리, ACL | Device identity, bonding/권한 |
| 검증 | 중복/재구독/retained | 장치 검색/재연결/권한 회복 |

**금지할 주장:** LAMP Core가 이미 MQTT/BLE를 지원한다거나, 프로토콜 수준의 전달 보장이 LAMP 전체의 end-to-end 무손실 처리 보장을 의미한다는 주장.

[설계 아키텍처](../architecture/protocol-bridges.md)
