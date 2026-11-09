# titanium-calm — omp 티타늄 테마의 눈 편한 버전

[omp](https://github.com/can1357/oh-my-pi) 내장 **titanium** 테마를 그대로 복제하고, 색 몇 개만 눈이 편하도록 바꾼 테마입니다. 티타늄의 상징인 전기 파랑은 그대로 두고, omp 18.18부터 기본으로 켜진 *Colorful Markdown* 기능이 답변 곳곳에 칠하는 **네온 보라(굵은 글씨)·형광 초록(인라인 코드)** 을 차분한 색으로 바꿨습니다. ✓ 성공 표시·명령어 이름 등에 쓰이던 형광 초록도 함께 낮췄습니다.

![변경 전 / 후](screenshots/before-after.png)

## 설치 (3단계)

1. [`themes/titanium-calm.json`](themes/titanium-calm.json) 파일을 omp 테마 폴더 `~/.omp/agent/themes/` 에 넣습니다 (폴더가 없으면 만드세요).
2. omp 설정 → **Appearance → Dark Theme** 에서 `titanium-calm` 을 고릅니다.
3. **Appearance → Display → Colorful Markdown** 이 켜져 있는지 확인합니다 (18.18부터 기본 켬).

끝입니다. 그 외에는 아무것도 바뀌지 않습니다. 티타늄 전체를 복제한 파일이라 단독으로 동작하고, omp가 업데이트돼도 그대로 유지됩니다 (대신 내장 티타늄이 나중에 바뀌어도 따라가지는 않습니다).

## 무엇이 바뀌나

Colorful Markdown은 테마의 16색 터미널 팔레트(`terminal.ansi`)에서 정해진 칸을 꺼내 씁니다 — 굵게·기울임·H1 → 자홍 칸, H2·표 머리글 → 노랑 칸, H3 이하 → 파랑 칸, 인라인 코드 → 초록 칸. 이 테마는 그 칸들과 변수 하나만 바꿉니다.

| 요소 | titanium | titanium-calm |
|---|---|---|
| **굵은 글씨**, *기울임*, 큰 제목(H1) | `#d06fed` 네온 보라 | `#e5c68e` 은은한 금빛 |
| 인라인 `코드` | `#00ff88` 형광 초록 | `#8edab9` 민트 |
| 중간 제목(H2), 표 머리글 | `#f0c040` 노랑 | `#00b4ff` 전기 파랑 (= 강조색) |
| 작은 제목(H3 이하) | `#00b4ff` | `#00b4ff` (그대로) |
| ✓ 성공 표시, 수정 카드의 추가된 줄, 명령어 이름, git 상태 등 7곳 (`readoutGreen` 변수) | `#00ff88` | `#7ad689` |

목록 번호·링크·테두리·상태 표시줄 등 나머지는 전부 티타늄 그대로입니다.

## 왜 이 값인가

OKLCH(사람 눈 기준으로 밝기·채도·색상을 나타내는 색 체계)로 맞췄습니다.

- **밝기를 본문 글자에 맞춤** (L ≈ 0.84). 강조는 "색이 다른 본문"으로 읽혀야지, 더 밝거나 어두운 글자가 되면 안 됩니다 — 눈을 피로하게 하는 건 밝기 차이입니다.
- **채도는 강조색의 절반 이하.** 전기 파랑(채도 0.16)만 "구조"를 나타내는 색으로 남기고(제목·번호·링크), 굵은 글씨(0.08)와 코드(0.09)는 그 아래에 둡니다. 위계가 *파랑 구조 › 금빛 강조 › 민트 코드 › 본문* 순으로 읽힙니다. 원래의 보라(0.20)·초록(0.23)은 강조색보다 채도가 **더 높아서** 이 위계가 뒤집혀 있었습니다.
- **색상 간격 70° 이상**: 금빛(82°), 민트(165°), 파랑(237°). 보라·분홍 계열은 쓰지 않습니다.

중성 어두운 배경(`#191a1b`, Windows Terminal)에서 맞춘 값입니다. 밝은 배경 터미널에는 맞지 않습니다.

## 다른 테마에 옮기기

omp의 `defaults.json`(또는 자기 테마 파일)에서 테마 JSON을 복사한 뒤 `terminal.ansi` 의 **2번**(인라인 코드)·**3번**(H2·표 머리글)·**4번**(H3 이하)·**5번**(굵게·기울임·H1) 칸을 같은 원칙으로 바꾸면 됩니다 — 밝기는 본문에, 채도는 강조색의 절반으로. 성공·추가 줄·문법 강조에 형광 초록 하나를 돌려 쓰는 테마라면 `vars` 에서 그 변수를 찾아 한 번만 낮추세요.

## 출처 / 라이선스

[can1357/oh-my-pi](https://github.com/can1357/oh-my-pi)의 `titanium` 테마(MIT)에서 파생했습니다. 이 저장소도 MIT입니다 — [LICENSE](LICENSE) 참고.

---

## English

A drop-in variant of omp's built-in **titanium** theme. It keeps the electric-blue identity but tones down what *Colorful Markdown* (default on since 18.18) paints into every answer: bold is soft gold `#e5c68e` instead of neon purple `#d06fed`, inline code is mint `#8edab9` instead of neon green `#00ff88`, H2/table headers reuse the accent `#00b4ff`, and the `readoutGreen` variable (✓ lines, diff `+`, bash command names, git status) is softened to `#7ad689`.

Install: copy `themes/titanium-calm.json` to `~/.omp/agent/themes/`, pick `titanium-calm` under Settings → Appearance → Dark Theme, keep Colorful Markdown on.

Rule used (OKLCH): emphasis lightness ≈ body text (L ≈ 0.84), chroma ≤ half of the accent's (0.16), so the hierarchy reads blue structure › gold emphasis › mint code › prose. To port to another theme, retune `terminal.ansi` slots 2 (code), 3 (H2/table header), 4 (H3+) and 5 (bold/italic/H1) the same way.
