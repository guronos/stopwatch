Секундомер, верстка адаптивная по макету.
Возможность добавления новых блоков с секундомером, каждый блок независимо расчитывает свое время, функции паузы, остановки и сброса счетчика реализованы.
Активность вкладки, загруженность процессора не влияет на результат высичления времени.
P.S. погрешность в 100ms при интервальном вызове функции - допущение в пользу производительности (функция проверяет обновление прошедшего времени не более 10 раз в секунду).

# stopwatch

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
