# Яндекс.Облако


Открыть [Loginom Studio] (./app/) [`<HOST-IP>/app/`](./app/), рекомендуемый браузер Google Сhrome.

[Справка](https://help.loginom.ru/) по интерфесу Loginom Studio также доступна внутри программы по URL [`<HOST-IP>/app/help/`](./app/help/)


## Начало работы

После развертывания и запуска виртуальной машины в Яндекс.Облаке необходимо выполнить следующие действия:

1. Зайти на удаленный рабочий стол системы по протоколу RDP

2. Открыть ярлык к файлу `ReadMe.txt`, в котором находится информация:

* Loginom Web Admin Password: - пароль пользователя "admin", являющимся администратором Loginom для веб-интерфейса
* Password for system user .\loginom: - пароль пользователя ОС windows, от которого запукскаются и работают службы Loginom Server и веб-сервера
	
3.  Если не работает, то проверить наличие запущенных служб согласно [инструкции](https://help.loginom.ru/adminguide/server/setup.html#zapusk-sluzhb).
Ярлыки `Запуск веб-сервера` и `Запуск сервера Loginom` - запускают необходимые работы Loginom Studio службы.
	

## Продолжение работ

На рабочем столе в RDP-сессии есть дополнительные ярлыки:
	
1.	Ярлык `GuardantActivationWizard` - приложение для активации софтварного ключа ПО Loginom, [инструкция](	https://help.loginom.ru/adminguide/licenses/sp-activate.html) по активации в файле "Активация SP-ключей"
	https://help.loginom.ru/adminguide/licenses/sp-activate.html

2.	Ярлык `Задать пароль admin` - ведет к скрипту для задания нового пароля пользователя admin, в случае его утери

3.	Ярлык `Loginom Studio` - открывает веб страницу Loginom, предпочитаемый браузер Google Сhrome
	
	
## Дополнительная помощь

Техподдержка доступна по .....
	