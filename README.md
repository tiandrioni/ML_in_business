# python-flask-docker
Итоговый проект (пример) курса "Машинное обучение в бизнесе"

Стек:

ML: sklearn, pandas, numpy
API: flask
Данные: с https://www.kaggle.com/binaryjoker/airline-passenger-satisfaction

Задача: предсказать удовлетворенность клиента услугами авиакомпании. Бинарная классификация.

Используемые признаки:

Gender                             object
customer_type                      object
type_of_travel                     object 
customer_class                     object
age                                int
flight_distance                    int
inflight_wifi_service              int
departure_arrival_time_convenient  int
ease_of_online_booking             int
gate_location                      int
food_and_drink                     int
online_boarding                    int
seat_comfort                       int
inflight_entertainment             int
onboard_service                    int
leg_room_service                   int
baggage_handling                   int
checkin_service                    int
inflight_service                   int
cleanliness                        int
departure_delay_in_minutes         int
arrival_delay_in_minutes           float

Преобразования признаков: для object - OHE.

Модель: CatBoostClassifier

### Клонируем репозиторий и создаем образ
```
$ git clone https://github.com/tiandrioni/GB_docker_flask_example.git
$ cd GB_docker_flask_example
$ docker build -t fimochka/gb_docker_flask_example .
```

### Запускаем контейнер

Здесь Вам нужно создать каталог локально и сохранить туда предобученную модель (<your_local_path_to_pretrained_models> нужно заменить на полный путь к этому каталогу)
```
$ docker run -d -p 8180:8180 -p 8181:8181 -v <your_local_path_to_pretrained_models>:/app/app/models fimochka/gb_docker_flask_example
```

### Переходим на localhost:8181
