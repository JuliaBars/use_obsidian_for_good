## 📅 Планы на сегодня
- [ ] посмотреть
- [ ] почитать
- [ ] курсики пройти
 ---
> [!important] Выбрать что почитать
```dataview
TABLE WITHOUT ID file.link AS Читать
WHERE contains(file.tags, "#tbd/read")
LIMIT 5
```
> [!todo] Выбрать что посмотреть
```dataview
TABLE WITHOUT ID file.link AS Видео
WHERE contains(file.tags, "#tbd/video")
LIMIT 5
```
> [!success] Курсы

```dataview
TABLE WITHOUT ID 
	file.link AS "Курс",
	Прогресс_Бар AS "Прогресс",
	Тема,
	URL
FROM "Courses"
```
> [!example] Книги

```dataviewjs
dv.table(["Книги", "Прогресс", "Тема", "URL"], 
    dv.pages('"Книги"')
    .map(b => [
        b.file.link,
        `<p><progress max=100 value=${(b.read/b.total*100).toFixed(0)}></progress> ${(b.read/b.total*100).toFixed(0)}%</p>`,
        b.Тема,
        b.URL
    ])
)
```

> [!abstract] Рандомные заметки
```dataview
TABLE WITHOUT ID file.link AS Заметки
WHERE !startswith(file.folder, "Templates") AND !startswith(file.folder, "Courses") AND !startswith(file.folder, "Todo")
LIMIT 5
```



<% await tp.file.move("Todo/" + tp.date.now("D MMMM YYYY")) %>
