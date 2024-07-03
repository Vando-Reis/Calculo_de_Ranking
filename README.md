# Ranking de Jogadores

Este projeto em JavaScript permite classificar jogadores com base no número de vitórias. Ele lê as entradas do usuário para o total de vitórias e derrotas e, em seguida, calcula o saldo de vitórias para determinar o nível do jogador.

## Funcionalidades

- **Entrada do Usuário**: Solicita ao usuário o número de vitórias e derrotas.
- **Cálculo do Saldo de Vitórias**: Calcula o saldo de vitórias subtraindo derrotas das vitórias.
- **Classificação de Nível**: Classifica o jogador em um nível com base no saldo de vitórias.

## Níveis de Classificação

Os jogadores são classificados nos seguintes níveis com base no saldo de vitórias:

- **Ferro**: Menos de 10 vitórias.
- **Bronze**: Entre 10 e 20 vitórias.
- **Prata**: Entre 21 e 50 vitórias.
- **Ouro**: Entre 51 e 80 vitórias.
- **Diamante**: Entre 81 e 90 vitórias.
- **Lendário**: Entre 91 e 100 vitórias.
- **Imortal**: Mais de 100 vitórias.
- **Desconhecido**: Qualquer outra condição.

## Como Executar

Para executar este projeto, você precisará do Node.js instalado no seu sistema.

1. Clone este repositório:
    ```bash
    git clone https://github.com/seu-usuario/nome-do-repositorio.git
    ```

2. Navegue até o diretório do projeto:
    ```bash
    cd nome-do-repositorio
    ```

3. Execute o script JavaScript:
    ```bash
    node script.js
    ```

4. Insira os dados solicitados quando o script for executado.

## Estrutura do Código

```javascript
const readline = require('readline');

// Cria uma interface de leitura
const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
});

// Função para fazer perguntas ao usuário
function perguntar(pergunta) {
    return new Promise(resolve => rl.question(pergunta, resolve));
}

// Função principal que obtém entradas do usuário
(async function() {
    const vitorias = await perguntar('Total de vitórias? ');
    const derrotas = await perguntar('Total derrotas? ');
    
    rl.close(); // Fecha a interface
    
    const saldoVitorias = retornaCalculo(parseInt(vitorias), parseInt(derrotas));
    console.log('O Herói tem saldo de ' + saldoVitorias + ' e está no nível ' + classificarNivel(saldoVitorias));
})();

function retornaCalculo(vitorias, derrotas) {
    return vitorias - derrotas; // retorna o resultado da função retornaCalculo
}

function classificarNivel(saldoVitorias) {
    if (saldoVitorias < 10) {
        return 'Ferro';
    } else if (saldoVitorias >= 10 && saldoVitorias <= 20) {
        return 'Bronze';
    } else if (saldoVitorias > 20 && saldoVitorias <= 50) {
        return 'Prata';
    } else if (saldoVitorias > 50 && saldoVitorias <= 80) {
        return 'Ouro';
    } else if (saldoVitorias > 80 && saldoVitorias <= 90) {
        return 'Diamante';
    } else if (saldoVitorias > 90 && saldoVitorias <= 100) {
        return 'Lendário';
    } else if (saldoVitorias > 100) {
        return 'Imortal';
    } else {
        return 'Desconhecido';
    }
}
