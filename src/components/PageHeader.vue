<template>
    <div id="page-header-section">
        <h1 id="page-header-text">
            Your Most Important Risks
        </h1>
        <div id="header-buttons">
            <button class="header-button" v-for="(risk, index) in risks" :key="index" :class="{ selected: index === 0 }"
                @click="headerButtonClicked">
                {{ risk.value }}
            </button>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            risks: [
                {
                    id: 1,
                    value: "Heart Health"
                },
                {
                    id: 2,
                    value: "Body Composition"
                },
                {
                    id: 3,
                    value: "Diabetes"
                },
                {
                    id: 4,
                    value: "Tobacco Use"
                },
                {
                    id: 5,
                    value: "Alcohol"
                },
                {
                    id: 6,
                    value: "Drug Use"
                },
                {
                    id: 7,
                    value: "Cancer"
                },
                {
                    id: 8,
                    value: "Additional Biometrics"
                },
            ]
        }
    },
    methods: {
        headerButtonClicked() {
            console.log('header button clicked');
        }
    }
}
</script>
<style scoped>
#page-header-section {
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 20px;
    justify-items: center;
    margin-top: 10px;
}

#page-header-text {
    font-weight: bold;
}

#header-buttons {
    display: flex;
    flex-direction: row;
    justify-content: center;
    flex-wrap: wrap;
    width: 60%;
    gap: 10px;
}

.header-button {
    border-radius: 40px;
    border: 1px solid #B0E0E6;
    background-color: white;
    padding: 15px;
    color: black;
    font-weight: bold;
}

.header-button:hover {
    cursor: pointer;
}

.selected {
    background: red;
    color: white;
    border: 2px solid #FFCCCB;
}
</style>