# TP-lab02
Лабораторная работа №2
Часть 1
1. Создала пустой репозиторий на github.com под названием «tp-lab2»
2. Выполняю инструкцию по созданию первого коммита на странице репозитория

В файл README.md ввожу текст echo "# TP-lab02" >> README.md 
Инициализирую git init 
Добавляю README.md git add README.md
Делаю коммит git commit -m "first commit"
Создаю ветку main git branch -M main
Привязываюсь к репозиторию git remote add origin
git pull --rebase origin main
Пушу в ветку main git push origin main

3. Реализовываю программу с плохим стилем кода

cat > "Hello world.cpp" << EOF
#include <iostream>

using namespace std;
int main(int argc, char** argv){
 cout << "Hello world" << endl;
}
EOF

4. Добавляю этот файл в локальную копию репозитория
git add "Hello world.cpp"

5. Делаю коммит git commit -m "Bad style"
6. Изменяю исходный код:  

Вызываю редактор nano sudo nano "Hello world.cpp"
В редакторе меняю код программы на

include <iostream>
include <string>
using namespace std;
int main() {
cout << "Hello world!";
string name;
cout << "Please enter name";
cin >> name;
cout << "Hello world from " << name;
}

7. git commit -a -m "Changed cpp file"
8. git push origin main
9. git log

Часть 2
1. Создаю локальную ветку patch1
git checkout -b patch1
2. Вношу изменения в ветке patch1 по исправлению кода и избавления от using namespace std
В файле "Hello world.cpp"
include <iostream>
include <string>
int main() {
std::string name;
std::cout << "Please enter name";
std::cin >> name;
std::cout << "Hello world from " << name;
}
3. git add "Hello world.cpp"
git commit -m "patched hello_world.cpp"
git push origin patch1
4. Проверяю, что ветка patch1 доступна в удалённом репозитории
5. Создаю pull-request patch1 -> main
6. В локальной копии в ветке patch1 добавляю в исходный код комментарии
7. git add "Hello world.cpp"
git commit -m "added comment"
git push origin patch1
8. Проверяю, что новые изменения есть в pull-request
9. Выполняю слияние веток и удаляю ветку patch1
10. git checkout main
git pull origin main
11. git log
12. git branch -d patch1

Часть 3
1. Создаю новую локальную ветку patch2
git checkout -b patch2
2. Изменяю code style с помощью утилиты clang-format.
brew install clang-format
clang-format -i -style=Mozilla "Hello world.cpp"
3. git add "Hello world.cpp"
git commit -m "changed codestyle"
git push origin patch2
4. В ветке main в удаленном репозитории изменяю комментарии
5. Убеждаюсь, что в pull-request появились конфликты
6. Исправляю конфликты
git pull origin main --rebase
nano "Hello world.cpp"
git rebase --continue
7. git push -f origin patch2
8. Конфликты пропали
9. Merge pull request
