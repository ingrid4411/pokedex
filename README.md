# pokedex de javascript

html

<!DOCTYPE html>  
<html lang="pt-BR">  
<head>  
    <meta charset="UTF-8">  
    <meta name="viewport" content="width=device-width, initial-scale=1.0">  
    <link rel="stylesheet" href="style.css">  
    <title>Pokédex</title>  
</head>  
<body>  
    <h1>Pokédex</h1>  
    <input type="text" id="search" placeholder="Digite o nome do Pokémon...">  
    <button id="searchBtn">Buscar</button>  
    <div id="result"></div>  

    <script src="script.js"></script>  
</body>  
</html>  



#css
body {  
    font-family: Arial, sans-serif;  
    text-align: center;  
    background-color: #f0f0f0;  
}  

#search {  
    padding: 10px;  
    margin: 10px;  
}  

#result {  
    margin-top: 20px;  
    padding: 20px;  
    border: 1px solid #ccc;  
    background-color: #fff;  
    display: inline-block;  
}  


#javascript

document.getElementById('searchButton').addEventListener('click', function() {  
    const pokemonName = document.getElementById('searchInput').value.toLowerCase();  
    const url = `https://pokeapi.co/api/v2/pokemon/${pokemonName}`;  

    fetch(url)  
        .then(response => {  
            if (!response.ok) {  
                throw new Error('Pokémon não encontrado');  
            }  
            return response.json();  
        })  
        .then(data => {  
            const pokemonDetails = `  
                <h2>${data.name.toUpperCase()}</h2>  
                <img src="${data.sprites.front_default}" alt="${data.name}" />  
                <p>Altura: ${data.height / 10} m</p>  
                <p>Peso: ${data.weight / 10} kg</p>  
            `;  
            document.getElementById('pokemonDetails').innerHTML = pokemonDetails;  
        })  
        .catch(error => {  
            document.getElementById('pokemonDetails').innerHTML = `<p>${error.message}</p>`;  
        });  
});  





