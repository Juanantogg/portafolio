<template lang="pug">
  .home
    Header(
      :header='sections[0].level'
      @showAbout='changeView'
    )
    About(
      :aboutMe='sections[1].level'
      @showHeader='changeView2'
    )
</template>

<script>
import Header from '@/components/header/Header'
import About from '@/components/about/About'

export default {
  name: 'home',
  components: {
    Header,
    About
  },
  data () {
    return {
      sections: [
        { section: 'header', level: 0 },
        { section: 'aboutMe', level: 1 },
        { section: 'mySkills', level: 1 },
        { section: 'whatIDo', level: 1 },
        { section: 'myExperience', level: 1 },
        { section: 'whereIGo', level: 1 },
        { section: 'contactMe', level: 1 }
      ]
    }
  },
  methods: {
    changeView (section) {
      this.sections[0].level = -1
      this.sections[1].level = 0
    },
    changeView2 (section) {
      this.sections[0].level = 0
      this.sections[1].level = 1
    }
  }
}
</script>
