# Prompt for Claude Code: update the Oriel deck to v4 (defense, jury template)

Paste everything below the line into Claude Code in VS Code, in the same `~/Desktop/oriel-deck` project.

---

Tomorrow is our project defense. The Oriel deck must be rebuilt for a **new concept and a fixed jury template**. The talk is 5 minutes and **15 slides**.

**New concept.** The market is Russian universities. We have two clients: university students and the universities themselves, and we solve a problem for each. Oriel is a tracker for the student **and** a platform for the university to see students' psychological state every day. Private psychologists are a future plan only: they appear in one small line, nowhere else. Remove every slide about private psychologists as a segment.

**Jury template** (slide order must follow it): Problem → Solution → Target audience → Market → How it works and how it makes money → Roadmap → Team → Contacts.

Keep everything that already works: Electron shell, fullscreen window that covers the menu bar, the top-right hover pill (minimize / window / quit), black start, any key = next, ← = back, one set of ~1800 dots gliding between formations, text fading in from blur, monochrome SF Pro style. Do not break any of it.

## References (download and study every one before you code)

- All 15 slides on one sheet: https://cxlvcl.github.io/oriel-presentation/deck/v4/all.jpg
- One by one, 1920×1080: https://cxlvcl.github.io/oriel-presentation/deck/v4/01.jpg … https://cxlvcl.github.io/oriel-presentation/deck/v4/15.jpg
- Motion video (~70 s): https://cxlvcl.github.io/oriel-presentation/deck/v4/preview.mp4
- **Reference implementation** (a single-file HTML prototype of all 15 slides, the exact texts, positions and formation math): https://cxlvcl.github.io/oriel-presentation/deck/v4/deck.html

`curl` all of them into `reference/v4/`. View the images, extract frames from the video with ffmpeg at 2 fps, and read `deck.html` fully. Port its formations (the `FORMS` object) and its slide markup into our `dots.js` / `slides.js` structure; do not paste the prototype in as-is. Where the prototype and this prompt disagree, this prompt wins. v1–v3 references are no longer valid for slide content.

## Slide list v4

Russian text is final, use it exactly as in `deck.html`. Numbers in parentheses are fade-in delays in seconds. «Kept» = the slide or formation exists in v3; reuse it.

0. **Black.** Nothing.
1. **Intro** — kept (dots fly in, sphere, «Oriel», acronym).
2. **Hall test (QR)** — kept; small text is now «Отсканируйте QR. Анонимно, результат видите только вы. В конце покажу, что получилось у зала.»
3. **01 · Проблема · 4%** — kept `grid100` (10×10, the 4 centre dots light up at 0.9 s). Label «01 · ПРОБЛЕМА». Bottom line «Об остальных 96% вуз узнаёт, когда уже поздно.» (was «служба»).
4. **1 психолог на 1 900** — kept `onecrowd`. Label «01 · ПРОБЛЕМА · ПСИХОЛОГИЧЕСКАЯ СЛУЖБА».
5. **Тренд** — kept `trend`. Label «01 · ТРЕНД».
6. **Две стороны** — `buildup` (kept, the calm line that turns into noise, small ring at 30% x). New texts: label «01 · ДВЕ СТОРОНЫ ОДНОЙ ПРОБЛЕМЫ», headline «Студент копит тревогу неделями.» + grey «Вуз узнаёт, когда уже поздно.» Under the line at 77vh: white «Oriel замечает здесь» centred under the ring; grey «Вуз узнаёт здесь» centred under the right end, with tiny mono «пересдача · академ · отчисление» under it.
7. **02 · Решение** — `orbits` (kept). Label «02 · РЕШЕНИЕ», headline «Трекер для студента.» + grey «Платформа для вуза.» Orbit labels: «Студент» (under the sphere), grey «Психологическая служба» (inner), grey «Руководство вуза» (outer). Bottom-left small text from `deck.html`.
8. **02 · Чем мы отличаемся** — the compare table (kept), 7 rows with Samsung Health. Column 3 header is now «Служба видит динамику» (was «Психолог видит динамику»), column 4 «Кабинет для вуза». Cell values exactly as in `deck.html` (Oriel row all full). Footnote «По открытым данным, октябрь 2026. Кабинет вуза в Oriel — в разработке, к пилоту.» No dots on the canvas on this slide.
9. **NEW · 03 · Целевая аудитория — formation `two`.** Two rotating spheres (520 dots each) at x 27% / 73%, y 38%, radius 10% of height; the right one spins the other way and is 25% dimmer. Headline «Два клиента.» + grey «Одна проблема.» Two persona blocks under the spheres (1.0 / 1.5): «Аня, 18 лет» (tag «пользователь · студентка») and «Психологическая служба вуза» (tag «заказчик · вуз») with texts from `deck.html`. Bottom line (2.2) «Первый вход: первокурсники-очники в вузах с психологической службой. Сессия — пик тревоги.»
10. **04 · Рынок** — `squares` (kept from v3 market slide). Label «04 · РЫНОК»; small text «Через психологическую службу вуза. 4,66 млн студентов в России, 538 вузовских служб.»
11. **NEW · 05 · Как работает — formation `flow`.** Three groups on one row at y 44%: x 20% a ring of 30 dots (radius 11% of height) lighting up one by one from 0.4 s every 45 ms around a small sphere of 160 dots; x 50% a 16×10 block of dim dots where a 3×3 group lights up at 1.6 s (a group that is struggling); x 80% one bright pulsing dot with a pulsing ring of 24 dots, from 2.2 s. Between the groups two dotted streams of 40 dots each slide left to right forever. Headline «Студент отмечает.» + grey «Вуз видит.» Three centred captions at 64vh (1.0 / 1.6 / 2.2): «Студент», «Платформа», «Служба». Tiny mono line at 90vh: «Личные записи видит только студент. Вузу — только обезличенные цифры групп.»
12. **NEW · 05 · Как зарабатывает — formation `money`.** 400 dots in a 25×16 grid on the right (from 52vw + 6 px, top 25vh, step 2.6% of height), filling row by row from 0.7 s (each row 70 ms later, alpha .75, before that .06). Left: label, huge «300 ₽», «за студента в год.» + grey «Платит вуз.», small text, tiny mono «Цена — допущение для пилота, финальная — в договоре.» Above the grid tiny mono «1 точка = 10 студентов · вуз на 4 000 студентов»; under it (2.4) «= 1,2 млн ₽ в год» with small «с одного вуза. Дальше — кабинет частного психолога.»
13. **06 · Дорожная карта** — `timeline`, now **five** nodes at x 7 / 26 / 45 / 64 / 83%; the first node (done) is brighter and bigger with a pulsing ring of 24 dots. Headline «Пилот этой зимой.» + grey «Грант весной.» Captions (1.0 / 1.4 / 1.8 / 2.2 / 2.6): «Октябрь 2026», «Ноябрь», «Декабрь – январь», «Весна 2027», «Сентябрь 2027» with texts from `deck.html`.
14. **NEW · 07 · Команда — formation `team`.** A dotted rectangle (420 dots, alpha .32) at 7–59% x, 30–88% y: this is where the team photo will go. Right column: three grey placeholders «Имя Фамилия / роль · опыт». **Build this slide so the photo and the people are data:** in `slides.js` keep `team = { photo: null, people: [{ name, role }] }`. When `photo` is set, the image appears inside the frame (object-fit: cover, slight grayscale is fine, fades in like text, the dotted frame stays as its border); when `people` has entries, they replace the placeholders. We will send the photo and descriptions later, so adding them must be a 2-line change.
15. **08 · Контакты** — sphere on the left (centre 27% x, 40% y), the mission «Заметить тревогу раньше.» + grey «И не оставлять студента с ней одного.» under it. Right: label «08 · КОНТАКТЫ», «Запустим пилот» + grey «в нашем вузе этой зимой», what we need from the university, then QR + «Артём Алексеев / основатель · @telegram», «почта · сайт проекта», «QR — тест тревожности, 2 минуты». «Спасибо» bottom right. Keep the contact strings in `slides.js` (they are placeholders until we send the real ones).

Remove from v3: «Тревога копится неделями» mission slide, «Один студент. Три уровня поддержки», the 30-day ring slide, «Картина курса каждый день», «Между сессиями — не тишина» (private psychologist), «?» and «!» slides, the Russia map, «Не деньги» and the old pilot slide. Their content now lives in slides 6, 7, 11, 13 and 15.

## Rules that stay

- Monochrome only, SF Pro / SF Mono, no colour, no glow, no 3D models, no phones.
- Dots never pop: every change is a glide with a small random per-dot delay; unused dots fade out in place.
- Bug to avoid (it happened in the prototype): when dots are thrown out for the intro, also reset their alpha and radius, otherwise they become NaN and nothing draws when you jump to a slide directly.
- 60 fps on an Intel MacBook Pro 2018 at 1080p, no per-frame allocations (precompute the Fibonacci point sets once).
- Slide text and table data in `slides.js`, formations in `dots.js`.

## Done when

1. `npm start`: 16 states (black + 15 slides) match the v4 renders and the video.
2. The window still covers the whole screen and the top-right pill still works.
3. ← goes back through all slides and the dots glide back.
4. Setting `team.photo` to a local image path shows the photo inside the dotted frame on slide 14.
5. `npm run build` gives a working `Oriel.app` (x64) that runs offline.
6. You took a screenshot of every slide into `shots/v4/`, compared each with `reference/v4/`, and fixed every difference before saying it is done.
7. Update the Russian `README.md` with the new slide list.
