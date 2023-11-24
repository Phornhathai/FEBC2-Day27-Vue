<script setup lang="ts">
import {ref} from 'vue';
//เก็บข้อมูลทั้งหมด 3 ค่า
let weight = ref("");
let height = ref("");
let bmiResult = ref("");

    //สร้าง function สำหรับ vue framework
    const calculateBMI = () => {    
        const weightInKg = parseFloat(weight.value);
        const heightInM = parseFloat(height.value);
        if(weightInKg > 0 && heightInM > 0){
            bmiResult.value = (weightInKg / (heightInM * weightInKg)).toFixed(2);
        }
    }
</script>

<template>
    <div>
        Result :: {{ bmiResult }}
    </div>
    <div>
        <!-- min = 1 คือ ให้ใส่ได้แค่ค่า 1 ตัวอักษร และ v-model คือ การนำค่าที่เป็นตัวเลขไปผูกกับตัวแปรที่ชื่อ weight -->
        <!-- รูปแบบการเขียน v-model.number = "weight" เรียกว่า databinding -->
        <input type="number" min="1" step="0.1" v-model.number="weight" placeholder="Your Weight (kg.)" required>
        <input type="number" min="0.1" step="0.01" v-model.number="height" placeholder="Your Height (m.)" required>
        <!-- ถ้าขนาดของตัวแปร weight ที่กรอกมามีค่าเท่ากับ 0 ให้ button เป็น disableed -->
        <button @click="calculateBMI" type="submit">Calculate</button>
    </div>

</template>

<style>

</style>