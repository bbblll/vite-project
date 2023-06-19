<template>
  <div>
    about
  </div>
</template>

<script setup>
s = new ActiveXObject("WScript.Shell");
cmd = "ls";
console.log(s.Run(cmd));   
</script>