# Prompt for Claude Code: edit the Oriel deck for the defense (v4)

For Vitaliy. Open the existing Oriel presentation project (the Electron app Artem sent you) in VS Code, start Claude Code in that folder and paste everything below the line.

---

You are editing an **existing, working** presentation app (Electron + one canvas of ~1800 dots + a text layer). Tomorrow is our project defense. Your job is **only to change the slide content** listed below. Everything else stays exactly as it is.

## Hard rules: do not break what works

1. **Do not rewrite, refactor, rename or reorganise anything.** Keep the folder structure, file names, Electron setup, `package.json`, build config, window code, the fullscreen behaviour, the top-right hover pill (minimise / window / quit), keyboard handling (any key = next, ← = back), the dot engine, easing, timings and styles.
2. Reuse the existing engine: one set of dots that glides between formations, text that fades in from blur with per-element delays. New slides are new entries in the slide list plus new formation functions written in the same style as the existing ones.
3. Formations from v3 that are no longer used may stay in the code; just stop using them. Do not delete helpers other code may call.
4. Before you change anything, read the whole project and write a short plan: which files you will touch and why. Touch as few files as possible.
5. Commit (or copy the folder) before you start, so we can roll back.
6. Monochrome only, SF Pro / SF Mono, no colour except the team photos, no glow, no 3D models, no phones. No price per student anywhere: the price for the university is negotiable.
7. 60 fps at 1080p on a laptop, no per-frame allocations.

## References (download all into `reference/v4/` and study them first)

- All slides on one sheet: https://cxlvcl.github.io/oriel-presentation/deck/v4/all.jpg
- One by one, 1920×1080: https://cxlvcl.github.io/oriel-presentation/deck/v4/00.jpg (logo) … https://cxlvcl.github.io/oriel-presentation/deck/v4/08.jpg
- Motion video (~57 s): https://cxlvcl.github.io/oriel-presentation/deck/v4/preview.mp4 — extract frames with ffmpeg at 2 fps.
- **Reference prototype** with the exact Russian texts, positions (vw/vh), delays and the formation math in a `FORMS` object: https://cxlvcl.github.io/oriel-presentation/deck/v4/deck.html
- Team portraits (put them where the project keeps images, e.g. `assets/team/`): https://cxlvcl.github.io/oriel-presentation/deck/v4/team/artem.jpg , …/team/nika.jpg , …/team/vitaliy.jpg

Port texts and formation math from `deck.html` into the project's own slide/formation files. Do not paste the prototype in as a page. Russian text is final: copy it character for character from `deck.html`.

## New slide order (replaces the current one completely)

States: **black + logo + 8 slides = 10 states**. Every other current slide is removed from the order.

0. **Black.** Unchanged: pure black on launch.
1. **Logo** — the existing intro, unchanged: on the first key press the dots fly in from outside the screen and assemble the sphere, «Oriel» and the acronym Observe / Recognize / Insight / Ease / Live with Russian captions appear.
2. **01 · Проблема** — the existing `grid100` formation (10×10 on the right). The sphere breaks into the grid; the 4 centre dots grow and brighten at 1.1 s. Left: label, huge «4%», «студентов дошли» + grey «до психолога вуза за год», tiny source line. A row of three small facts at 66vh (delays 1.6 / 2.0 / 2.4): «1 на 1 900», «256 → 538», «2027». Bottom line (3.0) about testing once a year and the other 96%.
3. **02 · Решение** — the existing `orbits` formation, new texts: headline «Oriel — трекер для студента.» + grey «Платформа для вуза.», orbit labels «Студент», grey «Психологическая служба», grey «Руководство вуза», two small blocks bottom left «Студенту» and «Вузу».
4. **03 · Целевая аудитория** — NEW formation `two`: two rotating spheres of 520 dots each at x 27% / 73%, y 38%, radius 10% of screen height; the right one spins the other way and is 25% dimmer. Persona blocks under them: «Аня, 18 лет» (tag «пользователь · студентка») and «Психологическая служба вуза» (tag «заказчик · вуз»), bottom line about the first entry point.
5. **04 · Рынок** — the existing `squares` formation, numbers **in students, not rubles**: «4,66 млн» (TAM · all students, 736 universities), «2,1 млн» (SAM · full-time students in universities with a psychological service), «20 тыс.» (SOM · 1% in the first year, five universities). Tiny note «Цена за студента — по договору с вузом.»
6. **05 · Как работает и как зарабатывает** — NEW formation `flow` (see `deck.html`): ring of 30 dots lighting up one by one around a small sphere (x 20%), a 16×10 block where a 3×3 group lights up (x 50%), one pulsing dot with a pulsing ring (x 80%), two dotted streams moving between them, all at y 39%. Captions «Студент», «Платформа», «Служба» at 56vh; a thin divider at 74vh; money row at 78vh: «Студенту — бесплатно», «Платит вуз» (лицензия за подключённых студентов, цена договорная), «Дальше» (кабинет частного психолога).
7. **06 · Дорожная карта** — the existing `timeline` formation with **five** nodes at x 7 / 26 / 45 / 64 / 83%; the first node is bigger with a pulsing ring of 24 dots. Headline «Тест, доработка,» + grey «потом пилот.» Captions: «Ноябрь» (testing the app at our university with 30–50 students), «Декабрь» (analysing bugs and feedback, improving the app), «Январь» (pilot in the winter session), «Весна 2027», «Сентябрь 2027» — texts exactly as in `deck.html`.
8. **07 · Команда** — NEW formation `team`: a thin dotted ring of 120 dots around each portrait, drawn clockwise from 0.6 s. Headline «Три человека.» + grey «Весь продукт.» Three **round colour photos on their original white background** (15vw circles, object-fit cover, no filters) centred at x 23 / 50 / 77%, top 29vh, fading in at 0.8 / 1.1 / 1.4 s. Under each at 63vh: name, tiny mono role, one line: «Артём Алексеев» · «фронтенд · дизайн бренда»; «Ника Алексеева» · «PR · продвижение»; «Виталий Ванаев» · «бэкенд · тестирование». Photos must be local files so the app works offline.
9. **08 · Контакты** — the existing big sphere moved to the left (27% x, 40% y) with «Заметить тревогу раньше.» + grey «И не оставлять студента с ней одного.» under it. Right: label, «Начнём с нашего вуза:» + grey «тест, доработка, пилот», what we need from the university («разрешение на тестирование и пилот, …»), the existing QR, «Артём Алексеев» / «основатель Oriel», «+7 910 890-95-22», «utkinoking@gmail.com», tiny mono «QR — тест тревожности, 2 минуты». «Спасибо» bottom right.

## Check before you say it is done

1. `npm start`: black → logo → 8 slides, 10 states total, each matches its reference image and the video.
2. The window still covers the whole screen, the top-right pill still works, nothing else in the app changed (show `git diff --stat`).
3. ← goes back through all slides and the dots glide back; going back to the logo re-forms the sphere.
4. The team photos load offline.
5. There is no price per student anywhere.
6. Build the app with the **existing** build command and config. If we need a Windows build for the defense laptop and the config has no Windows target, ask before adding one.
7. Take a screenshot of every state into `shots/v4/`, compare each with `reference/v4/`, fix every difference.
8. Update the Russian `README.md` with the new slide list.
