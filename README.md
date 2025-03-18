// Lista de participantes
const participantes = [
    "Alice", "Bruno", "Carla", "Diego", "Eduarda", "Fernando"
];

// Função para embaralhar a lista usando o algoritmo Fisher-Yates
function embaralharLista(lista) {
    for (let i = lista.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [lista[i], lista[j]] = [lista[j], lista[i]];
    }
}

// Função para sortear os amigos secretos
function sortearAmigoSecreto(participantes) {
    let sorteados = [...participantes];
    do {
        embaralharLista(sorteados);
    } while (sorteados.some((pessoa, index) => pessoa === participantes[index]));
    
    return participantes.map((pessoa, index) => ({
        amigo: pessoa,
        sorteado: sorteados[index]
    }));
}

// Executa o sorteio e exibe os pares
const resultado = sortearAmigoSecreto(participantes);
console.log("🎁 Resultado do Amigo Secreto 🎁");
resultado.forEach(par => {
    console.log(`${par.amigo} -> ${par.sorteado}`);
});
