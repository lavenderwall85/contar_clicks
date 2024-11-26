<script>
    let contador = 0;
    let tiempo = 10; 
    let timer;
    let mensaje = "Haz clic en el botón para comenzar";
    let tiempoRestante = tiempo;

    function comenzar() {
        contador = 0;
        tiempoRestante = tiempo;
        mensaje = "¡Haz clic!";

        timer = setInterval(() => {
            if (tiempoRestante > 0) {
                tiempoRestante--;
            } else {
                clearInterval(timer);
                mensaje = `¡Tiempo terminado! Hiciste ${contador} clics.`;
            }
        }, 1000);
    }

    function hacerClick() {
        if (tiempoRestante > 0) {
            contador++;
        }
    }

    function reiniciar() {
        clearInterval(timer);
        mensaje = "Haz clic en el botón para comenzar";
        tiempoRestante = tiempo;
    }
</script>

<main class="contenedor">
    <div class="juego">
        <h1>Contar Clicks</h1>
        <p>{mensaje}</p>
        <p>Tiempo restante: {tiempoRestante}s</p>
        <button on:click={hacerClick}>Haz clic</button>
        <button on:click={comenzar}>Comenzar</button>
        <button on:click={reiniciar}>Reiniciar</button>
        <p>Total de clics: {contador}</p>
    </div>
</main>
