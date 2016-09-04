```md
#MongoDB - Aula 02 - Exercício
autor: Randler Ferraz Almeida

##Respondendo exercicio


Deadpool(mongod-3.2.7) test> use be-mean-pokemons
switched to db be-mean-pokemons

Deadpool(mongod-3.2.7) be-mean-pokemons> show dbs
be-mean           → 0.005GB
be-mean-instagram → 0.000GB
cursonode         → 0.000GB
local             → 0.000GB
nodejscurso       → 0.000GB
twitter-mongo     → 0.000GB
winedb            → 0.000GB

Deadpool(mongod-3.2.7) be-mean-pokemons> show collections

Deadpool(mongod-3.2.7) be-mean-pokemons> var pokemon1 = {'name':'Pikachu', 'description':'rato que da choque', 'type':'eletric', attack: 30, defense: 20, height: 6.0}

Deadpool(mongod-3.2.7) be-mean-pokemons> var pokemon2 = {'name':'Kadabra', 'description':'Entorta as colher doido', 'type':'psychic', attack: 20, defense: 20, height: 56.5}

Deadpool(mongod-3.2.7) be-mean-pokemons> var pokemon3 = {'name':'Haunter', 'description':'Fantasminha camarada o escambau', 'type':'ghost', attack: 30, defense: 20, height: 0.1}

Deadpool(mongod-3.2.7) be-mean-pokemons> var pokemon4 = {'name':'Charmeleon', 'description':'Foda bagarai', 'type':'fire', attack: 30, defense: 30, height: 19.0}

Deadpool(mongod-3.2.7) be-mean-pokemons> var pokemon5 = {'name':'Wartotle', 'description':'Tartaruga com rabo de nuvem', 'type':'water', attack: 30, defense: 40, height: 22.5}

Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert(pokemon1)
Inserted 1 record(s) in 24ms
WriteResult({
  "nInserted": 1
})

Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert(pokemon2)
Inserted 1 record(s) in 3ms
WriteResult({
  "nInserted": 1
})

Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert(pokemon3)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert(pokemon4)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.insert(pokemon5)
Inserted 1 record(s) in 2ms
WriteResult({
  "nInserted": 1
})

Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
  "name": "Pikachu",
  "description": "rato que da choque",
  "type": "eletric",
  "attack": 30,
  "defense": 20,
  "height": 6
}
{
  "_id": ObjectId("57cb9b13cc5835423e5192e7"),
  "name": "Kadabra",
  "description": "Entorta as colher doido",
  "type": "psychic",
  "attack": 20,
  "defense": 20,
  "height": 56.5
}
{
  "_id": ObjectId("57cb9b16cc5835423e5192e8"),
  "name": "Haunter",
  "description": "Fantasminha camarada o escambau",
  "type": "ghost",
  "attack": 30,
  "defense": 20,
  "height": 0.1
}
{
  "_id": ObjectId("57cb9b18cc5835423e5192e9"),
  "name": "Charmeleon",
  "description": "Foda bagarai",
  "type": "fire",
  "attack": 30,
  "defense": 30,
  "height": 19
}
{
  "_id": ObjectId("57cb9b1bcc5835423e5192ea"),
  "name": "Wartotle",
  "description": "Tartaruga com rabo de nuvem",
  "type": "water",
  "attack": 30,
  "defense": 40,
  "height": 22.5
}
Fetched 5 record(s) in 5ms

Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {name: "Kadabra"}

Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.findOne(query)
{
  "_id": ObjectId("57cb9b13cc5835423e5192e7"),
  "name": "Kadabra",
  "description": "Entorta as colher doido",
  "type": "psychic",
  "attack": 20,
  "defense": 20,
  "height": 56.5
}

Deadpool(mongod-3.2.7) be-mean-pokemons> var poke = db.pokemons.findOne(query)

Deadpool(mongod-3.2.7) be-mean-pokemons> poke.description = "Ele entorta as culier maluko";
Ele entorta as culier maluko

Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.save(poke)
Updated 1 existing record(s) in 4ms
WriteResult({
  "nMatched": 1,
  "nUpserted": 0,
  "nModified": 1
})

Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find()
{
  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
  "name": "Pikachu",
  "description": "rato que da choque",
  "type": "eletric",
  "attack": 30,
  "defense": 20,
  "height": 6
}
{
  "_id": ObjectId("57cb9b13cc5835423e5192e7"),
  "name": "Kadabra",
  "description": "Ele entorta as culier maluko",
  "type": "psychic",
  "attack": 20,
  "defense": 20,
  "height": 56.5
}
{
  "_id": ObjectId("57cb9b16cc5835423e5192e8"),
  "name": "Haunter",
  "description": "Fantasminha camarada o escambau",
  "type": "ghost",
  "attack": 30,
  "defense": 20,
  "height": 0.1
}
{
  "_id": ObjectId("57cb9b18cc5835423e5192e9"),
  "name": "Charmeleon",
  "description": "Foda bagarai",
  "type": "fire",
  "attack": 30,
  "defense": 30,
  "height": 19
}
{
  "_id": ObjectId("57cb9b1bcc5835423e5192ea"),
  "name": "Wartotle",
  "description": "Tartaruga com rabo de nuvem",
  "type": "water",
  "attack": 30,
  "defense": 40,
  "height": 22.5
}
Fetched 5 record(s) in 5ms



	```
	>
#Comandos da aula

	

