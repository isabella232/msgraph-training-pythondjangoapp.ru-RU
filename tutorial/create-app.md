<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="28499-101">В этом упражнении вы будете использовать [Джанго](https://www.djangoproject.com/) для создания веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="28499-101">In this exercise you will use [Django](https://www.djangoproject.com/) to build a web app.</span></span> <span data-ttu-id="28499-102">Если вы еще не установили Джанго, вы можете установить его из интерфейса командной строки (CLI) с помощью следующей команды.</span><span class="sxs-lookup"><span data-stu-id="28499-102">If you don't already have Django installed, you can install it from your command-line interface (CLI) with the following command.</span></span>

```Shell
pip install Django
```

<span data-ttu-id="28499-103">Откройте подсистему CLI, перейдите к каталогу, в котором у вас есть права на создание файлов, и выполните следующую команду, чтобы создать новое приложение Джанго.</span><span class="sxs-lookup"><span data-stu-id="28499-103">Open your CLI, navigate to a directory where you have rights to create files, and run the following command to create a new Django app.</span></span>

```Shell
django-admin.py startproject graph_tutorial
```

<span data-ttu-id="28499-104">Джанго создает новый каталог с именем `graph_tutorial` и формирование шаблонов для веб-приложения Джанго.</span><span class="sxs-lookup"><span data-stu-id="28499-104">Django creates a new directory called `graph_tutorial` and scaffolds a Django web app.</span></span> <span data-ttu-id="28499-105">Перейдите к новому каталогу и введите следующую команду для запуска локального веб-сервера.</span><span class="sxs-lookup"><span data-stu-id="28499-105">Navigate to this new directory and enter the following command to start a local web server.</span></span>

```Shell
python manage.py runserver
```

<span data-ttu-id="28499-106">Откройте браузер и перейдите по адресу `http://localhost:8000`.</span><span class="sxs-lookup"><span data-stu-id="28499-106">Open your browser and navigate to `http://localhost:8000`.</span></span> <span data-ttu-id="28499-107">Если все работает, вы увидите страницу приветствия Джанго.</span><span class="sxs-lookup"><span data-stu-id="28499-107">If everything is working, you will see a Django welcome page.</span></span> <span data-ttu-id="28499-108">Если вы не видите это, ознакомьтесь с [руководством по началу работы с Джанго](https://www.djangoproject.com/start/).</span><span class="sxs-lookup"><span data-stu-id="28499-108">If you don't see that, check the [Django getting started guide](https://www.djangoproject.com/start/).</span></span>

<span data-ttu-id="28499-109">Теперь, когда вы проверили проект, добавьте приложение в проект.</span><span class="sxs-lookup"><span data-stu-id="28499-109">Now that you've verified the project, add an app to the project.</span></span> <span data-ttu-id="28499-110">Выполните следующую команду в командной панели CLI.</span><span class="sxs-lookup"><span data-stu-id="28499-110">Run the following command in your CLI.</span></span>

```Shell
python manage.py startapp tutorial
```

<span data-ttu-id="28499-111">В результате будет создано новое приложение в `./tutorial` каталоге.</span><span class="sxs-lookup"><span data-stu-id="28499-111">This creates a new app in the `./tutorial` directory.</span></span> <span data-ttu-id="28499-112">Откройте `./graph_tutorial/settings.py` и добавьте новое `tutorial` приложение в `INSTALLED_APPS` параметр.</span><span class="sxs-lookup"><span data-stu-id="28499-112">Open the `./graph_tutorial/settings.py` and add the new `tutorial` app to the `INSTALLED_APPS` setting.</span></span>

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'tutorial',
]
```

<span data-ttu-id="28499-113">В интерфейсе командной строки выполните следующую команду, чтобы инициализировать базу данных для проекта.</span><span class="sxs-lookup"><span data-stu-id="28499-113">In your CLI, run the following command to initialize the database for the project.</span></span>

```Shell
python manage.py migrate
```

<span data-ttu-id="28499-114">Добавьте [урлконф](https://docs.djangoproject.com/en/2.1/topics/http/urls/) для `tutorial` приложения.</span><span class="sxs-lookup"><span data-stu-id="28499-114">Add a [URLconf](https://docs.djangoproject.com/en/2.1/topics/http/urls/) for the `tutorial` app.</span></span> <span data-ttu-id="28499-115">Создайте новый файл в `./tutorial` каталоге `urls.py` и добавьте указанный ниже код.</span><span class="sxs-lookup"><span data-stu-id="28499-115">Create a new file in the `./tutorial` directory named `urls.py` and add the following code.</span></span>

```python
from django.urls import path

from . import views

urlpatterns = [
  # /tutorial
  path('', views.home, name='home'),
]
```

<span data-ttu-id="28499-116">Теперь обновите проект Урлконф, чтобы импортировать его.</span><span class="sxs-lookup"><span data-stu-id="28499-116">Now update the project URLconf to import this one.</span></span> <span data-ttu-id="28499-117">Откройте `./graph_tutorial/urls.py` файл и замените его содержимое приведенным ниже содержимым.</span><span class="sxs-lookup"><span data-stu-id="28499-117">Open the `./graph_tutorial/urls.py` file and replace the contents with the following.</span></span>

```python
from django.contrib import admin
from django.urls import path, include
from tutorial import views

urlpatterns = [
    path('tutorial/', include('tutorial.urls')),
    path('admin/', admin.site.urls),
]
```

<span data-ttu-id="28499-118">Наконец, добавьте временное представление в `tutorials` приложение, чтобы убедиться в работоспособности МАРШРУТИЗАЦИИ URL-адресов.</span><span class="sxs-lookup"><span data-stu-id="28499-118">Finally add a temporary view to the `tutorials` app to verify that URL routing is working.</span></span> <span data-ttu-id="28499-119">Откройте файл `./tutorial/views.py` и добавьте в него указанный ниже код.</span><span class="sxs-lookup"><span data-stu-id="28499-119">Open the `./tutorial/views.py` file and add the following code.</span></span>

```python
from django.http import HttpResponse, HttpResponseRedirect

def home(request):
  # Temporary!
  return HttpResponse("Welcome to the tutorial.")
```

<span data-ttu-id="28499-120">Сохраните все изменения и перезапустите сервер.</span><span class="sxs-lookup"><span data-stu-id="28499-120">Save all of your changes and restart the server.</span></span> <span data-ttu-id="28499-121">Перейдите к `http://localhost:8000/tutorial`.</span><span class="sxs-lookup"><span data-stu-id="28499-121">Browse to `http://localhost:8000/tutorial`.</span></span> <span data-ttu-id="28499-122">Вы должны увидеть`Welcome to the tutorial.`</span><span class="sxs-lookup"><span data-stu-id="28499-122">You should see `Welcome to the tutorial.`</span></span>

<span data-ttu-id="28499-123">Прежде чем переходить, установите несколько дополнительных библиотек, которые будут использоваться позже:</span><span class="sxs-lookup"><span data-stu-id="28499-123">Before moving on, install some additional libraries that you will use later:</span></span>

- <span data-ttu-id="28499-124">[Запросы OAuthlib: OAuth для людей](https://requests-oauthlib.readthedocs.io/en/latest/) для обработки входа и потоков маркеров OAuth, а для совершения звонков в Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="28499-124">[Requests-OAuthlib: OAuth for Humans](https://requests-oauthlib.readthedocs.io/en/latest/) for handling sign-in and OAuth token flows, and for making calls to Microsoft Graph.</span></span>
- <span data-ttu-id="28499-125">[Пиямл](https://pyyaml.org/wiki/PyYAMLDocumentation) для загрузки конфигурации из файла ямл.</span><span class="sxs-lookup"><span data-stu-id="28499-125">[PyYAML](https://pyyaml.org/wiki/PyYAMLDocumentation) for loading configuration from a YAML file.</span></span>
- <span data-ttu-id="28499-126">[Python-датеутил](https://pypi.org/project/python-dateutil/) для синтаксического анализа строк даты ISO 8601, возвращенных из Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="28499-126">[python-dateutil](https://pypi.org/project/python-dateutil/) for parsing ISO 8601 date strings returned from Microsoft Graph.</span></span>

<span data-ttu-id="28499-127">Выполните следующую команду в командной панели CLI.</span><span class="sxs-lookup"><span data-stu-id="28499-127">Run the following command in your CLI.</span></span>

```Shell
pip install requests_oauthlib
pip install pyyaml
pip install python-dateutil
```

## <a name="design-the-app"></a><span data-ttu-id="28499-128">Проектирование приложения</span><span class="sxs-lookup"><span data-stu-id="28499-128">Design the app</span></span>

<span data-ttu-id="28499-129">Начните с создания каталога Templates и определения глобального макета для приложения.</span><span class="sxs-lookup"><span data-stu-id="28499-129">Start by creating a templates directory and defining a global layout for the app.</span></span> <span data-ttu-id="28499-130">Создайте новый каталог в `./tutorial` каталоге с именем. `templates`</span><span class="sxs-lookup"><span data-stu-id="28499-130">Create a new directory in the `./tutorial` directory named `templates`.</span></span> <span data-ttu-id="28499-131">В `templates` каталоге создайте новый каталог с именем `tutorial`.</span><span class="sxs-lookup"><span data-stu-id="28499-131">In the `templates` directory, create a new directory named `tutorial`.</span></span> <span data-ttu-id="28499-132">Наконец, создайте в этом каталоге новый файл с именем `layout.html`.</span><span class="sxs-lookup"><span data-stu-id="28499-132">Finally, create a new file in this directory named `layout.html`.</span></span> <span data-ttu-id="28499-133">Должен быть `./tutorial/templates/tutorial/layout.html`относительный путь из корневого каталога проекта.</span><span class="sxs-lookup"><span data-stu-id="28499-133">The relative path from the root of your project should be `./tutorial/templates/tutorial/layout.html`.</span></span> <span data-ttu-id="28499-134">Добавьте в этот файл приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="28499-134">Add the following code in that file.</span></span>

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Python Graph Tutorial</title>

    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/css/bootstrap.min.css"
      integrity="sha384-WskhaSGFgHYWDcbwN70/dfYBj47jz9qbsMId/iRN3ewGhXQFZCSftd1LZCfmhktB" crossorigin="anonymous">
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.1.0/css/all.css"
      integrity="sha384-lKuwvrZot6UHsBSfcMvOkWwlCMgc0TaWr+30HWe3a4ltaBwTZhyTEggF5tJv8tbt" crossorigin="anonymous">
    {% load static %}
    <link rel="stylesheet" href="{% static "tutorial/app.css" %}">
    <script src="https://code.jquery.com/jquery-3.3.1.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.3/umd/popper.min.js"
      integrity="sha384-ZMP7rVo3mIykV+2+9J3UJ46jBk0WLaUAdn689aCwoqbBJiSnjAK/l8WvCWPIPm49" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.1.1/js/bootstrap.min.js"
      integrity="sha384-smHYKdLADwkXOn1EmN1qk/HfnUcbVRZyYmZ4qpPea6sjB/pTJ0euyQp0Mk8ck+5T" crossorigin="anonymous"></script>
  </head>

  <body>
    <nav class="navbar navbar-expand-md navbar-dark fixed-top bg-dark">
      <div class="container">
        <a href="{% url 'home' %}" class="navbar-brand">Python Graph Tutorial</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarCollapse"
          aria-controls="navbarCollapse" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarCollapse">
          <ul class="navbar-nav mr-auto">
            <li class="nav-item">
              <a href="{% url 'home' %}" class="nav-link{% if request.resolver_match.view_name == 'home' %} active{% endif %}">Home</a>
            </li>
            {% if user.is_authenticated %}
              <li class="nav-item" data-turbolinks="false">
                <a class="nav-link{% if request.resolver_match.view_name == 'calendar' %} active{% endif %}" href="#">Calendar</a>
              </li>
            {% endif %}
          </ul>
          <ul class="navbar-nav justify-content-end">
            <li class="nav-item">
              <a class="nav-link" href="https://developer.microsoft.com/graph/docs/concepts/overview" target="_blank">
                <i class="fas fa-external-link-alt mr-1"></i>Docs
              </a>
            </li>
            {% if user.is_authenticated %}
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" data-toggle="dropdown" href="#" role="button" aria-haspopup="true" aria-expanded="false">
                  {% if user.avatar %}
                    <img src="{{ user.avatar }}" class="rounded-circle align-self-center mr-2" style="width: 32px;">
                  {% else %}
                    <i class="far fa-user-circle fa-lg rounded-circle align-self-center mr-2" style="width: 32px;"></i>
                  {% endif %}
                </a>
                <div class="dropdown-menu dropdown-menu-right">
                  <h5 class="dropdown-item-text mb-0">{{ user.name }}</h5>
                  <p class="dropdown-item-text text-muted mb-0">{{ user.email }}</p>
                  <div class="dropdown-divider"></div>
                  <a href="#" class="dropdown-item">Sign Out</a>
                </div>
              </li>
            {% else %}
              <li class="nav-item">
                <a href="#" class="nav-link">Sign In</a>
              </li>
            {% endif %}
          </ul>
        </div>
      </div>
    </nav>
    <main role="main" class="container">
      {% if errors %}
        {% for error in errors %}
          <div class="alert alert-danger" role="alert">
            <p class="mb-3">{{ error.message }}</p>
            {% if error.debug %}
              <pre class="alert-pre border bg-light p-2"><code>{{ error.debug }}</code></pre>
            {% endif %}
          </div>
        {% endfor %}
      {% endif %}
      {% block content %}{% endblock %}
    </main>
  </body>
</html>
```

<span data-ttu-id="28499-135">В этом коде [](http://getbootstrap.com/) добавляется начальная загрузка для простых стилей и [Шрифт Awesome](https://fontawesome.com/) для некоторых простых значков.</span><span class="sxs-lookup"><span data-stu-id="28499-135">This code adds [Bootstrap](http://getbootstrap.com/) for simple styling, and [Font Awesome](https://fontawesome.com/) for some simple icons.</span></span> <span data-ttu-id="28499-136">Он также определяет глобальную структуру с помощью панели навигации.</span><span class="sxs-lookup"><span data-stu-id="28499-136">It also defines a global layout with a nav bar.</span></span>

<span data-ttu-id="28499-137">Теперь создайте новый каталог в `./tutorial` каталоге с именем. `static`</span><span class="sxs-lookup"><span data-stu-id="28499-137">Now create a new directory in the `./tutorial` directory named `static`.</span></span> <span data-ttu-id="28499-138">В `static` каталоге создайте новый каталог с именем `tutorial`.</span><span class="sxs-lookup"><span data-stu-id="28499-138">In the `static` directory, create a new directory named `tutorial`.</span></span> <span data-ttu-id="28499-139">Наконец, создайте в этом каталоге новый файл с именем `app.css`.</span><span class="sxs-lookup"><span data-stu-id="28499-139">Finally, create a new file in this directory named `app.css`.</span></span> <span data-ttu-id="28499-140">Должен быть `./tutorial/static/tutorial/app.css`относительный путь из корневого каталога проекта.</span><span class="sxs-lookup"><span data-stu-id="28499-140">The relative path from the root of your project should be `./tutorial/static/tutorial/app.css`.</span></span> <span data-ttu-id="28499-141">Добавьте в этот файл приведенный ниже код.</span><span class="sxs-lookup"><span data-stu-id="28499-141">Add the following code in that file.</span></span>

```css
body {
  padding-top: 4.5rem;
}

.alert-pre {
  word-wrap: break-word;
  word-break: break-all;
  white-space: pre-wrap;
}
```

<span data-ttu-id="28499-142">Затем создайте шаблон для домашней страницы, использующей макет.</span><span class="sxs-lookup"><span data-stu-id="28499-142">Next, create a template for the home page that uses the layout.</span></span> <span data-ttu-id="28499-143">Создайте новый файл в `./tutorial/templates/tutorial` каталоге `home.html` и добавьте указанный ниже код.</span><span class="sxs-lookup"><span data-stu-id="28499-143">Create a new file in the `./tutorial/templates/tutorial` directory named `home.html` and add the following code.</span></span>

```html
{% extends "tutorial/layout.html" %}
{% block content %}
<div class="jumbotron">
  <h1>Python Graph Tutorial</h1>
  <p class="lead">This sample app shows how to use the Microsoft Graph API to access Outlook and OneDrive data from Python</p>
  {% if user.is_authenticated %}
    <h4>Welcome {{ user.name }}!</h4>
    <p>Use the navigation bar at the top of the page to get started.</p>
  {% else %}
    <a href="#" class="btn btn-primary btn-large">Click here to sign in</a>
  {% endif %}
</div>
{% endblock %}
```

<span data-ttu-id="28499-144">Обновите `home` представление, чтобы использовать этот шаблон.</span><span class="sxs-lookup"><span data-stu-id="28499-144">Update the `home` view to use this template.</span></span> <span data-ttu-id="28499-145">Откройте `./tutorial/views.py` файл и добавьте следующую новую функцию.</span><span class="sxs-lookup"><span data-stu-id="28499-145">Open the `./tutorial/views.py` file and add the following new function.</span></span>

```python
def initialize_context(request):
  context = {}

  # Check for any errors in the session
  error = request.session.pop('flash_error', None)

  if error != None:
    context['errors'] = []
    context['errors'].append(error)

  # Check for user in the session
  context['user'] = request.session.get('user', {'is_authenticated': False})
  return context
```

<span data-ttu-id="28499-146">Затем замените имеющееся `home` представление следующим.</span><span class="sxs-lookup"><span data-stu-id="28499-146">Then replace the existing `home` view with the following.</span></span>

```python
def home(request):
  context = initialize_context(request)

  return render(request, 'tutorial/home.html', context)
```

<span data-ttu-id="28499-147">Сохраните все изменения и перезапустите сервер.</span><span class="sxs-lookup"><span data-stu-id="28499-147">Save all of your changes and restart the server.</span></span> <span data-ttu-id="28499-148">Теперь приложение должно выглядеть по-другому.</span><span class="sxs-lookup"><span data-stu-id="28499-148">Now, the app should look very different.</span></span>

![Снимок экрана с переработанной домашней страницей](./images/create-app-01.png)