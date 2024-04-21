# Cards

## Установка

Для установки данного пакета можно воспользоваться готовим билдом, который можно скачать в данном репозитори, или выполнить сборку из исходников на локально машине.

### Сборка из исходников

Сборка python колеса:
```
pip install setuptools
make build
```

Установка колеса:
```
cd dist
pip install *.whl
```

## Использование 

По умолчанию данный пакет предоставляет реализацию API с использованием фреймворка FastAPI, в качестве СУБД используется SQLite. Однако можно реализовать собственне классы, которые будут заниматься обращением к другим СУБД или предоставлять интерфейс взаимодействия с системой с использованием любых других методов межпроцессного взаимодействия.

### Пример использования пакета


Создайте файл `main.py`
```
# main.py

from cards import ApiAppBuilder

app = ApiAppBuilder().app
```

Необходимо установить web сервер `uvicorn`:
```
pip install uvicorn
```

После чего в консоли выполните команду
```
uvicorn main:app --reload
```

После выполнения данной команды по адреу http://127.0.0.1:8000 будет доступен API сервиса.

Теперь перейдя по ссылке http://127.0.0.1:8000/docs, вы окажитесь на автоматически сгенерированной странице со спецификацией OpenAPI. Находясь на данной станице, вы можете протестировать работу предоставленных API ручек.

## CI/CD

Пайплан содержит 3 джобы: `build`, `test`, `deploy` 

- расширение `build`:
    - дописать необходимые зависимости в стадию `Install dependencies` джобы `build`
    - дописать необходимые действия в команды `lint` и `build` мейкфайла

- расширение `test`:
    - дописать необходимые зависимости в стадию `Install dependencies` джобы `test`
    - дописать необходимые действия в командe `test` мейкфайла

- расширение `deploy`:
    - comming soon...
    
