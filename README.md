# DateCalculator

## БГУИР Лабораторная работа 2
## Лабораторная работа1

***Создать файл, который выполняет следующее:
На вход пакетному файлу приходит цифра от 1 до 7 (как параметр пакетного файла). Данные шифры представляют дни недели (1 - это понедельник, 2 - это вторник и т.д.). Вывести в файл result.txt даты оставшихся дней по дню недели. Например, если ввели 5, то вывести даты всех оставшихся в текущем году (сейчас это 2023) пятниц.***

**Данный код является скриптом на языке Shell. Он выполняет следующие действия:**

## Работа файла SH:
```shell
#!/bin/bash
weekday=$1

current_date=$(date +"%Y-%m-%d")

next_year=$(date +"%Y" -d "+1 year")
next_year_start="${next_year}-01-01"

while [[ $current_date < $next_year_start ]]; do
    if [[ $(date +"%u" -d "$current_date") == $weekday ]]; then
        echo $current_date >> result.txt
        echo $current_date
    fi
    current_date=$(date +"%Y-%m-%d" -d "$current_date + 1 day")
done
```
`weekday=$1`: Эта строка присваивает значение первого аргумента командной строки переменной weekday.

`current_date=$(date +"%Y-%m-%d")`: Эта строка получает текущую дату и присваивает ее переменной current_date. Формат даты %Y-%m-%d означает год-месяц-день (например, 2023-10-05).

`next_year=$(date +"%Y" -d "+1 year") и next_year_start="${next_year}-01-01"`: Эти строки определяют следующий год и устанавливают его начальную дату в формате YYYY-01-01.

`while [[ $current_date < $next_year_start ]]; do (...) done`: Этот блок цикла выполняется до тех пор, пока current_date меньше next_year_start. Он использует конструкцию while и сравнивает даты с помощью оператора <.

`if [[ $(date +"%u" -d "$current_date") == $weekday ]]; then (...) fi`: Этот блок условия проверяет, соответствует ли день недели current_date значению переменной weekday. Он использует date +"%u" для получения номера дня недели (где 1 - понедельник, 2 - вторник, и т.д.) и сравнивает его с weekday.

`echo $current_date >> result.txt & echo $current_date`: Эти строки выводят current_date в файл result.txt и на экран соответственно.

`current_date=$(date +"%Y-%m-%d" -d "$current_date + 1 day")`: Эта строка увеличивает current_date на один день, используя date -d "$current_date + 1 day", и присваивает новое значение переменной current_date.

**Таким образом, код проходит через даты, начиная с текущей даты и до начала следующего года, проверяет их дни недели и выводит даты, соответствующие указанному дню недели, в файл result.txt и на экран.**

![image](https://github.com/jakxcvv/DateCalculator/assets/147064507/1a834e33-3671-4346-bf24-6d95d28e70c3)

![image](https://github.com/jakxcvv/DateCalculator/assets/147064507/6ad22476-a2f3-4961-bc38-3772ff3c26ae)
