# День 03. PowerShell. Создание пользователей

## `Microsoft.PowerShell.LocalAccounts`
Для управления локальными пользователями и группами в Windows существует встроенный  модуль Microsoft.PowerShell.LocalAccounts. С его помощью можно создавать или удалять локального пользователя, создавать новую группу и добавить в нее пользователей. 

```powershell
Get-Command -Module Microsoft.PowerShell.LocalAccounts

Get-Module -ListAvailable | where Name -Like "*LocalAccount*"
```

[Документация по Microsoft.PowerShell.LocalAccounts](https://learn.microsoft.com/ru-ru/powershell/module/microsoft.powershell.localaccounts/?view=powershell-5.1)

Коммандлеты в составе модуля Microsoft.PowerShell.LocalAccounts:
+ **Add-LocalGroupMember** – добавить пользователя в локальную группу
+ **Disable-LocalUser** – отключить локальную учетную запись
+ **Enable-LocalUser** – включить учетную запись
+ **Get-LocalGroup** – получить информацию о локальной группе
+ **Get-LocalGroupMember** – вывести список пользователей в локальной группе
+ **Get-LocalUser** – получить информацию о локальном пользователе
+ **New-LocalGroup** – создать новую локальную группы
+ **New-LocalUser** – создать нового пользователя
+ **Remove-LocalGroup** – удалить группу
+ **Remove-LocalGroupMember** – удалить члена из группы
+ **Remove-LocalUser** – удалить пользователя
+ **Rename-LocalGroup** – переименовать группу
+ **Rename-LocalUser** – переименовать пользователя
+ **Set-LocalGroup** – изменить группу
+ **Set-LocalUser** – изменить пользователя


### Создание пользователя(локального)
```powershell
New-LocalUser -Name ivanov -FullName "Ivanov Ivan Ivanovich" -AccountNeverExpires -PasswordNeverExpires
```

При таком создании пользователя пароль для него необходимо будет ввести в консоли сразу же после того как Вы нажмёте *Enter*

Вторая команда создает локальную учетную запись пользователя и задает пароль новой учетной записи для безопасной строки, сохраненной в `$Secure_String_Pwd`. 

```powershell
$Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force

New-LocalUser -Name ivanov -FullName "Ivanov Ivan Ivanovich" -AccountNeverExpires -PasswordNeverExpires -Password $Secure_String_Pwd
```
>[!NOTE]
> Преобразование обычной текстовой строки в защищенную строку. Эта команда преобразует строку обычного текста *P@ssW0rD!* в безопасную строку и сохраняет результат в переменной `$Secure_String_Pwd`. Чтобы использовать параметр `-AsPlainText`, команда также должна содержать параметр `-Force`.


### Добавление в группу
```powershell
Add-LocalGroupMember -Group Администраторы -Member ivanov
```



## Практическое задание
>[!CAUTION]
> Все проделанные Вами действия должны быть отражены в отчёте в виде скриншотов

1. Создать две виртуальные машины. На одну установить Windows Server 2012R2. На другую виртуальную машину установить Windows 10. Для каждой машины создать снимок состояния.

1. В Windows Server 2012R2 поднять роль Active Directory. В качестве имени домена указать Вашу фамилию на английском. Сделать снимок состояния виртуальной машины. Например:
```
ivanov.local
```

1. Создать доменную учетную запись с Вашим ФИО. Логин *admin*. Добавить в группу *Администраторы домена*.

1. Виртуальную машину с Windows 10 ввести в созданный домен. Войти под доменной учетной записью *admin*. Сделать снимок состояния виртуальной машины.

1. Получить список локальных пользователей и групп в Windows 10.

