<template>
    <div id="mainBody" :style="{height:this.$store.state.thisWindowHeight+'px'}">
        <div class="list-panel" ref="listPanel">
            <router-link :to="{name:'messageDisplay',params:{userId:'5309190090'}}" tag="div">
                <div class="row-panel">
                    <div class="item-subscript-panel">

                    </div>
                    <div class="item-avatar-panel">
                        <img :src="groupMsgImg" alt="用户头像">
                    </div>
                    <div class="item-nickname-panel">
                        <p class="title">掘金摸鱼群</p>
                        <p class="subtitle">暂无消息</p>
                    </div>
                    <div class="item-time-panel">
                        <!--<p>下午10:22</p>
                        <div class="msg-count-panel msg-count-more-panel">
                            <p></p>
                        </div>-->
                    </div>
                </div>
            </router-link>
        </div>
        <div class="content-panel" ref="contentPanel">
            <!--公用组件(消息展示)-->
            <router-view name="messageDisplay"/>
        </div>
    </div>
</template>

<script>
    export default {
        name: "msg-list",
        mounted() {
            if(this.getThisWindowWidth()<500){
                // 手机端打开
                this.$refs.listPanel.style.display = "none";
                this.$refs.contentPanel.style.width = "100%";
            }
        },
        methods: {
            getThisWindowWidth:()=>window.innerWidth,
        },
        data(){
            return{
                msgSubscriptIco:require("../assets/img/msg-subscript.png"),
                avatarIco:require("../assets/img/avatar-ico.png"),
                groupMsgImg:require("../assets/img/group-msg-img.png"),
                GroupBlocked:require("../assets/img/Group_Blocked@2x.png"),
                otherMsgImg:require("../assets/img/other-msg-img.jpg")
            }
        }
    }
</script>

<style lang="scss" scoped src="../assets/scss/msg-list.scss"></style>
