<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>세다</ion-title>
      </ion-toolbar>
    </ion-header>
    <ion-content :fullscreen="true" color="light">
      <ion-input type="number" v-model="no"></ion-input>
    </ion-content>
    <ion-footer>
      <ion-toolbar>
        <ion-grid>
          <ion-row>
            <ion-col>
              <ion-button size="full" :color="btn1>0 ? 'primary':'danger'" @click="toggle()">+ / - </ion-button>
            </ion-col>
            <ion-col>
              <ion-button size="full" :disabled="history.length<1" @click="historyBack()">이전</ion-button>
            </ion-col>
            <ion-col>
              <ion-button size="full" color="medium" @click="clear()">초기화</ion-button>
            </ion-col>
          </ion-row>
          <ion-row>
            <ion-col>
              <ion-button size="full" :color="btn1>0 ? 'primary':'danger'" @click="add(btn1)">{{btn1}}</ion-button>
            </ion-col>
            <ion-col>
              <ion-button size="full" :color="btn1>0 ? 'primary':'danger'" @click="add(btn2)">{{btn2}}</ion-button>
            </ion-col>
            <ion-col>
              <ion-button size="full" :color="btn1>0 ? 'primary':'danger'" @click="add(btn3)">{{btn3}}</ion-button>
            </ion-col>
          </ion-row>
        </ion-grid>
      </ion-toolbar>
    </ion-footer>
  </ion-page>
</template>

<style scoped>
  ion-input{
    height : 60vh;
    text-align: center;
    font-size: 15vh;
    font-weight: bold;
  }
  ion-grid,ion-row,ion-col{
    padding:0;
  }
  ion-button{
    height: 10vh;
    font-size : 3vh;
    font-weight: bold;
  }
</style>
<script lang="ts">
import { IonContent, IonHeader, IonFooter,
        IonPage, IonTitle, IonToolbar,
        IonInput,
        IonGrid,IonRow,IonCol,
        IonButton } from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'HomePage',
  components: {
    IonContent,
    IonHeader,
    IonFooter,
    IonPage,
    IonTitle,
    IonToolbar,
    IonInput,
    IonGrid,IonRow,IonCol,
    IonButton
  },
  data() {
      let no = 0 as number;
      let history = [] as any;
      let btn1 = 1 as number;
      let btn2 = 10 as number;
      let btn3 = 100 as number;
      return {
        no,
        history,
        btn1,btn2,btn3
      }
  },
  methods:{
    add(i : number){
      this.no =this.no*1 + i;
      this.history.push(this.no);
    },
    historyBack(){      
        this.history.pop();
        let size = this.history.length;
        this.no = this.history[size-1];

    },
    toggle(){
      this.btn1 *= -1;
      this.btn2 *= -1;
      this.btn3 *= -1;

    },
    clear(){
      this.no = 0;
      this.history = [];
    }
  }
});
</script>