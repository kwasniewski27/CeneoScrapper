# CeneoScrapper

## kod produktu, o którym będą pobierane opinie
84514582
## algorytm pobierania opinii o pojedynczym produkcie z serwisu Ceneo.pl
1.  Wysłanie żądania dostępu do strony z opiniami produktu
2.  Jeżeli operacja zakończy się sukcesem, wyodrębnienie z kodu strony fragmentów odpowiadających poszczególnym opiniom
3.  Dla każdej z opinii wydobycie z kodu HTML poszczególnych składowych i zapisanie ich w postaci złożonych struktur danych
4.  Jeżeli istnieje kolejna strona z opiniami, przejście na tę stronę i powtórzenie dla niej kroków 1-4
5.  Zapisanie wszystkich opinii w bazie danych

## Struktura opinii w serwisie Ceneo.pl
|składnia|zmienna|selektor|
|--------|-------|--------|
|opinia|review|div.js_product-review:not(.user-post--highlight)|
|identyfikator opinii|review_id|['data-entry-id']|
|autor|author|span.user-post__author-name|
|rekomendacja|recomendation|span.user-post__author-recomendation > em|
|liczba gwiazdek|stars|span.user-post__score-count|
|treść opinii|content|div.user-post__text|
|listę zalet|pros|div.review-feature__item--positive|
|listę wad|cons|div.review-feature__item--negative|
|ile osób uznało opinię za przydatną|likes|span[id^='votes-yes']|
|ile osób uznało opinię za nieprzydatną|dislikes|span[id^='votes-no']|
|data wystawienia opinii|publish_date|span.user-post__published > time:nth-child(1)['datetime']|
|data zakupu produktu|purchase_date|span.user-post__published > time:nth-child(2)['datetime']|