<template>
    <div id="from_box">
        <div class="from-content">
            <div class="from-content-item">
                <div class="item">
                    <div class="item-head">个人基本资料</div>
                    <div class="item-content clearfloat">
                        <div class="inp-short">姓名:<input type="text" v-model="fromData.head.name"></div>
                        <div class="inp-short">意向:<input type="text" v-model="fromData.head.intention"></div>
                        <div class="inp-short">邮箱:<input type="text" v-model="fromData.head.email"></div>
                        <div class="inp-short">电话:<input type="text" v-model="fromData.head.tel"></div>
                        <div class="inp-short">住址:<input type="text" v-model="fromData.head.address"></div>
                        <div class="inp-short">性别:<input type="text" v-model="fromData.head.sex"></div>
                        <div class="inp-short">毕业学校:<input type="text" v-model="fromData.head.school"></div>
                        <div class="inp-short">学历:<input type="text" v-model="fromData.head.graduation"></div>
                        <div class="inp-short">毕业时间:<input type="text" v-model="fromData.head.graduationTime" placeholder="2012-9 至 2016-7"></div>
                        <div class="inp-short">专业:<input type="text" v-model="fromData.head.major" placeholder=""></div>
                        <div class="inp-short">荣获:<input type="text" v-model="fromData.head.honor" placeholder="多份殊荣顿号隔开"></div>
                        <div class="inp-short">技能特长:<input type="text" v-model="fromData.head.speciality" placeholder="顿号隔开"></div>
                        <div class="inp-short">技能特长对应分数:<input type="text" v-model="fromData.head.specialityPer" placeholder="顿号隔开 如 80、90"></div>
                        <div class="inp-short">兴趣爱好:<input type="text" v-model="fromData.head.interest" placeholder="逗号隔开"></div>
                    </div>
                    <div class="item-footer"><i></i>&nbsp;&nbsp;&nbsp;</div>
                </div>
                <div class="item">
                    <div class="item-head">技术链接</div>
                    <div class="item-content">
                        <div class="inp-long">GitHub:<input type="text" placeholder="选填" v-model="fromData.blogLink.github"></div>
                        <div class="inp-long">技术博文:<input type="text" placeholder="选填" v-model="fromData.blogLink.blog"></div>
                    </div>
                    <div class="item-footer"><i></i>&nbsp;&nbsp;&nbsp;</div>
                </div>
                <div class="item">
                    <div class="item-head">
                        <span>工作经验</span>
                        <span class="item-head-time">时间:<input type="text" placeholder="2001-2 至 今" v-model="fromData.workExperience.time"></span>
                    </div>
                    <div class="item-content" v-if="workExperienceFlag>=0">
                        <div class="contt clearfloat">
                            <div class="inp-short">项目名称:<input type="text" placeholder="" v-model="fromData.workExperience.experience[0].name"></div>
                            <div class="inp-short">项目技术:<input type="text" placeholder="" v-model="fromData.workExperience.experience[0].skill"></div>
                            <div class="inp-short">项目时间:<input type="text" placeholder="2001-2 至 今" v-model="fromData.workExperience.experience[0].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">项目简介:
                            <input type="text" placeholder="1、" v-model="fromData.workExperience.experience[0].describe[0]" >
                            <input type="text" placeholder="2、" v-model="fromData.workExperience.experience[0].describe[1]">
                            <input type="text" placeholder="3、" v-model="fromData.workExperience.experience[0].describe[2]">
                        </div>
                    </div>
                    <div class="item-content" v-if="workExperienceFlag>=1">
                        <div class="contt clearfloat">
                            <div class="inp-short">项目名称:<input type="text" placeholder="" v-model="fromData.workExperience.experience[1].name"></div>
                            <div class="inp-short">项目技术:<input type="text" placeholder="" v-model="fromData.workExperience.experience[1].skill"></div>
                            <div class="inp-short">项目时间:<input type="text" placeholder="2001-2 至 今" v-model="fromData.workExperience.experience[1].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">项目简介:
                            <input type="text" placeholder="1、" v-model="fromData.workExperience.experience[1].describe[0]" >
                            <input type="text" placeholder="2、" v-model="fromData.workExperience.experience[1].describe[1]">
                            <input type="text" placeholder="3、" v-model="fromData.workExperience.experience[1].describe[2]">
                        </div>
                    </div>
                    <div class="item-content" v-if="workExperienceFlag>=2">
                        <div class="contt clearfloat">
                            <div class="inp-short">项目名称:<input type="text" placeholder="" v-model="fromData.workExperience.experience[2].name"></div>
                            <div class="inp-short">项目技术:<input type="text" placeholder="" v-model="fromData.workExperience.experience[2].skill"></div>
                            <div class="inp-short">项目时间:<input type="text" placeholder="2001-2 至 今" v-model="fromData.workExperience.experience[2].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">项目简介:
                            <input type="text" placeholder="1、" v-model="fromData.workExperience.experience[2].describe[0]" >
                            <input type="text" placeholder="2、" v-model="fromData.workExperience.experience[2].describe[1]">
                            <input type="text" placeholder="3、" v-model="fromData.workExperience.experience[2].describe[2]">
                        </div>
                    </div>
                    <div class="item-footer"><i class=" icon-plus-sign-alt icon-1x" @click="workIconClick" v-show="workExperienceFlag<2"></i>&nbsp;&nbsp;&nbsp;</div>
                </div>
                <div class="item">
                    <div class="item-head">
                        <span>项目经验</span>
                        <span class="item-head-time">时间:<input type="text" placeholder="2001-2 至 今" v-model="fromData.projectExperience.time"></span>
                    </div>
                    <div class="item-content" v-if="projectExperienceFlag>=0">
                        <div class="contt clearfloat">
                            <div class="inp-short">项目名称:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[0].name"></div>
                            <div class="inp-short">项目技术:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[0].skill"></div>
                            <div class="inp-short">项目时间:<input type="text" placeholder="2001-2 至 今" v-model="fromData.projectExperience.experience[0].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">项目简介:
                            <input type="text" placeholder="1、" v-model="fromData.projectExperience.experience[0].describe[0]">
                            <input type="text" placeholder="2、" v-model="fromData.projectExperience.experience[0].describe[1]">
                            <input type="text" placeholder="3、" v-model="fromData.projectExperience.experience[0].describe[2]">
                        </div>
                    </div>
                    <div class="item-content" v-if="projectExperienceFlag>=1">
                        <div class="contt clearfloat">
                            <div class="inp-short">项目名称:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[1].name"></div>
                            <div class="inp-short">项目技术:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[1].skill"></div>
                            <div class="inp-short">项目时间:<input type="text" placeholder="2001-2 至 今" v-model="fromData.projectExperience.experience[1].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">项目简介:
                            <input type="text" placeholder="1、" v-model="fromData.projectExperience.experience[1].describe[0]">
                            <input type="text" placeholder="2、" v-model="fromData.projectExperience.experience[1].describe[1]">
                            <input type="text" placeholder="3、" v-model="fromData.projectExperience.experience[1].describe[2]">
                        </div>
                    </div>
                    <div class="item-content" v-if="projectExperienceFlag>=2">
                        <div class="contt clearfloat">
                            <div class="inp-short">项目名称:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[2].name"></div>
                            <div class="inp-short">项目技术:<input type="text" placeholder="" v-model="fromData.projectExperience.experience[2].skill"></div>
                            <div class="inp-short">项目时间:<input type="text" placeholder="2001-2 至 今" v-model="fromData.projectExperience.experience[2].time"></div>
                        </div>
                        <div class="inp-long inp-long-more">项目简介:
                            <input type="text" placeholder="1、" v-model="fromData.projectExperience.experience[2].describe[0]">
                            <input type="text" placeholder="2、" v-model="fromData.projectExperience.experience[2].describe[1]">
                            <input type="text" placeholder="3、" v-model="fromData.projectExperience.experience[2].describe[2]">
                        </div>
                    </div>
                    <div class="item-footer"><i class=" icon-plus-sign-alt icon-1x" @click="pojIconClick" v-show="projectExperienceFlag<2"></i>&nbsp;&nbsp;&nbsp;</div>
                </div>

                <div class="item">
                    <div class="item-head">掌握技能</div>
                    <div class="item-content" v-if="skillFlag>=0">
                        <div class="contt clearfloat">
                            <div class="inp-short">技能分类:<input type="text" placeholder="" v-model="fromData.skill[0].type"></div>
                        </div>
                        <div class="inp-long inp-long-more">简介:
                            <input type="text" placeholder="1、" v-model="fromData.skill[0].describe[0]">
                            <input type="text" placeholder="2、" v-model="fromData.skill[0].describe[1]">
                            <input type="text" placeholder="3、" v-model="fromData.skill[0].describe[2]">
                        </div>
                    </div>
                    <div class="item-content" v-if="skillFlag>=1">
                        <div class="contt clearfloat">
                            <div class="inp-short">技能分类:<input type="text" placeholder="" v-model="fromData.skill[1].type"></div>
                        </div>
                        <div class="inp-long inp-long-more">简介:
                            <input type="text" placeholder="1、" v-model="fromData.skill[1].describe[0]">
                            <input type="text" placeholder="2、" v-model="fromData.skill[1].describe[1]">
                            <input type="text" placeholder="3、" v-model="fromData.skill[1].describe[2]">
                        </div>
                    </div>
                    <div class="item-content" v-if="skillFlag>=2">
                        <div class="contt clearfloat">
                            <div class="inp-short">技能分类:<input type="text" placeholder="" v-model="fromData.skill[2].type"></div>
                        </div>
                        <div class="inp-long inp-long-more">简介:
                            <input type="text" placeholder="1、" v-model="fromData.skill[2].describe[0]">
                            <input type="text" placeholder="2、" v-model="fromData.skill[2].describe[1]">
                            <input type="text" placeholder="3、" v-model="fromData.skill[2].describe[2]">
                        </div>
                    </div>
                    <div class="item-footer"><i class=" icon-plus-sign-alt icon-1x" @click="skillIconClick" v-show="skillFlag<2"></i>&nbsp;&nbsp;&nbsp;</div>
                </div>

                <div class="item last-item">
                    <div class="item-head">自我评价</div>
                    <div class="item-content">
                        <div class="inp-long inp-long-more">评价:
                            <input type="text" placeholder="1、" v-model="fromData.selfAssessment[0]">
                            <input type="text" placeholder="2、" v-model="fromData.selfAssessment[1]">
                            <input type="text" placeholder="3、" v-model="fromData.selfAssessment[2]">
                        </div>
                    </div>
                    <div class="item-footer"><i class=" icon-plus-sign-alt icon-1x"></i>&nbsp;&nbsp;&nbsp;</div>
                </div>
            </div>
            <div class="xs"></div>
            <div class="xs2"></div>
            <div class="from-box-footer">
                <span class="butt" @click="createResClick">生成简历</span>
            </div>
        </div>
     </div>
</template>

<script>
    export default{
        data(){
            return {
                msg: 'hello vue',
                workExperienceFlag:0,
                projectExperienceFlag:0,
                skillFlag:0,
                fromData:{
                    "head":{
                        "name":"",
                        "intention":"",
                        "tel":"",
                        "email":"",
                        "address":"",
                        "age":"",
                        "sex":"",
                        "school":"",
                        "graduationTime":"",
                        "graduation":"",
                        "major":"",
                        "honor":"",
                        "interest":"",
                        "speciality":"",
                        "specialityPer":""
                    },
                    "blogLink":{
                        "github":"",
                        "blog":""
                    },
                    "workExperience":{
                        "time":"",
                        "experience":[
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    //"","",""
                                ]
                            },
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    //"","",""
                                ]
                            },
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    "","",""
                                ]
                            }
                        ]
                    },
                    "projectExperience":{
                        "time":"",
                        "experience":[
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    "","",""
                                ]
                            },
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    "","",""
                                ]
                            },
                            {
                                "name":"",
                                "skill":"",
                                "time":"",
                                "describe":[
                                    "","",""
                                ]
                            }
                        ]
                    },
                    "skill":[
                        {
                            "type":"",
                            "describe":[
                                "","",""
                            ]
                        },
                        {
                            "type":"",
                            "describe":[
                                "","",""
                            ]
                        },
                        {
                            "type":"",
                            "describe":[
                                "","",""
                            ]
                        }
                    ],
                    "selfAssessment":[
                        "","",""
                    ]
                }
            }
        },
        props:{
            resumeData:{
                type:Object
            }
        },
        created(){
//            console.log(this.resumeData);
            if(this.resumeData.formFlag){
                this.fromData = this.resumeData
            }
        },
        watch:{
            "fromData": {
                handler: function (val, oldVal) {
                    // 表单信息上传给 App.vue
                    this.$emit('listenFormList',{type:"fromData","fromData":this.fromData});
                },
                deep:true
            }
        },
        methods:{
            createResClick: function () {
                this.$emit('listenFormList',{type:"createResClick","showFlag":false});
            },
            workIconClick: function () {
                this.workExperienceFlag++;
            },
            pojIconClick: function () {
                this.projectExperienceFlag++;
            },
            skillIconClick: function () {
                this.skillFlag++;
            }
        },
        components: {}
    }
</script>

<style>
   @import './FormList.css';
</style>
