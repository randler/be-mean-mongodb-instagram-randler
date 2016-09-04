```md
# MongoDB - Aula 01 - Exercício
autor: Randler Ferraz Almeida

## Importando os restaurantes

	```
	$ mongoimport --db be-mean --collection restaurantes --host=127.0.0.1 --drop --file restaurantes.json
	
	2016-09-03T20:25:28.750-0300	connected to: 127.0.0.1
	2016-09-03T20:25:28.751-0300	dropping: be-mean.restaurantes
	2016-09-03T20:25:30.731-0300	imported 25359 documents

	```

## Contando os restaurantes

	```
	
	> db.restaurantes.find({}).count()
	25359
		
	```


# Comandos da aula

	-> Insert
	> db.teste.insert({nome: "Randler", idade: 30})
	WriteResult({ "nInserted" : 1 })
		
	-> show dbs
	be-mean            0.005GB
	be-mean-instagram  0.000GB
	cursonode          0.000GB
	local              0.000GB
	nodejscurso        0.000GB
	twitter-mongo      0.000GB

	-> Collections
	> show collections
	teste

	-> Var JSON
	> var json = {escola: "Webschool", active: true}
	> db.teste.insert(json)
	WriteResult({ "nInserted" : 1 })
	
## Pokemon
	
	-> Create
	> var pokemon = {'name':'Pikachu', 'description':'Rato eletrico bem fofinho', 'type':'eletric', attack: 100, height: 0.4}
	> db.pokemon.insert(pokemon)
	WriteResult({ "nInserted" : 1 })
	
	> pokemon
	{
	"name" : "Pikachu",
	"description" : "Rato eletrico bem fofinho",
	"type" : "eletric",
	"attack" : 100,
	"height" : 0.4
	}

	-> find
	> db.pokemons.find()
	{ "_id" : ObjectId("57cb6310068f66378687cd75"), "name" : "Pikachu", "description" : "Rato eletrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4 }

	-> mais var insert
	> var pokemon1 = {'name':'Bulbassauro', 'description':'Chicote de trepadeira', 'type':'grama', attack: 49, height: 0.4}
	> var pokemon2 = {'name':'Charmander', 'description':'Esse é o cão chuppando manga de fofinho', 'type':'fogo', attack: 52, height: 0.6}
	> var pokemon3 = {'name':'Squirtle', 'description':'Ejeta água que passarinho não bebe', 'type':'água', attack: 48, height: 0.5}
	
	->Insert	
	> db.pokemons.insert(pokemon1)
	WriteResult({ "nInserted" : 1 })
	> db.pokemons.insert(pokemon2)
	WriteResult({ "nInserted" : 1 })
	> db.pokemons.insert(pokemon3)
	WriteResult({ "nInserted" : 1 })

	-> find todos pokemons
	> db.pokemons.find()
	{ "_id" : ObjectId("57cb6310068f66378687cd75"), "name" : "Pikachu", "description" : "Rato eletrico bem fofinho", "type" : "eletric", "attack" : 55, "height" : 0.4 }
	{ "_id" : ObjectId("57cb6443068f66378687cd76"), "name" : "Bulbassauro", "description" : "Chicote de trepadeira", "type" : "grama", "attack" : 49, "height" : 0.4 }
	{ "_id" : ObjectId("57cb6447068f66378687cd77"), "name" : "Charmander", "description" : "Esse é o cão chuppando manga de fofinho", "type" : "fogo", "attack" : 52, "height" : 0.6 }
	{ "_id" : ObjectId("57cb644a068f66378687cd78"), "name" : "Squirtle", "description" : "Ejeta água que passarinho não bebe", "type" : "água", "attack" : 48, "height" : 0.5 }

	
