# **Шпаргалка по GIT. Работа с командной строкой.**
----
Команды для синхронизации локального репозитория с удалённым.

git remote add origin https://github.com/YandexPracticum/first-project.git — находясь в папке с локальным репозиторием, привязываем его к удалённому (URL у вас будет свой);

git push -u origin main — заливаем все файлы из локального репозитория в удалённый, который уже привязали.
====
Команды для того чтобы сделать сохранение — коммит.

git add название_файла — готовим выбранный файл к коммиту;

git add -A — чтобы ничего не потерять, можно подготовить к коммиту сразу все файлы, в которых были изменения;

git commit -m "комментарий к коммиту" — делаем коммит. К сохранённым файлам оставляем комментарий для того, чтобы проще было понять, какие сделаны изменения.

Забыл что-то добавить в коммит— git commit --amend:

Запуск команды откроет Vim. Он предложит изменить комментарий к последнему коммиту. Нажмите i, чтобы начать писать, и введите новый комментарий к коммиту. Как закончите, нажмите esc, введите :wq и нажмите Enter. Так вы сохраните новый комментарий и выйдете из Vim.

git log — посмотреть подробный лог коммитов.

git log --oneline — посмотреть короткий просмотр коммитов.

git diff — посмотреть изменения в «рабочей зоне»; они маркируются гитом как modifided, new или deleted.

git diff --staged — посмотреть изменения, добавленные в staged.

git diff a9928ab 11bada1 — сравнить изменения двух коммитов.

----
Команды для публикации изменений:

git pull — забрать изменения, сделанные другими разработчиками;

git push — опубликовать изменения в удалённый репозиторий.

----
Команды для отмены изменений:

Когда всё перестаёт работать, проще всего откатиться назад — вернуться к последнему коммиту. За это отвечает команда git reset.

git reset HEAD. Подход не затрагивает файлы, с которыми вы работаете. Если файл был изменён или добавлен, но не переведён в staged, сброс изменений этот файл не затронет.

git reset --hard. Команда удаляет вообще все изменения: и из staged, и из рабочей зоны. После неё вернуть изменения не выйдет.

Команда git reset --hard позволяет вернуться к любому коммиту. Для этого после команды указывают номер коммита — первые 7 цифр его хеша.

----
Команды для работы с ветками:

git branch название_ветки — создать новую ветку.

git checkout название_ветки — переключиться в ветку.

git checkout -b название_ветки — создать ветку и сразу переключиться в неё.

git branch -D название_ветки — удалить ветку. Чтобы всё прошло хорошо, нужно переключиться из удаляемой ветки.

git merge название_ветки — скопировать все изменения из ветки в ветку. Чтобы перенести изменения из ветки develop в ветку main, нужно находиться в ветке main и ввести git merge develop;

git revert -m основной_родитель хеш_коммита — отмена коммита слияния веток. Опция -m со значением больше 0 указывает на основную ветку, которая будет сохранена.

git revert хеш_коммита — отмена изменений выбранного коммита. Он не был создан при слиянии, поэтому имеет одного предка.

git stash — скрытие незакоммиченных изменений в текущей рабочей ветке. Опция save название_стэша даёт этим изменениям имена.

git stash pop — возврат последних изменений в любой ветке.

git stash list — показ списка спрятанных во всех ветках изменений и, если для стэша не задано имя, последнего коммита в этой ветке.

git stash apply stash@{n} — возврат выбранных спрятанных изменений из листа стэша, где n — номер в нём.

git stash clear — очистка листа стеша.

----
## **Работа с командной строкой - bash**

pwd — покажи в какой я папке;

ls — покажи файлы в папке, где я сейчас;

cd first-project — перейди в папку first-project;

cd first-project/html — перейди в папку html, находящуюся в папке first-project;

cd .. — перейди на уровень выше в родительскую папку;

cd ~ — перейди в домашнюю директорию (у нас это /Users/stas_basov);

mkdir second-project — в текущей папке создай папку с именем second-project;

rm about.html — удали файл about.html;

rmdir images — удали папку images;

rm -r second-project — удали папку second-project и всё, что она содержит;

touch index.html — создай файл index.html в текущей папке;

touch index.html style.css script.js — если нужно создать несколько файлов, их имена можно вводить через пробел.

----
Быстрая навигация

↑ — показать предыдущую команду из буфера.

↓ — показать следующую команду из буфера.

Tab — автоматически дописать команду или путь.

Ctrl + A — перейти в начало строки.

Ctrl + E — перейти в конец строки.

----
Копирование и перемещение

cp — копировать файл. После команды перечисляют файлы для копирования, а затем — директорию, где должны оказаться копии.

mv — переместить файл. Синтаксис аналогичен команде cp.

----
Полезные команды

Команды можно передавать терминалу списком, разделяя двумя амперсандами &&.

Скопировать кодBASH# создали папку, перешли в неё, создали два файла, инициализировали гит mkdir simple && cd simple && touch index.html style.css && git init

----
Просмотр и редактирование

cat — вывести на экран содержимое текстового файла.

cat -n — выполнить команду cat, пронумеровав строки.

cat -s — выполнить команду cat, удалив повторяющиеся строки.

----
### **Текстовый редактор Vim**

esc — перейти в командный режим, например, для выхода из vim.

i — перейти в командный режим для редактирования, например, чтобы оставить комментарий.

esc и :q! — выйти из vim, не сохранив файл.

esc и :wq — выйти из vim, сохранив файл.


----
#### **Хеш — идентификатор коммита**

	•	Git преобразует информацию о коммитах с помощью алгоритма SHA-1 и для каждого из них 		рассчитывает уникальный идентификатор — хеш.
	•	Хеш — основной идентификатор коммита и позволяет узнать его автора, дату и содержимое 		закоммиченных файлов.
	•	Все хеши, а также таблицу соответствий хеш → информация о коммите Git хранит в папке. 	git.

----

##### **Получить сокращённый лог — git log --oneline**

Получить сокращённый лог можно с помощью команды git log с флагом --oneline (англ. «одной строкой»). В терминале появятся только первые несколько символов хеша каждого коммита и их комментарии.
Сокращённый лог полезен, если в репозитории уже много коммитов — например, сотни или тысячи. В этом случае можно быстро найти нужный по описанию.

	•	Можно вызвать не только полный лог, но и сокращённый — это делается командой git log 		--oneline.
	•	В сокращённом логе выводятся сокращённые хеши — их можно использовать точно так же, 		как и полные.

----


