---
title: "Claude 5시간 한도, 리셋 시간을 일하는 중간으로 옮기는 법"
description: Slop을 만들다 정오마다 Claude 한도에 걸려서, 출근 전에 5시간 창을 미리 열어 두는 작은 도구 claude-warmup을 만들었어요.
project: claude-warmup
image: https://jungtaejoon.github.io/claude-warmup/og.png
---

[Slop](https://jungtaejoon.github.io/slop/)을 Claude Code로 만들면서 거의 매일 같은 장면을 봤어요. 오전 내내 열심히 작업하다가 정오쯤 "한도 도달, 14:00에 리셋". 가장 손이 잘 풀리는 시간에 두 시간을 기다려야 했죠. 그래서 리셋이 어떻게 정해지는지 찾아보고, 작은 도구를 하나 만들었어요.

## 리셋은 첫 메시지로부터 5시간 뒤

Claude Pro·Max의 세션 한도는 시계 기준이 아니라 **창의 첫 메시지로부터 5시간**이에요([공식 도움말](https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work)). 9시에 처음 물어보면 14시에 리셋돼요. 웹, 앱, Claude Code가 이 한도를 같이 쓰고, 주간 한도는 이와 별도예요.

내 리셋 시각은 Claude Code에서 `/usage`를 치면 바로 보여요. 이 명령은 로컬에서 돌아서 토큰을 쓰지 않아요.

## 창을 미리 열면 리셋이 앞당겨져요

9시에 일을 시작한다면 6시에 짧은 메시지 하나를 보내 두면 돼요.

| 시간 | 창 |
| --- | --- |
| 6시~11시 | 첫 창 (실제로는 9~11시만 써요) |
| 11시 | 새 창. 오전 작업으로 한도에 걸릴 즈음이에요 |
| 16시 | 또 새 창 |

한도가 늘어나지는 않아요. 기다리는 시간이 집중이 잘 되는 시간에서 빠질 뿐이에요.

## 자동으로 하기: claude-warmup

매일 6시에 일어나서 메시지를 보낼 수는 없으니 [claude-warmup](https://jungtaejoon.github.io/claude-warmup/ko/)을 만들었어요.

- 5분마다 `/usage`로 확인하고(토큰 0), **열린 창이 없을 때만** haiku에 "hi"를 보내요.
- 내 컴퓨터나 내 서버에서 돌고, 로그인 정보는 읽지 않아요. 토큰을 다른 서비스에 맡길 필요가 없어요.
- 터미널에서 세션·주간 사용량과 리셋 시각을 보여 줘요.
- macOS·Linux·Windows에서 돌아가요. 맥이 꺼져 있을 때를 위해 무료 서버에 설치하는 스크립트도 있어요.

```bash
npm install -g github:jungtaejoon/claude-warmup
claude-warmup install
claude-warmup config hours 06:00-23:00
```

저는 Oracle Cloud 무료 서버에 올려 두고 써요. 맥을 꺼 둬도 매일 아침 6시에 창이 열리고, 11시와 16시에 리셋이 와요.

더 자세한 원리와 확인 방법은 [Claude 사용량 한도 리셋 가이드](https://jungtaejoon.github.io/claude-warmup/ko/claude-usage-limit-reset/)에 정리해 뒀어요. 코드는 [GitHub](https://github.com/jungtaejoon/claude-warmup)에 있어요.
