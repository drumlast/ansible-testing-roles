# Домашнее задание к занятию 5 «Тестирование roles»

---

## Molecule

Запуск `molecule test -s ubuntu_xenial` и вывод команды:
![molecule-clickhouse-role1](img/01.png)
![molecule-clickhouse-role2](img/02.png)
![molecule-clickhouse-role3](img/03.png)

Создание сценария `default` при помощи `molecule init scenario`
![molecule-vector-role-init](img/04.png)

Запуск тестирования сценария:
![molecule-vector-role-test1](img/05.png)
![molecule-vector-role-test2](img/06.png)
![molecule-vector-role-test3](img/07.png)
![molecule-vector-role-test4](img/08.png)
![molecule-vector-role-test5](img/09.png)

Тег на коммит с рабочим сценарием `git tag -a v1.0.1 -m "Release 1.0.1"`

---

## Tox

Все отработало успешно после выполнения команды `tox`
![vector-role-tox1](img/10.png)
![vector-role-tox2](img/11.png)

Тег на коммит с рабочим сценарием `git commit -m "Tox molecule_podman` - `git tag -a v1.0.0`