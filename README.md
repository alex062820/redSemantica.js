# redSemantica.js
Este código en JavaScript crea una red semántica con nodos que representan conceptos y arcos que describen sus relaciones. Utiliza clases para gestionar nodos (Nodo), relaciones (Arco), y la red (RedSemantica). El código genera nodos como "Animal" y "AVE", establece sus conexiones, y muestra el resultado en la consola, finalizando con un mensaje.

class Nodo {
    constructor(etiqueta) {
        this.etiqueta = etiqueta;
        this.arcos = [];
    }

    agregarArco(destino, etiquetaArco) {
        this.arcos.push(new Arco(this, destino, etiquetaArco));
    }

    obtenerArcos() {
        return this.arcos.map(arco => arco.toString()).join('\n');
    }
}

class Arco {
    constructor(origen, destino, etiqueta) {
        this.origen = origen;
        this.destino = destino;
        this.etiqueta = etiqueta;
    }

    toString() {
        return `${this.origen.etiqueta} -- ${this.etiqueta} --> ${this.destino.etiqueta}`;
    }
}

class RedSemantica {
    constructor() {
        this.nodos = [];
    }

    crearNodo(etiqueta) {
        const nodo = new Nodo(etiqueta);
        this.nodos.push(nodo);
        return nodo;
    }

    mostrarRed() {
        console.log("Red Semántica:");
        this.nodos.forEach(nodo => {
            if (nodo.arcos.length > 0) {
                console.log(nodo.obtenerArcos());
            }
        });
    }

    finalizarRed() {
        console.log("Finalización de la red semántica.");
    }
}

// Ejemplo basado en la imagen proporcionada
function ejecutarRedSemantica() {
    const red = new RedSemantica();

    // Creación de los nodos
    const animal = red.crearNodo("Animal");
    const vida = red.crearNodo("vida");
    const sentir = red.crearNodo("sentir");
    const moverse = red.crearNodo("moverse");

    const ave = red.crearNodo("AVE");
    const mamifero = red.crearNodo("MAMIFERO");

    const bien = red.crearNodo("bien");
    const plumas = red.crearNodo("plumas");
    const huevos = red.crearNodo("huevos");

    const avestruz = red.crearNodo("AVESTRUZ");
    const albatros = red.crearNodo("ALBATROS");

    const largas = red.crearNodo("largas");
    const noPuede = red.crearNodo("no puede");
    const muyBien = red.crearNodo("muy bien");

    const ballena = red.crearNodo("BALLENA");
    const tigre = red.crearNodo("TIGRE");

    const piel = red.crearNodo("piel");
    const mar = red.crearNodo("mar");
    const leche = red.crearNodo("leche");
    const pelo = red.crearNodo("pelo");
    const carne = red.crearNodo("carne");

    // Establecimiento de las relaciones (arcos)
    animal.agregarArco(vida, "tiene");
    animal.agregarArco(sentir, "tiene");
    animal.agregarArco(moverse, "puede");
    animal.agregarArco(ave, "tipo de");
    animal.agregarArco(mamifero, "tipo de");

    ave.agregarArco(bien, "vuela");
    ave.agregarArco(plumas, "tiene");
    ave.agregarArco(huevos, "pone");
    ave.agregarArco(avestruz, "tipo de");
    ave.agregarArco(albatros, "tipo de");

    avestruz.agregarArco(largas, "patas");
    avestruz.agregarArco(noPuede, "vuela");

    albatros.agregarArco(muyBien, "vuela");

    mamifero.agregarArco(ballena, "tipo de");
    mamifero.agregarArco(tigre, "tipo de");

    ballena.agregarArco(piel, "tiene");
    ballena.agregarArco(mar, "vive en");

    tigre.agregarArco(leche, "da");
    tigre.agregarArco(pelo, "tiene");
    tigre.agregarArco(carne, "come");

    // Mostrar la red
    red.mostrarRed();

    // Finalizar la red
    red.finalizarRed();
}

// Ejecutar la red semántica
ejecutarRedSemantica();


// Ejecuta el archivo utilizando Node.js con el siguiente comando:
node redSemantica.js
