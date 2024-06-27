<script setup>
import { ref } from 'vue';

let showModal = ref(false);
const modelInput = ref('');
const notes = ref([]);

const hideModal = e => {
    if (e.target.classList.contains('overlay')) {
        console.log(notes);
        showModal.value = false;
    }
};

const createNote = () => {
    notes.value.push({
        id: Math.floor(Math.random() * 100000),
        text: modelInput.value,
        date: new Date(),
        backgroundColor: 'hsl(' + Math.random() * 360 + ', 100%, 75%)',
    });
    showModal.value = false;
    modelInput.value = '';
};
</script>

<template>
    <main>
        <div class="overlay" v-if="showModal" @click="hideModal">
            <div class="modal">
                <textarea v-model="modelInput" name="note" id="note" cols="30" rows="10"></textarea>
                <button @click="createNote">Add Note</button>
            </div>
        </div>
        <div class="container">
            <header>
                <h1>Notes</h1>
                <button @click="showModal = true">+</button>
            </header>
            <div class="cards-container">
                <div class="card" v-for="note in notes" :key="note.id" :style="{ backgroundColor: note.backgroundColor }">
                    <p class="main-text">{{ note.text }}</p>
                    <p class="date">{{ note.date.toDateString() }}</p>
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

    .overlay {
        position: absolute;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.384);
        z-index: 1;
        display: flex;
        align-items: center;
        justify-content: center;

        .modal {
            width: 60%;
            background-color: white;
            padding: 2rem;
            border-radius: 3rem;
            position: relative;
            display: flex;
            flex-direction: column;
        }

        button {
            background-color: $newColor;
            margin-top: 1rem;
        }
    }
}
</style>
