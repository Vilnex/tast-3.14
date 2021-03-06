# инструкцию по работе с GIT
-----------
----
![](/Pic/2560px-Git-logo.svg.png)
LICENSE:[MIT](./License.md)

---------
----
### Содержиние:
_Git — это набор консольных утилит, которые отслеживают и фиксируют изменения в файлах (чаще всего речь идет об исходном коде программ, но вы можете использовать его для любых файлов на ваш вкус). С его помощью вы можете откатиться на более старую версию вашего проекта, сравнивать, анализировать, сливать изменения и многое другое._







---

### Устанока:
[Уставнока](./Installation.md)

-----

### Настройка:
_Итак, мы установили GIT, теперь нужно добавить немного настроек. Есть довольно много опций, с которыми можно играть, но мы настроим самые важные: наше имя пользователя и адрес электронной почты. Откройте терминал и запустите команды:_
```
git config --global user.name "My Name"
git config --global user.email myEmail@example.com
```
_Теперь каждое наше действие будет отмечено именем и почтой. Таким образом, пользователи всегда будут в курсе, кто отвечает за какие изменения — это вносит порядок._

---

### Создание нового репозитория

_Как мы отметили ранее, GIT хранит свои файлы и историю прямо в папке проекта. Чтобы создать новый репозиторий, нам нужно открыть терминал, зайти в папку нашего проекта и выполнить команду `init`. Это включит приложение в этой конкретной папке и создаст скрытую директорию `.git`, где будет храниться история репозитория и настройки._
```
$ mkdir Desktop/Папка вашего проекта/
$ cd Desktop/Папка вашего проекта/
$ git init
```

- Командная строка должна выдать вот такое сообщение
```
Initialized empty Git repository in /home/user/Desktop/Папка вашего проекта/.git/
```
----

### Команды GIT:

- Теперь рассмотрим команды GIT, их немного больше и именно с помощью них вы будете выполнять все основные действия.А сейчас мы рассмотрим основные команды GIT,которые вам понадобятся для начала работы.


- [git add](./add.md)

- [git status](./status.md)

- [git commit](./commit.md)

- [git reset](./reset.md)

- [git rm](./rm.md)

- [git mv](./mv.md)

- [git clean](./clean.md)

- [git diff](./diff.md)

----

### Коммит

_Коммит представляет собой состояние репозитория в определенный момент времени. Это похоже на снапшот, к которому мы можем вернуться и увидеть состояние объектов на определенный момент времени.
Чтобы зафиксировать изменения, нам нужно хотя бы одно изменение в области подготовки (мы только что создали его при помощи `git add`), после которого мы может коммитить:_

```
$ git commit -m "Имя вашего коммита"
````
- Эта команда создаст новый коммит со всеми изменениями из области подготовки (добавление файла hello.txt). Ключ -m и сообщение "Вашего коммита" — это созданное пользователем описание всех изменений, включенных в коммит. Считается хорошей практикой делать коммиты часто и всегда писать содержательные комментарии.
----

### Настройка .gitignore

_В большинстве проектов есть файлы или целые директории, в которые мы не хотим (и, скорее всего, не захотим) коммитить. Мы можем удостовериться, что они случайно не попадут в `git add` при помощи файла `.gitignore`_

- Создайте вручную файл под названием .gitignore и сохраните его в директорию проекта.

- Внутри файла перечислите названия файлов/папок, которые нужно игнорировать, каждый с новой строки.

- Файл .gitignore должен быть добавлен, закоммичен и отправлен на сервер, как любой другой файл в проекте.

##### Вот хорошие примеры файлов, которые нужно игнорировать:

- Логи
- Артефакты систем сборки
- Папки node_modules в проектах node.js
- Папки, созданные IDE, например, Netbeans или IntelliJ
- Разнообразные заметки разработчика.

Файл .gitignore, исключающий все перечисленное выше, будет выглядеть так:

```
*.log
build/
node_modules/
.idea/
my_notes.txt
```
----

### Работа с ветками

_Ветвление — это возможность работать над разными версиями проекта: вместо одного списка с упорядоченными коммитами история будет расходиться в определённых точках. Каждая ветвь содержит легковесный указатель HEAD на последний коммит, что позволяет без лишних затрат создать много веток. Ветка по умолчанию называется master, но лучше назвать её в соответствии с разрабатываемой в ней функциональностью._

- _Итак, есть общий указатель `HEAD` и `HEAD` для каждой ветки. Переключение между ветками предполагает только перемещение `HEAD` в `HEAD` соответствующей ветки._

![](/Pic/Ветка.png)

- ##### Команды

- `git branch` <имя ветки> — создаёт новую ветку с HEAD, указывающим на HEAD. Если не передать аргумент <имя ветки>, то команда выведет список всех локальных веток;
- `git checkout` <имя ветки> — переключается на эту ветку. Можно передать опцию -b, чтобы создать новую ветку перед переключением;
- `git branch` -d <имя ветки> — удаляет ветку.



    
    
_Локальный и удалённый репозитории могут иметь немало ветвей, поэтому когда вы отслеживаете удалённый репозиторий — отслеживается удалённая ветка `(git clone привязывает вашу ветку master к ветке origin/master удалённого репозитория)`._



- ##### Привязка к удалённой ветке:

- `git branch` -u <имя удалённого репозитория>/<удалённая ветка> — привязывает текущую ветку к указанной удалённой ветке;
- `git checkout` --track <имя удалённого репозитория>/<удалённая ветка> — аналог предыдущей команды;
- `git checkout -b` <ветка> <имя удалённого репозитория>/<удалённая ветка> — создаёт новую локальную ветку и начинает отслеживать удалённую;
- `git branch --vv` — показывает локальные и отслеживаемые удалённые ветки;
- `git checkout` <удалённая ветка> — создаёт локальную ветку с таким же именем, как у удалённой, и начинает её отслеживать.

- ##### Слияние

_Ветку, в которую мы хотим слить изменения, будем называть основной, а ветку, из которой мы будем их сливать, — тематической.

 Слиние включает в себя создание нового коммита, который основан на общем коммите-предке двух ветвей и указывает на оба HEAD в качестве предыдущих коммитов. Для слияния мы переходим на основную ветку и используем команду `git merge <тематическая ветка>`._

![](/Pic/Слияние.png)

- Если обе ветви меняют одну и ту же часть файла, то возникает конфликт слияния — ситуация, в которой Git не знает, какую версию файла сохранить, поэтому разрешать конфликт нужно собственноручно. Чтобы увидеть конфликтующие файлы, используйте `git status`.

##### Перемещение

Для перемещения используется команда `git rebase <основная ветка> <тематическая ветка>,` которая воспроизводит изменения тематической ветки на основной; HEAD тематической ветки указывает на последний воспроизведённый коммит.

#### Откат коммитов — revert и reset

_Похожие дебаты по поводу того, что лучше использовать, возникают, когда вы хотите откатить коммит. Команда `git revert <коммит> `создаёт новый коммит, отменяющий изменения, но сохраняющий историю, в то время как `git reset <коммит>` перемещает указатель `HEAD`, предоставляя более чистую историю (словно бы этого коммита никогда и не было). Важно отметить, что это также означает, что вы больше не сможете вернуться обратно к этим изменениям, например, если вы всё-таки решите, что отмена коммита была лишней._

----

#### Клонирование репозитория

- _Сейчас другие пользователи GitHub могут просматривать ваш репозиторий. Они могут скачать из него данные и получить полностью работоспособную копию вашего проекта при помощи команды `clone`._

`$ git clone "Ссылка на ваш Github"`

- Новый локальный репозиторий создается автоматически с GitHub в качестве удаленного репозитория.

----

#### Конфликт слияния

Предполагается ситуация: есть ветка `master` и есть ветка `feature.` В изъятии веток есть комиссии, сделанные после рассхождения веток. В ветку masterпытаемся влить ветку `feature( git merge feature)`, встречаем конфликт, т.к. в захвате веток есть изменения в одной и той же строке в файле `index.html.`

При возникновении конфликта, репозиторий находится в состоянии прерванного слияния. Необходимо оставить в конфликтных ситуациях только нужный код, проиндексировать изменения и зафиксировать.

````
git merge feature                 # влить в активную ветку изменения из ветки feature 
git merge-base master feature     # показать хэш важную общую коммит для двух принимаемых веток 
git checkout --ours index.html    # оставить в конфликтном файле (index.html) состояние ветки, В КОТОРУЮ мы вливаем (в видимости — из ветки master) 
git checkout --theirs index.html # оставляем в конфликтном файле (index.html) состояние ветки, ИЗ КОТОРОЙ мы вливаем (в видимости — из ветки feature) 
git checkout --merge index .html   # показать в конфликтном файле (index.html) сравнение свойств сливаемых веток (для ручного употребления)
git checkout --conflict=diff3 --merge index.html # показать в конфликтном файле (index.html) сравнение характеристик сливаемых веток плюс то, что было на месте спора в коммите, на кого разошлись сливаемые ветки
git reset --hard   # это закончилось прерванное слияние, восстановить восстановление директории и индекс, как было в момент коммита, на котором произошло событие HEAD, а я пойду немного поплачу 
git reset --merge # это закончилось прерванное слияние, но оставить изменения, не закоммиченные до слияния (для обнаружения, когда слияние делается не на чистом статусе) 
git reset --abort # то же, что и строки выше
````
---

#### Удалённые репозитории

_Пока что мы обсуждали использование Git только на локальной машине. Однако мы можем хранить историю коммитов удалённых репозиториев, которую можно отслеживать и обновлять. `git remote -v` выводит список удалённых репозиториев, которые мы отслеживаем, и имена, которые мы им присвоили._

_При использовании команды `git clone <url репозитория>` мы не только загружаем себе копию репозитория, но и неявно отслеживаем удалённый сервер, который находится по указанному адресу и которому присваивается имя origin._

Наиболее употребляемые команды:

````
git remote add <имя> <url> — добавляет удалённый репозиторий с заданным именем;
git remote remove <имя> — удаляет удалённый репозиторий с заданным именем;
git remote rename <старое имя> <новое имя> — переименовывает удалённый репозиторий;
git remote set-url <имя> <url> — присваивает репозиторию с именем новый адрес;
git remote show <имя> — показывает информацию о репозитории.

Следующие команды работают с удалёнными ветками:

git fetch <имя> <ветка> — получает данные из ветки заданного репозитория, но не сливает изменения;
git pull <имя> <ветка> — сливает данные из ветки заданного репозитория;
git push <имя> <ветка> — отправляет изменения в ветку заданного репозитория. Если локальная ветка уже отслеживает удалённую, то можно использовать просто git push или git pull.
````
----












GIT logo by Jason Long - http://git-scm.com/download















ads/logos, License:[CC BY 3.0](https://creativecommons.org/licenses/by/3.0/) 