<template>
    <div style="overflow: hidden !important;">
        <router-view/>
        <div id="stepLine">
            <div class='progress'>
                <div class='progress_inner'>
                  <div class='progress_inner__step'>
                    <label for='step-1'>疫苗知识图谱</label>
                  </div>
                  <div class='progress_inner__step'>
                    <label for='step-2'>基本知识图谱</label>
                  </div>
                  <div class='progress_inner__step'>
                    <label for='step-3'>预防知识图谱</label>
                  </div>
                  <!-- <div class='progress_inner__step'>
                    <label for='step-4'>形式知识图谱</label>
                  </div>
                  <div class='progress_inner__step'>
                    <label for='step-5'>文献知识图谱</label>
                  </div> -->
                  <input :checked="activeMap('map1')" id='step-1' name='step' type='radio' @click="turnTo('map1')">
                  <input :checked="activeMap('map2')" id='step-2' name='step' type='radio' @click="turnTo('map2')">
                  <input :checked="activeMap('map3')" id='step-3' name='step' type='radio' @click="turnTo('map3')">
                  <input id='step-4' name='step' type='radio'>
                  <input id='step-5' name='step' type='radio'>
                  <div class='progress_inner__bar'></div>
                  <div class='progress_inner__bar--set'></div>
                  <div class='progress_inner__tabs'></div>
                  <!-- <div class='progress_inner__status'>
                    <div class='box_base'></div>
                    <div class='box_lid'></div>
                    <div class='box_ribbon'></div>
                    <div class='box_bow'>
                      <div class='box_bow__left'></div>
                      <div class='box_bow__right'></div>
                    </div>
                    <div class='box_item'></div>
                    <div class='box_tag'></div>
                    <div class='box_string'></div>
                  </div> -->
                </div>
              </div>
              
        </div>
    </div>
</template>

<script>
    export default {
        beforeCreate() {
            this.$Loading.start();
        },
        methods: {
            turnTo(msg) {
                console.log(this.$route.name);
                if (this.$route.name != msg) {
                    this.$router.push(msg)
                }
            },
            activeMap(mapName){
                if(mapName == this.$route.name){
                    return true;
                }
            }
        },
        mounted() {
            this.$Loading.finish();
        }
    }
</script>

<style scoped>
    h1 {
        text-align: center !important;
        margin-top: 40px
    }
    
    #stepLine {
        position: fixed;
        height: 10%;
        bottom: 0;
        left: 0;
        width: 100%;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_base,
    .progress_inner #step-4:checked+input+div+div+div+div>.box_base,
    .progress_inner #step-2:checked+input+input+input+div+div+div+div>.box_base,
    .progress_inner #step-3:checked+input+input+div+div+div+div>.box_base,
    .progress_inner #step-1:checked+input+input+input+input+div+div+div+div>.box_base {
        top: 50%;
        left: 0px;
        opacity: 1;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_item,
    .progress_inner #step-4:checked+input+div+div+div+div>.box_item,
    .progress_inner #step-2:checked+input+input+input+div+div+div+div>.box_item,
    .progress_inner #step-3:checked+input+input+div+div+div+div>.box_item,
    .progress_inner #step-1:checked+input+input+input+input+div+div+div+div>.box_item {
        top: -30px;
        left: 0px;
        opacity: 0;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_lid,
    .progress_inner #step-4:checked+input+div+div+div+div>.box_lid,
    .progress_inner #step-2:checked+input+input+input+div+div+div+div>.box_lid {
        top: -20px;
        left: 0px;
        opacity: 0;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_item,
    .progress_inner #step-4:checked+input+div+div+div+div>.box_item,
    .progress_inner #step-2:checked+input+input+input+div+div+div+div>.box_item {
        top: -10px;
        left: 0px;
        opacity: 1;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_item,
    .progress_inner #step-4:checked+input+div+div+div+div>.box_item,
    .progress_inner #step-3:checked+input+input+div+div+div+div>.box_item {
        top: 10px;
        left: 0px;
        opacity: 1;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_lid,
    .progress_inner #step-4:checked+input+div+div+div+div>.box_lid,
    .progress_inner #step-3:checked+input+input+div+div+div+div>.box_lid {
        top: -1px;
        left: 0px;
        opacity: 1;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_ribbon,
    .progress_inner #step-4:checked+input+div+div+div+div>.box_ribbon,
    .progress_inner #step-3:checked+input+input+div+div+div+div>.box_ribbon {
        top: 70%;
        left: 0px;
        opacity: 0;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_bow,
    .progress_inner #step-4:checked+input+div+div+div+div>.box_bow,
    .progress_inner #step-3:checked+input+input+div+div+div+div>.box_bow {
        top: 0px;
        left: 0px;
        opacity: 0;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_ribbon,
    .progress_inner #step-4:checked+input+div+div+div+div>.box_ribbon {
        top: 50%;
        left: 0px;
        opacity: 1;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_bow,
    .progress_inner #step-4:checked+input+div+div+div+div>.box_bow {
        top: -10px;
        left: 0px;
        opacity: 1;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_tag {
        top: 10px;
        left: 20px;
        opacity: 1;
    }
    
    .progress_inner #step-5:checked+div+div+div+div>.box_string {
        top: 10px;
        left: 20px;
        opacity: 1;
    }
    
    * {
        box-sizing: border-box;
    }
    
    .progress_inner__step:before,
    .progress_inner,
    .progress_inner__status .box_base,
    .progress_inner__status .box_item,
    .progress_inner__status .box_ribbon,
    .progress_inner__status .box_bow,
    .progress_inner__status .box_bow__left,
    .progress_inner__status .box_bow__right,
    .progress_inner__status .box_tag,
    .progress_inner__status .box_string {
        position: absolute;
        left: 0;
        right: 0;
        top: 50%;
        -webkit-transform: translateY(-50%);
        transform: translateY(-50%);
        margin: auto;
    }
    
    .progress_inner__bar,
    .progress_inner__bar--set {
        height: 6px;
        left: 10%;
        background: repeating-linear-gradient(45deg, #1ea4ec, #1ea4ec 4px, #1f8bc5 4px, #1f8bc5 10px);
        transition: width 800ms cubic-bezier(0.915, 0.015, 0.3, 1.005);
        border-radius: 6px;
        width: 0;
        position: relative;
        z-index: -1;
    }
    
    .progress_inner__step:before {
        width: 20px;
        height: 20px;
        color: #70afd0;
        background: white;
        line-height: 20px;
        border: 3px solid #a6cde2;
        font-size: 12px;
        top: 3px;
        border-radius: 100%;
        -webkit-transition: all .4s;
        transition: all .4s;
        cursor: pointer;
        pointer-events: none;
    }
    
    .progress_inner__step {
        width: 20%;
        font-weight: bolder;
        -webkit-transition: all .4s;
        transition: all .4s;
        float: left;
        text-align: center;
        position: relative;
    }
    
    .progress_inner__step label {
        padding-top: 40px;
        top: -20px;
        display: block;
        position: relative;
        cursor: pointer;
    }
    
    .progress_inner__step:hover {
        color: white;
    }
    
    .progress_inner__step:hover:before {
        color: white;
        background: #1ea4ec;
    }
    
    .progress_inner {
        position: absolute;
        width: 60%;
        bottom: 0;
        left: 23%;
    }
    
    .progress_inner #step-5:checked+div {
        width: 80%;
    }
    
    .progress_inner #step-5:checked+div+div+div>.tab:nth-of-type(5) {
        opacity: 1;
        top: 0;
    }
    
    .progress_inner #step-5:checked+div+div+div+div {
        right: 10%;
    }
    
    .progress_inner #step-4:checked+input+div {
        width: 60%;
    }
    
    .progress_inner #step-4:checked+input+div+div+div>.tab:nth-of-type(4) {
        opacity: 1;
        top: 0;
    }
    
    .progress_inner #step-4:checked+input+div+div+div+div {
        right: 30%;
    }
    
    .progress_inner #step-3:checked+input+input+div {
        width: 40%;
    }
    
    .progress_inner #step-3:checked+input+input+div+div+div>.tab:nth-of-type(3) {
        opacity: 1;
        top: 0;
    }
    
    .progress_inner #step-3:checked+input+input+div+div+div+div {
        right: 50%;
    }
    
    .progress_inner #step-2:checked+input+input+input+div {
        width: 20%;
    }
    
    .progress_inner #step-2:checked+input+input+input+div+div+div>.tab:nth-of-type(2) {
        opacity: 1;
        top: 0;
    }
    
    .progress_inner #step-2:checked+input+input+input+div+div+div+div {
        right: 70%;
    }
    
    .progress_inner #step-1:checked+input+input+input+input+div {
        width: 0%;
    }
    
    .progress_inner #step-1:checked+input+input+input+input+div+div+div>.tab:nth-of-type(1) {
        opacity: 1;
        top: 0;
    }
    
    .progress_inner #step-1:checked+input+input+input+input+div+div+div+div {
        right: 90%;
    }
    
    .progress_inner__step:before {
        content: "";
    }
    
    .progress_inner__bar--set {
        width: 40%;
        top: -6px;
        background: #70afd0;
        position: relative;
        z-index: -2;
    }
    
    .progress_inner__tabs .tab {
        opacity: 0;
        position: absolute;
        top: 40px;
        text-align: center;
        margin-top: 80px;
        box-shadow: 0px 2px 1px #80b7d5;
        padding: 30px;
        background: white;
        border-radius: 10px;
        -webkit-transition: all .2s;
        transition: all .2s;
    }
    
    .progress_inner__tabs .tab h1 {
        margin: 0;
    }
    
    .progress_inner__tabs .tab p {
        font-weight: 400;
        opacity: 0.8;
    }
    
    .progress_inner input[type="radio"] {
        display: none;
    }
</style>