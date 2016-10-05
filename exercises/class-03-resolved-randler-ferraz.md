```md
#MongoDB - Aula 04 - Exercício
autor: Randler Ferraz Almeida

##Respondendo exercicio da aula 03

# 1) Liste todos Pokemons com a altura menor que 0.5

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
	Fetched 1 record(s) in 9ms

# 2) Liste todos Pokemons com a altura maior ou igual que 0.5

	Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {height: {$gte: 0.5}}
	Deadpool(mongod-3.2.7) be-mean-pokemons> query
	{
	  "height": {
	    "$gte": 0.5
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

# 3) Liste todos Pokemons com a altura menor ou igual que 0.5 E do tipo grama

	Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{height: {$lte: 0.5}, type: "grass"}]}
	Deadpool(mongod-3.2.7) be-mean-pokemons> query
	{
	  "$and": [
	    {
	      "height": {
		"$lte": 0.5
	      }
	    },
	    {
	      "type": "grass"
	    }
	  ]
	}
	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 2ms

# 4) Liste todos Pokemons com o name 'Pikachu' OU com attack menor ou igual que 0.5

	Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {$or: [{attack: {$lte: 0.5}}, {name: "Pikachu"}]}
	Deadpool(mongod-3.2.7) be-mean-pokemons> query
	{
	  "$or": [
	    {
	      "attack": {
		"$lte": 0.5
	      }
	    },
	    {
	      "name": "Pikachu"
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
	Fetched 1 record(s) in 3ms


# 5) Liste todos Pokemons com attack MAIOR OU IGUAL QUE 48 E com height menor ou igual que 0.5

	Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {$and: [{attack: {$gte: 48}},{height: {$lte: 0.5}}]}
	Deadpool(mongod-3.2.7) be-mean-pokemons> query
	{
	  "$and": [
	    {
	      "attack": {
		"$gte": 48
	      }
	    },
	    {
	      "height": {
		"$lte": 0.5
	      }
	    }
	  ]
	}
	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
	Fetched 0 record(s) in 1ms

```>
#Comandos da aula 04









