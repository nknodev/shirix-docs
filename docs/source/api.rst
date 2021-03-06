API
=====

.. _endpoint:

Endpoints
------------
v1 - https://shirix-api.nkno.site/v1

v2 - https://shirix-api.nkno.site/v2



.. _v1:

v1
------------

.. _/getop:
/getOpening
------
получение опенингов по shikimori_id

.. code-block:: console

  GET /v1/getOpening?id=32  -  id  аниме на шикимори, либо id на MAL *ОБЯЗАТЕЛЬНЫЙ

.. code-block:: console

  {
     "ok": true,
     "themes": [
               {
                  "title": "Thanatos -If I Can't Be Yours-",
                  "theme_id": "32-00",
                  "type": "ED",
                  "artist": null,
                  "mirrors": [
                     {
                        "quality": "BD, 1080",
                        "mirror": "https://animethemes.moe/video/EvangelionEndOfEvangelion-ED1.webm",
                        "audio": "http://animethemes-api.herokuapp.com/api/v1/theme/32-00/0/audio"
                     }
                  ],
                  "notes": null,
                  "episodes": "",
                  "category": null
               }
               ]
   }

.. _/getep:
/getEpisodes
------
Получение списка всех доступных озвучек со всеми доступными эпизодами по shikimoriid

.. code-block:: console

  GET /v1/getEpisodes?id=32  -  id аниме на шикимори, либо id на MAL *ОБЯЗАТЕЛЬНЫЙ

.. code-block:: console

  {
      "ok": true,
      "casts": [
                  {
                     "name": "Digital Force",
                     "kodik_id": 1181,
                     "episodes_count": 2,
                     "type": "voice",
                     "episodes": {
                        "1": "//aniqit.com/seria/643037/9982aac21d30e953089a65544eddec8b/720p",
                        "2": "//aniqit.com/seria/643038/774eaeaafb86cf666ba20cc518e272d2/720p"
                     }
                  }
               ]
   }


.. _/getanisearch:
/getSearchAnime
------
Поиск аниме. Показывается 50штук на 1страницу.

.. code-block:: console

  GET /v1/getSearchAnime?q=Унеси меня на луну  -  поисковой запрос *ОБЯЗАТЕЛЬНЫЙ
                         page=1 - страница

.. code-block:: console

  {
      "ok": true,
      "message": "yeah",
      "results": [
                   {
                     "id": 41389,
                     "name": "Tonikaku Kawaii",
                     "russian": "Унеси меня на Луну",
                     "image": {
                       "original": "/system/animes/original/41389.jpg?1637057457",
                       "preview": "/system/animes/preview/41389.jpg?1637057457",
                       "x96": "/system/animes/x96/41389.jpg?1637057457",
                       "x48": "/system/animes/x48/41389.jpg?1637057457"
                     },
                     "url": "/animes/41389-tonikaku-kawaii",
                     "kind": "tv",
                     "score": "7.92",
                     "status": "released",
                     "episodes": 12,
                     "episodes_aired": 12,
                     "aired_on": "2020-10-03",
                     "released_on": "2020-12-19"
                   }
   }


.. _v2:

v2
------------
.. _/getsh:
/getSchedule
------
Расписание аниме. Указывается по азиатскому времени.

.. code-block:: console

  GET /v2/getSchedule?day=sunday  -  день за который получаем расписание, если не указывать day он установится в значение today

.. code-block:: console

   {
     "ok": true,
     "message": "sorry guys, i can't get ru title of anime, i dumb",
     "ids": [
      51037
     ],
     "releases": [
                   {
                   "id": 51037,
                   "title_en": "Duel Masters King Max",
                   "pic": "https://cdn.myanimelist.net/images/anime/1191/122796l.jpg",
                   "bc_time": "08:30",
                   "bc_tz": "Asia/Tokyo"
                   }
     ]
    }


.. _/getplayer:
/getPlayer
------
Измененный плеер кодик без рекламы, с плюшками.

.. note::

   Плеер активен 24часа после создания ссылки на плеер через запрос

.. note::

   Внимание! С недавних пор в API начала наблюдаться ошибка "can't work with serial". Данная ошибка вызвана тем, что Кодик обновил систему iframe по которой мы получали прямую ссылку. Чтобы получить прямую ссылку в текущих условиях, вам нужно передать ссылку Кодик не на сериал(//aniqit.com/serial/44281/ee91817bd88c4d378ebf9d24cfa118c2/720p), а на определенную серию этого сериала(//aniqit.com/seria/157612/2116b0693328735fa422174757185d03/720p), ссылку на конкретную серию вы можете получить через /getEpisodes. Благодарим за понимание, команда Shirix.

.. code-block:: console

  GET /v2/getPlayer?link=//aniqit.com/seria/643038/774eaeaafb86cf666ba20cc518e272d2/720p  -  ссылка на плеер, который преобразовываем

.. code-block:: console

   {
     "ok": true,
     "player":"https://shirix-player.web.app/?360=https://cloud.kodik-storage.com/useruploads/beb49eb3-3c5e-4270-b15a-7ac0039d8889/2d1ba10b9a6f9a38f3126e3cfcbc6f4d:2022061611/360.mp4&480=https://cloud.kodik-storage.com/useruploads/beb49eb3-3c5e-4270-b15a-7ac0039d8889/2d1ba10b9a6f9a38f3126e3cfcbc6f4d:2022061611/480.mp4&720=https://cloud.kodik-storage.com/useruploads/beb49eb3-3c5e-4270-b15a-7ac0039d8889/2d1ba10b9a6f9a38f3126e3cfcbc6f4d:2022061611/720.mp4"
    }
