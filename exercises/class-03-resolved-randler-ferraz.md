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

```

#Comandos da aula 04 Parte 1

##	-> Operadores de modificação
	
###### $set -> Modifica um valor ou cria ele, caso não exista

	Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {"_id": ObjectId("57f577aff4d5a0ff9273bbcf")}

	Deadpool(mongod-3.2.7) be-mean-pokemons> var mod = { $set: {name: 'Testemon', attack: 8000, defense: 8000, height: 2.1, description: "Pokemon de teste"}}

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("57f577aff4d5a0ff9273bbcf"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8000,
	  "defense": 8000,
	  "height": 2.1
	}
	Fetched 1 record(s) in 2ms



###### $unset -> Remover campos
	
	Deadpool(mongod-3.2.7) be-mean-pokemons> var mod = {$unset: {height: 1}}
	
	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	
	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("57f577aff4d5a0ff9273bbcf"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8000,
	  "defense": 8000
	}
	Fetched 1 record(s) in 2ms

	
###### $inc -> incrementa um valor no campo com a quantidade desejada

**Sintaxe incrementando**

	Deadpool(mongod-3.2.7) be-mean-pokemons> var mod = {$inc: {attack: 1}}

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("57f577aff4d5a0ff9273bbcf"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8001,
	  "defense": 8000
	}
	Fetched 1 record(s) in 2ms

	POKEMON EVOLUI E GANHA 100
	
	Deadpool(mongod-3.2.7) be-mean-pokemons> var mod = {$inc: {attack: 100}}

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("57f577aff4d5a0ff9273bbcf"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8101,
	  "defense": 8000
	}
	Fetched 1 record(s) in 2ms

**Sintaxe decrementando**

	Deadpool(mongod-3.2.7) be-mean-pokemons> var mod = {$inc: {attack: -101}}

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("57f577aff4d5a0ff9273bbcf"),
	  "description": "Pokemon de teste",
	  "name": "Testemon",
	  "attack": 8000,
	  "defense": 8000
	}
	Fetched 1 record(s) in 1ms	

##	->Operadores de Array

###### $push -> adiciona um valor ao campo do array

	Deadpool(mongod-3.2.7) be-mean-pokemons> var query = {name: /pikachu/i}
	
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
	Fetched 1 record(s) in 2ms

	Deadpool(mongod-3.2.7) be-mean-pokemons> var mod = {$push: {moves: 'choque do trovão'}}
	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
	  "name": "Pikachu",
	  "description": "rato que da choque",
	  "type": "eletric",
	  "attack": 30,
	  "defense": 20,
	  "height": 6,
	  "moves": [
	    "choque do trovão"
	  ]
	}
	Fetched 1 record(s) in 2ms

###### $pushAll -> Adiciona cada valor do [Array_de_valores], caso o campo seja um array

	Deadpool(mongod-3.2.7) be-mean-pokemons> var attacks = ['investida', 'ataque rapido', 'bola eletrica']

	Deadpool(mongod-3.2.7) be-mean-pokemons> var mod = {$pushAll:{moves: attacks}}

	Deadpool(mongod-3.2.7) be-mean-pokemons> mod
	{
	  "$pushAll": {
	    "moves": [
	      "investida",
	      "ataque rapido",
	      "bola eletrica"
	    ]
	  }
	}
	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})
	
	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
	  "name": "Pikachu",
	  "description": "rato que da choque",
	  "type": "eletric",
	  "attack": 30,
	  "defense": 20,
	  "height": 6,
	  "moves": [
	    "choque do trovão",
	    "investida",
	    "ataque rapido",
	    "bola eletrica"
	  ]
	}
	Fetched 1 record(s) in 2ms


###### $pull -> Retira o valor do campo, caso o campo seja um array existente

	Deadpool(mongod-3.2.7) be-mean-pokemons> var mod = {$pull:{moves: 'bola eletrica'}}

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
	  "name": "Pikachu",
	  "description": "rato que da choque",
	  "type": "eletric",
	  "attack": 30,
	  "defense": 20,
	  "height": 6,
	  "moves": [
	    "choque do trovão",
	    "investida",
	    "ataque rapido"
	  ]
	}
	Fetched 1 record(s) in 2ms


###### $pullAll -> retira cada valor do [Array_de_valores], caso o campo seja um array existente

	Deadpool(mongod-3.2.7) be-mean-pokemons> var attacks = ['investida', 'ataque rapido']

	Deadpool(mongod-3.2.7) be-mean-pokemons> attacks
	[
	  "investida",
	  "ataque rapido"
	]

	Deadpool(mongod-3.2.7) be-mean-pokemons> var mod = {$pullAll:{moves: attacks}}

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 4ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	Deadpool(mongod-3.2.7) be-mean-pokemons> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
	  "name": "Pikachu",
	  "description": "rato que da choque",
	  "type": "eletric",
	  "attack": 30,
	  "defense": 20,
	  "height": 6,
	  "moves": [
	    "choque do trovão"
	  ]
	}
	Fetched 1 record(s) in 1ms



#Comandos da aula 04 Parte 2


##	-> Options 
**serve para configurar alguns valores diferentes do padrão para o update**

###### upsert -> serve para caso o documento não seja encontrado pela query ele insira o objeto que está sendo passado como modificação

	
	> var mod = {$set: {active: true}}

	> var options = {upsert: true}

	> var query = {name: /pikachu/i}

	> db.pokemons.update(query, mod, options)

	Updated 1 existing record(s) in 1ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
	  "name": "Pikachu",
	  "description": "rato que da choque",
	  "type": "eletric",
	  "attack": 30,
	  "defense": 20,
	  "height": 6,
	  "moves": [
	    "choque do trovão"
	  ],
	  "active": true
	}
	Fetched 1 record(s) in 2ms

	__Pokemon inexistente__

	> var query = {name: /squirtle/i}
	
	> mod
	{
	  "$set": {
	    "active": true
	  }
	}

	> options
	{
	  "upsert": true
	}

	> db.pokemons.update(query, mod, options)

	Updated 1 new record(s) in 3ms
	WriteResult({
	  "nMatched": 0,
	  "nUpserted": 1,
	  "nModified": 0,
	  "_id": ObjectId("57f658a3b75a6ac3a64e946a")
	})

	> var query = {"_id": ObjectId("57f658a3b75a6ac3a64e946a")}

	> query
	{
	  "_id": ObjectId("57f658a3b75a6ac3a64e946a")
	}

	> db.pokemons.find(query)
	{
	  "_id": ObjectId("57f658a3b75a6ac3a64e946a"),
	  "active": true
	}
	Fetched 1 record(s) in 2ms

###### $setOnInsert -> define valore que serão adicionados apenas se ocorrer um upsert
	
	> var mod = { $set: {active: true}, $setOnInsert: {name: "NaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}}

	> var query = {name: /naoexistemon/i}

	> mod
	{
	  "$set": {
	    "active": true
	  },
	  "$setOnInsert": {
	    "name": "NaoExisteMon",
	    "attack": null,
	    "defense": null,
	    "height": null,
	    "description": "Sem maiores informações"
	  }
	}

	> var query = {name: /naoexistemon/i}

	> var mod = { $set: {active: true}, $setOnInsert: {name: "NaoExisteMon", attack: null, defense: null, height: null, description: "Sem maiores informações"}}

	> var options = {upsert: true}

	> mod
	{
	  "$set": {
	    "active": true
	  },
	  "$setOnInsert": {
	    "name": "NaoExisteMon",
	    "attack": null,
	    "defense": null,
	    "height": null,
	    "description": "Sem maiores informações"
	  }
	}

	> db.pokemons.update(query, mod, options)

	Updated 1 new record(s) in 3ms
	WriteResult({
	  "nMatched": 0,
	  "nUpserted": 1,
	  "nModified": 0,
	  "_id": ObjectId("57f65a90b75a6ac3a64e946b")
	})

	> var id = {"_id": ObjectId("57f65a90b75a6ac3a64e946b")}

	> db.pokemons.find(id)
	{
	  "_id": ObjectId("57f65a90b75a6ac3a64e946b"),
	  "active": true,
	  "name": "NaoExisteMon",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações"
	}
	Fetched 1 record(s) in 2ms

###### Multi -> impede que faça update sem where (com ele voce pode alterar todos os dados)

	> var query = {}
	> var mod = {$set: {active: false}}
	> var options = {multi: true}
	> db.pokemons.update(query, mod, options)

	Updated 10 existing record(s) in 3ms
	WriteResult({
	  "nMatched": 10,
	  "nUpserted": 0,
	  "nModified": 10
	})
	

###### writeConcern -> descreve a garantia que o MongoDB fornece ao relatar o sucesso de uma operação de escrita

##	->Find
	
	
###### Operadores de Array


	> var query = {}

	> var mod = {$set: {moves: ['investida']}}

	> var options = {multi: true}
	
	> db.pokemons.update(query, mod, options)

	Updated 10 existing record(s) in 3ms
	WriteResult({
	  "nMatched": 10,
	  "nUpserted": 0,
	  "nModified": 10
	})


###### Adicionando mais attacks
	
	> var query = {name: /pikachu/i}

	> var mod = {$push: {moves: 'choque do trovao'}}

	> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})


	> var query = {name: /Wartotle/i}

	> var mod = {$push: {moves: 'hidro bomba'}}
	
	> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})


	> var query = {name: /Charmeleon/i}

	> var mod = {$push: {moves: 'lança-chamas'}}
	
	> db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

	
	> var query = {name: /testemon/i}

	> var mod = {$push: {name: "Bulbassauro", description: "Um dinossauro doidão", type: "grass", attack: 30, defense: 20, height: 20, moves: 'lança-chamas'}}
	
	>db.pokemons.update(query, mod)
	Updated 1 existing record(s) in 2ms
	WriteResult({
	  "nMatched": 1,
	  "nUpserted": 0,
	  "nModified": 1
	})

###### $in -> retorna o(s) documento(s) que possui (em) algum dos valores passado no [Array_de_valores]

	> var query = {moves:{$in: [/choque do trovao/i]}}
	
	> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
	  "name": "Pikachu",
	  "description": "rato que da choque",
	  "type": "eletric",
	  "attack": 30,
	  "defense": 20,
	  "height": 6,
	  "moves": [
	    "investida",
	    "choque do trovao"
	  ],
	  "active": false
	}
	Fetched 1 record(s) in 3ms

	> var query = {moves:{$in: [/choque do trovao/i, /teste/i]}}
	
	> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
	  "name": "Pikachu",
	  "description": "rato que da choque",
	  "type": "eletric",
	  "attack": 30,
	  "defense": 20,
	  "height": 6,
	  "moves": [
	    "investida",
	    "choque do trovao"
	  ],
	  "active": false
	}
	Fetched 1 record(s) in 2ms

	> var query = {moves:{$in: [/choque do trovao/i, /hidro bomba/i]}}
	
	> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b0fcc5835423e5192e6"),
	  "name": "Pikachu",
	  "description": "rato que da choque",
	  "type": "eletric",
	  "attack": 30,
	  "defense": 20,
	  "height": 6,
	  "moves": [
	    "investida",
	    "choque do trovao"
	  ],
	  "active": false
	}
	{
	  "_id": ObjectId("57cb9b1bcc5835423e5192ea"),
	  "name": "Wartotle",
	  "description": "Tartaruga com rabo de nuvem",
	  "type": "water",
	  "attack": 30,
	  "defense": 40,
	  "height": 22.5,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba"
	  ]
	}
	Fetched 2 record(s) in 2ms


###### $nin -> (NOT in) retorna documentos se nenhum dos valores for encontrado

	
	
	> var query = {moves:{$nin: [/choque do trovao/i]}}
	
	> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b13cc5835423e5192e7"),
	  "name": "Kadabra",
	  "description": "Ele entorta as culier maluko",
	  "type": "psychic",
	  "attack": 20,
	  "defense": 20,
	  "height": 56.5,
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57cb9b16cc5835423e5192e8"),
	  "name": "Haunter",
	  "description": "Fantasminha camarada o escambau",
	  "type": "ghost",
	  "attack": 30,
	  "defense": 20,
	  "height": 0.1,
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57cb9b18cc5835423e5192e9"),
	  "name": "Charmeleon",
	  "description": "Foda bagarai",
	  "type": "fire",
	  "attack": 30,
	  "defense": 30,
	  "height": 19,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas"
	  ]
	}
	{
	  "_id": ObjectId("57cb9b1bcc5835423e5192ea"),
	  "name": "Wartotle",
	  "description": "Tartaruga com rabo de nuvem",
	  "type": "water",
	  "attack": 30,
	  "defense": 40,
	  "height": 22.5,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba"
	  ]
	}
	{
	  "_id": ObjectId("57cb9e4692eb81e555089d95"),
	  "name": "Arcanine",
	  "description": "O Pokemon mais doido, doido",
	  "type": "fire",
	  "attack": 60,
	  "defense": 40,
	  "height": 155,
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57f577aff4d5a0ff9273bbcf"),
	  "description": "Um dinossauro doidão",
	  "name": "Bulbassauro",
	  "attack": 30,
	  "defense": 20,
	  "active": false,
	  "moves": "lança-chamas",
	  "type": "grass",
	  "height": 20
	}
	{
	  "_id": ObjectId("57f657b4b75a6ac3a64e9469"),
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57f658a3b75a6ac3a64e946a"),
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57f65a90b75a6ac3a64e946b"),
	  "active": false,
	  "name": "NaoExisteMon",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações",
	  "moves": [
	    "investida"
	  ]
	}
	Fetched 9 record(s) in 7ms

###### $all -> retorna documentos se todos os valores foram encontrados


	> var query = {moves:{$all: [/hidro bomba/i, /investida/i]}}

	> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b1bcc5835423e5192ea"),
	  "name": "Wartotle",
	  "description": "Tartaruga com rabo de nuvem",
	  "type": "water",
	  "attack": 30,
	  "defense": 40,
	  "height": 22.5,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba"
	  ]
	}
	Fetched 1 record(s) in 2ms


##	-> Operadores de negação

	
###### $ne (not Equal)

	> var query = {type:{$ne: 'eletric'}}
	
	> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b13cc5835423e5192e7"),
	  "name": "Kadabra",
	  "description": "Ele entorta as culier maluko",
	  "type": "psychic",
	  "attack": 20,
	  "defense": 20,
	  "height": 56.5,
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57cb9b16cc5835423e5192e8"),
	  "name": "Haunter",
	  "description": "Fantasminha camarada o escambau",
	  "type": "ghost",
	  "attack": 30,
	  "defense": 20,
	  "height": 0.1,
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57cb9b18cc5835423e5192e9"),
	  "name": "Charmeleon",
	  "description": "Foda bagarai",
	  "type": "fire",
	  "attack": 30,
	  "defense": 30,
	  "height": 19,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas"
	  ]
	}
	{
	  "_id": ObjectId("57cb9b1bcc5835423e5192ea"),
	  "name": "Wartotle",
	  "description": "Tartaruga com rabo de nuvem",
	  "type": "water",
	  "attack": 30,
	  "defense": 40,
	  "height": 22.5,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba"
	  ]
	}
	{
	  "_id": ObjectId("57cb9e4692eb81e555089d95"),
	  "name": "Arcanine",
	  "description": "O Pokemon mais doido, doido",
	  "type": "fire",
	  "attack": 60,
	  "defense": 40,
	  "height": 155,
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57f577aff4d5a0ff9273bbcf"),
	  "description": "Um dinossauro doidão",
	  "name": "Bulbassauro",
	  "attack": 30,
	  "defense": 20,
	  "active": false,
	  "moves": "lança-chamas",
	  "type": "grass",
	  "height": 20
	}
	{
	  "_id": ObjectId("57f657b4b75a6ac3a64e9469"),
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57f658a3b75a6ac3a64e946a"),
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57f65a90b75a6ac3a64e946b"),
	  "active": false,
	  "name": "NaoExisteMon",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações",
	  "moves": [
	    "investida"
	  ]
	}
	Fetched 9 record(s) in 7ms



###### $not (NOT)

	
	> var query = {name:{$not: /pikachu/i}}
	> db.pokemons.find(query)
	{
	  "_id": ObjectId("57cb9b13cc5835423e5192e7"),
	  "name": "Kadabra",
	  "description": "Ele entorta as culier maluko",
	  "type": "psychic",
	  "attack": 20,
	  "defense": 20,
	  "height": 56.5,
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57cb9b16cc5835423e5192e8"),
	  "name": "Haunter",
	  "description": "Fantasminha camarada o escambau",
	  "type": "ghost",
	  "attack": 30,
	  "defense": 20,
	  "height": 0.1,
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57cb9b18cc5835423e5192e9"),
	  "name": "Charmeleon",
	  "description": "Foda bagarai",
	  "type": "fire",
	  "attack": 30,
	  "defense": 30,
	  "height": 19,
	  "active": false,
	  "moves": [
	    "investida",
	    "lança-chamas"
	  ]
	}
	{
	  "_id": ObjectId("57cb9b1bcc5835423e5192ea"),
	  "name": "Wartotle",
	  "description": "Tartaruga com rabo de nuvem",
	  "type": "water",
	  "attack": 30,
	  "defense": 40,
	  "height": 22.5,
	  "active": false,
	  "moves": [
	    "investida",
	    "hidro bomba"
	  ]
	}
	{
	  "_id": ObjectId("57cb9e4692eb81e555089d95"),
	  "name": "Arcanine",
	  "description": "O Pokemon mais doido, doido",
	  "type": "fire",
	  "attack": 60,
	  "defense": 40,
	  "height": 155,
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57f577aff4d5a0ff9273bbcf"),
	  "description": "Um dinossauro doidão",
	  "name": "Bulbassauro",
	  "attack": 30,
	  "defense": 20,
	  "active": false,
	  "moves": "lança-chamas",
	  "type": "grass",
	  "height": 20
	}
	{
	  "_id": ObjectId("57f657b4b75a6ac3a64e9469"),
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57f658a3b75a6ac3a64e946a"),
	  "active": false,
	  "moves": [
	    "investida"
	  ]
	}
	{
	  "_id": ObjectId("57f65a90b75a6ac3a64e946b"),
	  "active": false,
	  "name": "NaoExisteMon",
	  "attack": null,
	  "defense": null,
	  "height": null,
	  "description": "Sem maiores informações",
	  "moves": [
	    "investida"
	  ]
	}
	Fetched 9 record(s) in 6ms


###### remove() -> (Delete)
	
	> var query ={"_id": ObjectId("57f65a90b75a6ac3a64e946b")}
	
	> db.pokemons.remove(query)
	Removed 1 record(s) in 2ms
	WriteResult({
	  "nRemoved": 1
	})
	

##	-> Exercício

	1)**Adicionar** 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, Squirtle, Bulbassauro e Charmander.
	2)**Adicionar** 1 movimento em todos os pokemons: 'desvio'
	3)**Adicionar** o pokemon 'AindaNaoExisteMon' caso ele não exista com todos os dados com o valor 'null' e a descrição: "Sem maiores informações".
	4)Pesquisar  todos os pokemons que possuam o ataque 'investida' e mais um que você adicionou, escolha seu pokemon favorito.
	5)Pesquisar **todos** os pokemons que possuam os ataques que você adicionou, escolha o seu pokemon favorito.
	6)Pesquisar **todos** que não são do tipo eletrico
	7)Pesquisar **todos** pokemons que tenham o ataque 'investida' **E** tenham a defesa **não menor ou igua** a 49.
	8)Remova **todos** os pokemons do tipo água e com atack menor que 50.
