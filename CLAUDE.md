# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```sh
npm run dev      # Start dev server at localhost:4321
npm run build    # Build production site to ./dist/
npm run preview  # Preview production build locally
```

## Architecture

This is an **Astro 5 blog** using the Content Collections API with static site generation.

- **Content Collections**: Blog posts live in `src/content/blog/` as `.md` or `.mdx` files. Schema defined in `src/content.config.ts`.
- **heroImage**: String URL (Unsplash direct URL). Not a local file — the schema uses `z.string().optional()`.
- **Routing**: `src/pages/blog/[...slug].astro` uses `getStaticPaths()` with `getCollection('blog')`. Slug = file path relative to `src/content/blog/`.
- **Layouts**: `src/layouts/BlogPost.astro` is the single layout for all blog posts.
- **Global config**: `src/consts.ts` exports `SITE_TITLE` and `SITE_DESCRIPTION`. Update `astro.config.mjs` `site` URL before deploying.
- **Integrations**: MDX, sitemap (`/sitemap-index.xml`), RSS (`/rss.xml`).

---

## 블로그 운영 규칙

### 블로그 정체성
- **테마**: 테크 & 바이브코딩 전문 컨텐츠 크리에이터
- **목표**: 검색 트래픽 기반 수익화 (Google AdSense, 제휴 마케팅)
- **독자층**: 개발자, 취업 준비생, AI 툴 관심자, 사이드프로젝트 빌더

### "새 글 작성" 트리거
사용자가 **"새 글 작성"** (또는 "글 써줘", "포스트 작성" 등)이라고 하면:
1. 이전 포스트와 다른 새로운 주제/앵글 자동 선택
2. `src/content/blog/` 에 `.md` 파일 생성
3. 아래 **글 작성 규칙**을 전부 적용

### 글 작성 규칙
- **분량**: 최소 5000자 (한국어 기준), 내용이 충분히 깊어야 함
- **어조**: AI 느낌 나지 않게 — 개인적인 경험담 섞기, 구어체와 문어체 혼용, 솔직한 감정·의견 표현, 완벽한 문장보다 자연스러운 흐름 우선
- **이미지**: Unsplash 직접 URL 사용, 포스트 본문에 최소 1개 삽입
  - 형식: `![설명](https://images.unsplash.com/photo-XXXXXXX?w=1200&q=80)`
  - `heroImage` frontmatter에도 Unsplash URL 사용
- **SEO**: 제목에 핵심 키워드 포함, `description` 100~150자, 본문 H2/H3으로 명확한 구조화, 첫 문단에 핵심 키워드 자연스럽게 포함
- **각 글의 의도**: 매번 다른 앵글 사용 (아래 주제 풀 참고)

### Frontmatter 형식
```yaml
---
title: 'SEO 키워드가 담긴 제목 (60자 이내)'
description: '검색 스니펫용 설명 — 핵심 키워드 포함, 100~150자'
pubDate: 'YYYY-MM-DD'
heroImage: 'https://images.unsplash.com/photo-XXXXXXX?w=1200&q=80'
---
```

### 파일명 규칙
- 영문 slug, 하이픈 구분: `vibe-coding-guide.md`, `cursor-ai-review-2025.md`

### 주제 풀 (순환하며 사용, 반복 금지)
1. **AI 코딩 툴 실전 리뷰** — Cursor, Claude Code, GitHub Copilot, Windsurf 등
2. **바이브코딩 경험담** — 프롬프트로 앱 만든 실제 과정, 막혔던 순간, 해결법
3. **개발자 생산성** — 워크플로우, 단축키, 툴 조합, 자동화
4. **사이드프로젝트 빌드 로그** — 아이디어부터 배포까지
5. **테크 트렌드 분석** — AI 에이전트, MCP, LLM 트렌드
6. **취업·이직 개발자 이야기** — 포트폴리오, 기술 스택 선택
7. **오픈소스 & 커뮤니티** — 유용한 라이브러리, GitHub 발굴
8. **비교글** — A vs B, 어떤 툴이 진짜 나은가?
9. **초보자 가이드** — "처음 해봤는데 이게 되네" 시리즈
10. **돈 되는 개발** — 프리랜서, 수익화, SaaS 아이디어

### 좋은 Unsplash 이미지 ID (주제별)
- 코딩/개발: `photo-1555066931-4365d14bab8c`, `photo-1517694712202-14dd9538aa97`
- AI/미래: `photo-1677442135703-1787eea5ce01`, `photo-1620712943543-bcc4688e7485`
- 생산성/작업: `photo-1499750310107-5fef28a66643`, `photo-1484480974693-6ca0a78fb36b`
- 트렌드/분석: `photo-1551288049-bebda4e38f71`, `photo-1460925895917-afdab827c52f`
- 사람/커뮤니티: `photo-1522202176988-66273c2fd55f`, `photo-1531482615713-2afd69097998`
