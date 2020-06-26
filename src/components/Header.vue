<template>
  <div>
  <b-nav tabs>
    <b-nav-item active><b>Fancy Quizz App</b></b-nav-item>
    <b-nav-item>Counter : {{numCorrect}}/{{total}}</b-nav-item>
    <b-nav-item disabled>Quizz</b-nav-item>
  </b-nav>
</div>
</template>
<script>
export default {
  props:['numCorrect','total']
}
</script>