### Домашнее задание к занятию 1 «Введение в Ansible» Баранов Сергей

## Подготовка к выполнению

1. Установите Ansible версии 2.10 или выше.
2. Создайте свой публичный репозиторий на GitHub с произвольным именем.
3. Скачайте [Playbook](./playbook/) из репозитория с домашним заданием и перенесите его в свой репозиторий.

### Основная часть

1. Попробуйте запустить playbook на окружении из `test.yml`, зафиксируйте значение, которое имеет факт `some_fact` для указанного хоста при выполнении playbook.

![monitoring](https://github.com/12sergey12/8.1_Ansible/blob/main/images/8.1-1.png)

2. Найдите файл с переменными (group_vars), в котором задаётся найденное в первом пункте значение, и поменяйте его на `all default fact`.

![monitoring](https://github.com/12sergey12/8.1_Ansible/blob/main/images/8.1-2.png)

3. Воспользуйтесь подготовленным (используется `docker`) или создайте собственное окружение для проведения дальнейших испытаний.

```
docker-compose.yml

version: '3'
services:
  centos7:
	image: pycontribs/centos:7
	container_name: centos7
	restart: unless-stopped
	entrypoint: "sleep infinity"

  ubuntu:
	image: pycontribs/ubuntu
	container_name: ubuntu
	restart: unless-stopped
	entrypoint: "sleep infinity"
```
4. Проведите запуск playbook на окружении из `prod.yml`. Зафиксируйте полученные значения `some_fact` для каждого из `managed host`.

![monitoring](https://github.com/12sergey12/8.1_Ansible/blob/main/images/8.1-4.png)

5. Добавьте факты в `group_vars` каждой из групп хостов так, чтобы для `some_fact` получились значения: для `deb` — `deb default fact`, для `el` — `el default fact`.

![monitoring](https://github.com/12sergey12/8.1_Ansible/blob/main/images/8.1-55.png)

6.  Повторите запуск playbook на окружении `prod.yml`. Убедитесь, что выдаются корректные значения для всех хостов.

![monitoring](https://github.com/12sergey12/8.1_Ansible/blob/main/images/8.1-6.png)

7. При помощи `ansible-vault` зашифруйте факты в `group_vars/deb` и `group_vars/el` с паролем `netology`.

![monitoring](https://github.com/12sergey12/8.1_Ansible/blob/main/images/8.1-7.1.png)

![monitoring](https://github.com/12sergey12/8.1_Ansible/blob/main/images/8.1-7.png)

8. Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь в работоспособности.

![monitoring](https://github.com/12sergey12/8.1_Ansible/blob/main/images/8.1-8.png)

9. Посмотрите при помощи `ansible-doc` список плагинов для подключения. Выберите подходящий для работы на `control node`.

![monitoring](https://github.com/12sergey12/8.1_Ansible/blob/main/images/8.1-9.png)

10. В `prod.yml` добавьте новую группу хостов с именем  `local`, в ней разместите localhost с необходимым типом подключения.

![monitoring](https://github.com/12sergey12/8.1_Ansible/blob/main/images/8.1-10.png)

11. Запустите playbook на окружении `prod.yml`. При запуске `ansible` должен запросить у вас пароль. Убедитесь, что факты `some_fact` для каждого из хостов определены из верных `group_vars`.

![monitoring](https://github.com/12sergey12/8.1_Ansible/blob/main/images/8.1-11.png)

12. Заполните `README.md` ответами на вопросы. Сделайте `git push` в ветку `master`. В ответе отправьте ссылку на ваш открытый репозиторий с изменённым `playbook` и заполненным `README.md`.

---
