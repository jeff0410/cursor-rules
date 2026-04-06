# curwor-rules

Cursor 에이전트용 **프로젝트 규칙**(`.mdc`) 모음입니다. TypeScript·React·Next.js·Tailwind 위주의 프론트엔드 작업 시 일관된 답변과 코드 스타일을 맞추기 위해 사용합니다.

## 구성

규칙 파일은 `frontend/` 아래 주제별 디렉터리에 있습니다.

| 경로 | 적용 방식 | 설명 |
|------|-----------|------|
| [frontend/common.mdc](frontend/common.mdc) | 항상 적용 | 응답 언어, TypeScript 관례, 네이밍, 주석 금지, 불확실 시 표현 방식 등 공통 원칙 |
| [frontend/styling/tailwind-no-styled-components.mdc](frontend/styling/tailwind-no-styled-components.mdc) | 항상 적용 | Tailwind만 사용, styled-components 신규 금지 및 기존 코드 수정 시 절차 |
| [frontend/react/react-hooks.mdc](frontend/react/react-hooks.mdc) | 항상 적용 | 소스 파일명 케밥케이스, 커스텀 훅 파일 분리·네이밍 |
| [frontend/react/tsx-component-exports.mdc](frontend/react/tsx-component-exports.mdc) | `**/*.tsx` | React 컴포넌트는 `export function` 선언문으로 export |
| [frontend/react/react-lists-and-structure.mdc](frontend/react/react-lists-and-structure.mdc) | `**/*.tsx` | 리스트 `key`, 중첩 컴포넌트 선언 금지, 조건부 렌더 |
| [frontend/react/react-effects.mdc](frontend/react/react-effects.mdc) | `**/*.{ts,tsx}` | `useEffect` 의존성·cleanup, 파생 상태·비동기 |
| [frontend/react/react-accessibility.mdc](frontend/react/react-accessibility.mdc) | `**/*.tsx` | 버튼·링크·레이블·이미지 `alt`, `button`/`a`에 `cursor-pointer` |
| [frontend/typescript/typescript-exports.mdc](frontend/typescript/typescript-exports.mdc) | `**/*.ts` | `.ts`에서 함수·훅 export는 `export const` 화살표 함수 |
| [frontend/typescript/typescript-unions-and-narrowing.mdc](frontend/typescript/typescript-unions-and-narrowing.mdc) | `**/*.{ts,tsx}` | 판별 유니온, `never` exhaustiveness, `enum` 지양, 단언 최소화 |
| [frontend/typescript/typescript-nullish.mdc](frontend/typescript/typescript-nullish.mdc) | `**/*.{ts,tsx}` | `??`·optional chaining, null/undefined 통일 |
| [frontend/nextjs/nextjs-app-router.mdc](frontend/nextjs/nextjs-app-router.mdc) | `**/app/**/*.{ts,tsx}` | 서버 컴포넌트 기본, `use client`, 서버 데이터 패칭, App Router·성능·에러 처리 |

`alwaysApply: true`인 규칙은 편집 중인 파일과 관계없이 컨텍스트에 포함되기 쉽고, `globs`가 있는 규칙은 해당 패턴에 맞는 파일을 다룰 때 위주로 적용됩니다.

## 사용 방법

1. 이 저장소를 클론하거나 서브모듈로 가져옵니다.
2. 사용할 `.mdc` 파일을 **대상 프로젝트**의 Cursor 규칙 디렉터리로 복사합니다. 일반적으로 프로젝트 루트의 `.cursor/rules/` 아래에 둡니다.
3. 프로젝트에 맞지 않는 규칙(예: Next.js를 쓰지 않는다면 `frontend/nextjs/`)은 복사 대상에서 제외해도 됩니다.

규칙을 통째로 공유하려면 `frontend` 전체를 `.cursor/rules/`로 복사하거나, 심볼릭 링크로 연결할 수 있습니다. 팀·CI 정책에 맞게 한 곳만 소스로 두고 배포하는 방식을 권장합니다.

## `.mdc` 메타데이터 요약

- **`alwaysApply: true`**: 해당 규칙을 항상 에이전트에 반영하고 싶을 때.
- **`globs`**: 특정 경로·확장자에서만 쓰고 싶을 때 (Cursor가 지원하는 패턴).
- **`description`**: 규칙 목록·검색 시 보이는 한 줄 설명.

## 기여·변경

새 규칙을 추가할 때는 기존 파일과 동일하게 YAML 프론트매터를 맞추고, 중복되는 내용은 `common.mdc`와 통합할지 여부를 한 번 검토하면 좋습니다.
