<template>
    <div id="show-menu">
        <div class="menu-cont">
            <div class="logo"><a target="_blank" href="https://github.com/rubycountryside"><i class="icon-github icon-5x"></i></a></div>
            <div class="file" @click="fileClick">
                <i class=" icon-file-alt icon-5x"></i>
                <p class="file-des">生成简历</p>
            </div>
            <div class="download-file" @click="downloadClick">
                <i class=" icon-download-alt icon-5x"></i>
            </div>
            <transition name="fade">
            <div class="download-choice" v-show="showDownloadChoice">
                <div class="dpi96 setdpi">
                    <p>96像素/英寸</p>
                    <p>A4 794×1123</p>
                    <input type="radio" @click="choiceClick({'width':794,'height':1123})">
                </div>
                <div class="dpi120 setdpi">
                    <p>120像素/英寸</p>
                    <p>A4 1487×2105</p>
                    <input type="radio" @click="choiceClick({'width':1487,'height':2015})">
                </div>
                <div class="custom">
                    width :<input type="text" v-model="customPx.width"  placeholder="px">
                    height:<input type="text" v-model="customPx.height"  placeholder="px">
                    <span class="ok-choice" @click="choiceClick({'width':parseInt(customPx.width),'height':parseInt(customPx.height)})">down</span>
                </div>
            </div>
            </transition>
        </div>
    </div>
</template>

<script>
    export default{
        data(){
            return {
                msg: 'hello vue',
                showDownloadChoice:false,
                customPx:{
                    width:"",
                    height:""
                }
            }
        },
        created(){

        },
        methods: {
            fileClick: function () {
                this.$emit('listenShowMenu', {"type": "fileClick", "showFlag": true});
            },
            downloadClick: function () {
                this.showDownloadChoice = !this.showDownloadChoice;
            },
            choiceClick: function (size) {
                if(size.width && size.height){
                    this.$emit('listenShowMenu', {"type": "choiceClick","size":size});
                    this.showDownloadChoice = !this.showDownloadChoice;
                }
            }
        },
        components: {}
    }
</script>

<style scoped>
    @import './ShowMenu.css'
</style>
