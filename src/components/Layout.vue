<template>
    <div class="wrapper">
        <!-- Header -->
        <header class="header">
            <nav>
                <ul>
                    <li>
                        <h1>VueQuest</h1>
                    </li>
                </ul>
            </nav>
        </header>

        <!-- Main Content -->
        <main>
            <!-- Slot for main content -->
            <slot name="main"></slot>
        </main>

        <!-- Footer -->
        <footer class="footer">
            <p class="pico-color-pumpkin-300">&copy; 2024 VueQuest. Tous droits réservés.</p>
        </footer>
    </div>
</template>

<script setup>
// Pas de script spécifique pour ce layout
</script>

<style>
.wrapper {
    height: 100vh;
    display: flex;

    /* Direction of the items, can be row or column */
    flex-direction: column;
}

header,
footer {
    height: 5%;
    margin-bottom: 7px;
}

footer {
    text-align: center;
}

main {
    display: flex;
    width: 100%;
    height: 90%;
    flex-direction: column;
    margin-top: 40px;

}

header h1 {
    font-size: 60px;
    font-weight: 600;
    background: -webkit-linear-gradient(#FFBF00, #FFA23A, #D24317);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    margin-left: 20px;
}

h1 {
    font-size: 24px;
    font-weight: 600;
    color: #FCEFD9;
}

h3 {
  font-weight: 500;
  font-size: 1.5rem;
  color: #FDDEA6;
  margin-bottom: 1rem;
}
</style>