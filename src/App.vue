<script setup></script>

<template>
    <main>
        <div class="container">
            <header>
                <h1>Notes</h1>
                <button>+</button>
            </header>
            <div class="cards-container">
                <div class="card">
                    <p class="main-text">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Perferendis, culpa!</p>
                    <p class="date">27/06/2024</p>
                </div>
            </div>
        </div>
    </main>
</template>

<style lang="scss">
main {
    height: 100vh;
    width: 100vw;
    display: flex;
    justify-content: center;

    .container {
        width: 90%;

        header {
            display: flex;
            justify-content: space-between;
            margin-top: 3rem;

            h1 {
                font-weight: bold;
            }

            button {
                border: none;
                padding: 1rem 2.5rem;
                background-color: $newColor;
                border-radius: 100%;
                font-weight: bold;
            }
        }

        .cards-container {
            margin-top: 3rem;
            display: flex;
            flex-wrap: wrap;

            .card {
                width: 20rem;
                height: 20rem;
                background-color: lightgreen;
                padding: 2rem;
                border-radius: 1.5rem;
                justify-content: space-between;
                margin: 0 2rem 2rem 0;
                display: flex;
                flex-direction: column;

                .date {
                    font-size: 1rem;
                }
            }
        }
    }
}
</style>
