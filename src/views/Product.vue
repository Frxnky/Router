<template>
  <div
    class="bg-image d-flex justify-content-center align-items-center"
    style="background-color: rgb(4, 40, 75)"
  >
    <v-container>
      <center><h1 style="color: white">Product</h1></center>
      <v-container class="d-flex flex-wrap">
        <v-card
          class="mx-auto mb-5"
          max-width="400"
          v-for="(i, index) in productlist"
          :key="index"
        >
          <v-img class="text-black align-end" height="350px" :src="i.imageurl">
            <v-card-title>{{ i.name }}</v-card-title>
          </v-img>

          <v-card-subtitle class="pb-0">{{ i.rightText }}</v-card-subtitle>

          <v-card-text class="text--primary">
            <div style="font-size: large">{{ i.leftText }}</div>
          </v-card-text>

          <v-card-actions>
            <v-btn color="info" text :to="'/detail/' + i.rightText"
              >detail</v-btn
            >
            <v-btn color="orange" @click="selected(i)"> Add </v-btn>
          </v-card-actions>
        </v-card>
      </v-container>

      <table class="table table-striped table-hover"></table>
      <v-container
        ><h4 class="text-danger fs-1">Total {{ total() }} Baht</h4></v-container
      >
      <v-container grid-list-xs class="white">
        <router-view :key="$route.path"></router-view>
      </v-container>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      productlist: [
        {
          name: "Adidas Folum Low",
          imageurl:
            "https://assets.adidas.com/images/h_840,f_auto,q_auto:sensitive,fl_lossy,c_fill,g_auto/7dc90f5536034dc2b5b0ada9001f525e_9366/Forum_Low_GY5831_01_standard.jpg",
          rightText:
            "มีเชือกผูกรองเท้าและสายรัดหนามเตย, 25% ของชิ้นส่วนที่ใช้ผลิตอัปเปอร์มีวัสดุรีไซเคิลเป็นส่วนประกอบอย่างน้อย 50%, อัปเปอร์ทำจากหนัง, สี: Cloud White / Shadow Navy / Cloud White",
          leftText: "Price : 36,00",
          active: false,
          price: 3600,
        },

        {
          name: "Adidas ULTRABOOST 22",
          imageurl:
            "https://assets.adidas.com/images/h_840,f_auto,q_auto:sensitive,fl_lossy,c_fill,g_auto/382b894cb4b348af8e8cadf900a2683b_9366/ULTRABOOST_22_GX5497_01_standard.jpg",
          rightText:
            "ยามของคำว่าดีที่สุดไม่เคยหยุดรอ และยังคงพัฒนาไปข้างหน้าอย่างต่อเนื่อง ในช่วงเวลาที่เปิดตัวรองเท้าอาดิดาส Ultraboost คู่แรก รองเท้ารุ่นนี้ได้กลายมาเป็นรองเท้าวิ่งที่ดีที่สุดเท่าที่เราเคยมีมา โดยเราได้ยกระดับความสบายและการตอบสนองให้ดียิ่งขึ้นในแต่ละครั้งที่พัฒนารุ่นใหม่ออกมา รองเท้าเวอร์ชันนี้มาพร้อมกับระบบ Linear Energy Point ที่จะช่วยให้คุณก้าวไปข้างหน้าพร้อมกับแรงส่งที่มากขึ้นในทุกย่างก้าว",
          leftText: "Price : 7,000",
          active: false,
          price: 7000,
        },

        {
          name: "Adidas SUPERSTAR",
          imageurl:
            "https://assets.adidas.com/images/h_840,f_auto,q_auto:sensitive,fl_lossy,c_fill,g_auto/3bef0134411b44be9cb8ada4005ade0b_9366/Superstar_GY0995_01_standard.jpg",
          rightText:
            "รองเท้าอาดิดาส Superstar เปิดตัวครั้งแรกในสนามบาสเกตบอล แต่ใช้เวลาไม่นานก่อนจะไปโลดแล่นในวงการฮิปฮอป และสวมใส่โดยผู้คนทั่วโลก ทั้งยังยืนหยัดอย่างมั่นคงมายาวนานกว่าห้าทศวรรษหลังจากนั้น และรองเท้าคู่นี้ก็พร้อมแล้วที่จะมาสั่นสะเทือนวงการ มาพร้อมสีสันที่ตัดกันอย่างโดดเด่นฉีกออกจากสีของดีไซน์ต้นฉบับเพื่อเติมพลังใหม่ ๆ ให้กับสไตล์คลาสสิก แต่ยังคงองค์ประกอบจากอดีตเอาไว้ไม่ว่าจะเป็นอัปเปอร์หนังหรือส่วนปกป้องนิ้วเท้าที่ดูเหมือนกับรองเท้าต้นฉบับจากยุค 70",
          leftText: "Price : 4,300",
          active: false,
          price: 4300,
        },

        {
          name: "Adidas ADIZERO BOSTON 10",
          imageurl:
            "https://assets.adidas.com/images/h_840,f_auto,q_auto:sensitive,fl_lossy,c_fill,g_auto/8b05bce744e54840b16ead1d00b48bfe_9366/Adizero_Boston_10_H67513_01_standard.jpg",
          rightText:
            "เพื่อความแกร่งของร่างกาย เพื่อความรู้สึกปลอดโปร่ง เพื่อสถิติใหม่ของตัวเอง ไม่ว่าจะวิ่งด้วยเหตุผลใด รองเท้า Adizero Boston 10 จะช่วยพิชิตที่สุดแห่งความเร็วได้ในแบบของคุณ พื้นชั้นกลางผสานเทคโนโลยี Lightstrike เข้ากับ Lightstrike Pro จึงทำให้รับแรงกระแทกได้มากกว่ารองเท้าวิ่งมาราธอนทั่วไป สัมผัสได้ถึงความคล่องตัวจากเทคโนโลยี ENERGYRODS ผลลัพธ์ที่ได้คือการตอบสนองอย่างดีเยี่ยมในทุกย่างก้าวที่จะทำให้วิ่งได้ไวเหมือนวันแข่งทุกครั้งที่สวมใส่รองเท้าคู่นี้",
          leftText: "Price :5500",
          active: false,
          price: 5500,
        },
        {
          name: "Adidas ADILETTE SHOWER",
          imageurl:
            "https://assets.adidas.com/images/h_840,f_auto,q_auto:sensitive,fl_lossy,c_fill,g_auto/354dd9e8cd944537827dadf80104e464_9366/Adilette_Shower_GZ3778_01_standard.jpg",
          rightText:
            "	ไม่ว่าจะอยู่ริมสระ ในห้องอาบน้ำ หรือบนโซฟา รองเท้าแตะคู่นี้รังสรรค์มาเพื่อการใช้ชีวิตแบบสุดเหวี่ยงทั้งทำงานและพักผ่อน มาในทรงสลิปออนที่ให้ความกระชับพอดี สวมและถอดง่ายได้ตามต้องการ ส่วนรับแรงกระแทกน้ำหนักเบาจะช่วยโอบรับเท้าด้วยความสบายตลอดวัน เติมเต็มลุคในสไตล์ Adilette ที่เป็นไอคอนด้วยโลโก้ adidas Badge of Sport",
          leftText: "Price : 1000",
          active: false,
          price: 1000,
        },
        {
          name: "Adidas DURAMO SL 2.0",
          imageurl:
            "https://assets.adidas.com/images/h_840,f_auto,q_auto:sensitive,fl_lossy,c_fill,g_auto/3e642d42742a484aa9b3ad6a00b266ca_9366/Duramo_SL_2.0_GW8345_01_standard.jpg",
          rightText:
            "ไม่ว่าจะเข้ายิมช่วงเช้า ออกไปทำธุระระหว่างวัน หรือนัดเจอเพื่อนยามเย็น รองเท้าอาดิดาสคู่นี้จะทำให้สไตล์ของคุณดูเป๊ะและเท้าของคุณรู้สึกถึงความสบาย สวมใส่คู่กับกางเกงวิ่งขาสั้นตัวโปรดเพื่อสร้างสรรค์ให้เกิดเป็นที่สุดของลุคสปอร์ตแบบลำลอง อัปเปอร์ผ้าตาข่ายจะช่วยให้เท้ารู้สึกเย็นสบาย ส่วนรับแรงกระแทกที่เบาเป็นพิเศษจะช่วยโอบประคองเท้าในทุกย่างก้าว",
          leftText: "Price : 2300",
          active: false,
          price: 2300,
        },  
        {
          name: "Adidas QUESTAR",
          imageurl:
            "https://assets.adidas.com/images/h_840,f_auto,q_auto:sensitive,fl_lossy,c_fill,g_auto/eea47a4d299341cbb9b7ad6b010f2043_9366/Questar_GZ0632_01_standard.jpg",
          rightText:
            "เมื่อได้หยิบรองเท้าอาดิดาสคู่นี้มาสวมแล้วผูกเชือกให้แน่น วันไหน ๆ ก็เหมาะสำหรับการวิ่ง ขอบล็อคข้อเท้าบุนุ่มจะมอบความกระชับมั่นคง ส่วนรับแรงกระแทกน้ำหนักเบาใต้ฝ่าเท้าจะมอบความยืดหยุ่นที่มากขึ้นเพื่อความสบายในทุกย่างก้าวตั้งแต่จังหวะลงส้นเท้าไปจนถึงยกปลายเท้าเหนือพื้น",
          leftText: "Price : 3000",
          active: false,
          price: 3000,


        }

      ],
    };
  },
  methods: {
    selected: function (i) {
      i.active = !i.active;
    },
    total: function () {
      var sum = 0;
      this.productlist.forEach(function (i) {
        if (i.active) {
          sum += i.price;
        }
      });
      return sum;
    },
  },
};
</script>

<style>
h2 {
  color: white;
}
</style>
