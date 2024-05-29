# консольные команды postgresql

* \dn+ 												- посмотреть все схемы
* \dt+ mail. 											- посмотреть таблицы в схеме mail
* \d+ mail.users										- посмотреть созданную таблицу с ее параметрами
* \l 													- посмотреть созданные базы (postgres, template0, template1 базы по умолчанию)
* select * from pg_shadow;							- посмотреть созданных пользователей от суперпользователя postgres (freebsd pgsql, linux postgres)