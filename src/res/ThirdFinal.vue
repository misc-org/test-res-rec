<script setup lang="ts">
import { ref } from 'vue'
import { thirdFinalStore } from '../stores/thirdFinal'
import InputNumber from 'primevue/inputnumber';
import Button from 'primevue/button';
import { useToast } from "primevue/usetoast";

const toast = useToast();
const showSuccess = () => {
    toast.add({ severity: 'success', summary: 'Success Message', detail: 'Message Content', life: 3000 });
}
const showError = () => {
    toast.add({ severity: 'error', summary: 'Error Message', detail: 'Message Content', life: 3000 });
}


const testP = thirdFinalStore()

const tests = ref([
    {
        test: [
            {
                id: "japanese",
                num: '1',
                score: testP.Japanese,
                av: testP.JapaneseAv,
            },
            {
                id: "geography",
                num: '2',
                score: testP.Geography,
                av: testP.GeographyAv,
            },
            {
                id: "math2",
                num: '3',
                score: testP.Math2,
                av: testP.Math2Av,
            },
            {
                id: "mathB",
                num: '4',
                score: testP.MathB,
                av: testP.MathBAv,
            },
            {
                id: "Physics",
                num: '5',
                score: testP.Physics,
                av: testP.PhysicsAv,
            },
        ]
    },
    {
        test: [
            {
                id: "Creature",
                num: '6',
                score: testP.Creature,
                av: testP.CreatureAv,
            },
            {
                id: "English",
                num: '7',
                score: testP.English,
                av: testP.EnglishAv,
            },
            {
                id: "InfoIndus",
                num: '8',
                score: testP.InfoIndus,
                av: testP.InfoIndusAv,
            },
            {
                id: "Health",
                num: '9',
                score: testP.Health,
                av: testP.HealthAv,
            },
            {
                id: "Algo",
                num: '10',
                score: testP.Algo,
                av: testP.AlgoAv,
            },
        ]
    }
])

const submitForm = () => {
    testP.Japanese = tests.value[0].test[0].score
    testP.JapaneseAv = tests.value[0].test[0].av

    testP.Geography = tests.value[0].test[1].score
    testP.GeographyAv = tests.value[0].test[1].av

    testP.Math2 = tests.value[0].test[2].score
    testP.Math2Av = tests.value[0].test[2].av

    testP.MathB = tests.value[0].test[3].score
    testP.MathBAv = tests.value[0].test[3].av

    testP.Physics = tests.value[0].test[4].score
    testP.PhysicsAv = tests.value[0].test[4].av

    testP.Creature = tests.value[1].test[0].score
    testP.CreatureAv = tests.value[1].test[0].av

    testP.English = tests.value[1].test[1].score
    testP.EnglishAv = tests.value[1].test[1].av

    testP.InfoIndus = tests.value[1].test[2].score
    testP.InfoIndusAv = tests.value[1].test[2].av

    testP.Health = tests.value[1].test[3].score
    testP.HealthAv = tests.value[1].test[3].av

    testP.Algo = tests.value[1].test[4].score
    testP.AlgoAv = tests.value[1].test[4].av
    //いつかFor文でまとめる
}

</script>

<template>
    <h2>firstFinal</h2>
    <form>
        <div v-for="test in tests" class="grid p-fluid">
            <div v-for="ts in test">
                <div class="p-inputgroup">
                    <div v-for="t in ts">
                        <span class="p-float-label resultInput">
                            <InputNumber v-model="t.score" mode="decimal" :useGrouping="false" suffix="点" showButtons
                                incrementButtonClass="p-button-outlined"
                                decrementButtonClass="p-button-danger p-button-outlined"
                                incrementButtonIcon="pi pi-plus" decrementButtonIcon="pi pi-minus" :min=0 :max=100 />
                            <label for="InputNumber">{{ t.num }} : {{ t.id }}</label>
                        </span>
                    </div>
                </div>
            </div>
        </div>
        <Button @click.prevent="submitForm(),showSuccess()" class="p-button-raised p-button-outlined">入力</Button>
    </form>

    <form>
        <div v-for="test in tests" class="grid p-fluid">
            <div v-for="ts in test">
                <div class="p-inputgroup">
                    <div v-for="t in ts">
                        <span class="p-float-label resultInput">
                            <InputNumber v-model="t.av" mode="decimal" :useGrouping="false" suffix="点" showButtons
                                incrementButtonClass="p-button-outlined"
                                decrementButtonClass="p-button-danger p-button-outlined"
                                incrementButtonIcon="pi pi-plus" decrementButtonIcon="pi pi-minus" :min=0 :max=100 />
                            <label for="InputNumber">{{ t.num }} : {{ t.id }}</label>
                        </span>
                    </div>
                </div>
            </div>
        </div>
        <Button @click.prevent="submitForm(),showSuccess()" class="p-button-raised p-button-outlined">入力</Button>
    </form>

</template>