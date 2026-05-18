# Pla de Transformació Digital 

## 1. Mapa de Processos
Hem optat per un model híbrid de mobilitat, prioritzant la rapidesa i l'eliminació d'errors humans.

### Pas 1:
El cambrer utilitza una tablet/smartphone a peu de taula. La comanda es sincronitza instantàniament via Wi-Fi amb el TPV central.

### Pas 2:
La comanda es divideix automàticament. Les begudes s'imprimeixen (o apareixen en pantalla) a la barra i el menjar a la cuina.

### Pas 3:
Quan tot sigui llest es notifica (el sistema) al cambrer. I al final es lliure el producte.

### Pas 4:
Quan el client es demana el compte es genera el tiquet des del TPV o impressora de cinturó i es processa el pagament.

---

## 2. Disseny de la Xarxa
Per garantir la seguretat de les dades bancàries i oferir un servei d'alta qualitat per a teletreballadors, implementarem una segmentació mitjançant VLANs.

### Arquitectura de xarxa:

- **VLAN 10 (Staff/Admin):** Xarxa oculta i xifrada per a TPVs, datàfons i impressores. Prioritat de trànsit alta (QoS).
- **VLAN 20 (Wifi clients):** Xarxa oberta amb portal captiu.

### Portal Captiu:
Abans de navegar, el client veu una pantalla de benvinguda amb el logo de la cafeteria i una promoció actual. Cal acceptar els termes d'ús.

### Aïllament (Client Isolation):
Els clients no poden veure's entre ells ni accedir als equips de l'empresa, per què estan en una xarxa diferent.

---

## 3. Pressupost de Hardware

| Element | Descripció | Unitats | Preu Unitari | Total |
|---|---|---|---|---|
| TPV Central + calaix efectiu | Pantalla tàctil 15" IP65 (Resistent a líquids) | 1 | 650€ | 650€ |
| tablets | Dispositius mòbils android “Motorola moto-g86 5G” | 2 | 199€ | 398€ |
| Router | Ubiquiti UniFi Dream Machine | 1 | 350€ | 350€ |
| Punt d'Accés | UniFi WiFi 6 Pro (Suporta +300 usuaris) | 1 | 180€ | 180€ |

### Total hardware
**1.578€**

---

## 4. Informe de Software

### Opcions analitzades:

- **Software Lliure (Odoo Community / Floreant POS):** Sense llicència mensual, però requereix un servidor local i manteniment tècnic propi.
- **Software Comercial (Revo / Square):** Pagament per subscripció (SaaS), suport 24/7 i actualitzacions al núvol incloses.

### Comparativa de Costos (S’acumulen amb els anys)

| Periode | Software Lliure (Instal·lació + Manteniment) | Software Comercial Revo (Subscripció ~79€/mes) |
|---|---|---|
| Any 1 | 1.200€ (Setup inicial del servidor) | 948€ |
| Any 3 | 2.400€ (any 1 + manteniment) | 2.844€ |

### Conclusió:
El software lliure és més rendible a partir del segon any, però el software comercial (com Revo) ofereix més estabilitat i aporta suport per part del desenvolupador, que redueix el risc de fallades per part del programari.

---

## 5. Pla de Contingència

### Què passa si falla la tecnologia:

#### Caiguda d'Internet:
- El sistema TPV i les impressores funcionen per xarxa cable, per tant la comunicació entre taula i cuina no s'atura.
- Els datàfons moderns tenen SIM 4G/5G propia per tant no cal que disposin d’una connexió wifi per a funcionar.
- En cas de no poder utilitzar les tecnologies es pot utilitzar temporalment llibreta i boli com de tota la vida.

#### Fallada Elèctrica:
- Instal·lació d'un SAI per al ordinador de la caixa central i per al router, per així permetre tancar els comptes oberts i seguir amb el funcionament de les comandes. (autonomia de 30-60 min).

## Readme de la tasca
[README](./README.md)