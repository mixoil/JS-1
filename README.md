## JS#1
У Иннокентия много друзей. В новом 2022 году Иннокентий стал понимать, что забывает у кого когда день рождения. Кеша не очень силён в программировании, поэтому он пришел на помощь к вам как к опытным программистам.

Кеша просмотрел всю свою телефонную книгу и сформировал для вас список друзей с их именами и датами рождения. Иннокентий, в отличие от вас, не знает никаких типов данных кроме строки, поэтому оба поля: день рождения и имя, он написал в виде строки.

1. Помогите написать Иннокентию функцию ``getNextBirthdays``, которая будет из массива объектов его друзей и переданной даты формировать новый массив только из тех друзей, чьи дни рождения будут находится в промежутке от переданной даты до конца года. Друзья Кеши в новом списке должны быть отсортированы по дню рождения.

	❗Обратите внимание: ``getNextBirthdays`` может получить некорректный список друзей или дату отсчета. В таком случае функция должна вернуть пустой массив.
	* Дата отсчета считается корректной, если она передана строкой в формате ``DD.MM.YYYY``;
	* Список друзей считается корректным, если он является массивом.

2. Чтобы Иннокентию узнать у кого из его друзей в каком месяце день рождения, требуется также реализовать функцию ``getMonthsList``, которая будет возвращать список месяцев с друзьями, у которых в этом месяце день рождения. Месяцы, в которых не оказалось людей, выводить не требуется. Список месяцев надо отсортировать от января до декабря. Ваша задача - вернуть массив объектов с двумя полями:
	* ``month`` - название месяца, записывается кириллицей со строчной буквы;
	* ``friends`` - массив друзей, которые родились в месяце ``month``.
		
	❗Обратите внимание: ``getMonthsList`` может получить некорректный список друзей. В таком случае функция должна вернуть пустой массив.
	* Список друзей считается корректным, если он является массивом.

### Примеры функций ``getNextBirthdays`` и ``getMonthsList``
```js
const phoneList = [
  {
    name: "Александра",
    birthdate: "21.05.2001",
  },
  {
    name: "Егор",
    birthdate: "06.08.1976",
  },
  {
    name: "Роман",
    birthdate: "14.04.2000",
  },
  {
    name: "Василий",
    birthdate: "27.02.1980",
  },
];

getNextBirthdays('28.02.1980', phoneList);

/*
[
  {
    name: 'Егор',
    birthdate: '06.08.1976',
  },
];
*/

getMonthsList(phoneList);

/*
[
   {
      month: 'февраль',
      friends: [
         {
            name: 'Василий',
            birthdate: '27.02.1980'
         }
      ]
   },
   {
      month: 'апрель',
      friends: [
         {
            name: 'Роман',
            birthdate: '14.04.2000'
         }
      ]
   },
   {
      month: 'май',
      friends: [
         {
            name: 'Александра',
            birthdate: '21.05.2001'
         }
      ]
   },
   {
      month: 'август',
      friends: [
         {
            name: 'Егор',
            birthdate: '06.08.1976'
         }
      ]
   }
]
*/
```

3. ⭐ Иннокентий не любит тратить много денег на подарки ко дням рождения. Поэтому он попросил написать ещё одну функцию – ``getMinimumPresentsPrice``. Эта функция принимает список друзей с еще одним полем – массивом из объектов подарков, в каждом из которых указывается название подарка и его стоимость. Ваша задача – вернуть объект с двумя полями:
	* ``friendsList`` – исходный список друзей только с минимальным по стоимости подарком из исходного списка желанных презентов;
	* ``totalPrice`` – сумма цен подарков всех друзей. У некоторых друзей нет списка с желанными подарками, для таких в поле с минимальным подарком надо записывать ``undefined``, а в сумме считать стоимость такого подарка за ``0``.

	❗Обратите внимание: объекты в ``friendsList`` вместо поля ``wishList`` должны иметь поле ``present`` с объектом подарка.

	❗Обратите внимание: ``getMinimumPresentsPrice`` может получить некорректный список друзей. В таком случае функция должна вернуть пустой массив.
	* Список друзей считается корректным, если он является массивом.
	
### Пример функции ``getMinimumPresentsPrice``
```js
const phoneList = [
  {
    name: 'Александра',
    birthdate: '21.05.2001',
    wishList: [
      {
        title: 'Книга "Изучаем программирование на JavaScript"',
        price: 250,
      },
      {
        title: 'Билет на концерт Макса Коржа',
        price: 1500,
      },
      {
        title: 'Книга "Чистый код. Создание, анализ и рефакторинг"',
        price: 200,
      },
    ],
  },
  {
    name: 'Егор',
    birthdate: '06.08.1976',
    wishList: [
      {
        title: 'Годовой абонимент в библиотеку',
        price: 400,
      },
      {
        title: 'Шариковая ручка',
        price: 750,
      },
    ],
  },
  {
    name: 'Роман',
    birthdate: '14.05.2000',
  },
  {
    name: 'Василий',
    birthdate: '27.02.1980',
    wishList: [
      {
        title: 'Годовой курс обучения на ИРИТ-РтФ',
        price: 100500,
      },
      {
        title: 'Путешествие на Марс',
        price: 999999999,
      },
    ],
  },
];

getMinimumPresentsPrice(phoneList);
/*
{
   friendsList: [
      {
         name: 'Александра',
         birthdate: '21.05.2001',
         present: {
            title: 'Книга "Чистый код. Создание, анализ и рефакторинг"',
            price: 200
         }
      },
      {
         name: 'Егор',
         birthdate: '06.08.1976',
         present: {
            title: 'Годовой абонимент в библиотеку',
            price: 400
         }
      },
      {
         name: 'Роман',
         birthdate: '14.05.2000'
      },
      {
         name: 'Василий',
         birthdate: '27.02.1980',
         present:{
            title: 'Годовой курс обучения на ИРИТ-РтФ',
            price: 100500
         }
      }
   ],
   totalPrice: 101100
}
*/
```
