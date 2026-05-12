# tochka-neomarket

> Личный форк репозитория [URFU2026-NeoMarket/neomarket-protocols](https://github.com/URFU2026-NeoMarket/neomarket-protocols) для отправки Pull Request'ов в общий протокольный репозиторий NeoMarket.

[![API Docs](https://img.shields.io/badge/API%20Docs-Swagger%20UI-85ea2d?logo=swagger)](https://urfu2026-neomarket.github.io/neomarket-protocols/)
[![OpenAPI](https://img.shields.io/badge/OpenAPI-3.0-6ba539?logo=openapi-initiative&logoColor=white)](https://swagger.io/specification/)
[![upstream](https://img.shields.io/badge/upstream-neomarket--protocols-0075ca?logo=github)](https://github.com/URFU2026-NeoMarket/neomarket-protocols)

---

## Что это

Репозиторий содержит OpenAPI 3.0-спецификации всех модулей маркетплейса NeoMarket.  
Это форк — изменения сюда вносятся только для подготовки PR в апстрим.

**Прямой работы здесь нет** — все правки → ветка → PR в [`neomarket-protocols`](https://github.com/URFU2026-NeoMarket/neomarket-protocols).

---

## Структура спек

| Директория | Модуль | Синдикат |
|-----------|--------|---------|
| `b2b/` | Seller Cabinet (B2B) | reference |
| `moderation/` | Moderation | reference |
| `b2c/catalog/` | Каталог + Карточка товара | Forge |
| `b2c/cart/` | Корзина + Избранное + Главная | Interface |
| `b2c/orders/` | Заказы | QA Corps |
| `shared/` | Общие схемы (Product, SKU, Invoice…) | все |

---

## Флоу для PR в апстрим

```
trueforme/tochka-neomarket          URFU2026-NeoMarket/neomarket-protocols
         │                                          │
         │  1. sync с upstream                      │
         │◄─────────────────────────────────────────┤
         │                                          │
         │  2. создать ветку                        │
         │     {syndicate}/{team}/{feature}         │
         │                                          │
         │  3. внести правки в openapi.yaml         │
         │                                          │
         │  4. push + открыть PR ──────────────────►│
         │                                          │
         │     автовалидация Spectral               │
         │     ревью координатора синдиката         │
         │     пишем @ulyanayou                     │
         │                                          │
         │  5. merge ◄──────────────────────────────│
```

### Команды

```bash
# добавить upstream один раз
git remote add upstream https://github.com/URFU2026-NeoMarket/neomarket-protocols.git

# синхронизировать форк с апстримом
git fetch upstream
git merge upstream/master

# создать рабочую ветку
git checkout -b forge/copypaste/text-search

# после правок
git push origin forge/copypaste/text-search
# → открыть PR на GitHub в URFU2026-NeoMarket/neomarket-protocols
```

---

## Локальная документация

```bash
npm install
npm run docs        # http://localhost:3000 — Swagger UI
npm run docs:serve  # если зависимости уже установлены
```

Онлайн: **[urfu2026-neomarket.github.io/neomarket-protocols](https://urfu2026-neomarket.github.io/neomarket-protocols/)**

---

## Валидация спек

На каждый PR в апстриме автоматически запускается [Spectral](https://stoplight.io/open-source/spectral) — OpenAPI-линтер по правилам из `.spectral.yaml`.  
Запустить локально:

```bash
npx @stoplight/spectral-cli lint b2b/openapi.yaml
npx @stoplight/spectral-cli lint b2c/catalog/openapi.yaml
# и т.д. для других модулей
```

---

## Координаторы синдикатов

| Синдикат | Отвечает за | Координатор |
|----------|-------------|-------------|
| Forge | B2C Каталог + Карточка | @Ulyanayou |
| Interface | B2C Корзина + Избранное + Главная | @shchavr |
| QA Corps | B2C Заказы | @TimofeyChugunov |
