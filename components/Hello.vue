<template>
  <q-layout
    ref="layout"
    view="lHh Lpr fff"
    :left-class="{'bg-grey-2': true}"
  >
    <q-toolbar slot="header" class="bg-light">
<!--
      <q-btn
        flat
        @click="$refs.layout.toggleLeft()"
      >
        <q-icon name="menu" />
      </q-btn>
-->

      <q-toolbar-title>
     <a href="http://selectcomtelecom.ca/for-home/">  <img src="http://selectcomtelecom.ca/for-home/assets/img/logo-selectcomtelecom.png" class="logo"></a>
        <h5 class="center sub">Find out How Much Internet Speed You Need</h5>
      </q-toolbar-title>
    </q-toolbar>

<!--    <div slot="left">-->
      <!--
        Use <q-side-link> component
        instead of <q-item> for
        internal vue-router navigation
      -->
       

<!--
      <q-list no-border link inset-delimiter>
        <q-list-header>Essential Links</q-list-header>
        <q-item @click="launch('http://quasar-framework.org')">
          <q-item-side icon="school" />
          <q-item-main label="Docs" sublabel="quasar-framework.org" />
        </q-item>
        <q-item @click="launch('http://forum.quasar-framework.org')">
          <q-item-side icon="record_voice_over" />
          <q-item-main label="Forum" sublabel="forum.quasar-framework.org" />
        </q-item>
        <q-item @click="launch('https://gitter.im/quasarframework/Lobby')">
          <q-item-side icon="chat" />
          <q-item-main label="Gitter Channel" sublabel="Quasar Lobby" />
        </q-item>
        <q-item @click="launch('https://twitter.com/quasarframework')">
          <q-item-side icon="rss feed" />
          <q-item-main label="Twitter" sublabel="@quasarframework" />
        </q-item>
      </q-list>
    </div>
-->

    <!--
      Replace following <div> with
      <router-view /> component
      if using subRoutes
    -->
    <div class="layout-padding center">
        <div class="row">
        <div class="col-sm-12 col-md-8 offset-md-2">
      <q-progress :percentage="progress" stripe animate color="positive" />
    </div>
    </div>
    </div>
<!--
             <div class="left" v-if="progress >= 28 && progress <= 98">
          <q-btn  outline rounded color="amber-10" small @click="goback()" class="left">   <q-icon name="arrow_back" /> </q-btn>
          </div>
-->
      <div class="layout-lesspadding center ">
        <div v-if="progress == 14" >
            <h4 >{{questions[0].question}}</h4> 
            <h6 >{{questions[0].sub}}</h6>
            <img v-if="progress == 14" :src="questions[0].link"> <br>
            <q-btn rounded color="amber-10" large v-for="a in questions[0].buttons" :key="a.value" @click="answer(a.value)"> {{ a.buttonname }} </q-btn>
        </div>
        <div v-if="progress == 28" >

            <h4 >{{questions[1].question}}</h4> 
            <h6 >{{questions[1].sub}}</h6>
            <img :src="questions[1].link"> <br>
            <q-btn rounded color="amber-10" large v-for="a in questions[1].buttons" :key="a.value" @click="answer(a.value)"> {{ a.buttonname }} </q-btn>

        </div> 
        <div v-if="progress == 42" >
<!--
                  <div class="left">
          <q-btn  outline rounded color="amber-10" small @click="goback()" class="left">   <q-icon name="arrow_back" /> </q-btn>
          </div>
-->
            <h4 >{{questions[2].question}}</h4> 
            <h6 >{{questions[2].sub}}</h6>
            <img :src="questions[2].link"> <br>
            <q-btn rounded color="amber-10" large v-for="a in questions[2].buttons" :key="a.value" @click="answer(a.value)"> {{ a.buttonname }} </q-btn>
        </div>     
        <div v-if="progress == 56" >      
<!--
            <div class="left">
          <q-btn  outline rounded color="amber-10" small @click="goback()" class="left">   <q-icon name="arrow_back" /> </q-btn>
          </div>
-->
            <h4 >{{questions[3].question}}</h4> 
            <h6 >{{questions[3].sub}}</h6>
            <img :src="questions[3].link"> <br>
            <q-btn rounded color="amber-10" large v-for="a in questions[3].buttons" :key="a.value" @click="answer(a.value)"> {{ a.buttonname }} </q-btn>
        </div>
        <div v-if="progress == 70" >
<!--
            <div class="left">
          <q-btn  outline rounded color="amber-10" small @click="goback()" class="left">   <q-icon name="arrow_back" /> </q-btn>
          </div>
-->
            <h4 >{{questions[4].question}}</h4> 
            <h6 >{{questions[4].sub}}</h6>
            <img :src="questions[4].link"> <br>
            <q-btn rounded color="amber-10" large v-for="a in questions[4].buttons" :key="a.value" @click="answer(a.value)"> {{ a.buttonname }} </q-btn>
        </div>      
        <div v-if="progress == 84" >
<!--
            <div class="left">
          <q-btn  outline rounded color="amber-10" small @click="goback()" class="left">   <q-icon name="arrow_back" /> </q-btn>
          </div>
-->
            <h4 >{{questions[5].question}}</h4> 
            <h6 >{{questions[5].sub}}</h6>
            <img :src="questions[5].link"> <br>
            <q-btn rounded color="amber-10" large v-for="a in questions[5].buttons" :key="a.value" @click="answer(a.value)"> {{ a.buttonname }} </q-btn>
        </div>      
        <div v-if="progress == 98" >
            <h4 >{{questions[6].question}}</h4> 
            <h6 >{{questions[6].sub}}</h6>
            <img :src="questions[6].link"> <br>
            <q-btn rounded color="amber-10" large v-for="a in questions[6].buttons" :key="a.value" @click="answer(a.value)"> {{ a.buttonname }} </q-btn>
        </div>        
       <div v-if="progress <= 98" >
        <h5>Recommended Internet Speed:</h5><h4> <span class="speed-result green"> {{speed}} </span> MBPS </h4>
    </div>
         <div v-if="progress > 98" >
<q-transition group enter="zoomIn">
             
              <img src="http://selectcomtelecom.ca/for-home/assets/img/result.svg"> <br>
             <h4> Internet Speed Recommended for You: </h4>
             <h4 style="line-height:30px"> <span class="speed-result green"> {{label}} </span> MBPS , <sup class="green">$</sup><span class="speed-result green">{{package}}<sup style="font-size:25px">.95</sup></span><span class="mo green">/mo.</span> </h4>   
             
             <div class="row">
 
  <div class="col-sm-12 col-md-6 offset-md-3">

             
<!--             <h4>Choose Your Package</h4>-->
             
      <q-slider v-model="snap" :min="0" :max="8" :step="2" :label-value="`${label}MBPS `" markers color="amber-10" /> 
      
      
<div class="q-slider non-selectable text-amber-10 mb-50">
    <div class="q-slider-handle-container">
        <div class="q-slider-track" style="display:none"></div>
        <div class="q-slider-mark" style="left: 0%; width: 0;opacity: 1; width: 20%;opacity: 1;background: none;"><div class="tag">15 MBPS </div></div>
        <div class="q-slider-mark" style="left: 25%; width: 0;opacity: 1; width: 20%;opacity: 1;background: none;"><div class="tag">30 MBPS </div></div>
        <div class="q-slider-mark" style="left: 50%; width: 0;opacity: 1; width: 20%;opacity: 1;background: none;"><div class="tag">60 MBPS </div></div>
        <div class="q-slider-mark" style="left: 75%; width: 0;opacity: 1; width: 20%;opacity: 1;background: none;"><div class="tag">120 MBPS </div></div>
        <div class="q-slider-mark" style="left: 100%; width: 0;opacity: 1; width: 20%;opacity: 1;background: none;"><div class="tag">200 MBPS </div></div>
        <div class="q-slider-track active-track" style="display:none"></div>
            <div class="q-slider-ring"></div>
        </div>
    </div>
</div>
</div>
                          <q-btn outline color="amber-10" small class="fixed-width-final q-btn-final"  @click="startover()">Start Over</q-btn>
             <a href="http://selectcomtelecom.ca/for-home/unlimited-internet" target="_blank"> <q-btn color="amber-10" small class="fixed-width-final q-btn-final">More Packages</q-btn></a>
             <a href="http://selectcomtelecom.ca/for-home/sign-up"> <q-btn outline color="amber-10" small class="fixed-width-final q-btn-final">Sign Up</q-btn></a>

             
             
           </q-transition> 
        </div>
          
          
     
             </div>
 

  </q-layout>
</template>

<script>
    import {
        dom,
        event,
        openURL,
        QLayout,
        QToolbar,
        QToolbarTitle,
        QBtn,
        QIcon,
        QList,
        QListHeader,
        QItem,
        QItemSide,
        QItemMain,
        QProgress,
        QSlider,
        QChip,
        QField
    } from 'quasar'

    export default {
        name: 'index',
        components: {
            QLayout,
            QToolbar,
            QToolbarTitle,
            QBtn,
            QIcon,
            QList,
            QListHeader,
            QItem,
            QItemSide,
            QItemMain,
            QProgress,
            QSlider,
            QChip,
             QField
        },
        data() {
            return {
                progress: 14,
                standard: 20,
                precision: 0.4,
                step: 30,
                snap: 0,
                questions: [
                    {
                        
                    'question': 'How many devices in your home are connected to the internet?',
                    'sub': '(Computers, smartphones, tablets, gaming consoles, smart TVs, smart home devices, etc.)',
                    'link': 'http://selectcomtelecom.ca/for-home/assets/img/devices.svg',
                    'buttons': [{
                            'buttonname': '1-3',
                            'value': 5
                        },
                        {
                            'buttonname': '4-7',
                            'value': 5
                        },
                        {
                            'buttonname': '8-10',
                            'value': 5
                        },
                        {
                            'buttonname': '10+',
                            'value': 5
                        }
                    ],
               

                    },                    
                    
                    {
                    'question': 'How many people use the internet at your home?',
                    'sub': '',
                    'link': 'http://selectcomtelecom.ca/for-home/assets/img/people.svg',
                    'buttons': [{
                            'buttonname': '1-2',
                            'value': 5
                        },
                        {
                            'buttonname': '3-4',
                            'value': 10
                        },
                        {
                            'buttonname': '4+',
                            'value': 20
                        }
        
                    ],

                    },
                    
                    {
                    'question': 'How often does your household use video chat or make internet phone calls?',
                    'sub': '(Skype, Vonage, Google Hangouts, FaceTime, etc.)',
                    'link': 'http://selectcomtelecom.ca/for-home/assets/img/calls.svg',
                    'buttons': [{
                            'buttonname': 'Rarely',
                            'value': 0
                        },
                        {
                            'buttonname': 'Weekly',
                            'value': 5
                        },
                        {
                            'buttonname': 'Daily',
                            'value': 5
                        }
        
                    ],

                    },               
                    
                    {
                    'question': 'How often does your household stream audio?',
                    'sub': '(Spotify, Pandora, Amazon Echo or Alexa, Google Home, etc.)',
                    'link': 'http://selectcomtelecom.ca/for-home/assets/img/music.svg',
                    'buttons': [{
                            'buttonname': 'Rarely',
                            'value': 0
                        },
                        {
                            'buttonname': 'Weekly',
                            'value': 5
                        },
                        {
                            'buttonname': 'Daily',
                            'value': 5
                        }
        
                    ],

                    },                 
                    
                    {
                    'question': 'How often does your household play online video games?',
                    'sub': '(Call of Duty, Battlefield, World of Warcraft, League of Legends, etc.)',
                    'link': 'http://selectcomtelecom.ca/for-home/assets/img/games.svg',
                    'buttons': [{
                            'buttonname': 'Rarely',
                            'value': 0
                        },
                        {
                            'buttonname': 'Weekly',
                            'value': 5
                        },
                        {
                            'buttonname': 'Daily',
                            'value': 10
                        }
        
                    ],

                    },                   
                    
                    {
                    'question': 'How often does your household watch TV or movies online?',
                    'sub': '(Netflix, Hulu, Amazon Prime, Roku, etc.)',
                    'link': 'http://selectcomtelecom.ca/for-home/assets/img/tv.svg',
                    'buttons': [{
                            'buttonname': 'Rarely',
                            'value': 0
                        },
                        {
                            'buttonname': 'Weekly',
                            'value': 5
                        },
                        {
                            'buttonname': 'Daily',
                            'value': 5
                        }
        
                    ],

                    },                    
                    
                    {
                    'question': 'How often does your household download large files?',
                    'sub': '(Torrents, databases, etc.)',
                    'link': 'http://selectcomtelecom.ca/for-home/assets/img/download.svg',
                    'buttons': [{
                            'buttonname': 'Rarely',
                            'value': 0
                        },
                        {
                            'buttonname': 'Weekly',
                            'value': 5
                        },
                        {
                            'buttonname': 'Daily',
                            'value': 10
                        }
        
                    ],
                    },
                ],
                speed: 0,
                speedvalue: 0
                
               
            }

        },
        computed: {
            
            package: function () {
                if (this.snap === 0)
                return '34'
                if (this.snap === 2)
                return '49'
                 if (this.snap === 4)
                return '59'
                 if (this.snap === 6)
                return '79'
                 if (this.snap === 8)
                return '94'
            },
            label: function () {
                if (this.snap === 0)
                return '15'
                if (this.snap === 2)
                return '30'
                 if (this.snap === 4)
                return '60'
                 if (this.snap === 6)
                return '120'
                 if (this.snap === 8)
                return '200'
            }
        },
        methods: {
            answer (addtospeed) {
                console.log(addtospeed);
                this.speedvalue = addtospeed;
                this.speed += addtospeed;
                this.progress += 14
                console.log('New Progress:', this.progress);
                if (this.progress === 112){
                    if (this.speed <= 15) {                
                    this.snap = 0
                    console.log(0)
                 }
                if (this.speed  <= 30 && this.speed > 15){ 
                    this.snap = 2
                    console.log(2)
                }
                 if (this.speed <= 60 && this.speed > 30){
                     this.snap = 4
                    console.log(4)
                 }
                 if (this.speed <= 120 && this.speed > 60){
                      this.snap = 6
                    console.log(6)
                 }
                 if (this.speed <= 200 && this.speed > 120) {                
                     this.snap = 8
                     console.log(8)
                 }
                }

                
            },
            
            startover () {
                this.speed = 0;
                this.progress = 14;
                console.log('Speed:', this.speed);
                console.log('New Progress:', this.progress);
            },
            
//            computedSnap () {
//                 console.log('HEY1', this.speed);
//                 if (this.speed === 15) {                
//                    this.snap = 0
//                    console.log(0)
//                 }
//
//                if (this.speed  === 30){ 
//                    this.snap = 2
//                    console.log(2)
//                }
//                 if (this.speed === 60){
//                     this.snap = 4
//                    console.log(4)
//                 }
//                 if (this.speed === 120)
//                 {
//                      this.snap = 6
//                    console.log(6)
//                 }
//                 if (this.speed === 200) {                
//                     this.snap = 8
//                     console.log(8)
//                 }}

            
//            goback () {
//                console.log('Addtospeed:', this.speedvalue);
//                this.speed -= this.speedvalue;
//                this.progress -= 14
//                console.log('New Progress:', this.progress);
//
//                
//            }

            
        },
        mounted() {

        },
        beforeDestroy() {

        }
    }
</script>


<style>
    
    import 'quasar-extras/animate/zoomIn.css'
    
    .ninetyfive{
        font-size: 23px!important
    }
    
    
    .green {
       color: #22b946
    }
    
    .mo {
            font-size: 20px;
    }
    
    .tag {
       text-align: center;
    font-size: 25px;
    font-family: 'Arial black';
    letter-spacing: -1.2px;;
    }
    
    .q-slider:not(.disabled):focus .q-slider-ring, .q-slider:not(.disabled):hover .q-slider-ring {
    opacity: 0;
    }

    .mb-50 {
        margin-bottom: 50px
    }
    
    
      .q-progress{
            height: 20px;
        }
    
    .layout-lesspadding{
     padding: 0 3rem;
    }
    .q-btn{ margin: 5px 20px;
     padding: 1rem 2.5rem;
    font-size: 20px;
    text-transform: none;
    }
    
     .q-btn-final{ margin: 5px 20px;
        margin: 5px 20px;
    padding: 1rem 1rem;
    font-size: 16px;
    text-transform: none;
    }
    
    .left {
        text-align: left;
        margin: 0 0 0 2rem;
        padding: 0.3rem 1.5rem;
    }
    
    img{max-width: 450px}
     
    .center {text-align: center}
     
    h1, h2, h3, h4, h5, h6 {
/*        font-family: 'Raleway', sans-serif*/
        font-weight: 300
    }
    .speed-result {
font-size: 40px;
    font-weight: 600;
        font-family: arial black;
        letter-spacing: -2px;
    }
    .fixed-width {
        width: 350px
    }
    
    .fixed-width-final {
        width: 200px
    }
    .logo {
        max-height: 40px
    }
    .q-toolbar{
        color: black;
    }
    .sub {
        white-space: normal
    }
    
    @media only screen and (max-width: 768px) {
        h4 {
            font-size: 20px;
        }
        h5 {
            font-size: 16px;
        }
            .q-btn{ margin: 5px 20px;
     padding: 0.5rem 2rem;
    }
        .fixed-width {
    width: 250px;
    font-size: 14px;
}
        .q-progress{
            height: 3px;
        }
        
            .tag {

    font-size: 13px;

    }
        .q-btn {
font-size: 14px;
    width: 150px;
    padding: 12px 0;
}
        
        
        .speed-result {
    font-size: 34px;
    }
    }
/*iphone 5 specifically*/
    @media only screen 
and (min-device-width : 320px) 
and (max-device-width : 568px) {
   .layout-lesspadding{
     padding: 1rem 1rem!important;
    }
    }
    
</style>