<template>
    <div class="index-wrapper">
        <div class="topic-wrapper animated" ref="wrapper">
            <div class="pipe-one bg-cover-all"></div>
            <div class="pipe-two bg-cover-all"></div>
            <div class="pipe-three bg-cover-all"></div>
            <div class="pipe-four bg-cover-all"></div>
            <div class="logo bg-cover-all"></div>
            <div class="gear-one bg-cover-all"></div>
            <div class="gear-two bg-cover-all"></div>
            <div class="map-box">
                <div class="title bg-cover-all"></div>
                <div class="content bg-cover-all">
                    <div class="map-wrap">
                        <img src="../../assets/map.jpg" preview="0" rel="preload" href="./img/map.jpg" as="image">
                    </div>
                </div>
            </div>
            <div class="activity-box">
                <div class="title bg-cover-all"></div>
                <div class="content-box">
                    <div class="help bg-cover-all">
                        <div class="photo-box flex-center animated swing infinite ">
                            <img src="../../assets/avatar_help.png">
                        </div>
                        <div class="text-box flex-center">
                            想知道重邮校园的秘密？ 想和学长学姐零距离接触？ 热心的学长学姐都在这里，他们是重邮小百科，为你答疑解惑！
                        </div>
                        <div class="know-more">
                            <img src="../../assets/more.png" class="more-btn" @click="handleSwitch({name: '活动', path: 'activity/help'})">
                        </div>
                    </div>
                    <div class="smile bg-cover-all">
                        <div class="photo-box flex-center animated swing infinite">
                            <img src="../../assets/avatar_smile.png">
                        </div>
                        <div class="text-box flex-center">
                            萌新你好，欢迎来鲜肉集中营报道！听说这里有好多萌新的照片，快来为你的班级注入萌新能量，美好的大学生活从认识新同学开始~
                        </div>
                        <div class="know-more">
                            <img src="../../assets/more.png" class="more-btn" @click="handleSwitch({name: '活动', path: 'activity/smile'})">
                        </div>
                    </div>
                </div>
            </div>
            <div class="similar-box">
                <div class="training">
                    <div class="title bg-cover-all"></div>
                    <div class="content bg-cover-all">
                        <div class="avatar-box flex-center">
                            <img src="../../assets/training.png" class="training animated pulse">
                        </div>
                        <div class="text-box">
                            迈着矫健的步伐，挺拔的身姿，跑道上留下他们勇往直前的足迹，重邮学子，他们像东方升起的旭日，续写着一段奋力拼搏的历史。
                        </div>
                        <div class="dots bg-cover-all"></div>
                        <div class="know-more">
                            <img class="more-btn" src="../../assets/more.png" @click="handleSwitch({name: '军训', path: 'training'})">
                        </div>
                    </div>
                </div>
                <div class="tips">
                    <div class="title bg-cover-all"></div>
                    <div class="content bg-cover-all">
                        <div class="avatar-box flex-center">
                            <img src="../../assets/tips.png" class="tips animated pulse">
                        </div>
                        <div class="text-box">
                            最常用的官方网页和微信公众号，了解学校最新动态；最完整的火车站、机场到学校的交通路线；最推荐的寝室神器和学校周边美食地图。
                        </div>
                        <div class="dots bg-cover-all"></div>
                        <div class="know-more">
                            <img class="more-btn" src="../../assets/more.png" @click="handleSwitch({name: '攻略', path: 'tips'})">
                        </div>
                    </div>
                </div>
                <div class="mien">
                    <div class="title bg-cover-all"></div>
                    <div class="content bg-cover-all">
                        <div class="avatar-box flex-center">
                            <img src="../../assets/mien.png" class="mien animated pulse">
                        </div>
                        <div class="text-box">
                            优秀教师和优秀学长学姐都在你身边，你会成为他们吗？更多精彩原创视频等你来戳！
                        </div>
                        <div class="dots bg-cover-all"></div>
                        <div class="know-more">
                            <img class="more-btn" src="../../assets/more.png" @click="handleSwitch({name: '风采', path: 'mien'})">
                        </div>
                    </div>
                </div>
                <div class="about">
                    <div class="title bg-cover-all"></div>
                    <div class="content bg-cover-all">
                        <div class="avatar-box flex-center">
                            <img src="../../assets/redrock.png" class="redrock animated pulse">
                        </div>
                        <div class="text-box" style="text-align:center;">
                            红岩网校工作站<br/> 让你看见互联网+和团队的力量
                        </div>
                        <div class="dots bg-cover-all"></div>
                        <div class="know-more">
                            <img class="more-btn" src="../../assets/more.png" @click="handleSwitch({name: '我们', path: 'about'})">
                        </div>
                    </div>
                </div>
            </div>
            <div class="qrcode-box">
                <div class="qrcode-wrap flex-between">
                    <div class="app bg-cover-all"><img class="qr-weixin bg-cover-all" src="../../assets/qr_app.png"></div>
                    <div class="weixin bg-cover-all"><img class="qr-weixin bg-cover-all" src="../../assets/qr_weixin.png"></div>
                </div>
                <div class="long-save bg-cover-all animated flash infinite"></div>
            </div>
        </div>
    </div>
</template>

<script>

export default {
  created () {
    setTimeout(() => {
      document.querySelector('.loading-box').outerHTML = ''
      var header = document.querySelector('.header .btns-box')
      header.classList.add('bounceIn')
      this.$refs.wrapper.classList.add('bounceIn')
      setTimeout(() => {
        this.$refs.wrapper.classList.remove('bounceIn')
        header.classList.remove('bounceIn')
      }, 2000)
    }, 3200)
  },
  methods: {
    handleSwitch (item) {
      this.$emit('launch', item.name)
      if (item.path === 'about') {
        window.location.href = 'http://hongyan.cqupt.edu.cn/aboutus/'
        return
      }
      this.$router.push({path: `/${item.path}`})
    },
    backtoTop () {
      var timer = null
      cancelAnimationFrame(timer)
      var startTime = +new Date()
      var b = document.body.scrollTop || document.documentElement.scrollTop
      var d = 500
      var c = b
      timer = requestAnimationFrame(function func () {
        var t = d - Math.max(0, startTime - (+new Date()) + d)
        document.documentElement.scrollTop = document.body.scrollTop = t * (-c) / d + b
        timer = requestAnimationFrame(func)
        if (t === d) {
          cancelAnimationFrame(timer)
        }
      })
    }
  },
  beforeRouteEnter (to, from, next) {
    next(vm => {
      vm.backtoTop()
    })
  }
}
</script>

<style lang="stylus" scoped>
.index-wrapper {
    height rem(3320)
    margin-top rem(50)
    position relative
    z-index 22
    .topic-wrapper {
        position relative
        width 100%
        z-index 20
        .gear-one {
            position absolute
            width rem(30)
            height rem(45)
            bottom rem(704)
            right rem(6)
            background-image url('../../assets/gear_one.png')
            z-index 6
        }
        .gear-two {
            position absolute
            width rem(30)
            height rem(40)
            bottom rem(732)
            right rem(6)
            background-image url('../../assets/gear_two.png')
            z-index 6
        }
        .pipe-one {
            position absolute
            width rem(45)
            height rem(193)
            top rem(186)
            right rem(2)
            background-image url('../../assets/pipe_one.png')
            z-index 21
        }
        .pipe-two {
            position absolute
            width rem(80)
            height rem(184)
            top rem(1586)
            left rem(5)
            background-image url('../../assets/pipe_two.png')
            z-index 22
        }
        .pipe-three {
            position absolute
            width rem(80)
            height rem(184)
            top rem(2027)
            right rem(2)
            background-image url('../../assets/pipe_three.png')
            z-index 24
        }
        .pipe-four {
            position absolute
            width rem(80)
            height rem(184)
            top rem(2468)
            left rem(5)
            background-image url('../../assets/pipe_two.png')
            z-index 26
        }
        .logo {
            position absolute
            width rem(50)
            height rem(46)
            top rem(1170)
            left rem(8)
            background-image url('../../assets/logo.png')
            z-index 24
        }
        .map-box {
            text-align center
            & > div {
                display inline-block
            }
            .title {
                width rem(120)
                height rem(48)
                background-image url('../../assets/title_map.png')
                margin-bottom rem(-20)
                margin-top rem(20)
            }
            .content {
                width rem(348)
                height rem(226)
                background-image url('../../assets/map_box.png')
                margin 0 auto
                display flex
                justify-content center
                align-items flex-end
                padding-right rem(19)
                padding-bottom rem(19)
                .map-wrap {
                    width rem(306)
                    height rem(148)
                    border rem(1.8) solid #493497
                    & > img {
                        width 100%
                        height 100%
                    }
                }
            }
        }
        .activity-box {
            text-align center
            margin-top rem(36)
            z-index 22
            position relative
            & > div {
                display inline-block
            }
            .title {
                width rem(120)
                height rem(48)
                background-image url('../../assets/title_activity.png')
            }
            .content-box {
                margin auto
                width rem(355)
                display flex
                flex-direction column
                & > div {
                    height rem(386)
                    position relative
                    .know-more {
                        position absolute
                        bottom 0
                        width 100%
                        height rem(80)
                        z-index 555
                        .more-btn {
                            width rem(110)
                            height rem(31)
                        }
                    }
                }
                & .photo-box {
                    width 100%
                    height rem(100)
                    margin-top rem(45)
                    animation-duration 10s
                    & > img {
                        width rem(130)
                        height rem(105)
                    }
                }
                .help {
                    background-image url('../../assets/help.png')
                    transform translateX(rem(7))
                    .photo-box img {
                        transform translateX(rem(-6))
                    }
                    .more-btn {
                        transform translateX(rem(-8))
                    }
                    .text-box {
                        margin 0 auto
                        width 70%
                        margin-top rem(20)
                        height rem(120)
                        font-size rem(14)
                        color #606266
                        transform translateX(rem(-2))
                        text-align left
                    }
                }
                .smile {
                    margin-top rem(16)
                    background-image url('../../assets/smile.png')
                    transform translateX(rem(-6.5))
                    .photo-box img {
                        width rem(110)
                        height rem(102)
                    }
                    .know-more {
                        z-index 555
                        bottom rem(-3)
                    }
                    .more-btn {
                        transform translateX(rem(-3))
                    }
                    .text-box {
                        margin 0 auto
                        width 68%
                        margin-top rem(20)
                        height rem(120)
                        font-size rem(14)
                        color #606266
                        transform translateX(rem(10))
                        text-align left
                    }
                }
            }
        }
        .similar-box {
            margin-top rem(30)
            display flex
            flex-direction column
            & > div {
                display inline-block
                width rem(340)
                margin auto
                transform translateX(rem(1))
                margin-top rem(28)
                &:nth-of-type(1) {
                    margin-top 0
                }
            }
            & .title {
                width rem(120)
                height rem(48)
                margin auto
                margin-bottom rem(5)
            }
            & .content {
                position relative
                text-align center
                .avatar-box {
                    width 100%
                    height rem(100)
                    padding-top rem(80)
                    & img {
                        animation-duration 3s
                        animation-iteration-count infinite
                    }
                    .training {
                        width rem(110)
                        height rem(82)
                    }
                    .tips {
                        width rem(110)
                        height rem(76)
                    }
                    .mien {
                        width rem(110)
                        height rem(71)
                    }
                    .redrock {
                        width rem(116)
                        height rem(72)
                    }
                }
                .dots {
                    position absolute
                    top 0
                    left rem(18.8)
                    transform translateY(rem(30))
                    width rem(301)
                    height rem(276)
                    background-image url('../../assets/dots.png')
                    z-index 5
                }
                .know-more {
                    position absolute
                    z-index 555
                    bottom rem(22)
                    width 100%
                    height rem(80)
                    .more-btn {
                        width rem(110)
                        height rem(31)
                    }
                }
                .text-box {
                    margin 0 auto
                    width 70%
                    margin-top rem(60)
                    transform translateX(rem(-2))
                    height rem(120)
                    text-align left 
                    font-size rem(14)
                    color #606266
                }
            }
            .training .content {
                height rem(360)
                background-image url('../../assets/left_box.png')
            }
            .tips .content {
                height rem(360)
                background-image url('../../assets/right_box.png')
            }
            .mien .content {
                height rem(360)
                background-image url('../../assets/left_box.png')
            }
            .about .content {
                height rem(360)
                background-image url('../../assets/end_box.png')
            }
            .tips {
                z-index 23
            }
            .mien {
                z-index 25
            }
            .about {
                z-index 28
            }
            .mien .title {
                background-image url('../../assets/title_mien.png')
            }
            .tips .title {
                background-image url('../../assets/title_tips.png')
            }
            .about .title {
                background-image url('../../assets/title_about.png')
            }
            .training .title {
                background-image url('../../assets/title_train.png')
            }
        }
        .qrcode-box {
            margin-top rem(60)
            & > div {
                margin auto
            }
            .qrcode-wrap {
                width rem(320)
                height rem(160)
                & > div {
                    width rem(155)
                    height rem(180)
                    position relative
                    background-image url('../../assets/qrcode_wrap.png')
                    & > img {
                        position absolute
                        top 30%
                        left 21%
                        width rem(93)
                        height rem(93)
                    }
                }
            }
            .long-save {
                margin-top rem(30)
                width rem(250)
                height rem(95)
                background-image url('../../assets/save.png')
                animation-duration 4s
            }
        }
    }
}
</style>