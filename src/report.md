## Part 1. Установка ОС

Версия Ubuntu:<br>
Команда: cat /etc/issue<br>
![UbuntuVersion](../screens/UbuntuVersion.png)

## Part 2. Создание пользователя

Создание пользователя с именем karleneg_2:<br>
Команда: sudo adduser karleneg_2<br>
![UserAdd](../screens/UserAdd_1.png)

Выдача прав администратора пользователю karleneg_2:<br>
Команда: sudo usermod -aG adm karleneg_2<br>
![UserAdd](../screens/UserAdd_2.png)

Проверка создания пользователя:<br>
Команда: cat /etc/passwd<br>
![CheckUsers](../screens/CheckUser.png)
## Part 3. Настройка сети ОС

Смена имени машины на user-1:<br>
Команда: hostnamectl set-hostname user-1<br>
Команда для проверки имени машины: cat /etc/hostname<br>
![HostName](../misc//screens/HostName.png)

### Установить временную зону, соответствующую вашему текущему местоположению.

Команда для установки временной зоны: sudo timedatectl set-timezone Europe/Mockow<br>
Вывод времени:<br>
![TimeShow_1](../screens/TimeShow_1.png)<br>

### Вывести названия сетевых интерфейсов с помощью консольной команды.

Команда для отображения названия сетевых интерфейсов: <br>
sudo ip link show<br>
![IpLinkShow](../screens/IpLinkShow.png)<br>

Устройство lo (loopback device) — это специальный виртуальный сетевой интерфейс, который ваш компьютер использует для связи с самим собой. Он используется в основном для диагностики и устранения неполадок, а также для подключения к серверам, работающим на локальном компьютере. С этим интерфейсом всегда связан адрес 127.0.0.1. У него есть dns-имя – localhost.

### Используя консольную команду получить ip адрес устройства, на котором вы работаете, от DHCP сервера.

Команда для получения ip адреса: ip r<br>
![IpShow](../screens/Ip.png)<br>

DHCP — протокол прикладного уровня модели TCP/IP, служит для назначения IP-адреса клиенту. Это следует из его названия — Dynamic Host Configuration Protocol. IP-адрес можно назначать вручную каждому клиенту, то есть компьютеру в локальной сети. Но в больших сетях это очень трудозатратно, к тому же, чем больше локальная сеть, тем выше возрастает вероятность ошибки при настройке. Поэтому для автоматизации назначения IP был создан протокол DHCP.

### Определить и вывести на экран внешний ip-адрес шлюза (ip) и внутренний IP-адрес шлюза, он же ip-адрес по умолчанию (gw).

Команда для вывода внутреннего ip-адреса шлюза: wget -q -O - ifconfig.me/ip<br>
![GWShow](../screens/GWShow.png)<br>

Команда для вывода внешнего ip-адреса шлюза: ip route | grep default<br>
![IPShow](../screens/IPShow.png)<br>

### Задать статичные (заданные вручную, а не полученные от DHCP сервера) настройки ip, gw, dns (использовать публичный DNS серверы, например 1.1.1.1 или 8.8.8.8).

Изменение параметров для: ip, gw, dns<br>
Для замены параметров: ip, gw, dns, был отредоктирован файла /etc/resolv.conf<br>
![ChangeParam](../screens/IpChange.png)<br>

Перезагрузка виртуальной машины<br>
Команда: reboot<br>

Пропинговка удаленных хостов 1.1.1.1 и ya.ru<br>
![PingHosts](../screens/Ping1111.png)<br>
![PingHosts](../screens/PingYa.png)<br>

## Part 4. Обновление ОС
Команда для получения обновления листа обновлений : sudo apt update<br>
![GETPACKAGES1](../screens/Update.png)<br>

Установка всех пакетов: sudo apt full-upgrade<br>
![GETPACKAGES2](../screens/UpdateInstall.png)<br>

Проверка обновлений: sudo apt update<br>
![GETPACKAGES3](../screens/CheckUpdate.png)<br>
Т.к команда вывела: All packages are up to date. Все пакеты были установлены.<br>

## Part 5. Использование команды sudo

Главное назначение sudo — это выполнить команду от имени другого пользователя, обычно от root. Смысл выполнения команды от root в том, что у него повышенные права доступа и, применяя sudo, обычный пользователь может выполнить те действия, на которые у него недостаточно прав.

Выдача прав на использование sudo пользователю karleneg_2:<br>
Команда: sudo usermod -a -G sudo karleneg_2<br>
![UserAdd](../screens/GiveSudo.png)

Переключение на другого пользователя<br>
Команда: su - karleneg_2<br>
![ChangeUser](../screens/ChangeUser.png)<br>

Изменение имени виртуальной машины на user:<br>
![ChangeHostname](../screens/ChangeHostname.png)<br>

## Part 6. Установка и настройка службы времени

Вывод времени(часового пояса в котором я сейчас нахожусь)<br>
Команда: date<br>
![DateShow](../screens/DateShow.png)<br>

Вывод полного отображения времени<br>
Команда: timedatectl show<br>
![FullTimeShow](../screens/FullTimeShow.png)<br>

## Part 7. Установка и использование текстовых редакторов

###Проверка наличия VIM, NANO, JOE на ОС<br>
Команда: sudo apt-get install X - (X = название редактора)<br>
VIM:<br>
![VIMCHECK](../screens/VIMCheck.png)<br>
NANO:<br>
![NANOCheck](../screens/NANOCheck.png)<br>
JOE:<br>
![JOECheck](../screens/JOECheck.png)<br>

###Создание файлов по Task:
Команда: touch test_X.txt(X - название редактора)<br>
VIM:<br>
![VIMCREATE](../screens/VIMCreate.png)<br>
NANO:<br>
![NANOCREATE](../screens/NANOCreate.png)<br>
JOE:<br>
![JOECREATE](../screens/JOECreate.png)<br>

Проверка создания:<br>
Команда: ls<br>
![CheckCreate](../screens/CheckCreate.png)<br>

### Запись своего никнейма в файлы с сохранением
VIM:<br>
Команда для открытия: vim text_vim.txt<br>
Для редактирования содержимого необходимо перейти в режим INSERT: для этого нужно нажать i<br>
Команда для выхода с сохранием: :wq<br>
![WritingNameVIM](../screens/VIMWriting.png)<br>
Проверка:<br>
![CheckSaveVIM](../screens/CheckSaveVIM.png)<br>
NANO:<br>
Команда для открытия: nano text_nano.txt<br>
Команда для выхода с сохранием: ctrl+x y<br>
![WritingNameNANO](../screens/NANOWriting.png)<br>
Проверка:<br>
![CheckSaveNANO](../screens/CheckSaveNANO.png)<br>
JOE:<br>
Команда для открытия: joe text_joe.txt<br>
Команда для выхода с сохранием: ctrl+k x<br>
![WritingNameJOE](../screens/JOEWriting.png)<br>
Проверка:<br>
![CheckSaveJOE](../screens/CheckSaveJOE.png)<br>

### Запись 21 School 21 в файлы без сохранением
VIM:<br>
Команда для выхода без сохранием: q!<br>
![VIMSchoolWriting](../screens/VIMSchoolWriting.png)<br>
Проверка:<br>
![CheckSaveNANO](../screens/CheckSaveVIM.png)<br>
NANO:<br>
Команда для выхода без сохранием: ctrl+x n<br>
![NANOSchoolWriting](../screens/NANOSchoolWriting.png)<br>
Проверка:<br>
![CheckSaveNANO](../screens/CheckSaveNANO.png)<br>
JOE:<br>
Команда для выхода без сохранием: ctrl+k q n<br>
![JOESchoolWriting](../screens/JOESchoolWriting.png)<br>
Проверка:<br>
![CheckSaveJOE](../screens/CheckSaveJOE.png)<br>
P.S: но JOE создал временный файл text_joe.txt~<br>
![JOETilda](../screens/JOETilda.png)<br>


### Поиск по содержимому файла через редактор и замена найденного содержимого
VIM:<br>
Команда для поиска: /karleneg<br>
Команда для замены: :%s/karleneg/21 School 21<br>
![VIMSearchWord](../screens/VIMSearchWord.png)<br>
![VIMReplaceWord](../screens/VIMReplaceWord.png)<br>
![VIMResult](../screens/VIMResult.png)<br>
NANO:<br>
Команда для поиска: ctrl+w<br>
Команда для замены: <br>
![NANOSearchWord](../screens/NANOSearchWord.png)<br>
![NANOReplaceWord_1](../screens/NANOReplaceWord_1.png)<br>
![NANOReplaceWord](../screens/NANOReplaceWord_2.png)<br>
![NANOResult](../screens/NANOResult.png)<br>
JOE:<br>
Команда для поиска: ctrl+k f<br>
Команда для замены: ctrl+k f <слово> r <слово><br>
![JOESearchWord](../screens/JOESearchWord.png)<br>
![JOEReplaceWord](../screens/JOEReplaceWord.png)<br>
![JOEResult](../screens/JOEResult.png)<br>

## Part 8. Установка и базовая настройка сервиса SSHD

Установка SSHD:<br>
Команда: sudo apt install openssh-server<br>
![InstallSSHD](../screens/InstallSSHD.png)<br>

Автостарт SSHD<br>
Команда: sudo update-rc.d ssh defaults<br>
![SetSSHDDefault](../screens/SetSSHDDefault.png)<br>

Перенастройка службы SSHd на порт 2022:<br>
Команда: sudo vim /etc/ssh/sshd_config<br>
![ChangePort](../screens/ChangePort.png)<br>

Вступление изменений в силу:<br>
Команда: /etc/init.d/ssh restrart<br>
![RestartSSH](../screens/RestartSSH.png)<br>

Проверка наличия процесса sshd:<br>
ps - отображает все процессы ОС. Можно использовать с grep для поиска нужного процесса.<br>
Флаги:<br>
    -ax - отображение всех процессов использую BSD стиль, принадлежащий пользователю и ОС.<br>
    -f - отображение в полном формате.<br>
    -v - отображение информации о версии.<br>
Команда: ps -a -x -f -v | grep sshd<br>
![CheckProccess](../screens/CheckProccess.png)<br>

Использование netstat -tan:<br>
Установка netstat<br>
Команда: sudo apt install net-tools<br>
![NetStatInstall](../screens/NetStatInstall.png)<br>

Объянение tan:<br>
    t - Отображение соединений через протокол TCP.<br>
    a - Отображает состояние всех сокетов.<br>
    n - Отображение IP-адреса, а не сетевого имени.<br>
Команда: netstat -tan<br>
![TANView](../screens/TANView.png)<br>
Значения столбцов:<br>
    Proto - протокол.<br>
    Recv-Q - Высокий Recv-Q означает, что данные помещаются в буфер приема TCP/IP, но приложение не вызывает recv() для их копирования из буфера TCP/IP в буфер приложения. Клиент может проверить приложение, прослушивающее порт, и убедиться, что оно работает должным образом.<br>
    Send-Q - High Send-Q означает, что данные помещены в буфер отправки TCP/IP, но не отправлены или отправлены, но не подтверждены. Таким образом, высокое значение в Send-Q может быть связано с перегрузкой сети сервера, проблемой производительности сервера или управлением потоком пакетов данных и так далее.<br>
    Local Address - локальный адрес/номер порта сокета.<br>
    Foreign Address - удаленный адрес/номер порта сокета.<br>
    State - состояние сокета.<br>
    0.0.0.0 или ::: - Все IP-адреса на локальной машине.<br>
## Part 9. Установка и использование утилит top, htop
![](../screens/.png)<br>

top - команда предоставляет сведенья о наиболее интенсивных процессах выполняемых в настоящее время.<br>
Запуск утилиты top:<br>
![WorkOfTOP](../screens/WorkOfTOP.png)<br>

Отображение uptime:<br>
Команда: top | grep top<br>
![UptimeShow](../screens/UptimeShow.png)<br>

Отображение количества авторизованных пользователей:<br>
Команда: top | grep user<br>
![UserShow](../screens/UserShow.png)<br>

Отображение общей загрузки системы:<br>
Команда: top | grep load averange<br>
![WorkloadShow](../screens/WorkloadShow.png)<br>

Отображение общего количества процессов:<br>
Команда: top |grep Tasks<br>
![FullProccessShow](../screens/FullProccessShow.png)<br>

Отображение загрузки CPU:<br>
Команда: top | grep Cpu<br>
![CPUWorkloadShow](../screens/CPUWorkloadShow.png)<br>

Отображение загрузки памяти:<br>
Команда: top | grep MiB<br>
![MemoryWorkloadShow](../screens/MemoryWorkloadShow.png)<br>

Отображение PID процесса занимающего больше всего памяти:<br>
Команда: top -o RES<br>
![PIDMemoryShow](../screens/PIDMemoryShow.png)<br>

Отображение PID процесса, занимающего больше всего процессорного времени:<br>
Команда: top -o TIME+<br>
![PIDTimeShow](../screens/PIDTimeShow.png)<br>

htop - Усовершенствованный вариант команды top. htop поддерживает работу с мышью, использует цвет в своем выводе и дает визуальные указания об использовании процессора, памяти и подкачки.<br>
Запуск утилиты htop:<br>
![WorkOfHTOP](../screens/WorkOfHTOP.png)<br>

Отображение данных отсортированный по PID, PERCENT_CPU, PERCENT_MEM, TIME:<br>
Команда:htop F6 выбор Enter<br>
PID:<br>
![PIDSortedShow](../screens/PIDSortedShow.png)<br>
PERCENT_CPU:<br>
![PERCENTCPUSortedShow](../screens/PERCENTCPUSortedShow.png)<br>
PERCENT_MEM:<br>
![PERCENTMEMSortedShow](../screens/PERCENTMEMSortedShow.png)<br>
TIME:<br>
![TIMESortedShow](../screens/TIMESortedShow.png)<br>

Отображение данных отфильтрованных для процесса SSHD:<br>
Команда: htop F4 sshd Enter<br>
![SSHDSortedShow](../screens/SSHDSortedShow.png)<br>

Отображение данных с процессом syslog, найденных, используя поиск:<br>
Команда:htop F3 syslog Enter<br>
![SyslogSortedShow](../screens/SyslogSortedShow.png)<br>

Отображение данных с добвленным выводом hostname, clock и uptime:<br>
Команда:htop F5<br>
![ApploadShow](../screens/ApploadShow.png)<br>

## Part 10. Использование утилиты fdisk
Команда: sudo fdisk -l<br>
![FDiskShow](../screens/FDiskShow.png)<br>
Название жесткого диска: ubuntu--vg-ubuntu-lv.<br>
Размер: 8854175744 байт.<br>
Количество секторов: 17293312 секторов.<br>
Размер swap: 1551356.<br>

## Part 11. Использование утилиты df
Команда: sudo df<br>
![dfShow](../screens/dfShow.png)<br>
Отчет для корневого раздела (/):<br>
    - размер раздела - 8408452.
    - размер занятого пространства - 4103804.
    - размер свободного пространства - 3855932.
    - процент использования - 52.
    - еденица измерения - Кб.

Команда: sudo df -Th<br>
![dfThShow](../screens/dfThShow.png)<br>
Отчет для корневого раздела (/):<br>
    - размер раздела - 8.1.
    - размер занятого пространства - 4.
    - размер свободного пространства - 3.7.
    - процент использования - 52%.
    - еденица измерения - Гб.
    - тип файловой системы для раздела - etx4.

## Part 12. Использование утилиты du

Использование du:<br>
Команда: sudo du<br>
![duShow](../screens/duShow.png)<br>

Вывести размер папок /home, /var, /var/log:<br>
Команда: sudo du -s -h /home /var && sudo du -s -h /var/log<br>
Флаги:<br>
    -s - отображения данных для каждого аргумента.<br>
    -h - вывод данных в читабельном для людей виде.<br>
![duDirsShow](../screens/duDirsShow.png)<br>

Вывести размер всего содержимого в /var/log:<br>
Команда: sudo du -h -a /var/log<br>
Флаг -a - выводить размер для всех файлов, а не только для директорий, по умолчанию размер выводится только для папок. <br>
![duLogShow](../screens/duLogShow.png)<br>

## Part 13. Установка и использование утилиты ncdu

Установка ncdu:<br>
Команда:sudo apt install ncdu<br>
![NCDUInstall](../screens/NCDUInstall.png)<br>

Отображение размера /home:<br>
Команда:ncdu /home<br>
![NCDUHome](../screens/NCDUHome.png)<br>

Отображение размера /var:<br>
Команда:ncdu /var<br>
![NCDUVar](../screens/NCDUVar.png)<br>

Отображение размера /var/log:<br>
Команда:ncdu /var/log<br>
![NCDULog](../screens/NCDULog.png)<br>


## Part 14. Работа с системными журналами
![](../screens/.png)<br>

Время последней успешной авторизации, имя пользователя и метод входа в систему:<br>
Команда: last<br>
![LastShow](../screens/LastShow.png)<br>
Время последней успешной авторизации: 30.10.2022 23:34.<br>
Имя пользователся: karleneg.<br>
Метод входа в система: tty1.<br>

Перезапустить службу SSHd:<br>
Команда: /etc/init.d/ssh restrart<br>

Сообщение о рестарте службы:<br>
Команда: sudo cat /var/log/syslog | grep <br>
![SysLogsCheck](../screens/SysLogsCheck.png)<br>

## Part 15. Использование планировщика заданий CRON
Установка CRON:<br>
Команда: sudo apt install cron<br>
![CRONInstall](../screens/CRONInstall.png)<br>

Планирование задачи в CRON:<br>
Команда: crontab -e<br>
![CRONCreateTask](../screens/CRONCreateTask.png)<br>

Заплонировать задачу uptime каждые 2 минуты:<br>
Команда: */2 * * * * uptime<br>
![CRONUptime](../screens/CRONUptime.png)<br>

Вывод текущих задач:<br>
Команда: crontab -l<br>
![CRONView](../screens/CRONView.png)<br>

Поиск в журналах логов о выполнении задачи uptime:<br>
Команда: sudo grep CRON /var/log/syslog<br>
![CRONCheck](../screens/CRONCheck.png)<br>

Удаление всех задач из планировщика CRON:<br>
Команда: crontab -r<br>
![CRONRemove](../screens/CRONRemove.png)<br>
