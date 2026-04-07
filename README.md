Part I

    Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).
    
    Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
    
    git pull origin master
Из https://github.com/MarsiSomeone/lb2
 * branch            master     -> FETCH_HEAD
Уже актуально.
touch README.md
git add README.md
git commit -m"add README"
[master 7e0e352] add README
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 lb2/README.md
git push origin master

Перечисление объектов: 4, готово.
Подсчет объектов: 100% (4/4), готово.
При сжатии изменений используется до 2 потоков
Сжатие объектов: 100% (2/2), готово.
Запись объектов: 100% (3/3), 304 байта | 304.00 КиБ/с, готово.
Всего 3 (изменений 1), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/MarsiSomeone/lb2.git
   c362cac..7e0e352  master -> master

    
    Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;.
    
    cat > hello_world.cpp <<EOF
> #include <iostream>    
>  
#include <iostream>    
using namespace std;  
int main()
{cout<<"aaa"<<endl; return 0;}  
> EOF



    
    
    Добавьте этот файл в локальную копию репозитория.
    
    git add hello_world.cpp
    
    Закоммитьте изменения с осмысленным сообщением.
    
    git commit -m "add"
    
    Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.
    nano hello_world.cpp

    
#include <iostream>    
    
#include <string>    
using namespace std; 
int main(){
cout<<"aaa"<<endl;

string n;
cout<<"Enter name: "
cin >> n;
cout<<endl<<"Hello world from "<<n<<endl;
 return 0;}  
 
    Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add?
    
    git commit -a -m "add update hello_world"
    
    Запуште изменения в удалёный репозиторий.
    
    git push origin master
    
    Проверьте, что история коммитов доступна в удалёный репозитории.

Part II

Note: Работать продолжайте с теми же репоззиториями, что и в первой части задания.

    В локальной копии репозитория создайте локальную ветку patch1.
    
    git branch
    
* master

    git checkout -b patch1

    
    Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;.
    
    nano hello_world.cpp
                            
#include <iostream>
#include <string>
int main(){

std::string n;
std::cout<<"Enter name: ";
std::cin >> n;
std::cout<<std::endl<<"Hello world from "<<n<<std::endl;
 return 0;}

    commit, push локальную ветку в удалённый репозиторий.
    
    git commit -a -m "patch 1 hello world update"
    git push -u origin patch1

    Проверьте, что ветка patch1 доступна в удалёный репозитории.
    
    
    Создайте pull-request patch1 -> master.
    
    
    В локальной копии в ветке patch1 добавьте в исходный код комментарии.
    
      //main function
    int main(){
    //world execute.(me)
    std::string n;//variabre
    std::cout<<"Enter name: ";//output comment
    std::cin >> n;//input function
    std::cout<<std::endl<<"Hello world from "<<n<<std::endl;//final output
     return 0;}
     
    commit, push.
    
git commit -a -m "patch 1 hello world update comment"
[patch1 325af86] patch 1 hello world update comment
 1 file changed, 7 insertions(+), 5 deletions(-)
 git push -u origin patch1


    Проверьте, что новые изменения есть в созданном на шаге 5 pull-request
    
    
    В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории.
    
    
    Локально выполните pull.
    
    git pull

    
    С помощью команды git log просмотрите историю в локальной версии ветки master.
    
    git log
commit 50ddb03db69052dec68820da0379dff61c500f3f (HEAD -> master, origin/master)
Merge: 76b6f7e 325af86
Author: MarsiSomeone <116425915+MarsiSomeone@users.noreply.github.com>
Date:   Mon Apr 6 01:56:25 2026 +0300

    Merge pull request #1 from MarsiSomeone/patch1
    
    patch 1 hello world update

commit 325af8674b3bad31b32c9e22ed84c6c08c47ee84 (origin/patch1, patch1)
Author: MarsiSomeone <sirlovaolga@gmail.com>
Date:   Mon Apr 6 01:53:51 2026 +0300

    patch 1 hello world update comment

commit 04c6003c3b9ea6548d1934beb7be30098a0ac61d
Author: MarsiSomeone <sirlovaolga@gmail.com>
Date:   Mon Apr 6 01:40:16 2026 +0300

    patch 1 hello world update

commit 76b6f7e1a6053e33e07033f1a65054a9e3b14400
Author: MarsiSomeone <sirlovaolga@gmail.com>
Date:   Tue Mar 31 22:03:13 2026 +0300

    add update hello_world

commit ca14853f9ff64a8d9e7e94dc2ae94ab54de0ee6a
Author: MarsiSomeone <sirlovaolga@gmail.com>
Date:   Tue Mar 31 21:49:23 2026 +0300

    add

commit 7e0e352ab5cbc9d78e65c4466cd7f899b4bdc19e
Author: MarsiSomeone <sirlovaolga@gmail.com>
Date:   Tue Mar 31 21:14:55 2026 +0300

    add README

commit c362cac4eeca9577ec4f1b3dd437f61e512af361
Author: MarsiSomeone <sirlovaolga@gmail.com>
Date:   Tue Mar 31 20:52:25 2026 +0300

    added sources

commit ff466379d7324a9c62a046d9c9eaf6bcfaf54c32
Author: MarsiSomeone <sirlovaolga@gmail.com>
Date:   Tue Mar 31 20:23:54 2026 +0300

    added README.md
(END)

:

    
    Удалите локальную ветку patch1.
    
    git branch -d patch1
Ветка patch1 удалена (была 325af86).

    

Part III

Note: Работать продолжайте с теми же репоззиториями, что и в первой части задания.

    Создайте новую локальную ветку patch2.
    
    git checkout -b patch2
Переключились на новую ветку «patch2»

    
    
    Измените code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla.
    
    
    
    commit, push, создайте pull-request patch2 -> master.
    
    
    В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.
    
    
    Убедитесь, что в pull-request появились конфликтны.
    
    
    Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты.
    
    
    Сделайте force push в ветку patch2
    
    
    Убедитель, что в pull-request пропали конфликтны.
    
    
    Вмержите pull-request patch2 -> master.
    
    

