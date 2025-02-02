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

### 4. Konwersja liczby FLOAT 
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
Funkcja print_bytes iteruje po kolejnych bajtach w danym obszarze pamięci, wyświetlając każdy z nich w formacie szesnastkowym. Pozwala to na wizualizację struktury danych w surowej formie.

Funkcja print_binary
```c
void print_binary(void *ptr, size_t size) {
    unsigned char *bytes = (unsigned char *)ptr;
    for (size_t i = 0; i < size; i++) {
        for (int j = 7; j >= 0; j--) {
            printf("%d", (bytes[i] >> j) & 1);
        }
        printf(" ");
    }
    printf("\n");
}

```
Funkcja ta przedstawia zawartość pamięci w formie binarnej. Przechodzi przez każdy bajt, a następnie przez każdy jego bit, wyświetlając 0 lub 1. Daje to możliwość analizy surowej binarnej reprezentacji danych.

Funkcja subtraction_U2
```c
void subtraction_U2(int a, int b) {
    printf("Liczba A: %d\n", a);
    printf("Liczba B: %d\n", b);
    int result = a - b;
    printf("Wynik A - B = %d\n", result);
    printf("Bajty A: ");
    print_binary(&a, sizeof(a));
    printf("Bajty B: ");
    print_binary(&b, sizeof(b));
    printf("Bajty wyniku: ");
    print_binary(&result, sizeof(result));
}
```
Funkcja demonstruje odejmowanie w U2, prezentując liczby i ich reprezentacje binarne, co ułatwia zrozumienie bitowej logiki odejmowania.

Funkcja float_conversation
```c
void float_conversion(float f) {
    printf("FLOAT: %f\n", f);
    printf("Bajty FLOAT: ");
    print_binary(&f, sizeof(f));

    uint32_t binary;
    memcpy(&binary, &f, sizeof(f));

    int sign = (binary >> 31) & 1;
    int exponent = ((binary >> 23) & 0xFF) - 127;
    int mantissa = binary & 0x7FFFFF;
    
    printf("Znak: %d\n", sign);
    printf("Eksponent: %d\n", exponent);
    printf("Mantysa: 1.%d\n", mantissa);

    float reconstructed;
    memcpy(&reconstructed, &binary, sizeof(binary));
    printf("Odwrotnie przekonwertowany FLOAT: %f\n", reconstructed);
}
```
Konwertuje liczbę float na składowe (znak, eksponent, mantysa) standardu IEEE 754 i z 
powrotem. Wyświetla oryginalną liczbę, jej reprezentację binarną oraz wydzielone 
składowe, demonstrując sposób zapisu liczb zmiennoprzecinkowych w pamięci. 

## Wynik działania programu
![](/wyniki.png)

## Autor
Michał Kurpiewski 21253

## Licencja
Licencja MIT
