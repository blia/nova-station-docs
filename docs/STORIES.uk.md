# Історії Nova Station

Nova Station - доволі абстрактна ідея операційного середовища. Ці історії показують, що саме вона має змінити на практиці.

Це ще не демонстрації готового продукту й не обіцянка, що всі функції вже існують. Це конкретні сценарії, через які ми формуємо архітектуру та перевіряємо, чи справді project-first модель працює.

## Перемикаємо Project, а не вкладки

Уявімо, що я паралельно працюю над API та frontend.

У терміналі відкриті вкладки для обох частин. У браузері також. Логи, задачі, код, чати й агенти розкидані між різними інструментами. Щоб перемкнути контекст, мені доводиться вручну збирати його з вікон і власної пам'яті.

У Nova Station API та frontend можуть бути окремими Projects. Я обираю API Project і отримую його код, логи, браузер, задачі, агентів, статус і presentation. Обираю frontend Project - відновлюється інший цілісний контекст.

Людина обирає роботу. Система відновлює середовище навколо неї.

## Запит із телефона, виконання на workstation

Я прошу Nova Station із телефона згенерувати зображення.

Телефон є точкою взаємодії, але не зобов'язаний виконувати важку задачу. Station бачить довірену workstation із відповідною GPU та моделлю, запускає задачу там, відстежує progress, приймає готовий image artifact у Project state і повертає preview на телефон.

Повне зображення може з'явитися на планшеті, TV або media outlet.

Source device, executor device і output device можуть бути трьома різними пристроями.

## Відео існує навіть без video outlet

Я прошу показати останнє відео з каналу, який дивлюся. Агент використовує video-service connector і отримує media reference.

Якщо в поточному Project є media outlet, відео запускається. Якщо його немає, запит не стає невдалим. Station може зберегти reference і запропонувати text summary, audio-only playback, queue на потім, тимчасовий media outlet, перехід в інший Project або compatibility surface.

Неможливість показати результат не означає неможливість його отримати, обчислити, зберегти або зрозуміти.

## English Tutor без екрана

Raspberry Pi має тільки мікрофон і speaker. Він запускається одразу в English Learning Project із tutor agent, voice/audio outlet та audiobook або dictionary connectors.

Project пам'ятає playback position, питання, corrections, vocabulary progress та історію занять. Пізніше той самий Project можна продовжити на ноутбуці чи телефоні вже з іншою presentation.

Nova Station не вимагає, щоб кожен корисний комп'ютер мав desktop.

## Відновлення роботи на іншій машині

Комп'ютер або development VM втрачено. На іншій машині Station входить у той самий account і відновлює Projects зі snapshots, ordered events та artifacts.

Вона не відновлює живу пам'ять Linux-процесів. Вона відновлює довговічний логічний стан, яким володіє Nova Station: історію Project, accepted outputs, конфігурацію, agent memory, object references і restore points.

Якщо мережа недоступна, роботу можна продовжити локально в degraded mode й синхронізувати пізніше.

## Один Project, різні ролі пристроїв

Ноутбук показує основну Board проєкту. Другий монітор стає media outlet. Телефон - віртуальною клавіатурою, approval surface або пультом. Speaker відповідає за voice input та audio output.

Усі пристрої не стрімлять один і той самий екран. Кожен Station Runtime node повідомляє свої capabilities й отримує ролі, доречні для активного Project.

Project спільний. Його presentations різні.

## IDE стає меншою

Сучасні редактори постійно перетворюються на важкі IDE, бо кожен із них забирає собі project context, terminal, Git, tests, debugger, logs, packages, notifications, AI та layout management.

Nova Station переносить це середовище в Project. Code editor може зосередитися на редагуванні. Language tools, build/test status, Git hosting, terminal commands, logs та agents стають окремими connectors і outlets навколо спільного Project state.

Editor редагує code. Project є environment.

## Нове обладнання підключається один раз

Розробник створює новий controller або незвичний hardware device. Замість окремої інтеграції в кожну програму він реалізує один Station outlet, який описує capabilities та semantic roles пристрою.

Programs, які вже розуміють ці roles, можуть використовувати девайс, не знаючи його бренд чи власний протокол.

Outlet model перетворює hardware support на повторно використовувану системну можливість.

## Інші сценарії

У приватному архітектурному каталозі також зберігаються car, smart-home, entertainment, presentation, VR, Time Machine, proactive-agent, parallel-execution, compatibility та replay сценарії. Вони потраплятимуть у публічну документацію, коли стануть достатньо конкретними для відповідального пояснення.

Повернутися до [огляду проєкту](../README.md), прочитати [Vision](VISION.md) або перейти до [Announcements](ANNOUNCEMENTS.md).
