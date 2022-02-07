<script setup >
import ItemCard from './item-card.vue'
import { computed, ref } from 'vue';

const items = [
  {
    name: "Model 3",
    category: "Tesla",
    price: "48,490",
    date: "2020-09-04",
    imgUrl: "https://media.istockphoto.com/photos/electric-sports-car-the-tesla-model-3-picture-id1277254968?k=6&m=1277254968&s=612x612&w=0&h=4j3WhZQD95BJyqOnML2sDatX9SFQomJclLyd5bbV3FU="
  },

  {
    name: "Model X",
    category: "Tesla",
    price: "89,990",
    date: "2017-08-08",
    imgUrl: "https://media.istockphoto.com/photos/tesla-model-x-travelling-on-the-freeway-in-silicon-valley-picture-id1191552504?k=6&m=1191552504&s=612x612&w=0&h=NWHap01jKkYzC5BT-9gaKYr8phGeO1ZUYHnGPLQ5RUM="
  },

  {
    name: "Model S",
    category: "Tesla",
    price: "82,990",
    date: "2019-04-01",
    imgUrl: "https://media.istockphoto.com/photos/tesla-model-s-on-the-highway-picture-id582261244?k=6&m=582261244&s=612x612&w=0&h=LwYAD7oI6Xy9gsRM7OZ10Nsq-ehGsSmLcbPwQEmZBpg="
  },

  {
    name: "Model Y",
    category: "Tesla",
    price: "48,190",
    date: "2020-02-02",
    imgUrl: "https://media.istockphoto.com/photos/tesla-model-y-in-austin-texas-at-360-bridge-picture-id1272025387?k=6&m=1272025387&s=612x612&w=0&h=o_W18f-pFNdHsSpdaNejXSS7G8XnWfayhinzZVWhQU8="
  },

  {
    name: "Cayenne",
    category: "Porsche",
    price: "67,500",
    date: "2017-12-20",
    imgUrl: "https://media.istockphoto.com/photos/porsche-cayenne-picture-id1138819485?k=6&m=1138819485&s=612x612&w=0&h=uSPCZUofVb5ComBHUpH5qZ5QB7B1WWcKFxNzm53W2ME="

  },

  {
    name: "Macan",
    category: "Porsche",
    price: "52,100",
    date: "2019-07-12",
    imgUrl: "https://media.istockphoto.com/photos/porsche-macan-gts-crossover-suv-picture-id508107322?k=6&m=508107322&s=612x612&w=0&h=syLuqvZng-mEbqJblhY3q6wWxcUlaijknWO9ea90CJo="

  },

  {
    name: "Camry",
    category: "Toyota",
    price: "24,425",
    date: "2015-06-29",
    imgUrl: "https://media.istockphoto.com/photos/toyota-camry-in-motion-picture-id905266220?k=6&m=905266220&s=612x612&w=0&h=8iRQyhjJYVn_ppC6x3LTLGzG0P67NyCvuQqxvO40ryI="

  },

  {
    name: "Accord",
    category: "Honda",
    price: "24,800",
    date: "2018-10-02",
    imgUrl: "https://media.istockphoto.com/photos/honda-accord-in-the-city-picture-id649004692?k=6&m=649004692&s=612x612&w=0&h=7WnRBZcLQ6-Y2FrKKVxya3nwJ6U-CLeZUuk-D5RVlu8="

  },

  {
    name: "Civic",
    category: "Honda",
    price: "20,650",
    date: "2015-04-04",
    imgUrl: "https://media.istockphoto.com/photos/new-honda-civic-front-picture-id458119929?k=6&m=458119929&s=612x612&w=0&h=h8uh7Bqgw2l1Hhg2TmX05VSBnp2cxrjpTBtvPYpKiD4="

  },
  {
    name: "CX-5",
    category: "Mazda",
    price: "26,940",
    date: "2012-11-03",
    imgUrl: "https://media.istockphoto.com/photos/new-2018-mazda-cx5-red-cx5-suv-car-japanese-car-moving-vehicle-picture-id1069236296?k=6&m=1069236296&s=612x612&w=0&h=CO2YJA51esFD2an-sKkhusVifvwTwhBXR3ebxD6h3Fg="

  },
  {
    name: "GLE Coupe",
    category: "Mercedes-Benz",
    price: "76,500",
    date: "2020-02-05",
    imgUrl: "https://media.istockphoto.com/photos/mercedesbenz-gle-43-4matic-coupe-picture-id894961460?k=6&m=894961460&s=612x612&w=0&h=aKbMi31eXuJOSVEKlesIzsJlLM6QhUe0k_5V-FJvH0M="

  },
  {
    name: "CLA",
    category: "Mercedes-Benz",
    price: "37,850",
    date: "2019-06-09",
    imgUrl: "https://media.istockphoto.com/photos/mercedes-benz-cla-picture-id472122163?k=6&m=472122163&s=612x612&w=0&h=IIRhsoWfMXXy6b_aTMtSA2dgSTPK4pSD-_M5vh8OY6M="

  },
  {
    name: "GLA 250",
    category: "Mercedes-Benz",
    price: "37,280",
    date: "2017-05-02",
    imgUrl: "https://media.istockphoto.com/photos/mercedesbenz-gla-2020-test-drive-day-picture-id1297389811?k=6&m=1297389811&s=612x612&w=0&h=NOPBUppwL9aFKKoha3phbhpHUw6hYSdsW5NlFejp4RU="

  },
  {
    name: "RX 350",
    category: "Lexus",
    price: "45,175",
    date: "2015-01-01",
    imgUrl: "https://media.istockphoto.com/photos/hybrid-suv-lexus-nx-on-the-road-picture-id657915058?k=6&m=657915058&s=612x612&w=0&h=DGCgfv-pBE75oOUktrX_WpGSadnEmRcm5iPfa49BOQw="

  },
  {
    name: "NX 300",
    category: "Lexus",
    price: "37,510",
    date: "2018-09-12",
    imgUrl: "https://media.istockphoto.com/photos/lexus-nx-200t-car-picture-id480681192?k=6&m=480681192&s=612x612&w=0&h=Ne9_r4aioLH_jpiK41fHpTr-ADdKsHcFMOOPXT9DGp8="

  },
  {
    name: "Urus",
    category: "Lamborghini",
    price: "218,000",
    date: "2021-08-16",
    imgUrl: "https://media.istockphoto.com/photos/lamborghini-urus-picture-id1184360237?k=6&m=1184360237&s=612x612&w=0&h=cDC3bjJCG9fZC8VpJnuoK73du-hKLnij-14eKHxuLyA="

  },
  {
    name: "Aventador",
    category: "Lamborghini",
    price: "393,695",
    date: "2020-09-11",
    imgUrl: "https://media.istockphoto.com/photos/lamborghini-aventador-lp-7504-superveloce-picture-id1083962000?k=6&m=1083962000&s=612x612&w=0&h=VBYRfp0408ZHqDTdJ69pIJP7z_zhj2T7z8OB-28adSU="

  },
  {
    name: "A3",
    category: "Audi",
    price: "33,500",
    date: "2019-05-08",
    imgUrl: "https://media.istockphoto.com/photos/audi-a3-sportback-on-a-street-picture-id1255388367?k=6&m=1255388367&s=612x612&w=0&h=nh2TLu9W-68-3_PgN1-0qkXYaw4mfFZviKY1sY_fjJ8="

  },
  {
    name: "X3",
    category: "BMW",
    price: "43,000",
    date: "2018-03-11",
    imgUrl: "https://media.istockphoto.com/photos/-picture-id1206921084?k=6&m=1206921084&s=612x612&w=0&h=o8ETeAQHAuzOerMorNWxPnDpyhSyrxiy6vvIQ8TLd4Y="

  },
  {
    name: "2 Series",
    category: "BMW",
    price: "37,500",
    date: "2019-01-15",
    imgUrl: "https://media.istockphoto.com/photos/coupe-competition-picture-id1187329409?k=6&m=1187329409&s=612x612&w=0&h=qDHLX8yA8WVGmEwFU8k56z72uobZfcGkHH14zzpLPc4="
  },
];
const defaultOrder =JSON.parse(JSON.stringify(items))
let selected = ref("Category");
let sorted = ref("Sort by");
// const categoryFilteringAndSorting = computed(() => {
//   if(sorted.value == 1) console.log("jlkfds");
//   else if(sorted.value == 2) console.log("jlkfds")
//   else if(sorted.value == 3) .sort((a, b) => new Date(a.created) - new Date(b.created));


//   if(selected.value == "Category") return items;
//   else return items.filter((item) => item.category === selected.value);

// } );

const categoryFilteringAndSorting = computed(() => {
  // let temp = filtering(items);
  // return sorting(temp);
  return filtering(sorting(items));

});

const filtering = (items) => {
  if (selected.value == "Category") return items;
  else return items.filter((item) => item.category === selected.value);
}

const sorting = (items) => {
  if (sorted.value == "1") {
      return items.sort(function(a, b) {
      return parseFloat(a.price.replace(/,/g, '')) - parseFloat(b.price.replace(/,/g, ''));
      });
  }
  else if (sorted.value == "2"){
      return items.sort(function(a, b) {
      return parseFloat(b.price.replace(/,/g, '')) - parseFloat(a.price.replace(/,/g, ''));
      });
  }
  else if (sorted.value == "3") return items.sort((a, b) => new Date(b.date) - new Date(a.date))
  else{
    return defaultOrder;
  }
}













</script>
<template>
  <div class="container mt-5">
    <div class="d-flex">
      <div class="mx-2">
        <select class="form-select" v-model="selected" aria-label="Default select example">
          <option selected value="Category">Category</option>
          <option value="Tesla">Tesla</option>
          <option value="Porsche">Porsche</option>
          <option value="Toyota">Toyota</option>
          <option value="Honda">Honda</option>
          <option value="Mazda">Mazda</option>
          <option value="Mercedes-Benz">Mercedes-Benz</option>
          <option value="Lexus">Lexus</option>
          <option value="Lamborghini">Lamborghini</option>
          <option value="Audi">Audi</option>
          <option value="BMW">BMW</option>
        </select>
      </div>

      <div>
        <select class="form-select" v-model="sorted" aria-label="Default select example">
          <option selected value="Sort by">Sort by:</option>
          <option value="1">Price: Low to High</option>
          <option value="2">Price: High to Low</option>
          <option value="3">Newest Arrivals</option>
        </select>
      </div>
    </div>

    <div class="d-flex flex-wrap pt-4">
      <ItemCard
        v-for="item in categoryFilteringAndSorting"
        :key="item.name"
        :item="{ name: item.name, category: item.category, price: item.price, date: item.date, imgUrl: item.imgUrl }"
      ></ItemCard>
    </div>
  </div>
</template>


    <!-- <div class="d-flex flex-wrap pt-4">
      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/electric-sports-car-the-tesla-model-3-picture-id1277254968?k=6&m=1277254968&s=612x612&w=0&h=4j3WhZQD95BJyqOnML2sDatX9SFQomJclLyd5bbV3FU="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">Model 3</h5>
          <p class="card-text">Category: Tesla</p>
          <p class="card-text">Price: $48,490</p>
          <p class="card-text">Date: 2020-09-04</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/tesla-model-x-travelling-on-the-freeway-in-silicon-valley-picture-id1191552504?k=6&m=1191552504&s=612x612&w=0&h=NWHap01jKkYzC5BT-9gaKYr8phGeO1ZUYHnGPLQ5RUM="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">Model X</h5>
          <p class="card-text">Category: Tesla</p>
          <p class="card-text">Price: $89,990</p>
          <p class="card-text">Date: 2017-08-08</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/tesla-model-s-on-the-highway-picture-id582261244?k=6&m=582261244&s=612x612&w=0&h=LwYAD7oI6Xy9gsRM7OZ10Nsq-ehGsSmLcbPwQEmZBpg="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">Model S</h5>
          <p class="card-text">Category: Tesla</p>
          <p class="card-text">Price: $82,990</p>
          <p class="card-text">Date: 2019-04-01</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/tesla-model-y-in-austin-texas-at-360-bridge-picture-id1272025387?k=6&m=1272025387&s=612x612&w=0&h=o_W18f-pFNdHsSpdaNejXSS7G8XnWfayhinzZVWhQU8="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">Model Y</h5>
          <p class="card-text">Category: Tesla</p>
          <p class="card-text">Price: $48,190</p>
          <p class="card-text">Date: 2020-02-02</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/porsche-cayenne-picture-id1138819485?k=6&m=1138819485&s=612x612&w=0&h=uSPCZUofVb5ComBHUpH5qZ5QB7B1WWcKFxNzm53W2ME="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">Cayenne</h5>
          <p class="card-text">Category: Porsche</p>
          <p class="card-text">Price: $67,500</p>
          <p class="card-text">Date: 2017-12-20</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/porsche-macan-gts-crossover-suv-picture-id508107322?k=6&m=508107322&s=612x612&w=0&h=syLuqvZng-mEbqJblhY3q6wWxcUlaijknWO9ea90CJo="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">Macan</h5>
          <p class="card-text">Category: Porsche</p>
          <p class="card-text">Price: $52,100</p>
          <p class="card-text">Date: 2019-07-12</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/toyota-camry-in-motion-picture-id905266220?k=6&m=905266220&s=612x612&w=0&h=8iRQyhjJYVn_ppC6x3LTLGzG0P67NyCvuQqxvO40ryI="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">Camry</h5>
          <p class="card-text">Category: Toyota</p>
          <p class="card-text">Price: $24,425</p>
          <p class="card-text">Date: 2015-06-29</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/honda-accord-in-the-city-picture-id649004692?k=6&m=649004692&s=612x612&w=0&h=7WnRBZcLQ6-Y2FrKKVxya3nwJ6U-CLeZUuk-D5RVlu8="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">Accord</h5>
          <p class="card-text">Category: Honda</p>
          <p class="card-text">Price: $24,800</p>
          <p class="card-text">Date: 2018-10-02</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/new-honda-civic-front-picture-id458119929?k=6&m=458119929&s=612x612&w=0&h=h8uh7Bqgw2l1Hhg2TmX05VSBnp2cxrjpTBtvPYpKiD4="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">Civic</h5>
          <p class="card-text">Category: Honda</p>
          <p class="card-text">Price: $20,650</p>
          <p class="card-text">Date: 2015-04-04</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/new-2018-mazda-cx5-red-cx5-suv-car-japanese-car-moving-vehicle-picture-id1069236296?k=6&m=1069236296&s=612x612&w=0&h=CO2YJA51esFD2an-sKkhusVifvwTwhBXR3ebxD6h3Fg="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">CX-5</h5>
          <p class="card-text">Category: Mazda</p>
          <p class="card-text">Price: $26,940</p>
          <p class="card-text">Date: 2012-11-03</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/mercedesbenz-gle-43-4matic-coupe-picture-id894961460?k=6&m=894961460&s=612x612&w=0&h=aKbMi31eXuJOSVEKlesIzsJlLM6QhUe0k_5V-FJvH0M="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">GLE Coupe</h5>
          <p class="card-text">Category: Mercedes-Benz</p>
          <p class="card-text">Price: $76,500</p>
          <p class="card-text">Date: 2020-02-05</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/mercedes-benz-cla-picture-id472122163?k=6&m=472122163&s=612x612&w=0&h=IIRhsoWfMXXy6b_aTMtSA2dgSTPK4pSD-_M5vh8OY6M="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">CLA</h5>
          <p class="card-text">Category: Mercedes-Benz</p>
          <p class="card-text">Price: $37,850</p>
          <p class="card-text">Date: 2019-06-09</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/mercedesbenz-gla-2020-test-drive-day-picture-id1297389811?k=6&m=1297389811&s=612x612&w=0&h=NOPBUppwL9aFKKoha3phbhpHUw6hYSdsW5NlFejp4RU="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">GLA 250</h5>
          <p class="card-text">Category: Mercedes-Benz</p>
          <p class="card-text">Price: $37,280</p>
          <p class="card-text">Date: 2017-05-02</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/hybrid-suv-lexus-nx-on-the-road-picture-id657915058?k=6&m=657915058&s=612x612&w=0&h=DGCgfv-pBE75oOUktrX_WpGSadnEmRcm5iPfa49BOQw="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">RX 350</h5>
          <p class="card-text">Category: Lexus</p>
          <p class="card-text">Price: $45,175</p>
          <p class="card-text">Date: 2015-01-01</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/lexus-nx-200t-car-picture-id480681192?k=6&m=480681192&s=612x612&w=0&h=Ne9_r4aioLH_jpiK41fHpTr-ADdKsHcFMOOPXT9DGp8="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">NX 300</h5>
          <p class="card-text">Category: Lexus</p>
          <p class="card-text">Price: $37,510</p>
          <p class="card-text">Date: 2018-09-12</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/lamborghini-urus-picture-id1184360237?k=6&m=1184360237&s=612x612&w=0&h=cDC3bjJCG9fZC8VpJnuoK73du-hKLnij-14eKHxuLyA="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">Urus</h5>
          <p class="card-text">Category: Lamborghini</p>
          <p class="card-text">Price: $218,000</p>
          <p class="card-text">Date: 2021-08-16</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/lamborghini-aventador-lp-7504-superveloce-picture-id1083962000?k=6&m=1083962000&s=612x612&w=0&h=VBYRfp0408ZHqDTdJ69pIJP7z_zhj2T7z8OB-28adSU="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">Aventador</h5>
          <p class="card-text">Category: Lamborghini</p>
          <p class="card-text">Price: $393,695</p>
          <p class="card-text">Date: 2020-09-11</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/audi-a3-sportback-on-a-street-picture-id1255388367?k=6&m=1255388367&s=612x612&w=0&h=nh2TLu9W-68-3_PgN1-0qkXYaw4mfFZviKY1sY_fjJ8="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">A3</h5>
          <p class="card-text">Category: Audi</p>
          <p class="card-text">Price: $33,500</p>
          <p class="card-text">Date: 2019-05-08</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/-picture-id1206921084?k=6&m=1206921084&s=612x612&w=0&h=o8ETeAQHAuzOerMorNWxPnDpyhSyrxiy6vvIQ8TLd4Y="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">X3</h5>
          <p class="card-text">Category: BMW</p>
          <p class="card-text">Price: $43,000</p>
          <p class="card-text">Date: 2018-03-11</p>
        </div>
      </div>

      <div class="card m-2" style="width: 18rem">
        <div class="card-body">
          <img
            src="https://media.istockphoto.com/photos/coupe-competition-picture-id1187329409?k=6&m=1187329409&s=612x612&w=0&h=qDHLX8yA8WVGmEwFU8k56z72uobZfcGkHH14zzpLPc4="
            class="card-img-top"
            alt="..."
          />
          <h5 class="card-title pt-2">2 Series</h5>
          <p class="card-text">Category: BMW</p>
          <p class="card-text">Price: $37,500</p>
          <p class="card-text">Date: 2019-01-15</p>
        </div>
      </div>
    </div> -->



<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
