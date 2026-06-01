# OI UI Operating System

**OI UI** — это полнофункциональная операционная система для сенсорных устройств, разработанная на **C/C++** с использованием графической библиотеки **SDL2**.

## 📋 Описание

OI UI — это демонстрационная ОС, которая включает:

- **Ядро ОС** с управлением процессами и памятью
- **Графический сервер** на базе SDL2
- **UI фреймворк** для создания интерфейсов
- **Экран загрузки** (Boot Screen) с анимацией
- **Главный экран** (Home Screen) с приложениями
- **Система настроек** (Settings)
- **Поддержка сенсорного ввода**

## 🏗️ Архитектура

```
OI UI OS
├── Kernel (kernel.c)
│   ├── Process Management
│   ├── Memory Management
│   ├── System Information
│   └── Device Management
├── Graphics Server (graphics.c)
│   ├── SDL2 Rendering
│   ├── Primitive Drawing
│   ├── Text Rendering
│   └── Texture Management
├── UI Framework (ui.c)
│   ├── UI Elements
│   ├── Screen Management
│   ├── Event Handling
│   └── Layout System
└── Applications
    ├── Boot Screen (boot_screen.c)
    ├── Home Screen (home_screen.c)
    └── Settings (settings_screen.c)
```

## 🛠️ Требования

- **GCC/Clang** компилятор
- **CMake** 3.10+
- **SDL2** библиотеки:
  - `libsdl2-dev`
  - `libsdl2-ttf-dev`
  - `libsdl2-image-dev`

## 📦 Установка зависимостей

### Ubuntu/Debian

```bash
sudo apt-get install -y libsdl2-dev libsdl2-ttf-dev libsdl2-image-dev cmake build-essential
```

### Fedora

```bash
sudo dnf install SDL2-devel SDL2_ttf-devel SDL2_image-devel cmake gcc
```

### macOS

```bash
brew install sdl2 sdl2_ttf sdl2_image cmake
```

## 🔨 Сборка

```bash
cd /home/ubuntu/oi_ui_os
mkdir -p build
cd build
cmake ..
make -j4
```

## ▶️ Запуск

```bash
./build/oi_ui_os
```

## 🎮 Использование

### Управление

- **Мышь/Сенсор**: Нажимайте на элементы интерфейса
- **ESC**: Выход из приложения

### Экраны

#### 1. Boot Screen (Экран загрузки)
- Отображается при запуске ОС
- Показывает прогресс загрузки
- Длится ~8 секунд

#### 2. Home Screen (Главный экран)
- Сетка приложений (8 приложений)
- Статус-бар с временем, батареей и сигналом
- Информация о системе внизу

#### 3. Settings (Настройки)
- Управление яркостью
- Управление звуком
- Wi-Fi и Bluetooth
- Режим самолёта
- Информация о батарее и памяти

## 📁 Структура проекта

```
oi_ui_os/
├── include/
│   ├── kernel.h       # Заголовок ядра ОС
│   ├── graphics.h     # Заголовок графического сервера
│   └── ui.h           # Заголовок UI фреймворка
├── src/
│   ├── main.c         # Главная программа
│   ├── kernel.c       # Реализация ядра
│   ├── graphics.c     # Реализация графики
│   ├── ui.c           # Реализация UI
│   ├── boot_screen.c  # Экран загрузки
│   ├── home_screen.c  # Главный экран
│   └── settings_screen.c # Экран настроек
├── build/             # Директория сборки
├── assets/            # Ресурсы (шрифты, изображения)
├── CMakeLists.txt     # Конфигурация сборки
└── README.md          # Этот файл
```

## 🎨 Цветовая схема

| Цвет | RGB | Использование |
|------|-----|---------------|
| Primary | 33, 150, 243 | Основной синий цвет |
| Secondary | 76, 175, 80 | Вторичный зелёный цвет |
| Accent | 255, 152, 0 | Акцентный оранжевый цвет |
| Background | 245, 245, 245 | Фон интерфейса |
| Text | 33, 33, 33 | Основной текст |
| Border | 224, 224, 224 | Границы элементов |

## 📊 Системные характеристики

- **Разрешение**: 1080x1920 (Full HD)
- **DPI**: 420 (как у современных смартфонов)
- **Память**: 2GB (симуляция)
- **Батарея**: 100% (симуляция)
- **Процессы**: До 64 одновременных процессов

## 🔧 API

### Kernel API

```c
void kernel_init();
SystemInfo* kernel_get_system_info();
DeviceInfo* kernel_get_device_info();
uint32_t kernel_create_process(const char* name);
void kernel_kill_process(uint32_t pid);
```

### Graphics API

```c
bool graphics_init(int width, int height, const char* title);
void graphics_clear(Color color);
void graphics_draw_rect(Rect rect, Color color, bool filled);
void graphics_draw_circle(int x, int y, int radius, Color color, bool filled);
void graphics_draw_text(const char* text, int x, int y, Color color);
```

### UI API

```c
Screen* ui_create_screen(const char* name);
UIElement* ui_create_button(int x, int y, int w, int h, const char* label);
UIElement* ui_create_icon(int x, int y, int size, const char* icon_name);
void ui_add_element(Screen* screen, UIElement* element);
void ui_show_screen(Screen* screen);
void ui_handle_touch(int x, int y);
```

## 🐛 Известные ограничения

1. **Эмодзи**: Используются для иконок приложений (требуют поддержки шрифтом)
2. **Приложения**: Это заглушки, не полнофункциональные приложения
3. **Файловая система**: Не реализована
4. **Сеть**: Только симуляция
5. **Звук**: Не реализован

## 🚀 Возможные улучшения

- [ ] Реальная файловая система
- [ ] Система приложений (загрузка динамических библиотек)
- [ ] Многопроцессность и многопоточность
- [ ] Система разрешений и безопасности
- [ ] Поддержка жестов (свайп, пинч-зум)
- [ ] Анимации переходов между экранами
- [ ] Система уведомлений
- [ ] Поддержка виджетов
- [ ] Темная тема
- [ ] Поддержка различных разрешений экрана

## 📝 Лицензия

Этот проект создан в образовательных целях.

## 👨‍💻 Разработчик

**Manus AI** — Autonomous General AI Agent

---

**Версия**: 1.0  
**Дата**: 2026-06-01  
**Язык**: C11  
**Платформа**: Linux/macOS/Windows (с SDL2)
