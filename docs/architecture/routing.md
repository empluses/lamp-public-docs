# URI Chain과 서비스 연결

## 라우팅 개념

서비스 경로는 다음과 같이 표현할 수 있습니다.

```text
/clientGateway/risk/check/TRCODE
```

위 문자열은 이해를 위한 **가상 예제**입니다. 실제 서비스명이나 공개 API 엔드포인트를 나타내지 않습니다. 라우팅은 URI의 서비스 세그먼트와 현재 Hop 위치를 보고 결정합니다.

- **Intermediate:** 다음 Supplier로 전달. `IChainHook`으로 전달 전과 회신 통과 시 공통 처리를 확장할 수 있습니다.
- **Terminal:** 최종 트랜잭션을 실행. `IRequestInterceptor`로 전후 처리를 확장할 수 있습니다.
- **Reply:** 전달 시 생성한 회신 문맥을 통해 역방향으로 돌아옵니다.

하나의 서비스는 URI에 따라 Intermediate 또는 Terminal이 될 수 있습니다. 이를 별도 서버 종류로 이해하지 않습니다.

## 설계상 장점과 주의점

서비스 연결 경로를 명시적으로 파악할 수 있고 중간 단계에서 캐시, 인증 또는 데이터 변환 기능을 구성할 수 있습니다. 반면 인증 문맥이 서비스 간 전달될 때의 책임, Hop별 제한, 타임아웃 및 실패 전파는 별도 설계가 필요합니다.

[서비스 개발 안내](../developer/service-development.md)
