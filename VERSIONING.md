# 공개 문서 버전·Git 태그 정책

## 최초 릴리스

- 문서 버전: **1.0-rc1**
- Git 태그 이름: **`1.0-rc1`** (접두사 `v` 없음)
- 문서 작성 기준일: **2026-11-20**
- 상태: 공개 검수용 Release Candidate. GA 아님

문서 버전은 LAMP Core, LAMP Financial, 고객사 구성요소의 개별 소프트웨어 버전과 **독립적으로 관리**합니다.

## 관리 규칙

1. **main**: 승인된 최신 문서. `feature/*` 브랜치에서 PR을 열어 검토하고 병합.
2. **릴리스 후보**: `1.0-rc1` → `1.0-rc2`처럼 동일 범위의 정확성·공개성·링크 수정.
3. **정식 공개**: 승인 후 `1.0.0` 태그, 릴리스 노트, 문서 사이트 배포. 자동으로 GA 전환하지 않음.
4. **패치**: 공개 문서의 오류 및 표현 수정은 `1.0.1` 등 패치 버전.
5. **내용 추가**: 상위 사용자 기능 설명이나 개발 API 계약 변경 시 minor/major 고려.
6. **태그는 변경하지 않음**: 공개 후 태그를 강제 이동하지 않고 새 버전을 발행.

## 변경 기록과 추적성

각 문서 릴리스의 `CHANGELOG.md`에 변경 요약을 기록합니다. 내부 추적 레코드에는 문서 태그, 기준 `lamp`/`lamp-fin`/`lamp-workspace` SHA, 검토자, 공개 승인자, 테스트 근거를 남깁니다. 원본 SHA 및 민감한 내부 관리 정보를 공개하는 것이 적절한지는 별도로 심사합니다.

## 배포 절차

```bash
# GitHub에서 empluses/lamp-public-docs 빈 저장소 생성 후
# 준비된 로컬 Git 저장소에서 실행:
git remote add origin https://github.com/empluses/lamp-public-docs.git
git push -u origin main
git push origin 1.0-rc1
```

GitHub Pages 또는 별도 문서 도메인 배포는 공개 승인 이후 별도 설정합니다. 태그가 존재하는 것만으로 문서 사이트가 공개되는 것은 아닙니다.
