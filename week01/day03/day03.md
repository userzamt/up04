# День 03. PowerShell. Создание пользователей

## `Microsoft.PowerShell.LocalAccounts`
Для управления локальными пользователями и группами в Windows существует встроенный  модуль Microsoft.PowerShell.LocalAccounts. С его помощью можно создавать или удалять локального пользователя, создавать новую группу и добавить в нее пользователей. 

```powershell
Get-Command -Module Microsoft.PowerShell.LocalAccounts

Get-Module -ListAvailable | where Name -Like "*LocalAccount*"
```

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


## Практическое задание
>[!CAUTION]
> Все проделанные Вами действия должны быть отражены в отчёте в виде скриншотов
