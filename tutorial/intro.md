<!-- markdownlint-disable MD002 MD041 -->

<span data-ttu-id="6f17a-101">В этом руководстве рассказывается, как создать веб-приложение Python Джанго, которое использует API Microsoft Graph для получения сведений о календаре для пользователя.</span><span class="sxs-lookup"><span data-stu-id="6f17a-101">This tutorial teaches you how to build a Python Django web app that uses the Microsoft Graph API to retrieve calendar information for a user.</span></span>

> [!TIP]
> <span data-ttu-id="6f17a-102">Если вы хотите просто скачать заполненный учебник, можно скачать его двумя способами.</span><span class="sxs-lookup"><span data-stu-id="6f17a-102">If you prefer to just download the completed tutorial, you can download it in two ways.</span></span>
>
> - <span data-ttu-id="6f17a-103">Скачайте [Краткое руководство по Python](https://developer.microsoft.com/graph/quick-start?platform=option-Python) , чтобы получить рабочий код в минутах.</span><span class="sxs-lookup"><span data-stu-id="6f17a-103">Download the [Python quick start](https://developer.microsoft.com/graph/quick-start?platform=option-Python) to get working code in minutes.</span></span>
> - <span data-ttu-id="6f17a-104">Скачайте или скопируйте [репозиторий GitHub](https://github.com/microsoftgraph/msgraph-training-pythondjangoapp).</span><span class="sxs-lookup"><span data-stu-id="6f17a-104">Download or clone the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-pythondjangoapp).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6f17a-105">Необходимые компоненты</span><span class="sxs-lookup"><span data-stu-id="6f17a-105">Prerequisites</span></span>

<span data-ttu-id="6f17a-106">Прежде чем приступить к работе с этим руководством, на компьютере для разработки должен быть установлен [Python](https://www.python.org/) (с [PIP](https://pypi.org/project/pip/)).</span><span class="sxs-lookup"><span data-stu-id="6f17a-106">Before you start this tutorial, you should have [Python](https://www.python.org/) (with [pip](https://pypi.org/project/pip/)) installed on your development machine.</span></span> <span data-ttu-id="6f17a-107">Если у вас нет Python, посетите предыдущую ссылку для получения вариантов загрузки.</span><span class="sxs-lookup"><span data-stu-id="6f17a-107">If you do not have Python, visit the previous link for download options.</span></span>

> [!NOTE]
> <span data-ttu-id="6f17a-108">Это руководство было написано с помощью Python версии 3.7.0 и Джанго версии 2,1.</span><span class="sxs-lookup"><span data-stu-id="6f17a-108">This tutorial was written with Python version 3.7.0 and Django version 2.1.</span></span> <span data-ttu-id="6f17a-109">Действия, описанные в этом руководстве, могут работать с другими версиями, но не тестировались.</span><span class="sxs-lookup"><span data-stu-id="6f17a-109">The steps in this guide may work with other versions, but that has not been tested.</span></span>

## <a name="feedback"></a><span data-ttu-id="6f17a-110">Отзывы</span><span class="sxs-lookup"><span data-stu-id="6f17a-110">Feedback</span></span>

<span data-ttu-id="6f17a-111">Сообщите о нем в [репозиторий GitHub](https://github.com/microsoftgraph/msgraph-training-pythondjangoapp).</span><span class="sxs-lookup"><span data-stu-id="6f17a-111">Please provide any feedback on this tutorial in the [GitHub repository](https://github.com/microsoftgraph/msgraph-training-pythondjangoapp).</span></span>