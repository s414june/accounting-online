<template>
  <el-container class="w-full items-center">
    <el-header>
      <h1>別再花</h1>
    </el-header>
    <el-main>
      <el-button round class="w-56">
        <el-image src="/img/google.svg" class="mr-2 w-4" />
        以Google帳號登入
      </el-button>
      <table>
        <thead>
          <tr>
            <th>消費類型</th>
            <th>金額</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>1</td>
            <td>2</td>
          </tr>
        </tbody>
      </table>
    </el-main>
  </el-container>
</template>
<script setup lang="ts">
import { onMounted, ref } from "vue";
// Import the functions you need from the SDKs you need
import { initializeApp } from "firebase/app";
import { getAnalytics } from "firebase/analytics";
// TODO: Add SDKs for Firebase products that you want to use
// https://firebase.google.com/docs/web/setup#available-libraries
import { getFirestore } from "firebase/firestore";
import { doc, getDoc } from "firebase/firestore";

// Your web app's Firebase configuration
// For Firebase JS SDK v7.20.0 and later, measurementId is optional
const firebaseConfig = {
  apiKey: "AIzaSyCw7LLj6ZQohgmlDtV9i4_42o5hJMjg-Z0",
  authDomain: "accounting-online-8cbe5.firebaseapp.com",
  projectId: "accounting-online-8cbe5",
  storageBucket: "accounting-online-8cbe5.appspot.com",
  messagingSenderId: "1050802574579",
  appId: "1:1050802574579:web:7b427219663f5a80aa5386",
  measurementId: "G-09TJEN4W5S",
};

const spending = ref([
  {
    type: Number,
    count: Number,
  },
]);
onMounted(async () => {
  // Initialize Firebase
  const app = initializeApp(firebaseConfig);
  const analytics = getAnalytics(app);
  const db = getFirestore(app);

  const spendingSnap = await getDoc(doc(db, "amounting", "spending"));
  console.log(spendingSnap.data());
  //   spending.value = spendingSnap.data()
});
</script>
