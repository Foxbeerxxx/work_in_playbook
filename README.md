# Домашнее задание к занятию "`Введение в Ansible`" - `Татаринцев Алексей`


### Задание 1

1. `Добавляю в тест  test.yml`

```
  some_fact: "my_test_value" 
  ```
2. `Пробую запускать и смотрю вывод ansible-playbook -i inventory/test.yml site.yml`

![1](https://github.com/Foxbeerxxx/work_in_playbook/blob/main/img/img1.png)

3. `В вашем случае some_fact переопределяется в inventory/test.yml, но по заданию нужно найти его в group_vars`
4. `Изменяю group_vars/all/examp.yml`

```
---
some_fact: "all default fact 
```
5. `Закомментирую some_fact в inventory/test.yml`

```
---
  inside:
    hosts:
      localhost:
        ansible_connection: local
        #some_fact: "my_test_value" 

```
6. ` Проверяю ansible-playbook -i inventory/test.yml site.yml`

![2](https://github.com/Foxbeerxxx/work_in_playbook/blob/main/img/img2.png)


7. `Создаю Dockerfile в корне проекта:`
```
FROM ubuntu:22.04

RUN apt-get update && \
    apt-get install -y \
    ansible \
    python3 \
    ssh \
    sudo && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /ansible
COPY . .

CMD ["sleep", "infinity"]
```
8. `Сборка образа`

```
docker build -t ansible-lab .
```
9. `Запуск контейнера`

```
docker run -d --name ansible-test -v $(pwd):/ansible ansible-lab
```

10. `Настройка инвентаря ,создаею inventory/docker.yml`

```
all:
  hosts:
    ansible-test:
      ansible_connection: local
      some_fact: "docker_test_value"
```
![3](https://github.com/Foxbeerxxx/work_in_playbook/blob/main/img/img3.png)

11. `Проверка окружения`

```
docker exec -it ansible-test ansible --version

```
![4](https://github.com/Foxbeerxxx/work_in_playbook/blob/main/img/img4.png)

12. `Копирование prod.yml в контейнер`

```
docker cp inventory/prod.yml ansible-test:/ansible/inventory/
```

![5](https://github.com/Foxbeerxxx/work_in_playbook/blob/main/img/img5.png)


### Задание 3

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`

### Задание 4

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`
