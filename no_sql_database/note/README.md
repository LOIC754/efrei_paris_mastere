# MES NOTES DE COUR NO SQL DATA BASE 

cloner le repos du prof : [repos](https://github.com/charroux/rentalservice.git)
acceder au dossier training puis puis lancer la commande bash : quarto preview index.qmd cette commande permet d'accedeer aau cour du prof 


### TP Lab 08: Redis data and messaging
fonctionement de docker 
la CLI commande programme permet juste de tester si redis tourne 
les commndes de test de la CLI sont : 
docker compose --env-file .env.dev -f docker-compose.dev.yml up -d redis
docker compose --env-file .env.dev -f docker-compose.dev.yml ps redis
docker compose --env-file .env.dev -f docker-compose.dev.yml exec redis redis-cli PING 

pour les racourcir on peut cree un alias qui existera uniquement dans la section en cour sur bash comme suite 
alias = dc'docker compose --env-file .env.dev -f docker-compose.dev.yml'
puis on execute les commande de CLI comme suite 
dc up -d redis 
dc ps redis 
dc exec redis redis-cli PING
puis ouvrir le client redis dans la CLI 
docker compose --env-file .env.dev -f docker-compose.dev.yml exec redis redis-cli
ou 
dc exec redis redis

### Part A: Inspect the keyspace safely
  scan permet de scanner la base de donne 
  redis est une base qui est faite pour etre in memory 
#### 1.Create training:probe with any String value

SET training:probe hello          # OK

Elle crée une clé de type String nommée training:probe et y stocke la valeur "hello".

SET : écrire une valeur dans une clé.
training:probe : le nom de la clé. training: est le namespace du TP, probe (« sonde ») indique une clé de test.
hello : la valeur stockée en mémoire.



### redis evenement list 

1. penser en terme de service 
2. penser en terme d'agregat 
3. pense en gtermer de evenement 
4.penser en termer de conception : choix base no sql 
5. penser choix structure nosql 
6. programmmation 

avoir les agregat et les evenement stoker dans redis e ligne de commande 
