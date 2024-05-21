<script setup lang="ts">
const examScore = ref<number>(0);

const examPlace = ref(1);

const examPlaceTable = new Map();
examPlaceTable.set(1, 1700);
examPlaceTable.set(2, 900);
examPlaceTable.set(3, 500);

const examScoreMultiplierTable = new Map();
examScoreMultiplierTable.set(0, 0.3);
examScoreMultiplierTable.set(1, 0.15);
examScoreMultiplierTable.set(2, 0.08);
examScoreMultiplierTable.set(3, 0.04);
examScoreMultiplierTable.set(4, 0.02);
examScoreMultiplierTable.set(5, 0.01);

const examPlacePoint = computed(() => {
    return examPlaceTable.get(examPlace.value);
});

const examScorePoint = computed(() => {
    let _examScorePoint = 0;
    let _examScore = examScore.value;

    if (examScore.value <= 5000) {
        return Math.floor(_examScorePoint + (_examScore * examScoreMultiplierTable.get(0)));
    }
    _examScorePoint += 5000 * examScoreMultiplierTable.get(0);
    _examScore -= 5000;

    if (examScore.value <= 10000) {
        return Math.floor(_examScorePoint + (_examScore * examScoreMultiplierTable.get(1)));
    }
    _examScorePoint += 5000 * examScoreMultiplierTable.get(1);
    _examScore -= 5000;

    if (examScore.value <= 20000) {
        return Math.floor(_examScorePoint + (_examScore * examScoreMultiplierTable.get(2)));
    }
    _examScorePoint += 10000 * examScoreMultiplierTable.get(2);
    _examScore -= 10000;

    if (examScore.value <= 30000) {
        return Math.floor(_examScorePoint + (_examScore * examScoreMultiplierTable.get(3)));
    }
    _examScorePoint += 10000 * examScoreMultiplierTable.get(3);
    _examScore -= 10000;

    if (examScore.value <= 40000) {
        return Math.floor(_examScorePoint + (_examScore * examScoreMultiplierTable.get(4)));
    }
    _examScorePoint += 10000 * examScoreMultiplierTable.get(4);
    _examScore -= 10000;

    _examScorePoint += _examScore * examScoreMultiplierTable.get(5);
    return Math.floor(_examScorePoint);
});

const vocal = ref<number>(0);
const dance = ref<number>(0);
const visual = ref<number>(0);

const statusPoint = computed(() => {
    return Math.floor((vocal.value + dance.value + visual.value) * 2.3);
});

const idolPower = computed(() => {
    return examPlacePoint.value + examScorePoint.value + statusPoint.value;
});
</script>

<template>
    <h1>学マスの数字を計算するやつ</h1>
    <p>最終プロデュース評価 <span style="font-size: 3rem;">{{ idolPower }}</span>pts.</p>
    <div>
        <span>最終試験順位</span>
        <select v-model="examPlace">
            <option :value="1">1位</option>
            <option :value="2">2位</option>
            <option :value="3">3位</option>
        </select>
    </div>
    <div>
        <span>最終試験スコア</span>
        <input type="number" v-model="examScore" />
    </div>
    <div>
        <span>Vocal</span>
        <input type="number" v-model="vocal" />
    </div>
    <div>
        <span>Dance</span>
        <input type="number" v-model="dance" />
    </div>
    <div>
        <span>Visual</span>
        <input type="number" v-model="visual" />
    </div>
    <p>計算式 出典: 学園アイドルマスター 公式Discord</p>
    <NuxtLink to="/">← トップページに戻る</NuxtLink>
</template>
