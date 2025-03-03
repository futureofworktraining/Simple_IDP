PROMPT:

Jesteś doświadczonym programistą webowym. Zbuduj aplikację zgodnie ze specyfikacją dostarczoną przez użytkownika. Wygeneruj całe rozwiązanie w jednym pliku. Zawsze wypisuj cały kod bazowy.

Nazwa aplikacji: "Aplikacja do OCR" 

Specyfikacja aplikacji
Gem-in-Docs to internetowe narzędzie do zwiększania produktywności, zaprojektowane jako proof-of-concept do inteligentnego przetwarzania dokumentów (IDP). Wykorzystuje modele AI Gemini firmy Google do wyodrębniania ustrukturyzowanych danych z dokumentów przesłanych przez użytkownika (PDF i obrazy) w oparciu o zdefiniowane przez użytkownika pola danych. Aplikacja jest zbudowana przy użyciu Materialize CSS dla interfejsu użytkownika i JavaScript po stronie klienta dla logiki aplikacji i interakcji API. Dane są przechowywane lokalnie w przeglądarce użytkownika za pomocą localStorage.

Wykorzystane technologie:
Local Storage
Materialize CSS
Gemini REST API

Ogólne zasady programowania:
Pamiętaj o zaimplementowaniu wszystkich funkcji.
Pamiętaj o zadeklarowaniu wszystkich niezbędnych funkcji i elementów w kodzie.
Używaj najlepszych praktyk programowania JS, HTML i CSS.
Upewnij się że aplikacja będzie działać poprawnie.

Interfejs użytkownika
Ogólne zasady dotyczące interfejsu użytkownika:
Upewnij się, że strona internetowa jest poprawnie sformatowana i zgodna z poniższą specyfikacją.
Wygląda przyjemnie dla użytkownika.
Zachowaj odstępy, marginesy między różnymi elementami interfejsu użytkownika.
Upewnij się, że wszystko jest łatwe do odczytania.
Interfejs użytkownika aplikacji jest podzielony na dwa główne panele z górnym paskiem nawigacyjnym

Layout Strony:
Góra strony.
Wyświetla logo marki i nazwę aplikacji.
Po prawej stronie znajdują się dwa przyciski:
Przycisk Ustawienia (szara ikona "ustawienia"): Otwiera okno dialogowe Ustawienia, aby zarządzać kluczem API, modelem LLM, promptem.

Lewy panel:
Zajmuje 25% szerokości kontenera i jest umieszczony po lewej stronie.
Zawiera następujące elementy:
Obszar przeciągnij i upuść: Wyznaczony obszar dla użytkowników do przeciągania i upuszczania plików dokumentów. Zawiera również przycisk "Dodaj pliki" do wybierania plików za pomocą okna dialogowego wprowadzania plików.
Poniżej obszaru przeciągnij i upuść powinien znajdować się przycisk "Wyodrębnij". Przycisk powinien być wyłączony, gdy nie ma przesłanego dokumentu.
Przycisk "Wyodrębnij": Uruchamia wyodrębnianie danych dla przesłanego pliku za pomocą interfejsu API Google Gemini.
Po prawej stronie przycisku "Wyodrębnij" na tym samym poziomie powinien znajdować się spinner, który uruchamia się, gdy dane są wyodrębniane z dokumentu/obrazu.

Prawy panel (nazwa: Procesowanie Dokumentów):
Zajmuje pozostałą przestrzeń w kontenerze i jest umieszczony po prawej stronie.
Wyświetla obraz lub plik PDF przesłany za pomocą obszaru przeciągnij i upuść po lewej stronie.
Powinien automatycznie wyświetlać obraz po przesłaniu obrazu lub pliku PDF. Wyświetlacz powinien zajmować około 30% wysokości.

Po przetworzeniu obrazu lub pliku PDF wyniki powinny pojawić się poniżej w formie proceduralnie wygenerowanego formularza wejściowego.
Sztuczna inteligencja odpowie JSON i na podstawie tego JSON powinien zostać wygenerowany formularz.
Zawiera przycisk "Eksportuj" z rozwijanym menu (CSV, Excel (XLSX)), aby wyeksportować JSON jako tabelę. Aplikacja daje możliwość wyeksportowania danych do Excel lub CSV.
Wyświetlanie użycia tokenów: Wyświetla szacunkowe zużycie tokenów i koszt dla dokumentu.
Obszar komunikatów o błędach: Wyświetla komunikaty o błędach w kolorze czerwonym, jeśli wystąpią podczas przetwarzania.

Obliczanie użycia i kosztu tokenów:
Po każdym wywołaniu API aplikacja analizuje usageMetadata.totalTokenCount z odpowiedzi Gemini API.
Liczba tokenów i szacunkowy koszt są obliczane i wyświetlane w interfejsie użytkownika.
Koszt jest szacowany przy użyciu wartości "Koszt za milion tokenów" z ustawień użytkownika.
Liczba tokenów i koszt są śledzone dla każdego pliku.

Okna dialogowe - Ustawienia :
Okno dialogowe Ustawienia: Modalne okno dialogowe do zarządzania ustawieniami aplikacji.
Zawiera pola wejściowe dla: Klucz API Gemini (z szyfrowaniem po stronie klienta i tekstem pomocniczym), jego wartość powinna być zapisana i utrzymywana przez sesję, traktuj ją jak wartość hasła,
Model LLM (wybór rozwijany) domyślnie powinien to być gemini-2.0-flash-001,
Prompt (textarea) - Domyślny prompt powinien brzmieć: wyodrębnij dane z załączonego dokumentu. Wyodrębnij dane z załączonego dokumentu. Zwróć czysty JSON. Nie używaj zagnieżdżonych obiektów i tablic. Nie używaj JSON array jako obiektu początkowego,
Koszt za milion tokenów (wprowadzanie liczb) - domyślna wartość powinna wynosić 0,10.
Zawiera przyciski: "Zapisz" i "Anuluj" oraz przycisk "Wyczyść dane", który wyczyści dane powiązane z tą aplikacją

Modalne okno dialogowe Informacja prawna: Modalne okno dialogowe wyświetlające wyłączenie odpowiedzialności prawnej i warunki korzystania z aplikacji.
Zawiera przyciski "Zamknij" i "Rozumiem i kontynuuj".
Status, czy powiadomienie zostało potwierdzone, powinien zostać zapisany, aby nie trzeba było o to pytać ponownie.
Wyłączenie odpowiedzialności mówi:
Przed użyciem [nazwa aplikacji] prosimy o zapoznanie się z następującymi informacjami:
To jest aplikacja demonstracyjna:
[nazwa aplikacji] jest dostarczany jako demonstracja i proof of concept. Nie jest to w pełni obsługiwana, gotowa do produkcji aplikacja.
"Tak jak jest" i bez gwarancji:
Ta aplikacja jest dostarczana "tak jak jest", bez jakiejkolwiek gwarancji, wyraźnej lub dorozumianej, w tym między innymi gwarancji przydatności handlowej, przydatności do określonego celu i nienaruszania praw. W żadnym wypadku twórcy lub współtwórcy nie ponoszą odpowiedzialności za jakiekolwiek roszczenia, szkody lub inne zobowiązania, czy to w ramach umowy, deliktu, czy w inny sposób, wynikające z, z powodu lub w związku z aplikacją lub korzystaniem lub innymi działaniami w aplikacji. Używaj na własne ryzyko.
Użycie i potencjalne koszty API:
Chociaż [nazwa aplikacji] jest obecnie oferowany bezpłatnie, jego funkcjonalność opiera się na modelach AI Gemini firmy Google. Należy pamiętać, że korzystanie z niego może spowodować koszty API od Google, za które ponosisz wyłączną odpowiedzialność.
Prywatność i obsługa danych:
Brak plików cookie lub śledzenia użytkowników: Ta aplikacja nie wykorzystuje plików cookie ani nie śledzi działań użytkowników.
Lokalne przechowywanie w przeglądarce: Dane związane z aplikacją są przechowywane wyłącznie w lokalnej pamięci przeglądarki i nie są przesyłane na zewnątrz.
Przetwarzanie danych Google Gemini: Aby zapewnić swoją funkcjonalność, [nazwa aplikacji] przesyła przesłane pliki do serwerów AI Gemini firmy Google w celu przetworzenia.
Brak przechowywania plików: Sam [nazwa aplikacji] nie przechowuje ani nie zachowuje przesłanych plików ani przetworzonych danych poza aktywną sesją przetwarzania. Twoje pliki są przetwarzane, a wyniki są Ci przedstawiane. Pliki nie są przesyłane poza środowisko przeglądarki, z wyjątkiem transmisji do serwerów Google Gemini w celu przetworzenia.
Klikając "Rozumiem i kontynuuj", potwierdzasz, że przeczytałeś, zrozumiałeś i zgadzasz się na te warunki.

Stopka:
Nie dodawaj stopki.

Komunikacja z użytkownikiem:
Używaj toastów do komunikacji z użytkownikiem.
Powiadom użytkownika, czy obraz/dokument został przetworzony lub przesłany poprawnie.
Powiadom użytkownika o błędach.
Użyj następującej palety kolorów w zależności od typu powiadomienia:
Czerwona paleta kolorów dla błędów.
Zielony dla udanej transakcji.
Żółty z czarnym tekstem dla ostrzeżeń.
<GROUNDING>

Wywołania API (Google Gemini API)
Aplikacja wykonuje wywołania do interfejsu API Google Gemini w celu wyodrębnienia danych.
Adres URL punktu końcowego API: https://generativelanguage.googleapis.com/v1beta/models/{model}:generateContent?key={apiKey}
{model}: Symbol zastępczy dla wybranego modelu Gemini LLM (np. gemini-pro, gemini-pro-vision, gemini-1.5-flash-002). Model jest dynamicznie wstawiany z ustawień użytkownika.
{apiKey}: Symbol zastępczy dla klucza API Gemini użytkownika. Klucz API jest dynamicznie wstawiany z odszyfrowanej wartości localStorage.
Metoda żądania: POST
Nagłówki żądania:
Content-Type: application/json
Treść żądania (JSON):

{
  "contents": [
    {
      "role": "user",
      "parts": [
        {
          "text": "{dynamic_prompt}"
        },
        {
          "inlineData": {
            "mimeType": "{mime_type}",  // "application/pdf" or "image/jpg"
            "data": "{base64_encoded_file_content}"
          }
        }
      ]
    }
  ],
  "generationConfig": {
    "responseMimeType": "application/json",
    "maxOutputTokens": 4000,
    "temperature": 0.5,
    "topP": 0.95
  },
  "safetySettings": [
    {
      "category": "HARM_CATEGORY_DANGEROUS_CONTENT",
      "threshold": "BLOCK_ONLY_HIGH"
    },
    {
      "category": "HARM_CATEGORY_SEXUALLY_EXPLICIT",
      "threshold": "BLOCK_ONLY_HIGH"
    },
    {
      "category": "HARM_CATEGORY_HARASSMENT",
      "threshold": "BLOCK_ONLY_HIGH"
    }
  ],
  "systemInstruction": {
    "role": "model",
    "parts": [
      {
        "text": "You are a helpful assistant."
      }
    ]
  }
}
Use code with caution.
Json
Json
Use code with caution.
{dynamic_prompt}: Dynamicznie generowany ciąg promptu. Zawiera:

Podstawowy szablon promptu z ustawień (geminiPrompt).

Definicje pól danych (nazwy i opisy) sformatowane jako ciąg podobny do JSON.

Opcjonalny sufiks z wybranej partii (batch.suffix).

{mime_type}: Typ MIME przesłanego pliku (określony przez rozszerzenie pliku, zazwyczaj "application/pdf" lub "image/jpg").

{base64_encoded_file_content}: Ciąg zakodowany w Base64 zawartości przesłanego pliku.
Używaj kodu z ostrożnością.
Użycie klucza API: Klucz API Gemini jest pobierany (odszyfrowywany) z localStorage i dynamicznie wstawiany do adresu URL punktu końcowego API dla każdego żądania.

Lista dostępnych modeli gemini:
gemini-1.5-flash-8b-latest
gemini-1.5-pro-002
gemini-1.5-flash-002
gemini-exp-1206
gemini-2.0-flash-001
gemini-2.0-flash-thinking-exp-01-21

</GROUNDING>
Względy bezpieczeństwa
Szyfrowanie po stronie klienta: Klucz API Gemini jest szyfrowany po stronie klienta za pomocą AES za pośrednictwem biblioteki CryptoJS przed zapisaniem w localStorage. Uwaga: Szyfrowanie po stronie klienta nie jest w pełni bezpiecznym rozwiązaniem i zapewnia przede wszystkim zaciemnianie.

Stos technologiczny
Frontend: HTML, CSS (Materialize CSS Framework), JavaScript
Biblioteki JavaScript:
Materialize CSS JavaScript
xlsx-js (do eksportu do Excela)
CryptoJS (do szyfrowania klucza API)
