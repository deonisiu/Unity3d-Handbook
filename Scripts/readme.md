# Справочник по скриптам в Unity

## Списки и коллекции в Unity

Для хранения списков данных в Unity помимо массивов используются три основных класса:
1. Класс List
2. Класс Dictionary 
3. Класс Stack

### List
Если необходим неупорядоченный, последовательный список элементов любого одного типа данных, который растет и сжимается. Удобно добавлять и удалять элементы и последовательно их перебирать.
* Объекты класса List могут изменяться в инспекторе объектов Unity.
Пример кода:
``` C#
[System.Serializable] // позволяет встроить отображение класса в инспекторе Unity
public class Enemy {
	public int Health = 100;
	public int Damage = 10;
	public int ID = 0;
}
//------------------

public List<Enemy> Enemies = new List<Enemy>();

// метод Add вставляет элемент в конец списка
Enemies.Add (new Enemy());

// удалить элемент в начале списка (с индексом 0)
Enemies.RemoveRange(0, 1);

// обойти элементы списка
foreach(Enemy en in Enemies) {
	Debug.Log (en.ID);
}

// удалить все элементы списка в цикле
// обойти список в обратном порядке
for(int i=Enemies.Count-1; i>=0; i--) {
	Enemies.RemoveAt(i);
}
```

### Dictionary
Если нужна возможность быстро находить элементы по ключу, лучше всего испольщовать класс Dictionary. Для каждого элемента в Dictionary указывается пара значений *ключ*-*идентификатор*. Dictionary позволяет получить мгновенный доступ к элементу, зная его ключ. Класс Dicionary работает очень быстро, это делает его весьма полезным, когда нужен быстрый поиск данных по ключевым значениям.
Пример кода:
``` C#
// база данных слов, пары ключ/значение: <Word, Score>
public Dictionary<string, int> WordDatabase = new Dictionary<string, int>();

// добавить в базу
WordDatabase.Add("hello", 5);
WordDatabase.Add("car", 3);

// получить из базы с помощью ключа
Debug.Log("hello number is : " + WordDatabase["hello"].ToString());
```

### Stack
Стек - особый вид списка, основанный на модели "Последним вошел - первым вышел" (Last in, first out, LIFO). Вы можете добавлять и извлекать элементы из конца списка.
Пример кода:
``` C# 
// создание объекта PlayingCard
public ckass PlayingCard {
	public string Name;
	public int Attack;
	public int Defense;
}

public Stack<PlayingCard> CardStack = new Stack<PlayingCard> ();

//----------------

// добавить в стек
CardStack.Push(new PlayingCard());

// удалить из стека
CardStack.Pop();
```