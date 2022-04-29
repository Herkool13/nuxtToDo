<template>
  <div @mousemove="move($event)">
    <slot></slot>
    <div class="blur">
      <div class="img-box">
        <img
          src="~/assets/checklist/1.png"
          class="img-res"
          ref="img1"
          id="img1"
        />
        <img
          src="~/assets/checklist/2.png"
          class="img-res"
          ref="img2"
          id="img2"
        />
        <img
          src="~/assets/checklist/3.png"
          class="img-res"
          ref="img3"
          id="img3"
        />
        <img
          src="~/assets/checklist/4.png"
          class="img-res"
          ref="img4"
          id="img4"
        />
        <img
          src="~/assets/checklist/5.png"
          class="img-res"
          ref="img5"
          id="img5"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loc: {
        x: null,
        y: null,
      },
    };
  },
  methods: {
    move(event) {
      this.$refs.img1.style.left = `${58 + event.clientX / 900}rem`;
      this.$refs.img1.style.top = `${-10 + event.clientY / 800}rem`;
      // -----------
      this.$refs.img2.style.left = `${10 - event.clientX / 900}rem`;
      this.$refs.img2.style.top = `${-10 + event.clientY / 800}rem`;
      //-----------
      this.$refs.img3.style.left = `${68 - event.clientX / 900}rem`;
      this.$refs.img3.style.top = `${-30 - event.clientY / 500}rem`;
      //------------
      this.$refs.img4.style.left = `${5 + event.clientX / 900}rem`;
      this.$refs.img4.style.top = `${-30 - event.clientY / 800}rem`;
      //------------
      this.$refs.img5.style.left = `${22 + event.clientY / 300}rem`;
      this.$refs.img5.style.top = `${-38 + event.clientX / 800}rem`;
    },
  },
};
</script>

<style>
.img-box {
  position: relative;
  width: 90vw;
}
.img-res {
  position: absolute;
  width: 200px;
  z-index: -5;
}
#img1 {
  top: -10rem;
  left: 58rem;
}
#img2 {
  top: -10rem;
  left: 10rem;
}
#img3 {
  top: -30rem;
  left: 68rem;
}
#img4 {
  top: -30rem;
  left: 5rem;
}
#img5 {
  top: -38rem;
  left: 22rem;
}
.blur {
  z-index: -5;
  width: 100%;
  /* height: 90vh; */
  padding-top: 3rem;
  filter: blur(3px);
  -webkit-filter: blur(3px);
}
</style>