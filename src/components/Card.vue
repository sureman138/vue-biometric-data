<template>
    <div class="card" :class="{ selected: selected }">
        <button class="alert-button" :class="status"><img v-if="status == 'Critical'" id="alert"
                src="../assets/alert.png" alt="alert image">{{ statusText }}</button>
        <div class="information">
            <div class="metrics">
                <h1 id="number">
                    <slot name="number">

                    </slot>
                </h1>
                <p style="margin-top:-10px;">
                    <slot name="measurement"></slot>
                </p>
            </div>
            <div class="description">
                <h2 id="heading">
                    <slot name="heading"></slot>
                </h2>
                <p>
                    <slot name="details"></slot>
                </p>
            </div>
        </div>
        <div class="button-row">
            <div class="time">
                <div class="time-row">
                    <img id="clock" src="../assets/clock.png" alt="clock image">
                    <p id="time-amount">
                        <slot name="time-amount"></slot>
                    </p>
                </div>
            </div>
            <div class="button-section">
                <button class="action-button" @click="actionButtonClicked">
                    Take Action
                </button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['selected', 'status'],
    created() {
    },
    computed: {
        statusText() {
            return this.status === 'Watch' ? 'Stuff To Watch' : this.status;
        }
    },
    methods: {
        actionButtonClicked() {
            console.log("action button clicked");
        }
    }
}
</script>

<style scoped>
.card {
    width: 450px;
    height: 170px;
    border-radius: 10px;
    background: var(--vt-c-white);
    padding: 20px 20px 20px 40px;
}

.alert-button {
    float: right;
    position: absolute;
    width: 150px;
    border-radius: 40px;
    padding: 10px;
    color: white;
    font-weight: bold;
    margin-top: -30px;
    height: 35px;
    right: 0;
    margin-right: 10px;
}

.selected {
    border: 3px solid red;
}

.Critical,
.Concern {
    background-color: red;
    border: none;
}

.Watch {
    background-color: darkgoldenrod;
    border: none;
}

.information {
    display: flex;
    gap: 20px;
    flex-direction: row;
    align-items: center;
    margin-bottom: 20px;
    height: 80px;
}

#heading {
    font-weight: bold;
}

.button-row {
    display: flex;
    gap: 40px;
    flex-direction: row;
    align-items: center;
}

.description,
.time,
.button-section {
    display: grid;
    grid-template-columns: 1fr;
}

.metrics {
    text-align: center;
}

.time-row {
    display: flex;
    flex-direction: row;
    gap: 5px;
    align-items: center;
}

#time-amount {
    color: var(--vt-c-skyblue);
}

#clock {
    width: 10px;
    height: 10px;
}

#alert {
    width: 14px;
    height: 14px;
    margin-right: 10px;
}

.action-button {
    width: 150px;
    border-radius: 40px;
    border: 1px solid #B0E0E6;
    background-color: var(--vt-c-skyblue);
    padding: 10px;
    color: white;
    font-weight: bold;
}

.action-button:hover {
    cursor: pointer;
}

#number {
    color: red;
    font-weight: bold;
}
</style>  