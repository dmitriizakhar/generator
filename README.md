# Задание отбора Tinkoff Generation ML 'Языковая модель'
## Генератор текстов

Напишите утилиту, которая на основе заданных текстов генерирует свои.

**Это задание даже важнее математики**, но, вообще говоря, дописывать его до конца не обязательно.

**Можете решать любыми методами**. Приведенная ниже архитектура — это совет, а не строгое техзадание. Из ограничений только запрет на использование читерских внешних библиотек типа nltk – используйте только то, что есть по умолчанию в питоне.

Создайте репозиторий на гитхабе, залейте туда код и вставьте ссылку в форму. Обновляйте почаще — автор может, не дожидаясь конца отбора, связаться с вами и помочь советом.

## Как автор предлагает

Автор когда-то сам такое писал и предлагает следующий простой и эффективный метод: [биграммнная языковая модель](https://ru.wikipedia.org/wikSi/N-грамма).

По большому тексту для каждого слова составляется список слов, которые могут идти после него. В ML это называется *обучением*.
Хранить эту информацию можно в виде *словаря*: {слово : [одно-следующее-слово, другое-следующее-слово, ...]}.

При самой генерации следует выбрать какое-нибудь начальное слово. В ML оно называется *состоянием*. Все следующие слова последовательно случайно выбираются из списка слов, идущих после текущего в словаре. Выбор из этого словаря можно делать через `random.choice`. В ML это называется *сэмплированием*.

Основной код должен быть разбит на две части: обучение и генерация.

### Обучение:

* Считать входные данные из файлов.
* Очистить тексты: выкидывать неалфавитные символы, приводить к lowercase.
* Разбить тексты на слова (в ML это называется *токенизацией*).
* Сохранить модель в каком-нибудь формате, который позволяет восстановить слова и частоты биграмм.

### Генерация:

* Загрузить модель.
* Инициализировать её каким-нибудь сидом.
* Сгенерировать последовательность нужной длины.

### Детали:

* Удобно создать для обучения и генерации отдельные файлы и реализовать консольный интерфейс к ним через `argparse`.
* Для работы с текстами может пригодиться библиотека регулярных выражений `re`.
* Соблюдайте, пожалуйста, `pep8`. Пишите хороший код.
* Следуйте принципам ООП. Оберните модель в класс, у которого будет методы fit и generate.
* Для сохранения модели удобно использовать `pickle` или `dill`.
* Обучать модель можно на чем угодно – от «Войны и мира» и «Гарри Поттера» до текстов Монеточки и протоколов съездов КПСС.

Задание большое и творческое. Нам интересно оценить ваши знания питона и общее умение программировать. Не дописали до конца — не страшно, отправляйте, что есть.

### FAQ по всему отбору

> Правда ли, что от нас хотят генерацию последовательности слов, а не предложений?

Если придумаешь, как прикрутить пунктуацию и разбиение на предложения — большой плюс.
