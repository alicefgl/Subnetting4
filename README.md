# Subnetting4

CONSEGNA:

Creare il piano di indirizzamento per una rete così composta:
- la rete principale è la 172.130.20.0/24
- si vuole fare subnetting in modo da ottenere 4 sottoreti della stessa dimensione

- 1 router con 4 porte
- 8 PC
- 4 switch
- Ciascuna sottorete ha 1 switch e 2 PC, il router permette la comunicazione tra le 4 sottoreti

CONOSCENZE TEORICHE: Il subnetting è una suddivisione di una rete principale in diverse sottoreti che possono contenere un determinato numero di dispositivi ai quali corrisponde un indirizzo ip, per eseguire il calcolo del subnetting è perciò necessario definire gli intervalli delle combinazioni di indirizzi ip per ogni sottorete e la subnet mask relativa all'insieme. Questo processo si applica in base a determinate esigenze che costringono quindi chi struttura una rete ad abbandonare le classi di indirizzi, si avranno perciò delle configurazioni classless. ([Relazione sul subnetting di una rete in due](https://github.com/alicefgl/Subnetting/blob/main/README.md)).

SVOLGIMENTO:

1) Calcolo dei range di indirizzi ip per ogni sottorete:

In questo caso siccome è dato dalla consegna un indirizzo ip di classe C, l'unico ottetto dedicato agli host è l'ultimo, si avrà quindi un numero massimo di dispositivi pari a 256.
Il calcolo è quindi 256 / 4 = 64 =>  i range di indirizzi corrispondono ad una rete diversa ogni 64 combinazioni.

2) Definizione dei range per ogni sottorete:

sottorete 1:

172.130.20.0  -> id_rete

172.130.20.63  -> id_broadcast

sottorete 2:

172.130.20.64 -> id_rete

172.130.20.127  -> id_broadcast

sottorete 3:

172.130.20.128  -> id_rete

172.130.20.191  -> id_broadcast

sottorete 4:

172.130.20.192  -> id_rete

172.130.20.255  -> id_broadcast

Ai dispositivi si assegnano gli indirizzi ip compresi tra questi, escludendo perciò quelli relativi alla sottorete stessa o al broadcast.

3) Calcolo subnet mask:

Numero di sottoreti desiderate: 4 = 2^2
Si modificano quindi i primi due ottetti, che presentano 4 possibili combinazioni (lo stesso numero di sottoreti).
Se si pongono i primi due bit dell'ultimo ottetto a 1, la subnet mask sarà uguale a 11111111.11111111.11111111.11000000 = 255.255.255.192
In quanto 2^6 + 2^7 = 64 + 128 = 192
