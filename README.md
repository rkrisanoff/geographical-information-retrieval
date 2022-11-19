## Что есть в проекте с фонтанкой?

Предобработка текста:

*    стемминг  - это нормализация слов, приведение всех слов к единой форме
*   удаление стоп-слов - типа предлоги, союзы, т.д.

Что в классификации:
tfi-df - это как векторизация, но просто на учете частоты слова в документе на основе коллекции документа


## Что я предлагаю сделать

1. NER - извлечение именнованных сущностей. Так мы сможем разбить всю выборку документов (новостей) по районам - базово. Если усложнять, то можно было кластеризовать эти данные, чтобы документы объединять не по районам, но и по просто каким-то важным местам 

2. Тематическое моделирование - поиск тем среди набора документов одной территории.

Если брать пример из гетто:
1. Извлекли локации из текста
2. Определили то, где есть "Мурино" (мне ещё надо "Озерки", но я тебя не буду грузить) 
4. Возможно: посмотрели через картографические данные, что ещё из объектов есть в Мурино, которые фигурируют в новостях
5. Найти темы в этом наборе документов для определенной локации
6. Сделать визуализацию дополнительную (я ещё не додумала, но предполагаю, что - это карта с темами, диаграмма с частотами) 

## Что по статьям? 
[Analysis of combining Topic model, Sentiment, Geolocation information
approaches on Social Network](http://alumni.media.mit.edu/~pernghwa/papers/IR_final.pdf) - это самый близкий вариант к тому, что мне нравится и хочется сделать, основан на разных социальных сетях. Также используется NER - определяются большие географические районы, документы объединяются в большой документ, делается LDA (тематическое моделирование) и затем определяется тональсть текста 

[Analyzing Entities and Topics in News Articles Using Statistical Topic Models](http://www.datalab.uci.edu/papers/isi06_SENT.pdf) - здесь описана очень интересная тематическая модель и определение связей между сущностями, не думаю, что нужно глубоко смотреть, тем более текст не копируется из неё нормально

[Geographical Topic Modelling on Spatial Social Network Data](https://reader.elsevier.com/reader/sd/pii/S1877050921020445?token=F3C17793A99859327141F1554B17C18DE8060034F5321DDDC4C857557786129DA1B162A13B0F0FA9A7FD5BCF6D7F38B1&originRegion=eu-west-1&originCreation=20221118123522) - пафосная статья от ИТМО, которая не очень нравится, но они используют хорошие слова. ТУт используются гео-теги из-под постов и на этом строится тематическое моделирование

## Что по методам?


[Библиотека natasha для извлечения именованных сущностей. Внимание! Для работы алгоритма имена, локации и прочее должны быть с заглавной буквы](https://github.com/natasha/natasha)

[Ноутбук пример тематического моделирования и визуализации LDA](https://nbviewer.org/github/bmabey/hacker_news_topic_modelling/blob/master/HN%20Topic%20Model%20Talk.ipynb)


## Приложения
[Новости с фонтанки](https://drive.google.com/drive/folders/109_YyJ2iYDLpOEM47iAww8aNgi_H8daN?usp=share_link).

Файлы разбиты на 3 строчки:
- категории
- заголовок
- текст

<details>
<summary>Как использовать</summary>

```
import glob
from google.colab import drive
drive.mount('/content/drive')
news = glob.glob(f"path/to/directory/with/news/*.txt")
```
В `news` будут лежать пути к необходимым файлам
</details>
