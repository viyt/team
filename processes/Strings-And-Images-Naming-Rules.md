# Правила именования строковых ресурсов, ресурсов файлов изображений и параметров аналитики

## Общие правила
Для каждого названия существует единый формат обозначения с использованием префиксов "platform_screen_value",
где **platform** - это один из четырех вариантов:
* **ios** - используется только в ios-приложении;
* **android** - используется только в android-приложении;
* **web** - используется только в web-приложении;
* **common** - используется на всех платформах в неизменном виде;

и где **screen** - это:
* название экрана (страницы), например, **guild**, **profile**, **help**, etc.;
* название некоторой функциональности, не привязанной к какому-либо экрану (странице), например, **menu**, **alert**, etc.;
* **global** - для строк, используемых на разных экранах (страницах), и не привязанных к какой-либо определенной функциональности;

и **value** имеет специфическое значение в зависимости от типа ресурса (строки или файла изображения)

## Правила именования строк
Для строк **value** - однозначный идентификатор строки в рамках определенных перед ним префиксов

Например:
```
"common_global_level": "Уровень",
"common_season_completed": "Сезон завершен",

"ios_chat_write_first_message": "TODO",

"android_chat_cancel": "TODO",

"web_alert_not_supported_in_web_version": "Данная функция поддерживается только в мобильной версии приложения",
```


### Именование ключей

Все ключи должны быть написаны буквами в нижнем регистре и все слова/предлоги должны быть разделены знаком подчеркивания **_**


### Склонение слов после числительных.

Для конструкций типа "очко, очка, очков" используем следующие постфиксы:
* Первая форма **one**: 1 очко, 21 очко, 41 очко, etc.
* Вторая форма **two**: 2 очка, 3 очка, 4 очка, 74 очка, etc.
* Третья форма **many**: 5 очков, 0 очков, 11 очков, 237 очков, etc.

Ключ, написанный с использованием этих постфиксов должен присутствовать во всех трех формах. (= три ключа). <br />
Также слово, следующее *перед* постфиксом должно быть во множественном числе: **players**, **points**, etc. <br />
Ключ, уже имеющийся в трех формах может присутствовать также в варианте без постфикса.

Примеры:
```
"common_global_points_one": "очко",
"common_global_points_two": "очка",
"common_global_points_many": "очков",

"common_global_points": "Очки", /* Вариант без постфикса, присутствующий вместе с тремя формами */
```

Постфиксы one, two, many всегда идут последними в названии ключа.


### Значения строк

Строки всегда начинаются с буквы в верхнем регистре, и не должны целиком состоять из букв в верхнем регистре, за исключением
случаев, когда строка не может использоваться нигде в начале предложения или как отдельностоящее, как например,
склоняемые после числительных строки, с постфиксами one, two, many.


### Параметры в строках

Параметры в строки добавляются с помощью **%s**.

```
"common_season_must_invite": "Пригласите еще %s%s,\nчтобы сражаться за сезонные\nнаграды Студенческих гильдий!",
"common_season_level_reward":"Награда за открытие %s\u00A0уровня",
```

### Специальные символы

* **\u00A0** - Неразрывный пробел
* **\n** - Перенос строки (в веб-версии при билде заменяется на **\<br /\>**)
* **\u2011** - Неразрывное тире

*Примечание: Если для мобильных приложений все-таки не получится использовать строки с неэкранированным
обратным слешем в \n и в \u, то можно смело заменять их по всему файлу на \\\\n и \\\\u - для веб-версии они при билде все-равно заменятся на \n и \u*

## Правила именования событий аналитики

Для строковых значений аналитики всегда ставится преффикс **analytics**, а **value** - уникальный идентификатор в формате обозначения с использованием префиксов "key_type", то есть полный формат будет выглядеть analytics_platform_screen_key_type

где **key** - это идентификатор строкового значения аналитики;

и где **type** - это тип строкового значения, например, **click**, **parameter**, **slide**, **select** etc.;

```
"analytics_common_global_play_button_click"
"analytics_common_season_first_tab_select"
```

## Правила именования файлов изображений
Для файлов изображений **value** - уникальный идентификатор в формате обозначения с использованием префиксов "key_type_state", то есть полный формат будет выглядеть platform_screen_key_type_state

где **key** - это идентификатор изображения;

и где **type** - это тип элемента изображения, например, **icon**, **background**, etc.;

и где **state** - это состояние элемента, которое отображено в изображении, например, **normal**, **pressed**, **highlighted**, **selected**, **disabled**, **selector**, etc.;

Примеры:
```
"common_season_play_icon_normal.png"
"common_season_delete_button_selected.png"
```

**Все файлы изображений должны быть в формате .png или .pdf**

Примечание: не используйте сокращения и аббревиатуры для именования ресурсов (_bg, _ic, _btn, _sel etc.).

Примечание: для iOS должен добавляться обязательно постфикс @2x для ретина изображений и @3x для iPhone 6+/6s+ в случае использования .png. Если используется векторное изображение, то постфикс не нужен.
