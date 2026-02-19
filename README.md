# TypeScript `paths` без `baseUrl` (issue #62207)

Этот проект показывает корректный современный сценарий резолва из обсуждения
[TypeScript#62207](https://github.com/microsoft/TypeScript/issues/62207):
использование `paths` **без** `baseUrl`.

## Что внутри

- один конфиг: `tsconfig.json`;
- alias mapping через `paths`:
  - `@shared/*` -> `./src/shared/*`
  - `@app/*` -> `./src/app/*`
- пример импорта в `src/app/demo.ts`: `import { sum } from "@shared/math"`.

## Проверка

```bash
npm run typecheck
```

## Трассировка резолва TypeScript

```bash
npm run trace
```

В `--traceResolution` видно, что TS сопоставляет `@shared/math` с паттерном
`@shared/*` и успешно резолвит модуль в `src/shared/math.ts`.
