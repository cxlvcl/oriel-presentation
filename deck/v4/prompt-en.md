# Prompt for Claude Code: update the Oriel deck to v4 (defense, 8 slides)

Paste everything below the line into Claude Code in VS Code, in the same `~/Desktop/oriel-deck` project.

---

Tomorrow is our project defense. The Oriel deck must be rebuilt for a **new concept and a fixed jury template**: exactly **8 slides**, one per template block, 5-minute talk.

**New concept.** The market is Russian universities. We have two clients: university students and the universities themselves. Oriel is a tracker for the student **and** a platform for the university to see students' psychological state every day. Private psychologists are a future plan and appear in one small line only. **The price for the university is negotiable**: never show a price per student anywhere.

**Template, in this order:** 1 Проблема · 2 Решение · 3 Целевая аудитория · 4 Рынок · 5 Как работает и как зарабатывает · 6 Дорожная карта · 7 Команда · 8 Контакты.

Keep everything that already works: Electron shell, fullscreen window that covers the menu bar, the top-right hover pill (minimize / window / quit), black start, any key = next, ← = back, one set of ~1800 dots gliding between formations, text fading in from blur, monochrome SF Pro style. Do not break any of it.

## References (download and study every one before you code)

- All 8 slides on one sheet: https://cxlvcl.github.io/oriel-presentation/deck/v4/all.jpg
- One by one, 1920×1080: https://cxlvcl.github.io/oriel-presentation/deck/v4/01.jpg … https://cxlvcl.github.io/oriel-presentation/deck/v4/08.jpg
- Motion video (~50 s): https://cxlvcl.github.io/oriel-presentation/deck/v4/preview.mp4
- **Reference implementation** — a single-file HTML prototype of all 8 slides with the exact texts, positions and formation math: https://cxlvcl.github.io/oriel-presentation/deck/v4/deck.html

`curl` all of them into `reference/v4/`. View the images, extract frames from the video with ffmpeg at 2 fps, and read `deck.html` fully. Port its formations (the `FORMS` object) and its slide markup into our `dots.js` / `slides.js` structure; do not paste the prototype in as-is. Russian text is final: copy it exactly from `deck.html`. Where the prototype and this prompt disagree, this prompt wins. v1–v3 references are no longer valid.

## Slides

0. **Black.** Nothing.
1. **01 · Проблема — `grid100`.** On the first key press all dots fly in from far outside the screen (the old intro effect, now on this slide) and settle into a 10×10 grid on the right; at 2.0 s the 4 centre dots grow and brighten. Left: label, huge «4%», «студентов дошли» + grey «до психолога вуза за год», tiny source. A row of three small facts at 66vh (1.6 / 2.0 / 2.4): «1 на 1 900», «256 → 538», «2027». Bottom line (3.0) about testing once a year and the other 96%.
2. **02 · Решение — `orbits`** (kept from v3): student sphere with inner orbit «Психологическая служба» and outer orbit «Руководство вуза», a bright dot travelling on each. Headline «Oriel — трекер для студента.» + grey «Платформа для вуза.» Two small blocks bottom left: «Студенту», «Вузу».
3. **03 · Целевая аудитория — `two`.** Two rotating spheres (520 dots each) at x 27% / 73%, y 38%, radius 10% of height; the right one spins the other way and is 25% dimmer. Persona blocks under them: «Аня, 18 лет» (tag «пользователь · студентка») and «Психологическая служба вуза» (tag «заказчик · вуз»). Bottom line about the first entry point.
4. **04 · Рынок — `squares`** (kept from v3), but **in students, not rubles**: «4,66 млн» TAM · all students, 736 universities; «2,1 млн» SAM · full-time students in universities with a psychological service; «20 тыс.» SOM · 1% in the first year, five universities. Tiny note «Цена за студента — по договору с вузом.»
5. **05 · Как работает и как зарабатывает — `flow`.** Top half (y 39%): x 20% a ring of 30 dots lighting up one by one from 0.4 s (45 ms apart) around a small 160-dot sphere; x 50% a 16×10 block of dim dots where a 3×3 group lights up at 1.6 s; x 80% one bright pulsing dot with a pulsing ring of 24 dots from 2.2 s; two dotted streams of 40 dots each slide left to right between the groups forever. Captions at 56vh: «Студент», «Платформа», «Служба». A thin divider at 74vh (2.8), then the money row at 78vh (3.0 / 3.3 / 3.6): «Студенту — бесплатно», «Платит вуз» (лицензия за подключённых студентов, цена договорная), «Дальше» (кабинет частного психолога).
6. **06 · Дорожная карта — `timeline`**, five nodes at x 7 / 26 / 45 / 64 / 83%; the line draws itself left to right over 2.6 s; the first node (done) is bigger and brighter with a pulsing ring of 24 dots. Headline «Пилот этой зимой.» + grey «Грант весной.» Captions «Октябрь 2026», «Ноябрь», «Декабрь – январь», «Весна 2027», «Сентябрь 2027».
7. **07 · Команда — `team`.** A dotted rectangle (420 dots, alpha .32) at 7–59% x, 30–88% y where the team photo goes; three grey placeholders on the right. **Make the photo and people data:** `team = { photo: null, people: [{ name, role }] }` in `slides.js`. When `photo` is set, the image fills the frame (object-fit: cover, fades in like text, the dotted frame stays as its border); when `people` has entries they replace the placeholders. We will send the photo and descriptions later, so it must be a 2-line change.
8. **08 · Контакты — `sphere-contact`.** Big sphere on the left (27% x, 40% y) with «Заметить тревогу раньше.» + grey «И не оставлять студента с ней одного.» under it. Right: label, «Запустим пилот» + grey «в нашем вузе этой зимой», what we need from the university, QR + «Артём Алексеев / основатель · @telegram», «почта · сайт проекта». «Спасибо» bottom right. Keep the contact strings in `slides.js`; they are placeholders until we send the real ones.

Delete every other slide from v3 (intro sphere, QR invite, 1 psychologist, trend, mission line, ring, crowd, private psychologist bridge, «?», «!», compare table, Russia map, «Не деньги», old pilot).

## Rules that stay

- Monochrome only, SF Pro / SF Mono, no colour, no glow, no 3D models, no phones.
- Dots never pop: every change is a glide with a small random per-dot delay; unused dots fade out in place.
- When dots are thrown out for the fly-in, also reset their alpha and radius (otherwise they become NaN and nothing draws).
- 60 fps on an Intel MacBook Pro 2018 at 1080p, no per-frame allocations (precompute the Fibonacci point sets once).
- Slide text and data in `slides.js`, formations in `dots.js`.

## Done when

1. `npm start`: 9 states (black + 8 slides) match the v4 renders and the video.
2. The window still covers the whole screen and the top-right pill still works.
3. ← goes back through all slides and the dots glide back.
4. Setting `team.photo` to a local image shows it inside the dotted frame on slide 7.
5. There is no price per student anywhere in the app.
6. `npm run build` gives a working `Oriel.app` (x64) that runs offline.
7. You took a screenshot of every slide into `shots/v4/`, compared each with `reference/v4/`, and fixed every difference before saying it is done.
8. Update the Russian `README.md` with the new slide list.
