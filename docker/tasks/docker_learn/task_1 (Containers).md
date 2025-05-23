# Запускаем Docker контейнеры в разрезе мониторинга

- Читаем правила [Пункт 2](https://github.com/lamjob1993/linux-monitoring/blob/main/navigation/others/%D0%9F%D1%80%D0%B5%D0%B4%D0%B8%D1%81%D0%BB%D0%BE%D0%B2%D0%B8%D0%B5%20%D0%BA%20%D0%BA%D1%83%D1%80%D1%81%D1%83.md).

## Task 1
- Запускаем контейнеры "на коленке" в фоновом режиме.

### Шаг 1
- Запускаем **Prometheus**
- Возьмем [за пример запуска](https://github.com/prometheus/prometheus) официальный репозиторий **Prometheus**:
    - ```bash
      docker run --name prometheus -d -p 127.0.0.1:9090:9090 prom/prometheus
      ```
        - **`docker run`** - Скачивание образа (если не скачан) и последующий запуск контейнера **Prometheus**
            - Команда `docker run` скачивает образ и затем запускает из-под него контейнер
            - Если образ уже скачан, то контейнер будет просто запущен 
        - **`--name prometheus`** - Объявление имени контейнеру (удобно для управления, вместо ID)
        - **`-d`** - Запуск контейнера в фоновом режиме (detached)
        - **`-p 127.0.0.1:9090:9090`** - Проброс портов
            - **`127.0.0.1:9090`** - Порт `9090` на хосте (локальная машина), доступен только локально
            - **`:9090`** - Порт внутри контейнера, куда слушает **Prometheus**
            - **`127.0.0.1`** - Доступ к веб-интерфейсу **Prometheus** можно получить только с локальной машины или `http://localhost:9090`
            - **`-p 0.0.0.0:9090:9090`** - Теперь **Prometheus** будет доступен по IP хоста в локальной сети (например, `http://192.168.1.100:9090`)
        - **`prom/prometheus`** - Использует официальный образ **Prometheus** из **Docker Hub**
- Проверяем, что контейнер успешно запущен - `docker ps`
- Проверяем ПО на веб-морде - `http://192.168.1.100:9090`

### Шаг 2
- Запускаем **Grafana**
    - Тот же способ 

### Шаг 3
- Запускаем **Node Exporter**
    - Тот же способ 

### Шаг 4
- Проверяем веб-морды на всех ПО мониторинга
- Собираем мониторинг воедино
    - Prometheus
    - Grafana
    - Node Exporter 
- Далее снимаем метрики с дашборда [Node Exporter Full](https://grafana.com/grafana/dashboards/1860-node-exporter-full/)
