# 서비스 개발

## 서비스의 책임

서비스 컴포넌트는 네트워크·프로토콜을 직접 재구현하기보다 LAMP 요청 처리 생명주기의 지정된 확장 지점을 사용합니다. 원본 프로젝트는 `runServer()` 실행 구조와 다음 Hook 인터페이스를 문서화하고 있습니다.

| 확장 지점 | 적용 위치 | 대표 용도 |
|---|---|---|
| `IRequestInterceptor` | 최종 요청(Plugin 실행 단계) | 입력 정책, 접근 제어, 통계 |
| `IChainHook` | 중간 서비스/회신 경로 | 캐시, 빠른 응답, 응답 조정 |

```text
Request Arrives
  ├─ Intermediate → onBeforeForward → Supplier → onAfterReply
  └─ Terminal     → onBeforePlugin  → Plugin   → onAfterPlugin
```

## 구현할 때 확인할 항목

- Hook을 호출하는 스레드와 블로킹 제한
- 응답 원문과 변환 본문의 수명주기
- 인증 문맥의 범위와 권한 검증 위치
- 타임아웃 및 실패 전파
- 중복 요청·재시도 정책
- 운영 배포 및 종료 순서

이 RC는 정확한 C++ 메서드 서명과 헤더를 공식 공개 API로 확정하지 않습니다. 승인된 SDK의 버전별 헤더를 기준으로 구현해야 합니다.

[라우팅 구조](../architecture/routing.md)
