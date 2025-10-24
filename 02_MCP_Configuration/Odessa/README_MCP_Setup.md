# Настройка MCP для 1С:Предприятие 8.3.27

## Описание
MCP (Model Context Protocol) серверы для работы с платформой 1С:Предприятие 8.3.27.1688 и каркасной конфигурацией.

## Установка MCP серверов

### 1. Установка 1c-platform MCP Server
```bash
npm install -g @1c-platform/mcp-server
```

### 2. Установка 1c-metacode MCP Server  
```bash
npm install -g @1c-metacode/mcp-server
```

## Настройка в Cursor

### 1. Откройте настройки Cursor
- Windows: `Ctrl + ,`
- Mac: `Cmd + ,`

### 2. Найдите секцию MCP
Перейдите в раздел "Extensions" → "MCP"

### 3. Добавьте конфигурацию
```json
{
  "mcpServers": {
    "1c-platform": {
      "command": "npx",
      "args": ["@1c-platform/mcp-server"],
      "env": {
        "PLATFORM_VERSION": "8.3.27.1688",
        "CONFIGURATION_TYPE": "Framework",
        "LANGUAGE": "Russian"
      }
    },
    "1c-metacode": {
      "command": "npx",
      "args": ["@1c-metacode/mcp-server"],
      "env": {
        "PLATFORM_VERSION": "8.3.27.1688", 
        "CONFIGURATION_PATH": "./03_1C_Configuration/",
        "LANGUAGE": "Russian"
      }
    }
  }
}
```

## Возможности MCP серверов

### 1c-platform
- Анализ API платформы 1С
- Получение информации о методах и свойствах
- Проверка синтаксиса
- Документация по объектам платформы

### 1c-metacode  
- Анализ метаданных конфигурации
- Получение структуры объектов
- Анализ зависимостей
- Генерация кода

## Использование

### В Cursor
1. Откройте файл с кодом 1С
2. Используйте команды MCP через палитру команд (`Ctrl+Shift+P`)
3. Выберите нужную операцию MCP

### Доступные команды
- `MCP: Analyze 1C Code` - анализ кода 1С
- `MCP: Get Platform Info` - информация о платформе
- `MCP: Analyze Metadata` - анализ метаданных
- `MCP: Generate Code` - генерация кода

## Troubleshooting

### Проблемы с подключением
1. Проверьте установку Node.js
2. Убедитесь в корректности путей к MCP серверам
3. Проверьте настройки в Cursor

### Ошибки конфигурации
1. Проверьте версию платформы в настройках
2. Убедитесь в корректности пути к конфигурации
3. Проверьте права доступа к файлам

## Поддержка
- Документация: [ссылка на документацию]
- Issues: [ссылка на issues]
- Версия: 1.0.0
