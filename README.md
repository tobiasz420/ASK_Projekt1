# ASK Projekt 1

## Wstęp
Program został napisany w języku C i spełnia następujące wymagania:
1. Drukuje postać bajtową danych INT, FLOAT, DOUBLE
2. Drukuje postać binarną dla liczb jak w p 1
3. Prezentuje zasadę wykonywania odejmowania w U2
4. Prezentuje konwersję FLOAT -> DEC i DEC -> FLOAT

## Opis działania programu

### 1. Wyświetlanie postaci bajtowej liczb
Program przyjmuje liczby w formacie int, float i double, a następnie wypisuje ich 
reprezentację w pamięci jako ciąg bajtów. Dzięki temu można zobaczyć, jak wartości są 
przechowywane na poziomie niskopoziomowym.

### 2. Wyświetlanie postaci binarnej liczb 
Każda liczba jest również prezentowana w systemie binarnym. Program konwertuje bajty 
liczby na bity, umożliwiając analizę ich struktury. Jest to szczególnie użyteczne przy 
zrozumieniu formatów przechowywania danych. 

### 3. Prezentacja odejmowania w kodzie U2 (kodzie uzupełnień do dwóch) 
Kod uzupełnień do dwóch (U2) to sposób przechowywania liczb ujemnych w 
komputerze. Program demonstruje, jak działa odejmowanie liczb całkowitych w tym 
systemie. 
Przykładowo, jeśli odejmujemy 10 - 20, program pokaże, jak wartości te są zapisane w 
pamięci i jak uzyskiwany jest wynik w kodzie U2.

### 4. 4. Konwersja liczby FLOAT 
Program demonstruje sposób przechowywania liczb zmiennoprzecinkowych w 
standardzie IEEE 754. Pokazuje: 
- Jak wygląda reprezentacja float w pamięci 
- Jak liczba jest rozbijana na znak, wykładnik i mantysę 
- Jak można przekształcić te składniki z powrotem na liczbę dziesiętną

## Opis funkcji programu
Funkcja print_bytes
```c
void print_bytes(void *ptr, size_t size) {
  unsigned char *bytes = (unsigned char *)ptr;
  for (size_t i = 0; i < size; i++) {
    printf("%02X ", bytes[i]);
  }
  printf("\n");
}
```
