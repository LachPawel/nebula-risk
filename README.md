# 🌌 NEBULA RISK

**Gra losowa oparta na umiejętnościach i szczęściu | HackNation 2025**

---

## 📋 O Projekcie

**Nebula Risk** to innowacyjna gra free-to-play łącząca elementy umiejętności (timing) z losowością, stworzona w odpowiedzi na wyzwanie Totalizatora Sportowego. Gra wykorzystuje **kontrolę gestami dłoni** (MediaPipe) oraz **wizualizację 3D** (Three.js) do stworzenia angażującego doświadczenia opartego na koncepcji syntezy gwiazd w nebuli kosmicznej.

### 🎯 Główne Cechy

- **Kontrola gestami** - Używasz swojej dłoni jako kontrolera (bez potrzeby dotykania ekranu)
- **Mechanika umiejętności** - Musisz precyzyjnie wypuścić syntezę w odpowiednim momencie
- **Progresywna trudność** - 7 poziomów o rosnącym ryzyku i malejącej strefie celowania
- **Near-win experience** - System informuje, gdy byłeś blisko sukcesu
- **Antycypacja wyniku** - Każda decyzja buduje napięcie przed poznaniem rezultatu
- **Efekty wizualne** - Dynamiczne cząsteczki reagujące na stan gry (synteza, eksplozja, czarna dziura)

---

## 🎮 Jak Grać

### Zasady Podstawowe

1. **START**: Najedź dłonią na przycisk "ROZPOCZNIJ" i przytrzymaj przez ~1 sekundę
2. **SYNTEZA GWIAZDY**: 
   - Pokaż dłoń kamerze, aby rozpocząć ładowanie
   - Pasek ładowania będzie oscylował (0% → 100% → 0%)
   - **UWAGA**: Musisz wypuścić (schować rękę), gdy niebieski pasek jest w **żółtej strefie**
3. **WERYFIKACJA STABILNOŚCI**:
   - Jeśli trafiłeś w strefę → system sprawdzi, czy gwiazda jest stabilna (losowanie)
   - Jeśli chybiłeś → Natychmiastowa porażka
4. **DECYZJA**:
   - **WYPŁAĆ** - Zachowaj zdobyte punkty i zakończ grę
   - **RYZYKUJ** - Idź na wyższy poziom z większym mnożnikiem (ale mniejszą szansą)

### Progresja

| Poziom | Mnożnik | Szansa Sukcesu | Szerokość Strefy |
|--------|---------|----------------|------------------|
| 1      | x1.5    | 95%           | 25%             |
| 2      | x2.25   | 85%           | 22%             |
| 3      | x3.38   | 75%           | 19%             |
| 4      | x5.06   | 60%           | 16%             |
| 5      | x7.59   | 50%           | 13%             |
| 6      | x11.39  | 40%           | 10%             |
| 7      | x17.09  | 30%           | 7%              |

---

## 🛠️ Technologie

- **HTML5 / CSS3** - Struktura i styling
- **JavaScript (Vanilla)** - Logika gry
- **Three.js (r128)** - Renderowanie 3D i efekty cząsteczkowe
- **MediaPipe Hands** - Śledzenie dłoni w czasie rzeczywistym
- **WebGL** - Akceleracja graficzna

### Wymagania

- Przeglądarka z obsługą WebGL (Chrome, Firefox, Edge)
- Kamera internetowa
- Wyświetlacz: Desktop lub Mobile (responsywne)

---

## 🚀 Instalacja i Uruchomienie

### Metoda 1: Bezpośrednie uruchomienie

```bash
# Sklonuj repozytorium
git clone https://github.com/LachPawel/nebula-risk.git
cd nebula-risk

# Otwórz w przeglądarce (wymaga serwera HTTP dla MediaPipe)
# Opcja A: Python
python3 -m http.server 8000

# Opcja B: Node.js
npx http-server

# Otwórz: http://localhost:8000
```

### Metoda 2: Edytor na żywo

Możesz również otworzyć plik `index.html` bezpośrednio w przeglądarce, ale niektóre funkcje kamery mogą wymagać HTTPS.

---

## 📐 Architektura

### Struktura Kodu

```
index.html
├── UI Layer (DOM + CSS)
│   ├── HUD (wynik, poziom)
│   ├── Komunikaty stanu
│   └── Wirtualne przyciski
├── Three.js Scene
│   ├── System cząsteczek (8000 punktów)
│   ├── Kursor dłoni (ring)
│   └── Animacje fizyki (przyciąganie/eksplozja)
└── Game Logic
    ├── Tracking dłoni (MediaPipe)
    ├── Detekcja kolizji (reka ↔ przyciski)
    ├── Logika stanów (IDLE, CHARGING, DECISION, etc.)
    └── Mechanika losowania (RNG)
```

### Stany Gry

1. **IDLE** - Ekran startowy
2. **CHARGING** - Faza ładowania z timerem
3. **WIN_EXPLOSION** - Animacja złotej supernowej
4. **LOSS_IMPLOSION** - Animacja czarnej dziury
5. **DECISION** - Wybór: Wypłać lub Ryzykuj
6. **GAMEOVER** - Koniec rozgrywki

---

## 🎨 Design

### Paleta Kolorów

- **Nebula Blue** (#00ffff) - Cząsteczki, UI pozytywne
- **Nebula Purple** (#ff00ff) - Cząsteczki, efekty
- **Gold** (#ffaa00) - Sukces, eksplozja
- **Red** (#ff0055) - Porażka, ostrzeżenia
- **Dark Void** (#050505) - Tło

### Efekty Wizualne

- **Synteza**: Cząsteczki spiralnie wpadają do centrum, białe światło
- **Sukces**: Złota eksplozja, rozprzestrzeniające się fale energii
- **Porażka**: Implosja do czarnej dziury, zanikanie

---

## 🎯 Zgodność z Wymaganiami Wyzwania

### ✅ Założenia Obowiązkowe

- [x] Czytelne, łatwe zasady
- [x] Free-to-play
- [x] Istotny element losowości (weryfikacja stabilności gwiazdy)
- [x] Near-win experience ("Było tak blisko!")
- [x] Antycypacja wyniku (animacje ładowania + losowanie)
- [x] Komunikaty po polsku
- [x] Responsywność (desktop/mobile)

### 🔧 Opcje Dodatkowe

- [ ] Aspekt społecznościowy (możliwy rozwój: rankingi, tryb współpracy)
- [x] Progresja (7 poziomów, rosnąca trudność)
- [x] Second chance (decyzja Wypłać/Ryzykuj)
- [ ] Monetyzacja (możliwy rozwój: kosmetyki, power-upy)
- [ ] Lead generation (możliwy rozwój: system kont, newsletter)

---

## 🔮 Potencjał Rozwoju

### Krótkoterminowy (MVP+)
- System kont i logowania
- Rankingi globalne i lokalne
- Dzienne wyzwania z bonusami
- System osiągnięć (badges)

### Średnioterminowy
- Tryb multiplayer (współpraca 2 graczy w jednej syntezie)
- Sklep z kosmetykami (kolorystyki nebuli, efekty cząstek)
- System power-upów (freeze time, wider zone, lucky star)
- Integracja z portalami społecznościowymi (share wyników)

### Długoterminowy
- Narracja/kampania (odkrywanie galaktyki, misje story)
- Tryb turnieji z nagrodami
- VR/AR implementation
- Cross-platform sync (mobile app)

---

## 📊 Monetyzacja (Opcjonalne)

### Model F2P Etyczny

1. **Kosmetyki** - Motywy wizualne bez wpływu na gameplay
2. **Battle Pass** - Sezonowe nagrody za aktywność
3. **Premium Currency** - Kupowanie power-upów (nie pay-to-win)
4. **Reklamy wideo** - Opcjonalne za bonusy (nie inwazyjne)

**Transparentność**: Wszystkie współczynniki i szanse widoczne dla gracza

---

## 🔒 Zgodność z Regulacjami

- Brak elementów hazardowych (nie można wygrać prawdziwych pieniędzy)
- Pełna transparentność szans (widoczne procenty)
- Brak "lootboxów" w tradycyjnym sensie
- Odpowiednia kontrola dla 18+ (zgodnie z licencją TS)

---

## 👥 Autorzy

**Team**: 
- Paweł Lach  
- Bartosz Idzik

**Hackathon**: HackNation 2025 
**Wyzwanie**: Totalizator Sportowy - "Gaming: Los decyduje"

---

## 📄 Licencja

Projekt stworzony na potrzeby konkursu HackNation 2025.  
Kod udostępniony jako demo/prototyp.

---

## 🎬 Demo Video

[Link do wideo prezentującego rozgrywkę i mechanikę gry](https://youtu.be/G2P39kekYyE)

