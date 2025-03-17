<h1 align="center"> Challenge Amigo Secreto </h1>

Aplicativo que permite a los usuarios ingresar nombres de amigos para realizar un sorteo aleatorio y determinar un amigo secreto.

let listaAmigos = [];

function agregarAmigo() {
    let input = document.getElementById("amigo");
    let nombre = input.value.trim();

    if (nombre.length === 0) {
        alert("Por favor, inserte un nombre.");
        return;
    }

    listaAmigos.push(nombre);
    actualizarLista();
    input.value = ""; // Limpiar el campo de entrada
}

function actualizarLista() {
    let lista = document.getElementById("listaAmigos");
    lista.innerHTML = "";

    listaAmigos.forEach(amigo => {
        let elemento = document.createElement("li");
        elemento.textContent = amigo;
        lista.appendChild(elemento);
    });
}

function sortearAmigo() {
    if (listaAmigos.length === 0) {
        alert("No hay nombres en la lista para sortear.");
        return;
    }
    
    let indiceAleatorio = Math.floor(Math.random() * listaAmigos.length);
    let amigoSecreto = listaAmigos[indiceAleatorio];
    
    let resultado = document.getElementById("resultado");
    resultado.innerHTML = "";
    let li = document.createElement("li");
    li.textContent = `El amigo secreto es: ${amigoSecreto}`;
    resultado.appendChild(li);
}
