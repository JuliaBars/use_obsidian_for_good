## 📅 Планы на сегодня
- [ ] посмотреть
- [ ] почитать
- [ ] курсики пройти
 ---
> [!important] Выбрать что почитать
```dataview
TABLE WITHOUT ID file.link AS Читать
WHERE contains(file.tags, "#tbd/read")
```

> [!todo] Выбрать что посмотреть
```dataview
TABLE WITHOUT ID file.link AS Видео
WHERE contains(file.tags, "#tbd/video")
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


> [!abstract] Рандомные заметки
```dataview
TABLE WITHOUT ID file.link AS Заметки
WHERE !startswith(file.folder, "Templates") AND !startswith(file.folder, "Courses") AND !startswith(file.folder, "Todo")
LIMIT 5
```



<% await tp.file.move("Todo/" + tp.date.now("D MMMM YYYY")) %>
