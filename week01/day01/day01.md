# День 01. РЕД ОС. Работа с репозиториями. Пакетный менеджер. Работа с пакетами


## РЕД ОС
Российская операционная система общего назначения для серверов и рабочих станций. Занесена в Единый реестр российских программ. Сертифицирована в системе сертификации ФСТЭК России.

[Скачать образ РЕД ОС](https://redos.red-soft.ru/product/downloads/)


## Пакеты, зависимости и репозитории
Умение устанавливать, обновлять и удалять программное обеспечение относится к важнейшим навыкам работы с любой операционной системой. 

К сожалению в мире Linux, нет единого способа управления ПО, подходящего для всех дистрибутивов, разные семейства предполагают различные подходы, хотя общие принципы во многом совпадают.

 **Пакет** - это архив специального формата, который содержит все необходимые приложению бинарные и конфигурационные файлы, информацию о том, как их следует разместить в файловой системе, данные о зависимостях пакета, а также список действий которые необходимо выполнить в процессе установки.

Наиболее распространенными форматами пакетов являются:

+ RPM (рекурсивный акроним RPM Package Manager, ранее Red Hat Package Manager)

+ DEB (сокращение от Debian). 

Первый используется в основанных на Red Hat дистрибутивах, а второй - во всем многочисленном семействе систем на базе Debian и его производных, включая один из самых популярных дистрибутивов - Ubuntu.

Еще одна особенность пакетов Linux вытекает из следования некоторым постулатам философии Unix, а именно каждый пакет содержит только необходимый минимум файлов и библиотек, все остальные необходимые ему компоненты указываются в качестве зависимостей.

**Метапакеты** — это пакеты, которые не содержат фактическое программное обеспечение, а зависят от других пакетов для установки. 

**Менеджеры пакетов в Linux** — это программные инструменты, которые позволяют устанавливать, удалять и управлять пакетами программного обеспечения в операционной системе Linux.

На компьютерах пакеты программ не хранятся, менеджер скачивает их автоматически во время установки.

*А откуда тогда менеджер берёт пакеты?* Он их скачивает со специальных серверов в интернете (поэтому для установки программ в Linux требуется интернет), которые называются – репозиториями.

**Репозитории** – это сервера в интернете, на которых хранятся файлы пакетов приложений Linux и другая сопутствующая информация.

Практически у каждого дистрибутива Linux есть свой репозиторий, который содержит только совместимые и поддерживаемые конкретным дистрибутивом пакеты.


## dnf
**dnf** - это менеджер пакетов, который умеет запрашивать информацию о пакетах, получать пакеты из репозиториев, устанавливать и удалять их, используя автоматическое разрешение зависимостей, а также обновлять целиком систему до последних версий пакетов. 

DNF выполняет автоматическое разрешение зависимостей для пакетов, которые обновляются, устанавливаются или удаляются, и, таким образом, позволяют автоматически определять, получать и устанавливать все доступные по зависимостям пакеты.

Основные команды
| Команда |	Описание |
|:-------:|:---------|
|dnf install <имя_пакета> | Установка пакета с заданным именем |
|dnf reinstall <имя_пакета> | Переустановка пакета |
|dnf remove <имя_пакета> | Удаление пакета |
|dnf autoremove | Удаляет все пакеты, которые не нужны системе, если они не используются другими приложениями |
|dnf info <имя_пакета> | Показать информацию о пакете |
|dnf search <имя_пакета> | Поиск пакета по имени в репозитории |
|dnf list | Вывод имен всех доступных и установленных пакетов |
|dnf list installed | Вывод списка всех установленных пакетов |
|dnf list available | Вывод списка всех доступных пакетов |
|dnf repolist all | Вывод списка всех репозиториев |
|dnf repoinfo <имя_репозитория> | Информация о репозитории |
|dnf clean all | Удаление всех метаданных, кешированных пакетов и заголовков |
|dnf history | Вывод истории об использования dnf |
|dnf groupinstall <имя_группы> | Установка всех пакетов из группы с заданным именем |
|dnf groupupdate <имя_группы> | Обновление всех пакетов из группы с заданным именем |
|dnf groupremove <имя_группы> | Удаление всех пакетов из группы с заданным именем |
|dnf groupinfo <имя_группы> | Получить список пакетов, относящихся к группе |
|dnf grouplist | Вывод имен всех существующих групп пакетов |
|dnf provides <имя_файла или пакета> | Поиск пакета, к которому принадлежит определенный файл/подпакет |
|dnf update | Обновить все пакеты в системе |
|dnf download <имя_пакета> | Загружает из репозитория пакет |
|dnf repoquery --requires <имя_пакета> | Получить список зависимостей неустановленного пакета |


## rpm
**RPM** или **RPM Package Manager** - это пакетный менеджер, используемый в дистрибутивах Linux, основанных на Red Hat. Такое же название имеет формат файлов этого пакетного менеджера.

Синтаксис утилиты rpm
```bash
rpm -режимОпции пакет
```

Утилита может работать в одном из режимов:
+ **-q**, --query - запрос, получение информации;
+ **-i**, --install - установка;
+ **-V**, --verify - проверка пакетов;
+ **-U**, --upgrade - обновление;
+ **-e**, --erase - удаление.

Некоторые из ключей программы:
+ **-v** - показать подробную информацию;
+ **-h** - выводить статус-бар;
+ **--percent** - выводить информацию в процентах о процессе распаковки;
+ **--replacefiles** - заменять все старые файлы на новые без предупреждений;
+ **-i**- получить информацию о пакете;
+ **-l** - список файлов пакета;
+ **-R** - вывести пакеты, от которых зависит этот пакет.

```bash
# проверка установленного пакета
rpm -q mysql-community-server

# вывод списка всех файлов установленного RPM-пакета
rpm -ql curl

# вывод списка всех установленных пакетов
rpm -qa code

# обновление пакетов RPM
rpm -U mc
rpm -Uvh mc

# установка пакетов 
rpm -i google-chrome-stable_current_x86_64.rpm
rpm -ivh GeoIP-1.5.0-11.el7.x86_64.rpm

# узнать к какому пакету RPM относится файл
rpm -qf /usr/lib64/libGeoIP.so.1.5.0

# запрос информации об установленном RPM-пакете
rpm -qi code

# удаление пакета
rpm -e code

# удаление пакета, оставив в системе его зависимости
rpm -e --nodeps mysql-community-server
```

## 😈 Демоны
Демон — компьютерная программа в UNIX-подобных системах, запускаемая самой системой и работающая в фоновом режиме без прямого взаимодействия с пользователем. 

Примеры демонов:
+ httpd - диспетчер служб HTTP

+ sshd – демон, отвечающий за управление службой SSH

+ mysqld - служба СУБД MySQL

В РЕД ОС есть специальный инструмент для управления службами в Linux - команда `systemctl`. 

```bash
systemctl опции команда служба
```

Команды утилиты:
+ **list-units** - посмотреть все службы (юниты) которые сейчас загружены в память, аналог опции -t
+ **start** - запустить службу linux
+ **stop** - остановить службу linux
+ **restart** - перезапустить службу
+ **try-restart** - перезапустить службу, только если она запущена
+ **is-active** - проверить запущена ли служба linux
+ **is-failed** - проверить не завершилась ли служба с ошибкой
+ **status** - посмотреть состояние и вывод службы
+ **show** - посмотреть параметры управления службой в Linux
+ **list-dependencies** - посмотреть зависимости службы linux
+ **enable** - добавить службу в автозагрузку
+ **disable** - удалить службу из автозагрузки
+ **is-enabled** - проверить если ли уже служба в автозагрузке
+ **reenable** - сначала выполнить disable потом enable для службы

Команда systemctl поддерживает и другие команды, но здесь перечислены только самые популярные.

Основные опции:
+ **-t**, **--type** - отфильтровать список служб по типу
+ **--state** - отфильтровать список служб по состоянию
+ **-a**, **--all** - показать все известные службы, даже не запущенные
+ **-q** - минимальный вывод
+ **--version** - версия программы
+ **--no-pager** - не использовать постраничную навигацию
+ **--no-legend** - не выводить подробное описание

Большинство действий выполняются именно командами, а опции только помогают сделать вывод более удобным.




## Практическое задание
>[!CAUTION]
> Все проделанные Вами действия должны быть отражены в отчёте в виде скриншотов

1. Используя VirtualBox создать виртуальную машину и установить на неё операционную систему РЕД ОС 8

1. В ОС создать учетную запись ***user*** с паролем ***user***. Для учетной записи ***root*** дать пароль ***root***

1. Установить в РЕД ОС дополнения гостевой операционной системы. Прописать прокси сервер ***250-prep***

1. Прописать прокси-сервер в конфигурационном файле менеджера пакетов **dnf**. В файл конфигурации `/etc/dnf/dnf.conf` необходимо добавить следующую строку

> ```bash
> proxy=http://250-prep:3128
>```

1. Прописать прокси-сервер в командной строке запуска Chromium. Необходимо добавить следующий ключ `--proxy-server="http://250-prep:3128"`

1. Используя **dnf** обновить все пакеты. После чего сделать снимок состояния виртуальной машины

1. Используя **dnf** произвести поиск пакета по имени ***mysql***

1. Используя **dnf** сравнить состав пакета ***git*** и ***git-all***. Установить пакет ***git-all***. Создать снимок состояния виртуальной машины

1. Написать bash-скрипт сохраняющий в файл список всех установленных пакетов в именах которых присутствует подстрока *git*

1. Переработать скрипт из предыдущего задания. Организовать передачу подстроки для поиска через параметры командной строки. Результат поиска выводить в общий поток вывода. При выводе, в именах пакетов, удовлетворяющих поиску, подкрасить совпадения. Цвет подкраски на Ваше усмотрение. 

1. Установить VisualStudio Code в РЕД ОС. Отображать подробную информацию о ходе установки, а так же показать статус-бар. Создать кнопку запуска на рабочем столе для VisualStudio Code

1. Скачать пакет **mysql84-community-release-el8-1.noarch.rpm**. Установить пакет с помощью **rpm**

1. Написать bash-скрипт по поиску имен пакетов в репозиториях. Необходимо найти и вывести на экран список все пакетов, хранящихся в репозиториях, имена которых начинаются на *mysql*. Скрипт должен выводить только названия пакетов. Имя каждого найденного пакета выводится на отдельной строке. Из всех найденных пакетов, при выводе на экран выделить другим цветом текста и фона пакет mysql-community-server.

1. Используя **dnf** обновить все пакеты. Отметить изменения по сравнению с предыдущим обновление пакетов. 

1. Установить **mysql** как демон системы. Вывести информацию о состоянии работы демона **mysql**. Создать снимок состояния виртуальной машины

1. Написать bash скрипт, который выводит в терминал временный пароль учётной записи **root** СУБД MySQL, создаваемый при первом запуске. Пароль хранится в файле `/var/log/mysqld.log`. Вывести ТОЛЬКО сам ПАРОЛЬ.

1. Используя терминал Linux подключится к СУБД MySQL и сменить временный пароль для учетной записи ***root***. Задать следующий пароль - **Root_123**. Новый пароль сохранить в отчёте по практике.  

1. Создать учётную запись с полным доступом ко всем базам данных в СУБД MySql. Предоставить данной учётной записи доступ к СУБД с любого IP-адреса. В качестве имени, создаваемой учётной записи, использовать Вашу фамилию на английском языке. Установить следующий пароль - **Root_123**.  Используя терминал Linux подключится к СУБД MySQL с помощью созданной Вами учетной записи. 

1. Вывести список всех файлов установленного пакета **mysql**

1. Используя хост-машину произвести подключение к СУБД MySql на виртуальной машине. Первоначально подключиться с помощью MySql Shell.  Вывести информацию о текущей сессии подключения. Затем использую MySql Workbench создать подключение и подключиться к СУБД.  Вывести информацию со вкладки "Пользователи и привилегии".

1. Используя хост-машину и дамп базы данных(можно воспользоваться дампом из ПР25 по БД) восстановить БД. 

