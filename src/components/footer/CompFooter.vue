<template>
    <footer class="footer">
        <div class="text-box">
            <ul class="nav">
                <li v-for="(item, index) in items" :key="index" @click="jump(item)">{{item.text}}</li>
            </ul>
            <div class="rules">
                <p>本网站由红岩网校工作站负责开发，管理，</p>
                <p>不经红岩网校委员会书面同意，不得进行转载</p>
                <p>地址：重庆市南岸区崇文路2号（重庆邮电大学内）</p>
                <p>400065 E-mail :redrock@cqupt.edu.cn (023-62461084)</p>
            </div>
        </div>
        <div class="bg-footer bg-cover-all"></div>
    </footer>
</template>

<script>

export default {
  data () {
    return {
      items: [
        {
          text: '关于红岩网校 |',
          link: 'http://hongyan.cqupt.edu.cn/aboutus/'
        },
        {
          text: ' 网站地图 |',
          link: 'map'
        },
        {
          text: ' 指出错误 |',
          link: 'mailto:web@redrock.team'
        },
        {
          text: ' 管理入口',
          link: ''
        }
      ]
    }
  },
  methods: {
    jump (item) {
      if (item.link !== '' && item.link !== 'map') {
        window.location.href = item.link
      }
      if (item.link === 'map') {
        if (this.$route.path === '/index') {
          this.backtoTop()
        } else {
          this.$emit('launch', '首页')
          this.$router.push({ path: '/index' })
        }
      }
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
  }
}
</script>

<style lang="stylus" scoped>
.footer {
    position relative
    z-index 20
    margin-top rem(60)
    .text-box {
        text-align center
        margin-bottom rem(10)
        .nav {
            display flex
            justify-content center
            color #fff
            font-size rem(13)
            & > li {
                margin-left rem(4)
            }
            margin-bottom rem(6)
        }
        .rules {
            & > p {
                text-align center
                height rem(20)
                line-height rem(20)
                color #fff
                font-size rem(10)
                letter-spacing .5px
            }   
        }
    }
    .bg-footer {
        width 100%
        height rem(65)
        background-image url('../../assets/footer.png')
    }
}
</style>