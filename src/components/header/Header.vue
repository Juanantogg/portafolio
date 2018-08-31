<template lang='pug'>
  .header.min-height(:class='{"header-top": header === -1}')
    Navigation

    .container
      img.avatar(src="@/assets/images/avatar.jpg")
      h1.title Juan A. García
      h2.subtitle Desarrollador Web

      .skill
        span {{ oneSkill }}
        span.cursor(ref='cursor')
      ArrowDown(@moveToDown='changeToAbout')
        slot Sobre mí
</template>

<script>
import Navigation from './Header-Navigation'
import ArrowDown from '@/components/global/ArrowDown'

export default {
  name: 'Header',
  components: {
    Navigation,
    ArrowDown
  },
  data () {
    return {
      oneSkill: '',
      skills: [
        { skill: 'HTML', subtags: ['pug'] },
        { skill: 'CSS', subtags: ['Sass', 'Bootstrap'] },
        { skill: 'JavaScript', subtags: ['Gulp', 'Vue.js', 'React.js'] },
        { skill: 'Node.js', subtags: ['Express'] },
        { skill: 'PHP', subtags: ['Laravel'] },
        { skill: 'WordPress' },
        { skill: 'Bases de datos', subtags: ['MySQL', 'MongoDB'] },
        { skill: 'Linux' }
      ],
      values: ['Compromiso', 'Responsabilidad', 'Conocimiento']
    }
  },
  methods: {
    showSkill () {
      let currentSkill = 0
      let currentLetter = 0

      let intervalChangeSkill = () => {
        this.$refs.cursor.style.animationDuration = '.5s'

        let intervalAddLetter = setInterval(() => {
          this.oneSkill += this.skills[currentSkill].skill[currentLetter]
          currentLetter++

          if (this.skills[currentSkill].skill.length === currentLetter) {
            clearInterval(intervalAddLetter)
            currentLetter = 0
            currentSkill++

            setTimeout(() => {
              this.$refs.cursor.style.animationDuration = '.2s'

              let intervalRemoveLetter = setInterval(() => {
                this.oneSkill = this.oneSkill.slice(0, this.oneSkill.length - 1)

                if (this.oneSkill.length === 0) {
                  this.$refs.cursor.style.animationDuration = '.5s'
                  clearInterval(intervalRemoveLetter)
                  setTimeout(() => {
                    intervalChangeSkill()
                  }, 3000)
                }
              }, 200)
            }, 5000)
          }

          if (currentSkill === 7) currentSkill = 0
        }, 500)
      }

      intervalChangeSkill()
    },
    changeToAbout () {
      this.$emit('showAbout', 'about')
    }
  },
  mounted () {
    setTimeout(() => {
      this.showSkill()
    }, 2000)
  },
  props: ['header']
}
</script>

<style lang='scss' scoped>
.header {
  background-color: #000;
  color: #FFF;
  position: absolute;
  top: 0;
  z-index: 1;
}
.header-top {
  top: -100vh;
}
.container {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  position: relative;
  h2 {
    font-family: 'Roboto';
  }
}
.avatar {
  display: block;
  border-radius: 50%;
  border: 5px solid white;
  margin: 0 auto 16px;
}
.title, {
  text-align: center;
  font-size: 3em;
  width: 100%;
  span {
    text-align: center;
    display: none;
  }
}
.subtitle {
  text-align: center;
}
.skill {
  margin-top: 16px;
  display: flex;
  justify-content: center;
  font-size: 1.2em;
}
.cursor {
  display: inline-block;
  width: 2px;
  height: 23px;
  margin-left: 4px;
  background-color: #fff;
  animation-name: cursor;
  animation-duration: .5s;
  animation-iteration-count: infinite;
}

@keyframes cursor {
  0% {
    background-color: #fff;
  }
  100% {
    background-color: transparent;
  }
}
</style>
