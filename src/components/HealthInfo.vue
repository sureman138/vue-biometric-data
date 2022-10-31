<script setup>
import Card from './Card.vue'
import PageHeader from './PageHeader.vue'
</script>

<template>
    <PageHeader />
    <div class="section-header">
        <h2 class="header-text">
            Heart Health
        </h2>
        <div class="metric-bubble metric-bubble-red">2</div>
        <div class="metric-bubble metric-bubble-gold">5</div>
        <div class="metric-bubble metric-bubble-green">1</div>
    </div>
    <div class="card-section">
        <div v-for="(value, index) in heartHealthData" :key="index">
            <Card :selected="index === 0" :status="value.status">
                <template #number>{{ value.value }}</template>
                <template #measurement>{{ value.unit }}</template>
                <template #heading>{{ value.name }}</template>
                <template #details>{{ value.description }}</template>
                <template #time-amount>{{ value.timeDisplay }}</template>
            </Card>
        </div>
    </div>
    <div class="button-section">
        <button class="load-button" @click="loadButtonClick">
            Load More
        </button>
    </div>
    <hr>
    <div class="section-header">
        <h2 class="header-text">
            Body Composition
        </h2>
        <div class="metric-bubble metric-bubble-red">1</div>
        <div class="metric-bubble metric-bubble-gold">4</div>
        <div class="metric-bubble metric-bubble-green">2</div>
    </div>
    <div class="card-section">
        <div v-for="(value, index) in bodyCompositionData" :key="index">
            <Card :status="value.status">
                <template #number>{{ value.value }}</template>
                <template #measurement>{{ value.unit }}</template>
                <template #heading>{{ value.name }}</template>
                <template #details>{{ value.description }}</template>
                <template #time-amount>{{ value.timeDisplay }}</template>
            </Card>
        </div>
    </div>
    <div class="button-section">
        <button class="load-button" @click="loadButtonClick">
            Load More
        </button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            biometricValues: [
                {
                    id: 1,
                    name: "Fasting Glucose",
                    description: "25 mg/dl above the recommended level",
                    value: "151",
                    unit: "mg/dl",
                    timeDisplay: "2W",
                    actionLabel: "Take Action",
                    status: "Critical",
                    categoryId: 1
                },
                {
                    id: 2,
                    name: "Triglycerides",
                    description: "19 mg/dl above the recommended level",
                    value: "519",
                    unit: "mg/dl",
                    timeDisplay: "1M",
                    actionLabel: "Take Action",
                    status: "Concern",
                    categoryId: 1
                },
                {
                    id: 3,
                    name: "Existing Heart Disease",
                    description: "You reported that you've been diagnosed with some form of heart disease.",
                    timeDisplay: "1M",
                    value: "",
                    unit: "",
                    actionLabel: "Take Action",
                    status: "Concern",
                    categoryId: 1
                },
                {
                    id: 4,
                    name: "BMI - Obesity",
                    description: "6.1 above the recommended level",
                    timeDisplay: "2W",
                    value: "31.1",
                    unit: "",
                    actionLabel: "Take Action",
                    status: "Concern",
                    categoryId: 2
                },
                {
                    id: 5,
                    name: "Waist Circumference",
                    description: "Your waist circumference may lead to higher risk of certain chronic conditions.",
                    timeDisplay: "1M",
                    value: "",
                    unit: "",
                    actionLabel: "Take Action",
                    status: "Watch",
                    categoryId: 2
                },
            ]
        }
    },
    computed: {
        heartHealthData() {
            return this.biometricValues.filter(item => {
                return item.categoryId === 1;
            })
        },

        bodyCompositionData() {
            return this.biometricValues.filter(item => {
                return item.categoryId === 2;
            })
        }

    },
    methods: {
        loadButtonClick() {
            console.log("load button clicked");
        }
    },
    created() {
    }
}
</script>

<style scoped>
.card-section {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
    justify-items: center;
    margin-top: 40px;
}

@media (max-width: 800px) {
    .card-section {
        display: grid;
        grid-template-columns: 1fr;
        grid-gap: 20px;
        justify-items: center;
    }
}

.load-button {
    width: 150px;
    border-radius: 40px;
    border: 1px solid #B0E0E6;
    background-color: lightgray;
    padding: 10px;
    color: darkslategray;
    font-weight: bold;
}

.load-button:hover {
    cursor: pointer;
}

hr {
    background-color: lightgray;
    height: 2px;
    border: none;
}

.button-section {
    text-align: center;
    margin-top: 40px;
    margin-bottom: 40px;
}

.section-header{
    display:flex;
    justify-content: flex-start;
    flex-direction: row;
    margin-left:80px;
    margin-top:30px;
}

.header-text {
    color: var(--vt-c-skyblue);
    font-weight:bold;
}

.metric-bubble {
    height:30px;
    width:30px;
    text-align: center;
    padding:3px 0;
    color:white;
    border-radius: 50%;
    align-self: center;
    margin-left:10px;
}

.metric-bubble-red {
    background-color: red;
}

.metric-bubble-gold {
    background-color: darkgoldenrod
}
.metric-bubble-green {
    background-color: darkgreen;
}
</style>