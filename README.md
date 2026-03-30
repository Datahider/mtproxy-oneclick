# mtproxy-oneclick
Простая установка MTProxy на арендованный VPS

Устанавливает MTProxy + Nginx + sslh одной командой.

Работает на:
- Ubuntu 24.04
- Debian 12

Ничего вводить не нужно. Просто запускаешь и всё работает.

---

## 🚀 Установка

```bash
sudo bash mtproxy-oneclick.sh
```

---

## 📦 Что устанавливается

- MTProxy (Telegram proxy)
- sslh (мультиплексирование порта 443)
- nginx (сайт-заглушка)
- UFW (firewall)

---

## 🌐 Что будет после установки

Открываешь в браузере:

```
http://YOUR_IP
https://YOUR_IP
```

И видишь страницу с подтверждением, что сервер работает.

---

## 🔗 Подключение к MTProxy

Скрипт выведет ссылку после установки.

Пример:

```
tg://proxy?server=YOUR_IP&port=443&secret=SECRET
```

или:

```
https://t.me/proxy?server=YOUR_IP&port=443&secret=SECRET
```

---

## 🔧 Управление

```bash
systemctl status mtproxy
systemctl restart mtproxy
systemctl stop mtproxy
journalctl -u mtproxy -f
```

---

## 🔄 Обновление конфигурации MTProxy

Автоматически:
- каждый день в 03:00

Ручной запуск:
```bash
/opt/MTProxy/update-config.sh
```

---

## 🔌 Как это работает

Порт 443 делится через sslh:

```
443:
 ├── SSH      → 22
 ├── HTTPS    → nginx (8443)
 └── MTProxy  → 9443
```

---

## ⚠️ Важно

- HTTPS использует самоподписанный сертификат
- Браузер покажет предупреждение — это нормально
- Порты 8443 и 9443 закрыты извне

---

## 🧱 Требования

- Чистый сервер
- root доступ
- Интернет

---

## 💻 Где можно арендовать VPS


---

## 📄 Лицензия

MIT
