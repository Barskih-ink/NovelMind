# 

<h1 align="center">
  <img src="./Assets/logo.jpg" alt="NovelMind Icon" width="50" height="50" style="vertical-align: middle; margin-right: 10px;">
  NovelMind
</h1>
<p align="center">
  <img src="https://img.shields.io/badge/версия-1.0.0-blue.svg" alt="Версия">
  <img src="https://img.shields.io/badge/лицензия-MIT-green.svg" alt="Лицензия">
</p>

<p align="center">
  <strong>Инновационный визуальный редактор для создания визуальных новелл</strong>
</p>

NovelMind - это проект, направленный на упрощение процесса создания визуальных новелл, предоставляя разработчикам мощные инструменты в удобном визуальном интерфейсе, одновременно обеспечивая безопасность их работы.

## 📑 Оглавление

- [Ключевые особенности](#-ключевые-особенности)
- [Файловая система](#-файловая-система)
- [Система логирования](#-система-логирования)

## 🌟 Ключевые особенности

1. 🔐 **Безопасная файловая система**: Встроенная система шифрования файлов предотвращает несанкционированный доступ к ресурсам проекта.

2. 🖱️ **Визуальное позиционирование элементов**: Интуитивно понятный интерфейс позволяет разработчикам перетаскивать спрайты и другие элементы непосредственно на сцену.

3. 🎭 **Визуальное программирование**: Возможность визуально программировать ход новеллы, включая порядок диалогов и другие элементы повествования.

4. 🔧 **Внутренний язык программирования**: Собственный скриптовый язык для более тонкой настройки и программирования сложных сценариев.

5. 🚀 **Компиляция в исполняемый файл**: По завершении разработки, весь проект (включая ресурсы, диалоги и скрипты) может быть скомпилирован в единый исполняемый файл одним нажатием кнопки.

6. 🎮 **Простота использования**: Готовая новелла запускается простым запуском скомпилированного файла.

---

## 📁 Файловая система

Файловая система NovelMind обеспечивает безопасное хранение и управление файлами с использованием шифрования. Ниже представлена документация по компонентам ядра (Core) и API файловой системы.

<details>
<summary><strong>Компоненты ядра (Core)</strong></summary>

### Компоненты ядра (Core)

Основные компоненты включают следующие модули:

1. **Шифрование** (`encryption.py`)
   - Класс: `AdvancedEncryptor`
     - Методы: `__init__`, `_load_or_generate_key`, `_derive_key`, `encrypt`, `decrypt`

2. **Обработчик файлов** (`file_handler.py`)
   - Класс: `SecureFileHandler`
     - Методы: `__init__`, `add_file`, `read_file`, `delete_file`, `list_files`

3. **Инициализатор файловой системы** (`initializer.py`)
   - Класс: `FileSystemInitializer`
     - Методы: `__init__`, `initialize`, `_initialize_encryption`, `_create_empty_index`

4. **Безопасное хранилище** (`storage.py`)
   - Класс: `SecureStorage`
     - Методы: `__init__`, `_load_index`, `_save_index`, `add_file`, `get_file_path`, `remove_file`, `list_files`

5. **Вспомогательные функции** (`utils.py`)
   - Функции: `create_directory_if_not_exists`, `is_valid_path`

</details>

<details>
<summary><strong>API компоненты</strong></summary>

### API компоненты

API компоненты предоставляют высокоуровневые операции для управления файлами и развертывания системы:

1. **Файловые операции** (`file_operations.py`)
   - Класс: `FileOperations`
     - Методы: `__init__`, `add_file`, `read_file`, `delete_file`, `list_files`

2. **Системные операции** (`system_operations.py`)
   - Класс: `SystemOperations`
     - Методы: `deploy`

</details>

---

## 📊 Система логирования

Система логирования NovelMind предоставляет гибкие и многофункциональные возможности для ведения логов.

### Основные функции

1. 📈 **Многоуровневое логирование**: Поддержка уровней DEBUG, INFO, WARNING, ERROR и CRITICAL.
2. 📁 **Логирование в файл и консоль**: Логи записываются в файл.
3. 🔠 **Форматирование в JSON**: Возможность форматирования логов в JSON для упрощения анализа и парсинга.
4. 🔄 **Автоматическое логирование функций**: Декоратор для автоматического логирования вызовов функций, аргументов, возвращаемых значений и времени выполнения.
5. 🏛️ **Логирование классов**: Декоратор для автоматического применения логирования ко всем методам класса.
6. 🔍 **Дополнительный контекст**: Возможность добавления дополнительной контекстной информации к сообщениям логов.

<details>
<summary><strong>Класс Logger</strong></summary>

### Класс Logger

```python
Logger(log_file: str = 'app.log', use_json: bool = False)
```

#### Методы

- Методы логирования:
  - `debug(message: str, extra: Dict[str, Any] = None)`
  - `info(message: str, extra: Dict[str, Any] = None)`
  - `warning(message: str, extra: Dict[str, Any] = None)`
  - `error(message: str, extra: Dict[str, Any] = None)`
  - `critical(message: str, extra: Dict[str, Any] = None)`

- Методы-декораторы:
  - `log_function() -> Callable[[Callable], Callable]`
  - `log_class() -> Callable[[Type], Type]`

- Внутренние методы:
  - `_setup_logger(log_file: str, use_json: bool) -> logging.Logger`
  - `_log_function(func: Callable) -> Callable`
  - `_log(level: str, message: str, extra: Dict[str, Any] = None)`

#### Класс JsonFormatter

Внутренний класс, который форматирует записи логов как JSON строки.

</details>

### Примеры использования

<details>
<summary><strong>Базовое логирование</strong></summary>

```python
logger = Logger()
logger.info("Приложение запущено")
logger.error("Произошла ошибка", extra={"error_code": 500})
```
</details>

<details>
<summary><strong>Логирование функций</strong></summary>

```python
logger = Logger()

@logger.log_function()
def example_function(a, b):
    return a + b

result = example_function(3, 4)
```
</details>

<details>
<summary><strong>Логирование классов</strong></summary>

```python
logger = Logger()

@logger.log_class()
class ExampleClass:
    def method1(self):
        pass

    def method2(self, x):
        return x * 2

obj = ExampleClass()
obj.method1()
obj.method2(5)
```
</details>

<details>
<summary><strong>Логирование в формате JSON</strong></summary>

```python
json_logger = Logger(use_json=True)
json_logger.info("Это лог в формате JSON", extra={"user_id": 123})
```
</details>

---

<p align="center">
  Создано с ❤️ командой NovelMind
</p>