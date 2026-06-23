# bazi-calculator — восстановленная рабочая сборка (для Фудао)

Форк [alvamind/bazi-calculator-by-alvamind](https://github.com/alvamind/bazi-calculator-by-alvamind) (MIT).

## Зачем `restored/`

Рабочая сборка восстановлена из npm-пакета **`@aharris02/bazi-calculator-by-alvamind`** — это форк @aharris02 с:
- точным расчётом столпов дня и часа (в оригинале alvamind они багуют),
- Date-API в конструкторе,
- расширенным анализом: `favorableElements`, `dayMasterStrength`, `interactions`, скрытые стволы + Десять богов.

GitHub-репозиторий @aharris02 был удалён (остался только npm-dist), поэтому код **деобфусцирован** (js-beautify) и **очищен от отладочного DEBUG-вывода** (было 9 console.log-спамов → 0).

Сверено с npm-оригиналом на нескольких датах: **столпы / сила Господина дня / благоприятные стихии совпадают 1:1**.

## ⚠️ Важно
Оригинальный `../src/` (alvamind) содержит **баги в расчёте дня и часа** — для продакшена используется `restored/index.js`, а не он. Пример расхождения: 1975-07-07 alvamind даёт день `乙酉`, верно `甲申`.

## Сборка браузерного bundle
Нужны зависимости `date-fns` и `date-fns-tz`:
```bash
npm i date-fns date-fns-tz
npx esbuild restored/index.js --bundle --format=iife --global-name=BaziLib --minify --outfile=bazi.bundle.js
```
Результат — ~303kb, глобальный объект `BaziLib.BaziCalculator`.

---
*Автор сборки-восстановления: Denis Onosov (ODV999). ⚠️ Информация конфиденциальная.*
