# Руководство по контрибьюту в Hadaf 🚀 
*(English version below)*

Во-первых, спасибо, что решили помочь Hadaf! Именно благодаря таким неравнодушным разработчикам эта платформа становится реальностью для тех, кто в ней нуждается.

Мы — некоммерческая, волонтерская social-tech инициатива. Мы ценим любой вклад: будь то исправление бага, написание документации или предложение новой фичи.

Чтобы наша кодовая база оставалась чистой, безопасной и легко поддерживаемой, пожалуйста, следуйте этим правилам.

## 🧠 Золотое правило
**Никаких пушей напрямую в ветку `main`.** Все изменения должны делаться в отдельной ветке и отправляться через Pull Request (PR). Ветка `main` защищена, и слияние (merge) возможно только после код-ревью и аппрува от CTO.

## 🛠 Как внести свой вклад

### 1. Найдите задачу (Issue)
* Зайдите во вкладку **Issues** и посмотрите, где нужна помощь. Обращайте внимание на теги `good first issue` или `help wanted`.
* Если вы хотите разработать новую фичу или исправить баг, которого нет в списке, пожалуйста, **сначала создайте новый Issue**, чтобы обсудить это с командой.

### 2. Форк и ветвление (Fork & Branch)
1. Сделайте форк (Fork) репозитория на свой личный аккаунт GitHub.
2. Склонируйте проект на свой компьютер.
3. Создайте новую ветку от `main`. Используйте понятные названия:
   * `feat/your-feature-name` (для новых функций)
   * `fix/your-bugfix-name` (для исправления багов)
   * `docs/update-readme` (для работы с документацией)

### 3. Коммиты
* Пишите четкие и понятные сообщения к коммитам.
* Пример: `fix: исправлена ошибка в форме регистрации донора` или `feat: добавлена пагинация в список нужд`.
* Убедитесь, что ваш код соответствует текущему стилю проекта (Next.js для Frontend, Go для Backend).

### 4. Открытие Pull Request (PR)
* Сделайте push вашей ветки в ваш форкнутый репозиторий.
* Откройте PR в ветку `main` основного репозитория Hadaf.
* Полностью заполните шаблон PR. Опишите, что вы изменили, зачем, и прикрепите ссылки на связанные задачи (например, "Fixes #12").

## 🛑 Безопасность и приватность
* **НИКОГДА** не коммитьте секреты, файлы `.env`, API-ключи или пароли от баз данных.
* Если вы работаете с моковыми (тестовыми) данными, убедитесь, что они не содержат реальной персональной информации.

## 🤝 Процесс код-ревью
После того как вы откроете PR, он пройдет проверку (код-ревью). Мы можем попросить внести изменения или задать уточняющие вопросы — это нормальный инженерный процесс! Как только код будет одобрен, мы сольем его в `main`.

Спасибо за ваше время и желание сделать благотворительность прозрачной и эффективной. Давайте строить крутые вещи вместе!

---

# Contributing to Hadaf 🚀

First off, thank you for considering contributing to Hadaf! It's people like you that make this platform a reality for those who need it most. 

As a non-profit, volunteer-driven social tech initiative, we value every contribution—whether it's fixing a bug, writing documentation, or proposing a new feature.

To keep our codebase clean, secure, and maintainable, please follow these guidelines.

## 🧠 The Golden Rule
**Do not push directly to the `main` branch.** All changes must be made in a separate branch and submitted via a Pull Request (PR). The `main` branch is protected and requires review and approval from the CTO before merging.

## 🛠 How to Contribute

### 1. Find an Issue
* Check our **Issues** tab for things we need help with. Look for labels like `good first issue` or `help wanted`.
* If you want to build a new feature or fix a bug that isn't listed, please **open an issue first** to discuss it with the core team.

### 2. Fork & Branch
1. Fork the repository to your own GitHub account.
2. Clone the project to your local machine.
3. Create a new branch from `main`. Use a descriptive name:
   * `feat/your-feature-name` (for new features)
   * `fix/your-bugfix-name` (for bug fixes)
   * `docs/update-readme` (for documentation)

### 3. Commit Your Changes
* Write clear, concise commit messages. 
* Example: `fix: resolve issue with donor registration form` or `feat: add pagination to needs list`.
* Make sure your code follows the existing style and conventions of the project (Next.js for Frontend, Go for Backend).

### 4. Open a Pull Request (PR)
* Push your branch to your forked repository.
* Open a PR against the `main` branch of the Hadaf repository.
* Fill out the PR template completely. Describe what you changed, why you changed it, and link any relevant issues (e.g., "Fixes #12").

## 🛑 Security & Privacy
* **NEVER** commit secrets, `.env` files, API keys, or database credentials.
* If you are working with mock data, ensure it does not contain any real personal information.

## 🤝 Code Review Process
Once your PR is open, the core team (CTO or senior maintainers) will review your code. We might request changes or ask clarifying questions. This is a normal part of the engineering process! Once approved, we will merge it into `main`.

Thank you for dedicating your time to making charity transparent and effective. Let's build something great together.
