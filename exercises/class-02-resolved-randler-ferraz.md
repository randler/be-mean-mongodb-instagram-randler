```md
#MongoDB - Aula 03 - Exercício
autor: Randler Ferraz Almeida

##Respondendo exercicio da aula 02


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
# Comandos da aula 03


##	->Query

Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {name: "Pikachu"}
Deadpool(mongod-3.2.7) be-mean-pokemons> query
{
  "name": "Pikachu"
}
Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
  "name": "Pikachu",
  "description": "rato que da choque",
  "type": "eletric",
  "attack": 30,
  "defense": 20,
  "height": 6
}


##	-> Fields
Fetched 1 record(s) in 2ms
Deadpool(mongod-3.2.7) be-mean-pokemons> var fields = {name:1, description: 1}
Deadpool(mongod-3.2.7) be-mean-pokemons> fields
{
  "name": 1,
  "description": 1
}
Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query, fields)
{
  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
  "name": "Pikachu",
  "description": "rato que da choque"
}
Fetched 1 record(s) in 2ms
Deadpool(mongod-3.2.7) be-mean-pokemons> var fields = {name:1, description: 1, }

Deadpool(mongod-3.2.7) be-mean-pokemons> var fields = {name:1, description: 1, _id:0}
Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query, fields)
{
  "name": "Pikachu",
  "description": "rato que da choque"
}
Fetched 1 record(s) in 3ms


##	-> Operados Aritméticos

	<	é	$lt   -> less than
	<=	é	$lte  -> less than or equal
	>	é	$gt   -> greater than
	>=	é	$gte  -> greater tha or equal
	
Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {height: {$lt: 0.5}}
Deadpool(mongod-3.2.7) be-mean-pokemons> query
{
  "height": {
    "$lt": 0.5
  }
}
Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57cb9b16cc5835423e5192e8"),
  "name": "Haunter",
  "description": "Fantasminha camarada o escambau",
  "type": "ghost",
  "attack": 30,
  "defense": 20,
  "height": 0.1
}
Fetched 1 record(s) in 2ms
Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {height: {$lte: 0.5}}
Deadpool(mongod-3.2.7) be-mean-pokemons> query
{
  "height": {
    "$lte": 0.5
  }
}
Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57cb9b16cc5835423e5192e8"),
  "name": "Haunter",
  "description": "Fantasminha camarada o escambau",
  "type": "ghost",
  "attack": 30,
  "defense": 20,
  "height": 0.1
}
Fetched 1 record(s) in 2ms
Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {height: {$gt: 0.5}}
Deadpool(mongod-3.2.7) be-mean-pokemons> query
{
  "height": {
    "$gt": 0.5
  }
}
Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
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
{
  "_id": ObjectId("57cb9e4692eb81e555089d95"),
  "name": "Arcanine",
  "description": "O Pokemon mais doido, doido",
  "type": "fire",
  "attack": 60,
  "defense": 40,
  "height": 155
}
Fetched 5 record(s) in 5ms
Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {height: {$gte: 23}}
Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
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
  "_id": ObjectId("57cb9e4692eb81e555089d95"),
  "name": "Arcanine",
  "description": "O Pokemon mais doido, doido",
  "type": "fire",
  "attack": 60,
  "defense": 40,
  "height": 155
}
Fetched 2 record(s) in 3ms



##	-> Operadores Lógicos


	$or   -> OU

Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {$or: [{name: "Pikachu"}, {height: 155}]}
Deadpool(mongod-3.2.7) be-mean-pokemons> query
{
  "$or": [
    {
      "name": "Pikachu"
    },
    {
      "height": 155
    }
  ]
}
Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
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
  "_id": ObjectId("57cb9e4692eb81e555089d95"),
  "name": "Arcanine",
  "description": "O Pokemon mais doido, doido",
  "type": "fire",
  "attack": 60,
  "defense": 40,
  "height": 155
}
Fetched 2 record(s) in 3ms


	$nor   -> Not OU

Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {$nor: [{name: "Pikachu"}, {height: 155}]}
Deadpool(mongod-3.2.7) be-mean-pokemons> query
{
  "$nor": [
    {
      "name": "Pikachu"
    },
    {
      "height": 155
    }
  ]
}
Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
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
Fetched 4 record(s) in 3ms


	$and   -> E

Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{name: "Pikachu"}, {height: 155}]}
Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
Fetched 0 record(s) in 1ms
Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{name: "Arcanine"}, {height: 155}]}
Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
{
  "_id": ObjectId("57cb9e4692eb81e555089d95"),
  "name": "Arcanine",
  "description": "O Pokemon mais doido, doido",
  "type": "fire",
  "attack": 60,
  "defense": 40,
  "height": 155
}
Fetched 1 record(s) in 2ms



##	-> Operadores "Exixtênciais"

	$exists

# -> Atividade Aula 3

	1) Liste todos Pokemons com a altura menor que 0.5
	2) Liste todos Pokemons com a altura maior ou igual que 0.5
	3) Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama
	4) Liste todos Pokemons com o name 'Pikachu' OU com attack menor ou igual que 0.5
	5) Liste todos Pokemons com attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5



	

	

