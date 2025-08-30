# English for IT (Jekyll + Netlify)

이 저장소는 기술 영어 학습 가이드를 정적 사이트(Jekyll)로 배포하기 위한 구조입니다.

## 구조
```
Gemfile
_config.yml
netlify.toml
index.md                # 랜딩 페이지
00. 개요.md             # 각 글 (YAML front matter 포함)
01. 당신의 당신의 문제를 스스로 만든다.md
02. 번역기의 배신.md
... (계속)
_layouts/
_includes/
assets/css/style.css
```

## 로컬 개발
Prerequisite: Ruby (>=3.1) & Bundler

```powershell
# 의존성 설치
bundle install

# 개발 서버 실행
bundle exec jekyll serve --livereload
# 브라우저에서 http://127.0.0.1:4000 확인
```

## Netlify 배포
1. Netlify에서 New site from Git
2. 저장소 선택
3. Build command: `bundle exec jekyll build`
4. Publish directory: `_site`
5. 환경변수 (자동 설정됨): `JEKYLL_ENV=production`

`netlify.toml` 에 설정이 포함되어 있어 추가 설정 없이 배포됩니다.

### (선택) minima 테마 사용하고 싶다면?
현재 `_config.yml` 에서 `theme: minima` 를 제거하여 커스텀 레이아웃(`_layouts/default.html`)만 사용합니다. 만약 minima 기반으로 가고 싶다면:

1. Gemfile 최상단에 아래 추가:
	```ruby
	gem "minima", "~> 2.5"
	```
2. `_config.yml` 에 `theme: minima` 다시 추가
3. 필요시 `_includes/nav.html` / `_layouts/default.html` 수정 또는 삭제 (minima의 기본 레이아웃 사용)
4. `bundle install` 후 다시 배포

테마를 잇는 대신 현재 방식은 불필요한 의존성을 줄여 빌드 속도를 약간 단축합니다.

## 중복 파일 관련
`01.` 챕터 파일이 두 개 존재했으나 (`01. 당신의 당신의 문제를 스스로 만든다.md` / 오타 변형) 현재 `01. 당신의 당신의 문제를 스스로 만든다.md` 파일을 canonical 로 간주합니다. 다른 변형은 필요시 삭제하거나 redirect 구성을 할 수 있습니다.

## 향후 개선 아이디어
- 다국어(i18n) 지원 (영문 번역 추가)
- 검색 기능 (lunr.js)
- RSS feed (`jekyll-feed` 플러그인)
- Sitemap (`jekyll-sitemap`)

## 라이선스
MIT
