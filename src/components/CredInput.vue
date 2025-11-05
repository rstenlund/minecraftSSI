<script setup lang="ts">
import { ref } from 'vue'

// Create reactive references for the input values
const minecraftUsername = ref('')
const verificationCode = ref('')
const buttonText = ref('Verifiera')
// Function to handle verification code input and convert to uppercase
const handleCodeInput = (event: Event) => {
  const target = event.target as HTMLInputElement
  const upperValue = target.value.toUpperCase()
  verificationCode.value = upperValue
  target.value = upperValue
}

// Function to handle button click
const handleVerify = async () => {
  console.log('Minecraft Username:', minecraftUsername.value)
  console.log('Verification Code:', verificationCode.value)

  // You can add your verification logic here
  if (minecraftUsername.value && verificationCode.value) {
    // Process the credentials
    buttonText.value = 'Verifierar...'

    let req = await fetch(
      'http://92.5.118.191:3000/add?u=' + minecraftUsername.value + '&p=' + verificationCode.value,
    )
    minecraftUsername.value = ''
    verificationCode.value = ''

    let res = await req.json()
    if (res.message == 'Username added successfully') {
      buttonText.value = 'Verifierad!'
    } else {
      buttonText.value = 'Verifikation misslyckades'
    }
    console.log(res)
  } else {
    alert('Please fill in both fields')
  }
}
</script>

<template>
  <div class="inputs">
    <h3>Vänligen ange dina uppgifter nedan</h3>
    <input v-model="minecraftUsername" type="text" placeholder="Minecraft-användarnamn" />
    <input
      class="code"
      v-model="verificationCode"
      type="text"
      placeholder="kod"
      @input="handleCodeInput"
      style="text-transform: uppercase"
    />
    <button class="verify" @click="handleVerify">{{ buttonText }}</button>
  </div>
</template>

<style scoped>
.inputs h3 {
  width: 300px;
  text-align: center;
  margin-bottom: 10px;
}

.inputs {
  display: flex;
  width: 100%;
  height: 100%;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.inputs input {
  font-weight: bold;

  width: 300px;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin: 8px 0;
  box-shadow: none;
  transition:
    border-color 0.1s,
    box-shadow 0.1s;
}

.inputs input:focus {
  border-color: #66afe9;
  outline: none;
  box-shadow: 0 0 8px rgba(102, 175, 233, 0.6);
}

.inputs button {
  width: 300px;
  padding: 10px;
  font-size: 16px;
  color: #fff;
  background-color: #28a745;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.1s;
  margin: 10px 0;
  font-weight: bold;
}

.inputs button:hover {
  background-color: #218838;
}

@media (min-width: 1024px) {
  .inputs {
    align-items: flex-start;
    padding-left: 15mm;
  }
}
</style>
