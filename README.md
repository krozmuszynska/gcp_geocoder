# gcp_geocoder

Niniejsze repozytorium zawiera skrypty będące częścią pracy inżynierskiej.

Autor: Kinga Rozmuszyńska

Uczelnia: Szkoła Główna Gospodarstwa Wiejskiego

Warszawa, 30 Czerwca 2020 roku

## Zawartość repozytorium
Skrypt generujący lokalizację przestrzenne (współrzędne) na podstawie adresów w pliku Excel.

Do użycia pliku wymagany jest Python w wersji 3.8 oraz biblioteki:
- openpyxl
- geocoder

## Uruchomienie skryptów w lokalnym środowisku
W celu uruchomienia skryptów lokalnie (na swoim komputerze) należy wykonać poniższe kroki. W tym celu będziesz potrzebował zainstalowanego Pythona 3, szczegóły znajdziesz tutaj [python.org](https://www.python.org/downloads/). Potrzebujesz również `git`-a, żeby ściągnąć repozytorium na dysk, szczegóły znajdziesz tutaj [git-scm.com](https://git-scm.com/). Dalej za pomocą polecenia `pip` musisz zainstalować biblioteki `geojson` (do obsługi formatu GeoJSON), `openpyxl` (do odczytania plików Excel) oraz `jinja2` (do odczytania szablonów strony geoportalu).

W skrócie, po zainstalowaniu Python-a i Git-a wykonaj poniższe polecenia w terminalu:
```
$ git clone <GitHub address>
$ cd <projName>
$ virtualenv .venv --python=python3
$ source .venv/bin/activate
$ pip install -r requirements.txt
```

Twoje środowisko jest gotowe i możesz uruchomić kod z repozytorium:

```
$ python3 gcp_geocoder.py -i sample/dane.xlsx -o sample/dane_gps.xlsx -w "dane" -k <Twój klucz API KEY>
```

## Struktura danych wejściowych skryptu
Dane wejściowe są zapisane w formacie Microsoft Excel (xlsx). Arkusz zawiera co najmniej jeden skoroszyt z następującymi kolumnami:
1. ID - unikalny identyfikator obiektu
2. **Latitude [N]** - szerokość geograficzna punktu podawana w formie dziesiętnej. **To uzupełnia skrypt**
3. **Longitude [E]** - długość geograficzna punktu podawana w formie dziesiętnej **To uzupełnia skrypt**
4. Marker ID - przyporządkowany do punktu identyfikator znacznika (zostanie wykorzystany w dalszych pracach)
5. Name - tekstowa nazwa punktu, może zawierać kod HTML
6. Description - tekstowy opis punktu, może zawierać kod HTML
7. Search key - tekst po który zostanie użyty w wyszukiwarce punktów (zostanie użyty w dalszych pracach)
8. Street - nazwa ulicy, tekst
9. Building no - numer budynku, tekst (znaki, cyfry)
10. Local no - numer lokalu, tekst (znaki, cyfry)
11. ZIP - kod pocztowy
12. City - nazwa miejscowości
13. Country - nazwa kraju
14. Telephone - numer tlefonu
15. E-mail - adres email
16. Web - adres strony www
