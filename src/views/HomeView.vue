<script setup lang="ts">
import PesonPartial from '@/components/partials/PersonPartial.vue'
import { ref, onMounted } from 'vue'
import { useRouter } from 'vue-router';
import PersonsCarousel from '@/components/persons_carousel.vue';
import type { Person } from '@/types/types';

const { push } = useRouter();
const youtube = ref()
const sections: any = ref([]);
let observer: any = null;
let activeSectionId = '';
onMounted(() => {
  const options = {
    root: null,
    rootMargin: '0px',
    threshold: 0.5, // Adjust this threshold as needed
  };

  observer = new IntersectionObserver(handleIntersection, options);

  sections.value = document.querySelectorAll('div[id^="section"]');

  sections.value.forEach((section: any) => {
    observer.observe(section);
  });
});
const onReady = () => {
  youtube.value.playVideo()
}

const handleIntersection = (entries: any) => {
  entries.forEach((entry: any) => {
    if (entry.isIntersecting) {
      const sectionId = entry.target.id;
      if (sectionId !== activeSectionId) {
        // Push the hash to the URL using Vue Router
        push({ hash: `#${sectionId}` });
        activeSectionId = sectionId;
      }
    }
  });
};


const persons: Person[] = [
  {
    id: 1,
    name: "شريف الليثي",
    image: "sherif.png",
    position: "مؤسس دار تويا للنشر و التوزيع",

  }
]

</script>

<template>
  <section class="marginRight py-5">

    <!-- el san3a main -->
    <div id="section1" class="p-3 flex flex-column md:flex-row justify-content-center">
      <div class="w-full md:w-12  animation-duration-1000 animation-iteration-1">
        <img src="../images/elsan3a.png" class="max-w-12rem md:max-w-16rem flex mx-auto md:mx-0 my-5 md:my-0" alt="">
        <h2 class="secondaryColor"><span class="textColor">من</span> المتحدثين بالورشة</h2>
        <div class="flex my-3">
          <div class="flex align-items-center">
            <span class="material-symbols-outlined textColor text-3xl">
              calendar_month
            </span>
            <h4 class="textColor mx-2">١٩ نوفمبر ٢٠٢٣</h4>
          </div>
          <!-- <div class="flex align-items-center mx-2">
            <span class="material-symbols-outlined mx-2 textColor text-3xl">
              timer
            </span>
            <h4 class="textColor">٩ صباحاً</h4>
          </div> -->
        </div>
        <div class="slider-text-wrapper">
          <p class="textColor w-full aligned-paragraph ">شريف الليثي، ناشر مصري رائد أسس دار تويا للنشر والتوزيع عام 2015.
            يتميز بمساهماته الفعّالة في مجالات الثقافة والأدب والفن، حيث قام بتنظيم العديد من المبادرات التي تعزز التنوع
            الثقافي وتعمل على نشر الفهم والتواصل في المجتمع. يعتبر الليثي شخصية مهمة في المجال النشري، حيث يسعى جاهداً
            لتعزيز قيم الفن والمعرفة في مصر وخارجها.

          </p>
          <p class="textColor w-full  aligned-paragraph ">
            بفضل رؤيته الرائعة وجهوده المستمرة، ينطلق شريف الليثي لتحقيق تحول هائل في عالم النشر والصناعة الثقافية. من
            خلال إطلاق "الصنعة"، يقدم الليثي منصة استثنائية توحد جميع احتياجات الصناعة تحت سقف واحد، مما يعزز التفاعل
            والتواصل بين الأفراد والمؤسسات في هذا القطاع المتنوع. بتجميع جميع قطع النشر على هذه المنصة، يفتح الليثي أفقًا
            جديدًا من التفاعل والتعاون، مما يعزز التبادل الثقافي ويسهم في نمو الصناعة. بفضل هذه المبادرة الرائدة، يمهد
            شريف الليثي الطريق لمستقبل مشرق حيث يتم تحقيق التكامل الكامل لكل جوانب الصناعة عبر منصة "الصنعة".
          </p>

        </div>

        <!-- <h2 class="w-5 my-3 cursor-pointer gredientBg text-center p-3 borderRound">سجل الآن</h2> -->
      </div>
      <PesonPartial v-for="person in persons" :key="person.id" :person="person" />

    </div>

    <div class="zoomin animation-duration-1000 animation-iteration-1" style="margin-bottom: 10vh;">
      <h2 class="textColor p-3">باقي المتحدثين</h2>
      <div class="flex scroll-container flex-nowrap md:flex-wrap w-full m-auto justifyCenter">
        <img src="../images/asmaa.png" class="flex md:hidden max-w-30rem max-h-17rem" alt="">
        <img src="../images/Group 4.png" class=" max-h-17rem" alt="">
        <img src="../images/Group 1.png" class=" max-h-17rem" alt="">
        <img src="../images/Group 2.png" class=" max-h-17rem" alt="">
        <img src="../images/Group 3.png" class=" max-h-17rem" style="margin: 0 4rem;" alt="">
      </div>
      <div class="flex flex-column text-center md:hidden py-2 px-5 borderRound" style="background-color: #D9B58D;">
        <h1 class="">أسماء الراشدي</h1>
        <h4 class="">مسئولة الشباب</h4>
      </div>
    </div>
    <!-- el san3a main end -->

    <!-- Home -->
    <div id="sectionHome1"
      class="flex justify-content-center align-items-center animation-duration-1000 animation-ease-in-out">
      <div class="flex flex-column md:flex-row my-5">
        <div class="mx-auto md:mx-5 w-11 my-5">
          <img src="../images/elsan3a.png" class="my-5 flex mx-auto md:mx-0 max-w-16rem" alt="">
          <h1 class="secondaryColor">نبذة عنا</h1>
          <div class="borderRound mb-2 mt-1 secondaryBg" style="height: 0.5rem;"></div>
          <div class="flex align-items-center">
            <div class="hidden md:flex flex-column">
              <!-- <h2 class="my-5 secondaryColor cursor-pointer">نبذه عنا</h2> -->
              <h2 class="my-5 inactiveColor cursor-pointer">الرؤية</h2>
              <h2 class="my-5 inactiveColor cursor-pointer">المهمة</h2>
              <h2 class="my-5 inactiveColor cursor-pointer">القيم</h2>
            </div>
            <h3 class="font-bold textColor my-3 mx-2 md:mx-5">
              الصنعة هي مبادرة تعليمية تهدف إلى تدريب وتطوير مهارات الحرفيين في مختلف المجالات والصناعات اليدوية. تتميز
              هذه الورشة بمشاركة عدد كبير من الخبراء والمحترفين المتميزين في مجالات متنوعة، مما يسهم في تقديم تجارب وخبرات
              متنوعة وقيمة للمشاركين.
              يتم تنظيم ورشة الصنعة بشكل دوري أو عند الطلب، وتشمل مجموعة واسعة من المواضيع مثل النجارة، والخياطة، والفنون
              التقليدية، والحرف اليدوية المتنوعة مثل الخزف، النحت، النسيج، والأعمال الحرفية الأخرى.<br><br>

              باختصار، تُعد "الصنعة" بيئة تعليمية مثالية لتنمية وتطوير مهارات الحرفيين وصقل مواهبهم من خلال تجارب عملية
              وتوجيهات خبراء متميزين في مجالاتهم.
            </h3>
          </div>
        </div>
        <div class="flex scroll-container mx-auto md:mx-5 md:flex-column" style="max-width: 90vw;">
          <img src="../images/homePage1.png" class="max-w-14rem mx-3 md:mx-1 my-3" alt="">
          <img src="../images/homePage2.png" class="max-w-14rem mx-3 md:mx-1 my-3" alt="">
        </div>
      </div>
    </div>
  </section>

  <!-- Video Viewer -->
  <section id="sectionHome2" v-animateonscroll="{ enterClass: 'fadein', leaveClass: 'fadeout' }"
    class="flex justify-content-center align-items-center animation-duration-1000 animation-ease-in-out">
    <div class="videoViewerBg py-5">
      <h1 class="secondaryColor text-7xl text-center">اعرف تويا</h1>
      <p class="text-center primaryColor">دار النشر "تويا" تعد إحدى الدور النشر البارزة في مصر</p>
      <div class="flex w-10 justify-content-center my-5 m-auto" style="max-width: 300px !important;">
        <YouTube src="https://www.youtube.com/watch?v=9MD4lRBusQw" @ready="onReady" ref="youtube" />
      </div>
      <p class="w-10 md:w-8 text-center m-auto textColor font-bold">دار النشر "تويا" تعد إحدى الدور النشر البارزة في مصر
        والتي حظيت بشهرة واسعة بفضل تعزيزها للمحتوى الثقافي والعلمي من خلال نشر الكتب والأوراق البحثية. تمتاز دار النشر
        "تويا" بتقديم مجموعة متنوعة وغنية من الإصدارات التي تغطي مختلف المجالات الثقافية والعلمية.
        تمثلت أهمية دار النشر "تويا" في دورها الكبير في إثراء المكتبات والمجتمع القرائي المصري والعربي عمومًا، من خلال نشر
        الكتب التي تتنوع بين الأدب الكلاسيكي والحديث، والكتب العلمية والفلسفية، والأبحاث الأكاديمية.</p>
    </div>
  </section>

  <section id="sectionHome3" v-animateonscroll="{ enterClass: 'fadein', leaveClass: 'fadeout' }"
    class="flex justify-content-center align-items-center animation-duration-1000 animation-ease-in-out marginRight py-5 my-5">
    <div class="flex flex-column md:flex-row">
      <div>
        <h1 class="secondaryColor text-5xl md:text-7xl p-5">و كان رأيهم عننا...</h1>
        <h1 class="textColor w-10 px-5">“من افضل دور النشر اللي اتعاملنا معاها. حرفية في المعاملة و مواعيد مظبوطة. شكراً
          تويا”</h1>
        <h1 class="secondaryColor my-3 px-5">سلمي طارق</h1>
        <h3 class="px-5 textColor">كاتبة و مؤلفة</h3>
      </div>
      <img src="../images/asmaaB&W.png" class="maxWidth" alt="">
    </div>
  </section>

  <section id="sectionHome4" v-animateonscroll="{ enterClass: 'zoomin', leaveClass: 'fadeout' }"
    class="flex justify-content-center align-items-center animation-duration-1000 animation-ease-in-out marginRight py-5 my-5">
    <div class="p-5">
      <h1 class="primaryColor text-5xl my-3 md:my-0 md:text-7xl">شاركونا نجاحنا</h1>
      <p class="textColor textCenter w-12 md:w-10">هتتبنى دار النشر "تويا" استراتيجية نشر تتميز بالجودة والتنوع، حيث
        تسعى لاختيار المواضيع المتميزة والمؤلفين المبدعين والمتخصصين في مجالاتهم. بالإضافة
        إلى ذلك، تساهم في دعم الأبحاث العلمية والمقالات ذات الصلة بالمجتمع الأكاديمي والعلمي.<br>
        من خلال الكتب التي نشرتها والأوراق البحثية التي دعمتها، استطاعت دار النشر "تويا" أن تلعب دورًا
        هامًا في نشر المعرفة والثقافة والتحفيز على القراءة والتفكير النقدي في مصر. تجدر الإشارة إلى أن الدور
        الإعلامي الكبير الذي حققته دار النشر "تويا" يعكس تأثيرها وأهميتها في الساحة الثقافية والعلمية في مصر.
      </p>
      <div class="flex flex-wrap justify-content-center my-5 align-items-center">
        <img src="../images/VirginLogo.png" class="max-w-8rem my-3 md:max-w-12rem mx-2 md:mx-5" alt="">
        <img src="../images/booksClub.png" class="max-w-6rem my-3 md:max-w-12rem mx-2 md:mx-5" alt="">
        <img src="../images/hayden-booksLogo.png" class="max-w-5rem my-3 md:max-w-7rem mx-2 md:mx-5" alt="">
        <img src="../images/warner-booksLogo.png" class="max-w-7rem my-3 md:max-w-12rem mx-2 md:mx-5" alt="">
      </div>
    </div>
  </section>
</template>
<!-- <script lang="ts">
import { defineComponent } from 'vue'
import YouTube from 'vue3-youtube'

export default defineComponent({
    components: { YouTube },
    methods: {
        onReady() {
            this.$refs.youtube.playVideo()
        },
    },
})
</script> -->
<style>
.videoViewerBg {
  background-color: rgb(16, 18, 20);
}

.inactiveColor {
  color: #5B5044;
}

.justifyCenter {
  justify-content: center;
}

.gredientBg {
  background: linear-gradient(to bottom, rgb(217, 181, 141) 0%, rgb(203, 203, 203) 100%);
}

.marginRight {
  margin-right: 10rem;
}

.maxWidth {
  max-width: 33rem;
}

@media screen and (max-width : 600px) {
  .marginRight {
    margin-right: 0;
  }

  .justifyCenter {
    justify-content: start;
  }

  iframe {
    width: 360px !important;
  }

  .maxWidth {
    max-width: 18rem;
  }

  .textCenter {
    text-align: center;
  }

  .scroll-container {
    overflow-x: auto !important;
    /* Enable horizontal scrolling */
    -webkit-overflow-scrolling: touch !important;
    /* Enable smooth scrolling on iOS devices */
    scrollbar-width: none !important;
    /* Hide scrollbar for modern browsers */
    -ms-overflow-style: none !important;
    /* Hide scrollbar for IE and Edge */
    white-space: nowrap !important;
    /* Prevent content from wrapping */
    max-width: 95%;
  }
}
</style>
