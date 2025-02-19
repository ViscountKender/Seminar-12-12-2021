# Инструкция по работе с Git и удалёнными репозиториями

## Что такое Git?

Git - одна из реализаций распределённых систем контроля версий, имеющая как лольную версионность, так и версионность на сервере. Git является самой популярной системой контроля версий на сегодняшний день.

## Подготовка репозитория
Для того, чтобы создать репозиторий в указанной папке используется команда *git init*. Для этого достаточно написать команду *git init* в папке с будущем репозиторием. Это включит приложение в этой конкретной папке и создаст скрытую директорию .git, где будет храниться история репозитория и настройки. Это включит приложение в этой конкретной папке и создаст скрытую директорию .git, где будет храниться история репозитория и настройки.   


## Создание фиксаций
### Просмотр информации о изменениях

Для того, чтобы посмотреть информацию об изменениях, сделанных в текущей ветке, необходимо использовать команду *git status*. Для этого достаточно использовать *git status* в папке с репозиторием

### Добавление файла к коммиту
Для того, чтобы добавить файл к новому коммиту("сохранению") необходимо использовать команду *git add*. Используется она следующим образом: в папке с репозиторием пишем команду *git add <имя файла>*

### Создание коммитов

Для создания новой фиксации необходимо использовать команду *git commit*. Используется она следующим образом: в папке с репозиторием пишется команда *git commit -m "<сообщение к коммиту>"*. Все файлы коммита должны быть предворительно добавлены с помощью команды *git add*. Сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО***

## Перемещение между сохранениями
Для перемещения между коммиитами необходимо использовать команду *git checkout*. Используется она следующим образом в папке с репозиторием: *git checkout <номер комиита>*.

## Журнал изменений
Для просмотра журнала изменений необходимо использовать команду *git log*. Для этого нужно в папке с репозиторием написать *git log*

## Ветки в Git
### Создание веток в Git
Для того, чтобы создать новую ветку необходимо использовать команду *git brnach*. Используется она следующим образом в папке с репозиторием: *git branch <название ветки>*.
### Просмотр списка веток
Для того, чтобы просмотреть список веток необходимо использовать команду *git branch*. Для этого в папке с репозиторием надо набрать команду *git branch*

### Переход между ветками
Для того, чтобы перейти на другую ветку необходимо использовать команду *git checkout*. Используется она в папке с репозиторием следующим образом: *git checkout <название ветки>*.

## Слияние веток и разрешение конфликтов    
### Слияние веток
Для слияния веток необходимо использовать команду *git merge*. Используется она следующим образом: Для начала ***ОБЯЗАТЕЛЬНО*** перейти на ветку, куда мы сливаем изменения, после чего надо воспользоваться командой *git merge <название сливаемой ветке>*. Слияние может произойти автоматически, а может вознить конфликт. Про разрешение конфликтов смотри дальше.     
### Разрешение конфликтов при слиянии   
Помимо сценария, описанного в предыдущем пункте, конфликты регулярно возникают при слиянии ветвей или при отправке чужого кода. Иногда конфликты исправляются автоматически, но обычно с этим приходится разбираться вручную — решать, какой код остается, а какой нужно удалить. Посмотреть список не объединенных файлов можно с помощью команды git status. После редактирования конфликтной области и сохранения файла, нужно сообщить git о разрешении конфликта с помощью индексирования этого файла (после чего он перейдет в состояние «измененный»).   

## Удаление веток   
Прежде чем что-либо удалять необходимо посмотреть какие ветки у вас есть. Для того чтобы посмотреть локальные ветки используйте такую команду в папке с репозиторием:   
git branch  
Команда выведет список локальных веток, а текущая ветка будет выделена зеленым цветом и звездочкой. Для того чтобы удалить ветку необходимо использовать ту же команду branch с опцией -d. Например, для того чтобы удалить ветку (new_branch) выполните такую команду: 
git branch -d new_branch    
Если в этой ветке есть не зафиксированные изменения или коммиты, не отправленные на сервер, то программа может отказаться её удалять. Для того чтобы всё же удалить такую ветку используйте опцию -D:   
git branch -D new_branch   
## Настройка .gitignore 
В большинстве проектов есть файлы или целые директории, в которые мы не хотим (и, скорее всего, не захотим) коммитить. Мы можем удостовериться, что они случайно не попадут в git add -A при помощи файла .gitignore    
* Создайте вручную файл под названием .gitignore и сохраните его в директорию проекта.  
* Внутри файла перечислите названия файлов/папок, которые нужно игнорировать, каждый с новой строки.    
* Файл .gitignore должен быть добавлен, закоммичен и отправлен в репозиторий, как любой другой файл в проекте.   
## Удаленные репозитории    
Сейчас наш файл является локальным — существует только в директории .git на нашей файловой системе. Несмотря на то, что сам по себе локальный репозиторий полезен, в большинстве случаев мы хотим поделиться нашей работой или доставить код на сервер, где он будет выполняться    
### Подключение к удаленному репозиторию    
Чтобы загрузить что-нибудь в удаленный репозиторий, сначала нужно к нему подключиться.Cоздаlbv свой репозиторий в GitHub В нашем руководстве мы будем использовать адрес https://github.com/tutorialzine/awesome-project    
Чтобы связать наш локальный репозиторий с репозиторием на GitHub, выполним следующую команду в терминале. Обратите внимание, что нужно обязательно изменить URI репозитория на свой.    
git remote add origin https://github.com/tutorialzine/awesome-project.git   
Проект может иметь несколько удаленных репозиториев одновременно. Чтобы их различать, мы дадим им разные имена. Обычно главный репозиторий называется origin.   
### Отправка изменений на сервер    
Сейчас самое время переслать наш локальный файл на сервер. Этот процесс происходит каждый раз, когда мы хотим обновить данные в удаленном репозитории.
Команда, предназначенная для этого - push. Она принимает два параметра: имя удаленного репозитория (мы назвали наш origin) и ветку, в которую необходимо внести изменения (master — это ветка по умолчанию для всех репозиториев).
git push origin master
Counting objects: 3, done.  
Writing objects: 100% (3/3), 212 bytes | 0 bytes/s, done.   
Total 3 (delta 0), reused 0 (delta 0)   
To https://github.com/tutorialzine/awesome-project.git  
\* [new branch] master -> master    
В зависимости от сервиса, который вы используете, вам может потребоваться аутентифицироваться, чтобы изменения отправились. Если все сделано правильно, то когда вы посмотрите в удаленный репозиторий при помощи браузера, вы увидите наш файл.    
### Клонирование репозитория    
Сейчас другие пользователи GitHub могут просматривать ваш репозиторий. Они могут скачать из него данные и получить полностью работоспособную копию вашего проекта при помощи команды clone.  
git clone https://github.com/tutorialzine/awesome-project.git       
Новый локальный репозиторий создается автоматически с GitHub в качестве удаленного репозитория. 
### Запрос изменений с сервера  
Если вы сделали изменения в вашем удаленном репозитории, другие пользователи могут скачать изменения при помощи команды pull.   
git pull origin master  
From https://github.com/tutorialzine/awesome-project    
*\ branch master -> FETCH_HEAD  
Already up-to-date. 
Так как новых коммитов с тех пор, как мы склонировали себе проект, не было, никаких изменений доступных для скачивания нет.   




###### The end
