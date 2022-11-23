# Proiect Wordle ASC

Proiect realizat de Marcu Dragos-Ionut (grupa 151) si Rotaru Vlad-Marius (grupa 151) 

## Prezentare generala

Atat jocul cat si jucatorul au fost facute in C++. Nu exista o interfata grafica pentru joc, totul se transmite prin text ori omului care joaca, ori "robotului" care ghiceste optim cuvintele.

## Legatura intre programe

Legatura dintre robot si joc este facuta prin intermediul a doua fisiere text: "sem.txt" si "com.txt", prin care se transmite un "semnal de rulare", respectiv date relevante jocului wordle. Initial in fisierul "sem.txt" trebuie sa se afle o valoare diferita de 0, 1 si 2, noi alegem 3. Exista semafoare atat in codul jocului cat si in codul robotului care intra intr-un loop infinit de citire a fisierului "sem.txt" pana cand se primeste un "semnal de rulare" bun (1 pentru joc, 0 sau 2 (sau 3 in cazul in care s-a transmis cuvantul corect) pentru jucator).

## Aflarea cuvantului optim de catre "robot" folosind entropia

Inainte de orice am precalculat cel mai bun cuvant de ghicit primul, acesta fiind TAREI.

Primul pas dupa ce "robotul" trimite un cuvant este acela de a sterge dintr-o multime cuvintele care nu indeplinesc conditiile impuse de indiciul transmis de catre joc. Cuvintele ramase in multime dupa acest pas vor fi denumite "bune".

Al doilea pas pe care "robotul" il face este de a calcula entropia tuturor cuvintelor nefolosite pana acum in O(n*(k+p)), unde n este marimea vectorului de cuvinte nefolosite, k este marimea multimii de cuvinte care ar putea fi raspunsul corect, iar p este numarul de permutari posibile ale indiciului (3<sup>5</sup>). Entropia unui cuvant este calculata adunand probabilitatea (px) fiecariei permutari posibile de indicii pe acel cuvant de a fi transimsa de catre joc.
px = numarul cuvintelor bune care ar face jocul sa furnizeze permutarea / numarul total de cuvinte bune

Al treilea pas este sortarea cuvintelor dupa entropie, avand prioritate cuvintele bune peste cele care au fost eliminate ca posibile raspunsuri finale.

## Numarul mediu de incercari

3.99022

## Referinte 

https://en.wikipedia.org/wiki/Entropy_(information_theory)
https://www.youtube.com/watch?v=v68zYyaEmEA
