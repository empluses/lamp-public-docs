# 구현 근거 및 검증 상태 (RC)

**검토일: 2026-11-20.** GitHub의 README, 아키텍처 문서, 기존 매뉴얼, 소스 파일 및 E2E 테스트 스크립트를 **선별적으로 읽은 결과**입니다. 자체 빌드, E2E 실행, 성능 측정은 수행하지 않았습니다.

| 공개 설명 | 확인한 근거 | 평가 |
|---|---|---|
| Master/Node/Server 구성 | `lamp-core/apps/` 및 아키텍처 문서 | 코드 구조 확인, 실행 검증 미실시 |
| 요청 파이프라인 | `lamp-core/src/server/RequestPipeline.cpp` | 구현 파일 확인 |
| URI Chain Hook | `lamp-core/include/lamp/server/IChainHook.hpp` | 인터페이스 확인 |
| Plugin Loader / ABI | `lamp-core/src/plugin/PluginManager.cpp`, `lamp-core/include/lamp/plugin/PluginAbi.hpp` | 구현·계약 파일 확인 |
| Plugin Reload | `tests/scenarios/25_plugin_hotreload.sh` | E2E 스크립트 확인, 직접 실행하지 않음 |
| 개발자 워크플로 | `docs-site/content/ko/developer/` | 기존 매뉴얼 확인 |
| 금융 확장 계층 | `lamp-fin/README.md`, 주요 디렉터리 | 구조 확인 |
| 성능·SLA | 벤치마크 스크립트 존재 | 공식 측정·보증 자료 미확인 |
| Master HA | 기존 프로젝트 계획 문서 | 버전별 변경 가능, 현재 실행 검증 미실시 |

> **중요:** '구현 파일이 있다', 'E2E 스크립트가 있다', '그 테스트가 통과했다'는 서로 다른 상태입니다. RC 문서는 이 셋을 혼동하지 않습니다.

## 내부 근거 추적 (공개용 파일 경로만)

- `empluses/lamp/README.md`
- `empluses/lamp/docs/spec/LAMP_ARCHITECTURE.md`
- `empluses/lamp/docs/spec/LAMP_PLUGIN_SPEC.md`
- `empluses/lamp/docs-site/content/ko/developer/`
- `empluses/lamp/lamp-core/src/server/RequestPipeline.cpp`
- `empluses/lamp/lamp-core/src/plugin/PluginManager.cpp`
- `empluses/lamp/lamp-core/include/lamp/plugin/PluginAbi.hpp`
- `empluses/lamp/tests/scenarios/25_plugin_hotreload.sh`
- `empluses/lamp-fin/README.md`
- `empluses/lamp-workspace/README.md`

추후 릴리스에는 경로 외에 검증 당시의 소스 커밋 SHA, 테스트 실행 환경과 결과를 기록하도록 합니다. 비공개 저장소의 GitHub 링크가 누구에게나 열릴 것처럼 안내하지 않습니다.
