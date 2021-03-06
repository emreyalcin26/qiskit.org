<template>
  <main class="community-page education-page">
    <header>
      <CommunityHeader
        id="presentation"
        main-title="Qiskit for Educators"
        aside-position="start"
      >
        <p class="community-page__paragraph">
          Qiskit makes it easy to start learning quantum software to run on real
          quantum hardware. Teach your students with the same tools used by
          scientists and engineers worldwide to accelerate research towards
          practical applications for quantum computing.
        </p>
        <template #aside>
          <iframe
            class="header-video"
            width="560"
            height="315"
            src="https://www.youtube.com/embed/NHTDqdGfzcc"
            frameborder="0"
            allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          />
        </template>
      </CommunityHeader>
    </header>
    <div class="inner-navigation-scope">
      <InnerNavigation
        class="inner-navigation"
        :sections="[
          { anchor: 'video-series', label: 'Coding With Qiskit Series' },
          { anchor: 'textbook', label: 'Qiskit Textbook' },
          { anchor: 'host-an-event', label: 'Host Qiskit Events' }
        ]"
      />
      <PageSection id="video-series" framed>
        <h2 class="community-page__header">
          Coding With Qiskit Video Series
        </h2>
        <p class="community-page__paragraph">
          Accompany Abraham Asfaw through a series of video tutorials
          in our YouTube Channel explaining quantum computing through
          the use of Qiskit.
        </p>
        <ul class="actions">
          <li>
            <AppCta v-bind="youtubeAllEpisodesCtaLink">
              {{ youtubeAllEpisodesCtaLink.label }}
            </AppCta>
          </li>
        </ul>
        <template #aside>
          <iframe
            class="episode"
            width="560"
            height="315"
            src="https://www.youtube.com/embed/RrUTwq5jKM4"
            frameborder="0"
            allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen
          />
        </template>
      </PageSection>
      <PageSection id="textbook" aside-position="start" framed>
        <div class="education-page__textbook-copy">
          <h2 class="community-page__header">
            Qiskit Textbook
          </h2>
          <p class="community-page__paragraph">
            Leverage the power of quantum computing using Qiskit with this
            university course supplement covering introductory materials,
            advanced algorithms and hardware. Include problem sets and
            exercises for students.
          </p>
          <ul class="actions">
            <li>
              <AppCta v-bind="discoverTextbookCtaLink">
                {{ discoverTextbookCtaLink.label }}
              </AppCta>
            </li>
          </ul>
        </div>

        <template #aside>
          <TextbookPreview class="education-page__textbook-preview">
            <TextbookTOC />
          </TextbookPreview>
        </template>
      </PageSection>
      <PageSection id="host-an-event" framed>
        <h2 class="community-page__header">
          Host Qiskit Events
        </h2>
        <p class="community-page__paragraph">
          Bring Qiskit experts to your campus for guest lectures, hackathons,
          and other events. Guest lecture topics can range from quantum basics
          to advanced algorithms.
        </p>
        <ul class="actions">
          <li>
            <AppCta v-bind="requestAnEventCtaLink">
              {{ requestAnEventCtaLink.label }}
            </AppCta>
          </li>
        </ul>
      </PageSection>
    </div>
  </main>
</template>

<script lang="ts">
import { Component } from 'vue-property-decorator'
import QiskitPage from '~/components/logic/QiskitPage.vue'
import InnerNavigation from '~/components/ui/InnerNavigation.vue'
import CommunityHeader from '~/components/ui/CommunityHeader.vue'
import PageSection from '~/components/ui/PageSection.vue'
// @ts-ignore: Cannot find module
import TextbookPreview from '~/components/education/TextbookPreview.vue'
import AppCta from '~/components/ui/AppCta.vue'
// @ts-ignore: Cannot find module
import TextbookTOC from '~/content/education/textbook-toc.md'

import { YOUTUBE_ALL_EPISODES_CTA, DISCOVER_TEXTBOOK_CTA, REQUEST_AN_EVENT_CTA } from '~/constants/appLinks'

@Component({
  components: {
    InnerNavigation,
    CommunityHeader,
    PageSection,
    TextbookPreview,
    AppCta,
    TextbookTOC: TextbookTOC.vue.component
  },

  head () {
    return {
      title: 'Qiskit for Educators'
    }
  }
})
export default class extends QiskitPage {
  routeName: string = 'education'
  youtubeAllEpisodesCtaLink = YOUTUBE_ALL_EPISODES_CTA
  discoverTextbookCtaLink = DISCOVER_TEXTBOOK_CTA
  requestAnEventCtaLink = REQUEST_AN_EVENT_CTA
}
</script>

<style lang="scss">
@import '~/assets/scss/community-page.scss';

main {
  background-color: $ui-background;
}

.inner-navigation {
  position: sticky;
  top: 0;
  z-index: 100;
}

.actions {
  margin-top: $layout-01;
  list-style: none;
  display: flex;
  flex-direction: row;
}

#presentation {
  .header-video {
    max-width: 35rem;
    height: 20rem;
    box-shadow: 0  0.75rem 1.75rem -0.25rem $gray-100-a30,
                0   0.5rem    1rem  -0.5rem $gray-100-a30,
                0 -0.25rem    1rem -0.25rem $gray-100-a30;
  }

  .intro {
    @include mq($until: medium) {
      display: block;
    }
  }

  .copy-container {
    @include mq($until: medium) {
      max-width: 100%;
    }
  }

  .header-video {
    @include mq($until: medium) {
      display: none;
    }

    @include mq($until: large) {
      width: 19rem;
    }
  }
}

#video-series {
  color: $text-01;

  .episode {
    margin-left: $layout-03;
    transform: perspective(75rem) rotateY(-20deg) rotateX(5deg);
    border-radius: 0.5rem;
    box-shadow: 1.5rem 2.25rem 1.75rem 0 $gray-100-a30;
  }
}

#textbook {
  color: $inverse-01;
  background-color: $inverse-02;
  padding-bottom: $layout-05;

  .education-page__textbook-copy {
    position: sticky;
    top: $layout-06;
    align-self: start;
    background-color: $inverse-02;
    padding: 0;
    padding-left: $layout-05;

    @include mq($until: medium) {
      width: 100%;
      padding-left: 0;
    }
  }

  .education-page__textbook-preview {
    margin-top: -$layout-06;
    margin-left: -10%;
  }

  @include mq($until: medium) {
    min-height: auto;

  }
}

#host-an-event {
  color: $text-01;
  background-image:
    linear-gradient(#000000a0 0%, #000000a0 100%),
    url('/images/education/host-an-event-bg.jpg');
  background-position: 0, top;
  background-repeat: no-repeat;
  background-size: cover;
}

@media (max-height: 37.5rem) {
  #textbook {
    .copy-container {
      top: 1rem;
    }
  }
}
</style>
