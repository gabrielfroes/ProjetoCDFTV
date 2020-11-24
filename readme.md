# COMO USAR

## CRIAÇÃO DA COMBINAÇÃO (Lado computador)

    > let square = document.querySelector(".painelMemory");

### Sendo i o valor da div selecionada indo de 0 a 8

### Classe "memoryActive" cria um fundo azul na div selecionada.
    > square.children[i].classList.add("memoryActive");

### Ao todo ficaria assim:

    >   function memory() {
            let square = document.querySelector(".painelMemory");
            square.children[i].classList.add("memoryActive");
            setTimeout(() => {
                square.children[i].classList.remove("memoryActive");
            }, 600);
        }
### Utilize o setTimeout para criar o efeito de sumir após 600ms, caso não utilze o setTimeout com 600ms, a animação não poderá ser utilizada de novo e ocasionará erro.

### No exemplo utlizado foi usado a square.children[4]
<img src="https://media.giphy.com/media/SU4gRcGmULNJxDRXCb/giphy.gif" width='300px'>
<br>
<br>

## AO ERRAR A COMBINAÇÃO

    > let square = document.querySelector(".playerMemory");
    > let circles = document.querySelector(".circlesRight");

### Percorre todos os elementos para criar o fundo vermelho e animação piscando

    for (var i = 0; i < square.children.length; i++) {
        if (square.children[i].tagName == "DIV")
            square.children[i].classList.add("playerMemoryError");
    }
    for (var i = 0; i < circles.children.length; i++) {
        if (circles.children[i].tagName == "DIV")
            circles.children[i].classList.add("playerCircleError");
    }

### Remove todos os efeitos

#### Aconselho não mudar o valor do setTimeout

    > setTimeout(() => {
        for (var i = 0; i < square.children.length; i++) {
            if (square.children[i].tagName == "DIV")
                square.children[i].classList.remove("playerMemoryError");
        }
        for (var i = 0; i < circles.children.length; i++) {
            if (circles.children[i].tagName == "DIV")
                circles.children[i].classList.remove("playerCircleError");
        }
    }, 900);

### Ao todo ficaria assim:
    >   function error() {
            let square = document.querySelector(".playerMemory");
            let circles = document.querySelector(".circlesRight");

            for (var i = 0; i < square.children.length; i++) {
                if (square.children[i].tagName == "DIV")
                    square.children[i].classList.add("playerMemoryError");
            }
            for (var i = 0; i < circles.children.length; i++) {
                if (circles.children[i].tagName == "DIV")
                    circles.children[i].classList.add("playerCircleError");
            }
            setTimeout(() => {
                for (var i = 0; i < square.children.length; i++) {
                if (square.children[i].tagName == "DIV")
                    square.children[i].classList.remove("playerMemoryError");
                }
                for (var i = 0; i < circles.children.length; i++) {
                if (circles.children[i].tagName == "DIV")
                    circles.children[i].classList.remove("playerCircleError");
                }
            }, 900);
        }

<img src="https://media.giphy.com/media/MYVeoY8dyESVTF4ba8/giphy.gif" width='300px'>
<br>
<br>

## BOTÕES VERDES SIMULANDO NIVEL
    > let circles = document.querySelector(".circles")
### Sendo i de 0 a 4, adiciona o fundo verde no circulo
    > circles.children[i].classList.add("circleActive");
### Remove o fundo verde do circulo (Aconselho usar um timeout de 1 segundo)
    > circles.children[i].classList.remove("circleActive");
### Ao todo ficaria assim:
    >   function circleGreen() {
            let circles = document.querySelector(".circles");
            circles.children[i].classList.add("circleActive");
        }
### No exemplo usado foi utilizado a circles.children[0][1]:
### Por eu acrescentar a linha de código que remove a classe, o circulo verde some, sendo assim, caso não coloque, o fundo continuará verde.
<img src="https://media.giphy.com/media/voxPfNt40R80OMHtj5/giphy.gif" width='300px'>

<br>
<br>

## ATIVAR PAINEL PARA JOGADOR CLICAR

    > let square = document.querySelector(".playerMemory");
    > square.classList.add('playerActive')
### Ativa o fundo mais claro e o ponteiro do cursor fica "clicável"
    >   for (var i = 0; i < square.children.length; i++) {
            if (square.children[i].tagName == "DIV")
                square.children[i].classList.add("playerMemoryActive");
        }
### Seleciona todos as divs da grade do painel do jogador indo de 0 a 8
    >   let memory = document.getElementsByClassName("player_memory");

### Cria a animação de clique suave mudando para o fundo azul suavemente
    >   Array.prototype.forEach.call(memory, function (element) {
            element.addEventListener("click", function () {
            if (square.classList.contains("playerActive")) {
                console.log("O valor do elemento clicado é: " + element.dataset.memory);
                element.style.animation = "playermemoryClick .4s";
                setTimeout(() => {
                element.style.animation = "";
                }, 400);
            }
            });
        });
### Caso a classe 'playerActive' exista, o botão funciona, caso não, ele para de funcionar.

<br>
<br>

### Para saber qual div está clicando da grade utilize:
    > element.dataset.memory
#### Ele vai de 0 a 8, utilizando a função acima que ouve o clique do element e adicionando essa linha de código:
    > console.log("O valor do elemento clicado é: " + element.dataset.memory)
### Obtemos isso ao clicar no primeiro quadrado da grade do painel do jogador:
<img src="https://i.ibb.co/cFFBwC6/kkekaea.jpg" width="450px">

### A função completa ficaria assim:
    function active() {
        let square = document.querySelector(".playerMemory");
        let memory = document.getElementsByClassName("player_memory");
        square.classList.add('playerActive')
        for (var i = 0; i < square.children.length; i++) {
            if (square.children[i].tagName == "DIV")
            square.children[i].classList.add("playerMemoryActive");
        }

        Array.prototype.forEach.call(memory, function (element) {
            element.addEventListener("click", function () {
            if (square.classList.contains("playerActive")) {
                console.log("O valor do elemento clicado é: " + element.dataset.memory);
                element.style.animation = "playermemoryClick .4s";
                setTimeout(() => {
                element.style.animation = "";
                }, 400);
            }
            });
        });

        setTimeout(() => {
            square.classList.remove('playerActive')
            for (var i = 0; i < square.children.length; i++) {
            if (square.children[i].tagName == "DIV")
                square.children[i].classList.remove("playerMemoryActive");
            }
        }, 8000);
    }

### E teriámos isso de resultado:
<img src="https://media.giphy.com/media/TJCcbwCIIBAThyLxpV/giphy.gif" width='700px'>

<br>
<br>
<br>

# Resumo de cada classe utilizada e o que faz:
    > playerMemoryActive: Mexe no painel da direita (lado jogador), deixando o quadrado mais claro e criando um cursor clicável.

    > playermemoryClick: Nome de uma animação que deve ser utilizada junto a duração de 400ms, cria um efeito ao clicar no quadrado do painel do jogador, dando um fundo azul bem suave e desaparecendo.

    > circleActive: Cria um fundo verde para o circulo que simula o nível que o jogador está.

    > playerCircleError: Junto a classe 'playerMemoryError' cria um fundo vermelho simulando o erro do jogador.
    
    > playerMemoryError: Explicado acima. Deve ser utilizado junto a classe acima, porém com elementos diferentes.

    > memoryActive: Classe com uma animação que cria um fundo azul no elemento da grade do painel a esquerda (lado computador) e que deve ser removida logo após 600ms com setTimeout.
    
    > playerActive: Não tem estilização, apenas serve para criar uma condição no clique do efeito "playermemoryClick", caso ele exista, o player pode clicar.
