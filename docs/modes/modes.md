# Режими на работа

## Режим 1: Ползване на резервоара `MODE_USE_TANK`

Хидрофорната помпа черпи вода от резервоара и подава към сградата. Сондажът продължава да пълни резервоара на самотек, докато той не се напълни.

### Причина за включване:
- Нивото на резервоара е над минималното.

### Причина за изключване:
- Нивото на резервоара пада под минималното, което води до преминаване към Режим 2.

### Активни клапани:

- **Клапан 2 `valve_spring_to_tank`**: Отворен, ако `tank_high_level` е false.
- **Клапан 6 `valve_tank_to_pump`**: Отворен за подаване на вода от резервоара към хидрофорната помпа.
- **Клапан 7 `valve_pump_to_building`**: Отворен за подаване на вода към сградата.

### Неактивни клапани:

- **Клапан 1 `valve_supply_to_tank`**: Затворен, за да предотврати пълненето на резервоара от водопровода.
- **Клапан 3 `valve_pump_to_tank`**: Затворен, за да предотврати връщането на вода от помпата към резервоара.
- **Клапан 4 `valve_supply_to_pump`**: Затворен, за да не подава вода директно от водопровода към помпата.
- **Клапан 5 `valve_spring_to_pump`**: Затворен, защото помпата черпи вода от резервоара.

---

## Режим 2: Ползване на водопровода `MODE_USE_SUPPLY`

Вода от водопровода (ВиК) се подава директно към сградата, докато резервоарът се пълни от сондажа.

### Причина за включване:
- Нивото на резервоара е под минималното.
- Налягането във водопровода е достатъчно.

### Причина за изключване:
- Резервоарът се е напълнил, което води до преминаване към Режим 1.
- Налягането във водопровода спада, което води до преминаване към Режим 3.

### Активни клапани:

- **Клапан 2 `valve_spring_to_tank`**: Отворен за продължаване на пълненето на резервоара от сондажа.
- **Клапан 4 `valve_supply_to_pump`**: Отворен за подаване на вода към помпата.
- **Клапан 7 `valve_pump_to_building`**: Отворен за подаване на вода към сградата.

### Неактивни клапани:

- **Клапан 1 `valve_supply_to_tank`**: Затворен, защото резервоарът не се пълни от водопровода.
- **Клапан 3 `valve_pump_to_tank`**: Затворен за предотвратяване на връщане на вода от помпата.
- **Клапан 5 `valve_spring_to_pump`**: Затворен, защото водата се подава от водопровода.
- **Клапан 6 `valve_tank_to_pump`**: Затворен, защото резервоарът не подава вода към помпата.

---

## Режим 3: Захранване чрез смучене `MODE_MIXED_SUPPLY`

Вода се черпи едновременно от водопровода и сондажа при активна консумация в сградата, ако резервоарът е с ниско ниво и няма достатъчно налягане във водопровода.

### Причина за включване:
- Нивото на резервоара е под минималното.
- Налягането във водопровода е недостатъчно.
- Има активна консумация в сградата.

### Причина за изключване:
- Консумацията на вода спира, което води до преминаване към Режим 4.
- Налягането във водопровода се възстановява, което води до връщане към Режим 2.

### Активни клапани:

- **Клапан 4 `valve_supply_to_pump`**: Отворен, за да подаде вода от водопровода към помпата.
- **Клапан 5 `valve_spring_to_pump`**: Отворен, за да подаде вода от сондажа към помпата.
- **Клапан 7 `valve_pump_to_building`**: Отворен за подаване на вода към сградата.

### Неактивни клапани:

- **Клапан 1 `valve_supply_to_tank`**: Затворен, за да не пълни резервоара от водопровода.
- **Клапан 2 `valve_spring_to_tank`**: Затворен, защото водата се подава директно към помпата.
- **Клапан 3 `valve_pump_to_tank`**: Затворен, за да не връща вода от помпата към резервоара.
- **Клапан 6 `valve_tank_to_pump`**: Затворен, защото резервоарът не подава вода към помпата.

---

## Режим 4: Пълнене на резервоара чрез смучене `MODE_FILL_TANK`

Помпата черпи вода едновременно от водопровода и сондажа и връща водата в резервоара.

### Причина за включване:
- Нивото на резервоара е под минималното.
- Налягането във водопровода е недостатъчно.
- Няма активна консумация в сградата.

### Причина за изключване:
- Резервоарът се е напълнил, което води до преминаване към Режим 1 или Режим 2.
- Налягането във водопровода се възстановява, което води до връщане към Режим 2.

### Активни клапани:

- **Клапан 4 `valve_supply_to_pump`**: Отворен за подаване на вода към помпата.
- **Клапан 5 `valve_spring_to_pump`**: Отворен за подаване на вода от сондажа.
- **Клапан 3 `valve_pump_to_tank`**: Отворен за връщане на вода към резервоара.

### Неактивни клапани:

- **Клапан 1 `valve_supply_to_tank`**: Затворен.
- **Клапан 2 `valve_spring_to_tank`**: Затворен.
- **Клапан 6 `valve_tank_to_pump`**: Затворен.
- **Клапан 7 `valve_pump_to_building`**: Затворен, защото няма консумация.