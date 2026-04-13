# Sprawdzanie_hipotez
# Analiza funkcji mocy testów statystycznych z wykorzystaniem symulacji Monte Carlo

## Opis projektu
Projekt przedstawia badanie skuteczności i rzetelności trzech popularnych testów statystycznych: testu Z, testu t-Studenta oraz nieparametrycznego testu rang znakowanych Wilcoxona. Głównym celem jest weryfikacja hipotezy o wartości oczekiwanej ($H_0: \mu=1$ przeciwko $H_1: \mu \neq 1$) oraz analiza zachowania testów w warunkach idealnych, a także przy naruszeniu podstawowych założeń modelowych.

Analiza została oparta na metodach numerycznych, w tym symulacjach Monte Carlo, pozwalających na empiryczne wyznaczenie funkcji mocy testów i ocenę prawdopodobieństwa popełnienia błędu I rodzaju.

## Zakres analizy
Projekt bada działanie testów w trzech zróżnicowanych środowiskach danych:

1. **Warunki idealne (rozkład normalny, znana wariancja):** Dane generowane z rozkładu $N(\mu, 2^2)$. Weryfikacja działania testów w środowisku w pełni zgodnym z założeniami testu parametrycznego.
2. **Niedoszacowanie wariancji w modelu:** Dane generowane z rozkładu $N(\mu, 4^2)$, przy zachowaniu założenia statystyki testu Z o odchyleniu standardowym równym 2. Scenariusz ukazuje konsekwencje błędnej specyfikacji modelu i utratę kontroli nad poziomem istotności $\alpha$.
3. **Naruszenie założenia o normalności (rozkład asymetryczny):** Dane generowane z rozkładu wykładniczego $E(1/\mu)$. W tym etapie połączono analityczne wyprowadzenie funkcji mocy (dla testu Z) z symulacjami Monte Carlo (dla t-Studenta i Wilcoxona), obrazując wpływ rosnącej wariancji i asymetrii danych na kształt funkcji mocy.

## Kluczowe wnioski z badania
* **Odporność metod parametrycznych:** Test t-Studenta zachowuje skuteczność i kontroluje błąd I rodzaju nawet przy naruszeniu założeń o rozkładzie (przy odpowiednio dużej próbie, $N=100$).
* **Zagrożenia wynikające z założeń:** Test Z traci rzetelność w momencie błędnego oszacowania wariancji, stając się nadwrażliwym i zbyt często odrzucając prawdziwą hipotezę zerową.
* **Wydajność metod nieparametrycznych:** Test Wilcoxona potwierdza swoją przydatność jako bezpieczna alternatywa, osiągając moc zbliżoną do testów klasycznych przy braku wymogu normalności rozkładu.

## Wymagania i środowisko techniczne
Projekt został napisany w języku R. Do generowania danych i wyliczania statystyk testowych użyto wbudowanych funkcji środowiska (m.in. `rnorm`, `rexp`, `t.test`, `wilcox.test`, `pnorm`).

Wymagane biblioteki do reprodukcji wyników i wizualizacji:
* `ggplot2` - tworzenie wykresów funkcji mocy.
* `tidyr` - przekształcanie struktur danych na potrzeby wizualizacji (format long).

## Uruchomienie skryptu
1. Sklonuj repozytorium na swój dysk lokalny.
2. Zainstaluj wymagane pakiety, wpisując w konsoli R:
   ```R
   install.packages(c("ggplot2", "tidyr"))
