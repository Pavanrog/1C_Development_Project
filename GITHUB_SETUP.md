# Настройка GitHub для проекта

## Шаги для подключения к GitHub

### 1. Настройка Git конфигурации
```bash
git config --global user.name "Pavanrog"
git config --global user.email "ваш.email@example.com"
```

### 2. Создание репозитория на GitHub
1. Перейдите на https://github.com
2. Нажмите кнопку "New repository"
3. Введите название репозитория: `1C_Development_Project`
4. Выберите "Private" или "Public"
5. НЕ добавляйте README, .gitignore или лицензию (они уже созданы)
6. Нажмите "Create repository"

### 3. Подключение локального репозитория к GitHub

#### Вариант A: Использование Personal Access Token (рекомендуется)
1. Создайте Personal Access Token на GitHub:
   - Перейдите в Settings → Developer settings → Personal access tokens → Tokens (classic)
   - Нажмите "Generate new token (classic)"
   - Выберите scopes: `repo`, `workflow`, `write:packages`
   - Скопируйте токен (он показывается только один раз!)

2. Выполните команды:
```bash
# Добавьте удаленный репозиторий
git remote add origin https://github.com/Pavanrog/1C_Development_Project.git

# Добавьте файлы в индекс
git add .

# Сделайте первый коммит
git commit -m "Initial commit: Project structure and documentation"

# Отправьте в GitHub (используйте токен вместо пароля)
git push -u origin main
```

При запросе логина:
- Username: `Pavanrog`
- Password: `ваш_токен` (НЕ пароль от GitHub!)

#### Вариант B: Использование SSH (альтернативный)
Если настроили SSH ключи, используйте SSH URL:
```bash
git remote set-url origin git@github.com:Pavanrog/1C_Development_Project.git
git push -u origin main
```

### 4. Настройка SSH ключей (рекомендуется)
```bash
# Генерация SSH ключа
ssh-keygen -t ed25519 -C "rpa3611@gmail.com"

# Добавление ключа в ssh-agent
ssh-add ~/.ssh/id_ed25519

# Копирование публичного ключа
cat ~/.ssh/id_ed25519.pub
```

Затем добавьте скопированный ключ в GitHub:
1. Settings → SSH and GPG keys → New SSH key
2. Вставьте ключ и сохраните

### 5. Альтернативный способ через Cursor
1. Откройте Cursor
2. Нажмите Ctrl+Shift+P
3. Выберите "Git: Clone"
4. Введите URL репозитория
5. Выберите папку для клонирования

## Команды для работы с Git

### Основные команды
```bash
# Проверка статуса
git status

# Добавление файлов
git add .
git add filename

# Коммит
git commit -m "Описание изменений"

# Отправка в GitHub
git push

# Получение изменений
git pull

# Просмотр истории
git log --oneline
```

### Работа с ветками
```bash
# Создание новой ветки
git checkout -b feature/new-feature

# Переключение между ветками
git checkout main
git checkout feature/new-feature

# Слияние веток
git merge feature/new-feature
```

## Решение проблем с аутентификацией

### Ошибка "Authentication failed"
Если получаете ошибку аутентификации:

1. **Проверьте URL репозитория:**
```bash
git remote -v
```

2. **Если нужно изменить URL на SSH:**
```bash
git remote set-url origin git@github.com:Pavanrog/1C_Development_Project.git
```

3. **Если используете HTTPS с токеном:**
   - Убедитесь, что используете Personal Access Token, а не пароль
   - Токен должен иметь права `repo`

4. **Очистка кэша учетных данных (Windows):**
```bash
git config --global --unset credential.helper
```

### Альтернативные способы аутентификации

#### Через GitHub CLI
```bash
# Установите GitHub CLI
# Затем выполните:
gh auth login
```

#### Через Cursor
1. Откройте Cursor
2. Ctrl+Shift+P → "Git: Clone"
3. Введите URL репозитория
4. Cursor автоматически предложит аутентификацию

## Рекомендации

1. **Регулярно делайте коммиты** с описательными сообщениями
2. **Используйте ветки** для новых функций
3. **Следуйте соглашениям** именования коммитов
4. **Не коммитьте** временные файлы и конфиденциальную информацию

## Структура коммитов

Рекомендуемый формат сообщений коммитов:
- `feat: добавить новую функцию`
- `fix: исправить ошибку в модуле`
- `docs: обновить документацию`
- `refactor: рефакторинг кода`
- `test: добавить тесты`
