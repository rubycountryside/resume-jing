<template>
    <div id="show-resume">
        <div id="resume_content" class="resume-content">
            <section class="section-left">
                <div>
                    <div class="myImg">
                        <img src="../../assets/yujing.png" alt="">
                    </div>
                    <h3>{{resumeData.head.name}}</h3>
                    <h4>求职意向:{{resumeData.head.intention}}</h4></br>
                    <p><i class="icon-phone icon-2x"></i>&nbsp;{{resumeData.head.tel}}</p>
                    <p><i class="icon-envelope-alt icon-2x"></i>&nbsp;{{resumeData.head.email}}</p>
                    <p><i class="icon-map-marker icon-2x"></i>&nbsp;{{resumeData.head.address}}</p>
                </div>
                </br>

                <div class="edu">
                    <h3><span class="item-title">教育背景</span></h3>
                    <p>{{resumeData.head.school}} ({{resumeData.head.graduation}})</p>
                    <p>{{resumeData.head.graduationTime}}</p>
                    <p>专业:{{resumeData.head.major}}</p>
                    <h3>荣获</h3>
                    <p v-for="item in resumeData.head.honor.split('、')">{{item}}</p>
                </div>
                <div class="interest">
                    <h3><span class="item-title">兴趣爱好</span></h3>
                    <p><span class="inte-span" v-for="item in resumeData.head.interest.split('、')">{{item}}</span></p>
                </div>
                <div class="skill">
                    <h3><span class="item-title">技能特长</span></h3>
                    <div class="sk" v-for="(item,index) in resumeData.head.speciality.split('、')">{{item}}
                        <div class="sk-wrap">
                            <span class="sk-per" :style="{width:resumeData.head.specialityPer.split('、')[index]+'%'}"></span>
                        </div>
                    </div>
                </div>
            </section>
            <section class="section-right">
                <div class="blog-box clearfix">
                    <div class="blog">
                        <div class="title-name">BLOG LINK</div>
                        <div class="link personal-blog"><i class="icon-flag icon-1x"></i>技术博文 <a target="_blank" href="https://rubycountryside.github.io/">{{resumeData.blogLink.blog}}</a></div>
                        <div class="link github"><i class="icon-github-alt icon-1x"></i>Github: <a target="_blank" href="https://github.com/rubycountryside">{{resumeData.blogLink.github}}</a></div>
                    </div>
                </div>
                
                <div class="experience project-experience">
                    <div class="title">
                        <div class="title-name">项目经验</div>
                        <div class="title-date">{{resumeData.projectExperience.time}}</div>
                    </div>
                    <div class="show" v-for="item in resumeData.projectExperience.experience">
                        <div class="item" v-if="item.name">
                            <div class="item-title">
                                <span class="item-name">{{item.name}}</span>
                                <span class="item-date">{{item.time}}</span>
                            </div>
                            <ul>
                                <li v-for="des in item.describe" v-if="des!=''">{{des}}</li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div class="experience skill-experience">
                    <div class="title">
                        <div class="title-name">专业技能</div>
                    </div>
                    <div class="show" v-for="item in resumeData.skill">
                        <div class="item"  v-if="item.type">
                            <div class="item-title">
                                <span class="item-name">{{item.type}}</span>
                            </div>
                            <ul>
                                <li v-for="des in item.describe">{{des}}</li>
                            </ul>
                        </div>
                    </div>
                </div>
                <div class="experience self-evaluation">
                    <div class="title">
                        <div class="title-name">自我评价</div>
                    </div>
                    <p class="eval-detail" v-for="item in resumeData.selfAssessment">{{item}}</p>
                </div>
            </section>
        </div>
        <div v-html="resStyleCode"></div>
    </div>
</template>

<script>
    export default{
        data(){
            return{
                msg:'hello vue',
                ttc:80,
                resStyleCode:"",
                pfdSize:{
                    width:"",
                    height:""
                }
            }
        },
        props:{
            resumeData:{
                type:Object
            }
        },
        methods:{
            responseStyleCode: function (code) {
                this.resStyleCode = "<style>"+code+"</style>"
            }
        },
        components:{

        }
    }
</script>

<style scoped>
    #show-resume{
        float: left;
        width: 60%;
        height: 120%;
        background: #fff;
        padding: 1rem 2rem;
        overflow: auto;
        box-sizing: border-box;
    }
    .resume-content{
        width: 100%;
        height: 100%;
        box-shadow: 0 4px 12px 0 rgba(0,0,0,0.5);
        overflow: auto;
    }
    .resume-content::-webkit-scrollbar {
         display: none;
     }
     .myImg {
        width: 100px;
        height: 100px;
        border-radius: 50%;
        border: 1px solid #000;
        margin:9% auto;
     }
     .myImg img {
        width: 100px;
        height: 100px;
     }
     .clearfix::before, .clearfix::after{
        content: " ";
        display: table;
    }
    .clearfix::after {
        clear: both;
    }
    .clearfix {
        *zoom: 1;
    }
    .icon-2x {
        color:#fff;
    }
</style>
