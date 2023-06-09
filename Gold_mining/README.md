# Проекты Yandex Практикума

## Технологический процесс

Как золото получают из руды? 

Когда добытая руда проходит первичную обработку, получается дроблёная смесь. Её отправляют на флотацию (обогащение) и двухэтапную очистку.

Опишем каждую стадию: 
1. Флотация
Во флотационную установку подаётся смесь золотосодержащей руды. После обогащения получается черновой концентрат и «отвальные хвосты», то есть остатки продукта с низкой концентрацией ценных металлов.
На стабильность этого процесса влияет непостоянное и неоптимальное физико-химическое состояние флотационной пульпы (смеси твёрдых частиц и жидкости).
2. Очистка 
Черновой концентрат проходит две очистки. На выходе получается финальный концентрат и новые отвальные хвосты.

## Описание данных
### Технологический* процесс
- *Rougher feed* — исходное сырье
- *ougher additions* (или reagent additions) — флотационные реагенты: Xanthate, Sulphate, Depressant
- *Xanthate* **— ксантогенат (промотер, или активатор флотации);
- *Sulphate* — сульфат (на данном производстве сульфид натрия);
- *Depressant* — депрессант (силикат натрия).
- *Rougher process* (англ. «грубый процесс») — флотация
- *Rougher tails* — отвальные хвосты
- *Float banks* — флотационная установка
- *Cleaner process* — очистка
- *Rougher Au* — черновой концентрат золота
- *Final Au* — финальный концентрат золота

### Параметры этапов
- *air amount* — объём воздуха
- *fluid levels* — уровень жидкости
- *feed size* — размер гранул сырья
- *feed rate* — скорость подачи

## Наименование признаков
Наименование признаков должно быть такое:

`[этап].[тип_параметра].[название_параметра]`

Пример: `rougher.input.feed_ag`

Возможные значения для блока `[этап]`:
- *rougher* — флотация
- *primary_cleaner* — первичная очистка
- *secondary_cleaner* — вторичная очистка
- *final* — финальные характеристики

Возможные значения для блока `[тип_параметра]`:
- *input* — параметры сырья
- *output* — параметры продукта
- *state* — параметры, характеризующие текущее состояние этапа
calculation — расчётные характеристики

## Расчёт эффективности
Вам нужно смоделировать процесс восстановления золота из золотосодержащей руды. 
Эффективность обогащения рассчитывается по формуле

<img src=https://pictures.s3.yandex.net/resources/Recovery_1576238822.jpg higth=500 width=500>

где:
- C — доля золота в концентрате после флотации/очистки;
- F — доля золота в сырье/концентрате до флотации/очистки;
- T — доля золота в отвальных хвостах после флотации/очистки.

Для прогноза коэффициента нужно найти долю золота в концентратах и хвостах. Причём важен не только финальный продукт, но и черновой концентрат.

## Метрика качества
Для решения задачи используем метрику качества — **sMAPE** (англ. *Symmetric Mean Absolute Percentage Error, «симметричное среднее абсолютное процентное отклонение»).

Нужно спрогнозировать сразу две величины:
1. эффективность обогащения чернового концентрата rougher.output.recovery;
2. эффективность обогащения финального концентрата final.output.recovery.

Итоговая метрика складывается из двух величин:

<img src=https://pictures.s3.yandex.net/resources/_smape_1576238814.jpg higth=500 width=500>
