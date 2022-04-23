# 🇵🇱 Polish guide

### **Wprowadzenie**
Zacznijmy od tego, co to jest wogóle ```better-sqlite3``` ?
> ```Better-sqlite3``` jest to najszybsza, najprostsza oraz coraz popularniejsza biblioteka dla SQLite3 w Node.js. Która jest dużo razy wykorzystywana do botów discord m.in w bibliotece discord.js.<br>

## Porównanie innych bibliotek
|   |wybierz 1 wiersz &nbsp;`get()`&nbsp;|wybierz 100 wierszy &nbsp;&nbsp;`all()`&nbsp;&nbsp;|wybierz 100 wierszy `iterate()` |wstaw 1 wiersz `run()`|wstaw 100 wierszy w transakcji|
|---|---|---|---|---|---|
|better-sqlite3|1x|1x|1x|1x|1x|
|[sqlite](https://www.npmjs.com/package/sqlite) i [sqlite3](https://www.npmjs.com/package/sqlite3)|11.7x razy wolniej|2.9x razy wolniej|24.4x razy wolniej|2.8x razy wolniej|15.6x razy wolniej|


## Instalacja better-sqlite3
```js
npm install better-sqlite3
```
> Musisz używać [Node.js](https://nodejs.org/en/) w wersji 10.20.1 lub nowszej. Gotowe pliki binarne są dostępne dla wersji LTS. Jeśli masz problemy z instalacją, zapoznaj się z poradnikiem [rozwiązywania problemów]().

## Użycie
```js
const db = require('better-sqlite3')('hej.db', options);

const row = db.prepare('SELECT * FROM osoby WHERE id = ?').get(userId);
console.log(row.imie, row.nazwisko, row.email);
```
> ### W notacji modułu ES6:
```js
import Database from 'better-sqlite3';
const db = new Database('hej.db', options);
```

## Przykłady komend do bazy danych:

 Tworzenie tabeli "nazwa_tabeli", jeżeli nie istnieje z kolumnami "id", "data", "admin", "powod"
```js
db.prepare('CREATE TABLE IF NOT EXISTS nazwa_tabeli (id, data, admin, powod)').run()
```

---

 Tworzenie nowego wiersza w tabelii "nazwa_tabeli" z kolumnami "id", "nazwa" i wartościami "id serwera, gdzie wywołano komendę" i "nazwa serwera, gdzie wywołano komendę"
```js
db.prepare('INSERT INTO nazwa_tabeli (id, nazwa) VALUES (?, ?)').run(message.guild.id, message.guild.name)
```

---

 Aktualizowanie tabeli "nazwa_tabeli", ustawianie kolumny "status" na '(ZMIANA W REKLAMIE) OCZEKUJE NA WERYFIKACJĘ', gdzie wartość kolumny "id" to id serwera, gdzie wywołano komendę
```js
db.prepare('UPDATE nazwa_tabeli SET status = ? WHERE id = ?').run('(ZMIANA W REKLAMIE) OCZEKUJE NA WERYFIKACJĘ', message.guild.id)
```

---

 Wyciąganie wszystkich danych (* w miejscu *) lub konkretnej kolumny (nazwa_kolumny w miejscu *) z tabeli "nazwa_tabeli", gdzie kolumna "id" równa się id serwera, gdzie wywołano komendę
```js
db.prepare('SELECT * FROM nazwa_tabeli WHERE id = ?').get(message.guild.id)
```

---

 Usuwanie danych z tabeli "nazwa_tabeli" wiersza, gdzie kolumna "id" ma wartość id serwera, gdzie wywołano komendę
```js
db.prepare('DELETE FROM nazwa_tabeli WHERE id = ?').run(message.guild.id) 
```

> Wszystkie powyższe przykłady są stosowane oraz kompatybilne do botów discord. [discord.js](https://discord.js.org/#/)

# 🇬🇧 English guide (Soon)

### Announcements of the guide

The **English version** of the guide will be available soon :]
