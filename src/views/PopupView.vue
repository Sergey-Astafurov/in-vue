<template >
<div class="container">

<div class="info">{{ info }}</div>
  <button href="#" @click="isActive= !isActive" class="open-popup">Открыть попап</button>
  <div class="popup__bg" @click="close($event )"  :class="{active : isActive}">
    <div class="popup "  :class="{active: isActive}" v-if="isActive" >
      <h3 class="title">Форма отправки</h3>
      <b class="close-popup" @click="isActive = !isActive">X</b>
    <form class=" form" @submit.prevent="submit">
      <label>
        <input type="text" name="name" class="input" v-model="user.name">
        <div class="label__text">
          Ваше имя
        </div>
      </label>
      <label>
        <input type="tel" name="tel" class="input" v-model="user.tel">
        <div class="label__text">
          Ваш телефон
        </div>
      </label>
      <label>
        <input type="text" name="name" class="input" v-model="user.text">
        <div class="label__text">
          Ваше имя
        </div>
      </label><label>
        <input type="text" name="name" class="input" v-model="user.adresss">
        <div class="label__text">
          Ваше имя
        </div>
      </label>
      <label class="last">
        <input type="text" name="name" class="input" v-model="user.year">
        <div class="label__text">
            Ваше имя
        </div>
    </label>

    <button class="btn__submit"  type="submit">Отправить</button>
  </form>
  </div>
  </div>
</div>

</template>
<script>
export default {
data() {
  return {
    isActive:false,
    user: {
      name: '',
      tel: '',
      adresss: '',
      text: '',
      year: '',
    },
    info: 's',
  }
},
methods:{
  submit(){
    this.info = ''
    this.info = JSON.stringify(this.user)
    this.user.adresss = '';
    this.user.name = '';
    this.user.tel = '';
    this.user.text = '';
    this.user.year = '';
    this.isActive = false
  },
  close(event){
    if(event.target.classList[0] == 'popup__bg' ){
      this.isActive = false
    }
  }
}
}
</script>
<style scoped>
.container{
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.popup button {
  width: 100%;
  height: 45px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-size: 18px;
  border: 2px solid #2982ff;
  background: #2982ff;
  cursor: pointer;
  text-transform: uppercase;
  transition: 0.2s all;
}
.popup__bg {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background: rgba(0,0,0,0.5);
  opacity: 0;
  pointer-events: none;
  transition: 0.2s all;
}

.popup__bg.active {
  opacity: 1;
  pointer-events: all;
  transition: 0.5s all;
}
.popup {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) scale(0);
  background: #fff;
  max-width: 500px;
  padding: 25px;
  transition: 0.2s all;
}

.popup.active {
  transform: translate(-50%, -50%) scale(1);
  transition: 0.2s all;
}
.close-popup {
  position: absolute;
  top: 10px;
  right: 10px;
  cursor: pointer;
}
.popup label {
  margin-bottom: 10px;
  display: flex;
  flex-direction: column-reverse;
}

.popup .label__text {
  font-size: 14px;
  text-transform: uppercase;
  font-weight: 500;
  color: #cfd0d3;
  margin-bottom: 5px;
}

.popup input {
  height: 20px;
  font-size: 18px;
  outline: none;
}
.title{
  margin-bottom: 15px;
}
.form{
  width: 100%;
  display: flex;
  flex-wrap: wrap;

  justify-content: space-between;

}
.last{
  width: 100%;
}
.info{
  position: absolute;
  top: 200px;
  left: 30px;
}


</style>