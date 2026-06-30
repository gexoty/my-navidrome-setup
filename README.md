# Мой Setup SelfHosted музыки

Что он в себе содержит?

[MeTube](https://github.com/alexta69/metube) - Сервис по скачиванию видео\аудио из YouTube

[metadata-docker](https://hub.docker.com/r/oneandonlyjonnyponny/metadata-docker) - Web-Редактор Тегов в музыкальных файлах

[Dromeport](https://github.com/sensor0x0/Dromeport) - Сервис по скачиванию музыки из YouTube Music и Spotify с подгрузкой тегов из MusicBrainz

[Feishin](https://github.com/jeffvli/feishin) - SubSonic API совместимый Web-Плеер для Navidrome

[Transmission (docker)](https://github.com/linuxserver/docker-transmission) - Docker-Образ WebTorrent клиента

[Navidrome](https://github.com/navidrome/navidrome) - Стример музыкальной библиотеки файлов

## Используемые плагины Navidrome

[navidrome-shazam-plugin](https://github.com/Myzel394/navidrome-shazam-plugin)

[apple-music-plugin](https://github.com/navidrome/apple-music-plugin)

[discord-rich-presence-plugin](https://github.com/navidrome/discord-rich-presence-plugin)

[navidrome-lyrics-plugin](https://github.com/J0R6IT0/navidrome-lyrics-plugin)

## Запуск

Первым делом устанавливаем [Nginx Proxy Manager](https://github.com/NginxProxyManager/nginx-proxy-manager) и проверяем что появилась сеть 
```yaml
npm_default
```
После этого используем docker-compose.yml из репозитория.

При желании можете использовать файл navidrome.toml (для правильного разделения артистов)

В NPM хосты настраиваем следующим образом

| Host | Forward | Port | Security |
| :--- | :--- | :--- | :--- |
| dromeport.yourdomain.org | dromeport | 8080 | http basic auth |
| feishin.yourdomain.org | feishin | 9180 | Public |
| metadata.yourdomain.org | metadata-docker | 5000 | Public |
| metube.yourdomain.org | metube | 8081 | http basic auth |
| navidrome.yourdomain.org | navidrome | 4533 | Public |
| torrent.yourdomain.org | transmission | 9091 | Public |

И в ОБЯЗАТЕЛЬНОМ порядке подключаем SSL сертификаты (вкладка SSL). Ну и ставим галочки WebSocket Support и Block Common Exploits

В целом готово. Можно пользоваться
