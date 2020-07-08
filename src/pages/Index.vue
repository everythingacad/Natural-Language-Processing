<template>
  <Layout :sidebar="false">
    <div class="content">
      <!-- <h1>{{ $static.metadata.siteName }} - {{ this.description }}</h1> -->
      <h1>{{ this.description }}</h1>
      <div class="desc">
        <div class="content-desc">
          <h2>What is this?</h2>
          <h3>{{this.what}}</h3>
        </div>

         <div class="content-desc">
          <h2>Where do we find this?</h2>
          <h3>{{this.where}}</h3>
        </div>

         <div class="content-desc">
          <h2>Why do we need this?</h2>
          <h3>{{this.why}}</h3>
        </div>
      </div>
      <nav>
        <!-- To use other icons here, you need to import them in the Shortcut component -->
        <Shortcut link="/getting-started" text="Rookie" icon="book-open-icon" />
        <Shortcut link="/theme-configuration" text="Intermediate" icon="terminal-icon" />
        <Shortcut link="/theme-configuration#changing-colors" text="Production" icon="trending-up-icon" />
      </nav>
      <GitLink class="git" size="large" />
    </div>
  </Layout>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<script>
import GitLink from '~/components/GitLink.vue'
import Shortcut from '~/components/Shortcut.vue'

export default {
  components: {
    GitLink,
    Shortcut
  },
  data() {
    return {
      description: `Natural Language Processing`,
      what: `The science of teaching your computer to speak and understand your spoken language. SkyNet heavily depends on this.`,
      where: `Asking Alexa, Siri and Google to do something for you! That's just one of the many million applications out there.`,
      why: ` Imagine the possibilites of an intelligent talking computer. From analysing millions of documents to an AI that can write plays and lyrics!`,
      // how: ,
    }
  },
  metaInfo() {
    return {
      title: this.description,
      meta: [
        { key: 'description', name: 'description', content: 'A theme for static site documentation based on Gridsome, ready to deploy to Netlify in one click.' }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.content {
  display: flex;
  flex-direction: column;
}


h1 {
  text-align: center;
  max-width: 600px;
  margin: 1.5em auto 1.5em;
  font-size: 4em;

  @include respond-above(md) {
    max-width: 1000px;
  }
}

.desc{
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

.content-desc {
  display: flex;
  flex-direction: column;
  // max-width: 35%;
  word-wrap: break;
  flex-wrap: wrap;
  margin: auto;
}

h2 {
  font-size: 2rem;
  margin: auto auto 0.5em auto;
  text-align: center;
}

h3 {
  font-size: 1.5em;
  text-align: center;
  margin: auto auto 3em auto;
  max-width: 25ch;
}

nav {
  display: flex;
  justify-content: space-between;
  flex-direction: column;

  @include respond-above(sm) {
    flex-direction: row;
  }
}

.git {
  margin: 3em 0 0;
  align-self: center;

  @include respond-above(md) {
    margin: 5em 0 0;
  }
}
</style>
