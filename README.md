# Heroes Pulse — web build for timeforsheroes.eu

This repository holds the **built** web app of [Heroes Pulse](https://github.com/Lindfelt/heroes_app), exactly as it is served on timeforsheroes.eu. A push here is deployed to the website automatically.

The website serves this folder at `https://timeforsheroes.eu/themes/time4sheroes/assets/pulse/`; participants open it through `https://timeforsheroes.eu/pulse`. Answers go to `https://timeforsheroes.eu/api/pulse/answers`.

## Publishing a new build

From the app's repository:

```bash
flutter build web --release \
  --base-href /themes/time4sheroes/assets/pulse/ \
  --dart-define=ANSWERS_URL=https://timeforsheroes.eu/api/pulse/answers
```

Then replace everything in this repository except `.git` and this README with the contents of `build/web/`, leaving out `_headers`, and push:

```bash
rsync -a --delete --exclude /.git --exclude /README.md --exclude /_headers build/web/ <this repository>/
```

Both flags matter:

- **`--base-href`** — without it the app looks for its files at the site's root and shows a blank page.
- **`ANSWERS_URL`** — without it the app sends nothing, and answers stay on the participants' phones.

Build from the app's `master` with `AnswerQueue.send()` in place (the `send-answers` change).
