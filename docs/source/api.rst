API
=====

.. _endpoint:

Endpoints
------------
v1 - https://shirix-api.nkno.site/v1
v2 - https://shirix-api.nkno.site/v2



.. _getop:

v1
------------

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
