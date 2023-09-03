**РОССИЙСКИЙ УНИВЕРСИТЕТ ДРУЖБЫ НАРОДОВ**

**Факультет физико-математических и естественных наук**

**Кафедра прикладной информатики и теории вероятностей**

**ОТЧЕТ**

**по лабораторной работе № 1**

_дисциплина: Операционные системы_

Преподаватель: Велиева Татьяна Рефатовна

Студент: Муратов Кирилл Александрович

Группа: НПМбв-01-19

**МОСКВА**

2023 г.

**ЗАДАЧА:**

Изучить идеологию и применение средств контроля версий
Освоить умения по работе с git

**ЦЕЛЬ:**

Получение практических навыков работы VCS

**ИССЛЕДУЕМАЯ ОПЕРАЦИОННАЯ СИСТЕМА:**

1. CentOS

**ПО:**

1. Windows 10
2. Диспетчер Hyper-v от Microsoft
3. MobaXTern
4. OBS studio


**ТЕРМИНЫ:**

**SSH** (**secure shell** ) - сетевой протокол прикладного уровня, позволяющий производить удалённое управление операционной системой и туннелирование TCP-соединений.

**OS\ОС** – операционная система

**VM\ВМ** – virtualmachine (виртуальная машина)

**Linux** – семейство UNIX-подобных ОС на базе ядра Linux

**tmp** - специальная директория, которая очищается после перезагрузки системы. Тем самым позволяет экономить место, и не выполнять лишних действий по удалению одноразовых файлов.

**скрипт** - короткая не компилируемая программа

**ВИДЕО МАТЕРИАЛ:**

Начало работы

Подключение к ВМ Cent OS через SSH. При удачном соединение ввожу логин и пароль от пользователя, который был создан в ЛР#1.
![рис.1 Подключение к ВМ](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/1_ConnectToOSFromSSH.png)

Повышаю права доступа с помощью команды su -, и ввожу пароль
![рис.2 Повышение прав](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/2_Su_-.png)

Выполняю обновление системы с помощью команды yum update -y
![рис.3 Обновление системы](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/3_Update.png)

После выполнения обновления - перезагружаю ВМ командой init 6
![рис.4 Перезагрузка](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/4_init_6.png)

После перезагрузки ВМ авторизовываюсь, и повышаю права доступа. Далее перехожу в директорию tmp.
Выгружаю скрипт. Повышаю права. И выполняю установку.
![рис.5 Работа со скриптом](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/5_save_script.png)

Устанавливаю менеджер проектов dnf (yum install dnf -y). Будет нужен в ходе выполнения команд предусмотринной ЛР#2.
![рис.6 Установка dnf](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/6_install_dnf.png)

Для установки gh (git cli) стребуется установка пакета snap. Для начала предуется расширить репу с помощью команды dnf install epel-release -y
![рис.7 Epel](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/7_add_epel.png)

Далее идет установка snapd. dnf install snapd -y
![рис.8 Установка snapd](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/8_install_snapd.png)

Далее запуская службу и установка классических биндов. После этих действий необходимо перезагрузиться.
![рис.9 systemclt](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/9_ctl_bind.png)

После перезагрузки. Авторизовываюсь. Повышаю права. И выполняю установку gh с помошью команды snap install gh
![рис.10 установка git cli](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/10_install_gh.png)

Настройка git. Опеределяю: пользователя, почту, настройка вывода сообщений, ввод имя начальной ветки, настрока параметров autocrlf и safecrlf.
![рис.11 Глобальные настройки](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/11_global_settings.png)

Создаю клюк RSA с размером ключа 4096 ssh-keygen -t rsa -b 4096 -C "S1032142155@rudn.ru"
![рис.12 RSA](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/12_rsa_key.png)

Клонирую проект
![рис.13 Клонирование](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/13_clone.png)

Работаю со слонированным проектом. Проверяю послучения данных ls. Удаляю .json файл. Выполняю сборку make. Добавляю изменения git add. Комменирую изменения.
![рис.14 Работа с проектом](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/14_work_proj.png)

Вывод изменений и отправка данных на сервер.
![рис.15 push to git](https://github.com/kirksman/LabForRUDN_OS/blob/Lab%232/15_push.png)

**Вывод**

С помошью git cli получилось настроить конфигурацию git и получить копию проекта, ввести изменения и отправить себе отредактированный проект.

**Контрольные вопросы**

**1)Что такое системы контроля версий (VCS) и для решения каких задач они предназначаются?**

-Для решения таких проблем как раз и используется система контроля версий, она позволяет комфортно работать над проектом как индивидуально, так в коллективе. VCS отслеживает изменения в файлах, предоставляет возможности для создания новых и слияние существующих ветвей проекта, производит контроль доступа пользователей к проекту, позволяет откатывать исправления и определять кто, когда и какие изменения вносил в проект. Основным понятием VCS является репозиторий (repository) – специальное хранилище файлов и папок проекта, изменения в которых отслеживаются. В распоряжении разработчика имеется так называемая “рабочая копия” (working copy) проекта, с которой он непосредственно работает. Рабочую копию необходимо периодически синхронизировать с репозиторием, эта операция предполагает отправку в него изменений, которые пользователь внес в свою рабочую копию (такая операция называется commit) и актуализацию рабочей копии, в процессе которой к пользователю загружается последняя версия из репозитория (этот процесс носит название update).

**2)Объясните следующие понятия VCS и их отношения: хранилище, commit, история, рабочая копия.**

-хранилище - продставляет собой специальные директории проекта
-commit - эта операция предполагает отправку в него (VCS) изменений, которые пользователь внес в свою рабочую копию
-история - записи о изменениях (логирование) в проекте.
-рабочая копия - копия проекта на определенной момент времени. Дает возможность работать над проектом нескольким участником проекта.

**3)Что представляют собой и чем отличаются централизованные и децентрализованные VCS? Приведите примеры VCS каждого вида. (Ц - централизованные, Д - децентрализованные)**
   VS - ц отказоустойчивость. Если серсер не будет доступин, то никто не сможет синхронизироваться с репой.
    - д отказоустойчивость - Могут возникнуть проблемы со синхронизацией.

    - ц Обслуживание - При обслуживании как на уровне "железа" так и на уровне ПО - сервер может быть не доступин на некоторое время
    - д Обслуживание - Если и трубуется обслужтвание, то это будет мало заметно, т.к есть другие сервера для синхронизации.

    - ц разработка - относительно быстро, т.к нет обходимости реализовывать репликации
    - д разработка - затраты время на написание и тестирование репликации.

-централизованные - В централизованной системе все пользователи подключены к центральному владельцу сети или «серверу». Центральный владелец хранит данные, к которым могут получить доступ другие пользователи, а также информацию о пользователях. Эта информация о пользователе может включать профили пользователей, пользовательский контент и многое другое. Централизованная система проста в установке и может быстро развиваться.

-децентрализованные - Как следует из названия, у децентрализованных систем нет единого центрального владельца. Вместо этого они используют нескольких центральных владельцев, каждый из которых обычно хранит копию ресурсов, к которым пользователи могут получить доступ. Децентрализованная система может быть так же уязвима к сбоям, как и централизованная. Однако по своей конструкции система более устойчива к неисправностям. Это связано с тем, что при выходе из строя одного, нескольких центральных владельцев или серверов, другие продолжают работать и предоставляют пользователям доступ к данным.

**4)Опишите действия с VCS при единоличной работе с хранилищем.**
-Извлечение рабочей копии проекта. Вторая локальная копия хранится в качестве эталона (для нахождения изм/ для отката без обращения к серверу). Обновление рабочей копии. Модификация проекта. Фиксация изменений. Лучше использовать как-будто идет работа с общим проектом.

**5)Опишите порядок работы с общим хранилищем VCS.**
-Извлечение рабочей копии проекта. Вторая локальная копия хранится в качестве эталона (для нахождения изм/ для отката без обращения к серверу). Обновление рабочей копии.Модификация проекта. Фиксация изменений.

**6)Каковы основные задачи, решаемые инструментальным средством git?**
-Самое главное разработка ПО. Удобно отслеживать изменения. Сборка проекта (нужен компилятор). Релиз новых версий ПО. Тестирование проекта.

**7)Назовите и дайте краткую характеристику командам git.**
-git add    - добавляет содержимое рабочего каталога в индекс (staging area) для последующего коммита
-git status - показывает состояния файлов в рабочем каталоге и индексе: какие файлы изменены, но не добавлены в индекс; какие ожидают коммита в индексе
-git diff   - используется для вычисления разницы между любыми двумя Git деревьями
-git commit - берёт все данные, добавленные в индекс с помощью git add, и сохраняет их слепок во внутренней базе данных, а затем сдвигает указатель текущей ветки на этот слепок
-git reset  - используется в основном для отмены изменений
-git rm     - для удаления файлов из индекса и рабочей копии
-git mv     - удобный способ переместить файл
-git clean  - используется для удаления мусора из рабочего каталога. Это могут быть результаты сборки проекта или файлы конфликтов слияний
-git push   - отправка изменений в VCS
-git pull   - синхронизация проекта с VCS

8)Приведите примеры использования при работе с локальным и удалённым репозиториями.
-Для удаленного просмотра репозитория для начала нужно его склонировать и при необходимости выбрать ветку проекта.git remote -v (просмотр адреса чтения и записи)
-Так же для получения измененний можно использовать команду git fetch <name>

**9)Что такое и зачем могут быть нужны ветви (branches)?**

-Представляет собой ссылку на проект на обределенной стадии, но при этом master не блокируется для изменений и ведет commitы.
-Ветки удобны, когда нужно реализовать какой-то функциаонал вне основной велки проекта. Настроить манифест доступа к ветке.

**10)Как и зачем можно игнорировать некоторые файлы при commit?**

-Игнорирование части проекта необходимо, когда не нужно отправлять временные директории/файлы проекта, которые были созданы самим проектом.
-Игнорируемые файлы отслеживаются в специальном файле, .gitignore который сохраняется в корне репозитория