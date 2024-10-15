# Интелигентна система за управление на водоснабдяване

Проектът представлява система за управление на водоснабдяването на сграда, използвайки два водоизточника - сондажен източник (кладенец) и водопровод (ВиК), с резервоар за съхранение на вода. Системата автоматично избира и превключва между различни [режими на работа](./docs/modes/modes.md) в зависимост от наличието на вода в резервоара, налягането във водопровода и потреблението на вода в сградата. Основната цел е ефективно управление на водата, като се осигури непрекъснато водоснабдяване на сградата.

## Основни цели на проекта:

- Ефективно управление на водните ресурси.
- Осигуряване на непрекъснато водоснабдяване на сградата, независимо от основния източник на вода.
- Автоматично превключване между различните [режими на работа](./docs/modes/modes.md) в зависимост от моментната нужда и състоянието на системата.
- Повишаване на надеждността и сигурността на водоснабдителната система на сградата.

## Основни компоненти:

1. **Резервоар**: Съхранява вода, която може да бъде използвана за захранване на сградата. Пълни се от сондажа или водопровода в зависимост от режима.
2. **Хидрофорна помпа**: Използва се за подаване на вода от различни източници към сградата.
3. **Сондаж (Изворен източник)**: Подава вода към резервоара или директно към помпата, в зависимост от режима на работа.
4. **Водопровод (ВиК)**: Основен източник на вода, когато резервоарът е празен или налягането във водопровода е достатъчно.

## Сензори:

Системата разполага с различни сензори, които следят ключови параметри като нивото на водата в резервоара, налягането във водопровода и потреблението на вода в сградата. Тези сензори осигуряват обратна връзка към системата, позволявайки ѝ автоматично да променя режимите на работа според моментната ситуация, с цел оптимизация и надеждност на водоснабдяването.

## Клапани:

Системата включва набор от клапани, които контролират потока на водата между водопровода, резервоара, помпата и сградата. Клапаните се активират и деактивират в зависимост от текущия режим на работа.

## [Режими на работа:](./docs/modes/modes.md)

1. **Ползване на резервоара (MODE_USE_TANK)**: 
Помпата черпи вода от резервоара и подава към сградата. Сондажът пълни резервоара на самотек.
2. **Ползване на водопровода (MODE_USE_SUPPLY)**: 
Вода от водопровода подава директно към сградата, докато резервоарът се пълни от сондажа.
3. **Смучене и подаване към сградата (MODE_MIXED_SUPPLY)**: 
Ако налягането във водопровода е недостатъчно, системата черпи едновременно вода от сондажа и водопровода.
4. **Пълнене на резервоара със смучене (MODE_FILL_TANK)**: 
Помпата черпи вода едновременно от водопровода и сондажа и връща водата в резервоара.

## Автоматизация:

Системата автоматично преминава между режимите на базата на състоянието на сензорите. При ниско ниво на резервоара или при недостатъчно налягане във водопровода, системата избира най-подходящия режим за осигуряване на непрекъснато водоснабдяване на сградата.

---


