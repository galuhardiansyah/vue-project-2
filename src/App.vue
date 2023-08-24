<script setup>
import PersonalDetail from './components/PersonalDetail.vue'
import PersonalSummary from './components/PersonalSummary.vue'
import EmploymentHistory from './components/EmploymentHistory.vue'
import EducationInfo from './components/EducationInfo.vue'
import Skills from './components/Skills.vue'
</script>

<template>
  <main>
     <div class=" mx-auto max-w-[1080px] mt-20">
        <PersonalDetail />
        <PersonalSummary />
        <EmploymentHistory />
        <EducationInfo />
        <Skills />
      </div>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
