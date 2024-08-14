<template>
    <div class="flex flex-col w-full min-h-screen text-white bg-slate-800">
        <header>
            <div class="container py-6 mx-auto text-center">
                <h1 class="text-3xl font-bold text-white">VueQuiz</h1>
            </div>
        </header>
        <main class="container flex-grow p-4 mx-auto">
            <slot name="main"></slot>
        </main>
        <footer class="p-4 text-center bg-teal-700">
            <p>&copy; 2024 VueQuiz. Tous droits réservés.</p>
        </footer>
    </div>
</template>