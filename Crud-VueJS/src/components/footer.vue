<template>
  <div id="footer">
    <footer>
      <div class="container">
        <div class="row">
          <div class="col-sm">Created by: Frederiko C. M. Ribeiro</div>
          <div class="col-sm">Contact information:
        <a href="mailto:frederiko.cmr@gmail.com">frederiko.cmr@gmail.com</a></div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "Footer"
};
</script>

<style scoped>
footer {
  visibility: hidden;
  position: absolute;
  bottom: 0;
  width: 100%;
  height: 60px; 
  background: #81a6ac70;
  color: black;
}

</style>
