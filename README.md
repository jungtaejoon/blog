# Slop 로그

https://jungtaejoon.github.io/blog/

AI 결과물 판정 커뮤니티 [Slop](https://slop.ai.kr/)을 만들며 쓰는 블로그예요. 곁가지 프로젝트([claude-warmup](https://github.com/jungtaejoon/claude-warmup)) 글도 함께 있어요.
GitHub Pages가 Jekyll로 자동으로 만들어 줘서, 따로 빌드할 필요가 없어요.

## 두 언어

- 한국어 글은 `_posts/`, 영어 글은 `en/_posts/`에 넣어요. 영어 글 주소는 `/blog/en/...`가 돼요.
- 같은 글의 두 언어판은 머리말의 `ref` 값을 똑같이 맞춰요. 그러면 글 위의 언어 버튼과 검색엔진용 hreflang이 서로를 가리켜요.
- 처음 온 방문자는 브라우저 언어(한국어면 한국어, 아니면 영어)에 맞는 판으로 자동으로 옮겨져요. 언어 버튼을 누르면 그 선택을 기억해요. 검색 로봇은 옮기지 않아요.
- 한쪽 언어만 써도 돼요. 그때는 언어 버튼이 그 언어의 첫 화면으로 가요.

## 새 글 쓰기

1. `_posts/` 폴더에 `YYYY-MM-DD-영문-주소.md` 이름으로 파일을 만들어요. 예: `_posts/2026-11-12-first-gems.md`
   - GitHub 웹에서는 `_posts` 폴더 → **Add file → Create new file**. 휴대폰 GitHub 앱이나 브라우저에서도 돼요.
2. 맨 위에 머리말을 붙여요. `_templates/post.md`를 복사하면 편해요.

   ```yaml
   ---
   title: "글 제목"
   description: 목록과 검색 결과에 나오는 한두 문장 요약.
   project: slop          # slop(메인) 또는 claude-warmup(곁가지)
   ---
   ```
3. 그 아래에 마크다운으로 본문을 쓰고 커밋하면, 1~2분 뒤 블로그에 올라가요.

- 이미지는 `assets/img/`에 올리고 `![설명](/blog/assets/img/파일.png)`로 넣어요.
- 날짜를 미래로 쓰면 그날이 되기 전에는 보이지 않아요.
- 새 곁가지 프로젝트를 추가하려면 `_config.yml`의 `projects`에 항목을 넣고, `claude-warmup/index.md`처럼 목록 페이지를 하나 만들어요.

## 내 컴퓨터에서 미리 보기 (선택)

```bash
bundle install
bundle exec jekyll serve
```
