<template>
  <div class="resume">
    <div class="banner">
      <div class="banner__fullname">{{ person.name.first }} {{ person.name.middle }} {{ person.name.last }}</div>
      <div class="banner__position">{{ person.position }}</div>
      <div class="banner__employer">{{ person.employer }}</div>
      <div class="banner__employer">{{ person.location }}</div>
      <!-- <div v-if="person.birth" class="banner__location">{{ lang.born }} {{person.birth.year}} {{ lang.bornIn }} {{person.birth.location}}</div> -->
    </div>

    <div class="content">
      <div class="content__left">
        <div class="section">
          <div class="section-headline">
            {{ lang.about }}
          </div>

          <div class="section-content section-content--plain">
            <!-- {{ person.about }} -->
            <!-- Handle person.about here rather than data.yml for better emphasis and line breaks -->
            I'm a highly motivated and naturally curious individual with <b>6 years</b> of experience
            using <b>data science</b> & <b>machine learning</b> techniques.
            <br/>
            <br/>
            I exhibit an analytical and detail-oriented nature, while placing strong value on building relationships.
            {{ person.knowledge }}
          </div>
        </div>

        <div
          v-if="person.skills"
          class="section">
          <div class="section-headline">
            {{ lang.skills }}
          </div>

          <div class="section-content-grid">
            <a
              v-for="(skill, index) in person.skills"
              class="grid-item"
              :key="index"
              :class="{ link: skill.url !== undefined}"
              :href="skill.url">
              <span class="squarred-grid-item">
                {{ skill.name }}
              </span>
            </a>
          </div>
        </div>

        <div
          v-if="person.awards"
          class="section">
          <div class="section-headline">
            Awards
          </div>

          <div class="section-content section-content--plain">
            <a v-for="(award, index) in person.awards" class="grid-item">
              <span>{{ award.name }}<br/></span>
              <span>{{ award.org }} | {{ award.timeperiod }}<br/><br/></span>
            </a>
          </div>
        </div>

        <div class="section">
          <div class="section-headline">
            {{ lang.contact }}
          </div>

          <div class="section-content section-content--plain">
            <div class="section-link">
              <i class="section-link__icon material-icons">business</i>{{ person.contact.street }}<br/>{{ person.contact.city }}
            </div>

            <a
              class="section-link link"
              :href="contactLinks.email">
              <i class="section-link__icon material-icons">mail</i>{{ person.contact.email }}
            </a>

            <div class="section-link">
              <i class="section-link__icon material-icons">phone</i>{{ person.contact.phone }}
            </div>

            <a
              v-if="person.contact.website"
              class="section-link link"
              :href="person.contact.website">
              <i class="section-link__icon fa fa-globe"></i>{{ person.contact.website }}
            </a>

            <a
              v-if="person.contact.linkedin"
              class="section-link link"
              :href="contactLinks.linkedin">
              <i class="section-link__icon fa fa-linkedin"></i>{{ person.contact.linkedin }}
            </a>

            <a
              v-if="person.contact.github"
              class="section-link link"
              :href="contactLinks.github">
              <i class="section-link__icon fa fa-github"></i>{{ person.contact.github }}
            </a>

            <a
              v-if="person.contact.medium"
              class="section-link link"
              :href="contactLinks.medium">
              <i class="section-link__icon fa fa-medium"></i>{{ person.contact.medium }}
            </a>
          </div>
        </div>
      </div>

      <div class="content__right">
        <div class="section">
          <div class="section-headline">
            <i class="section-headline__icon material-icons">work</i>{{ lang.experience }}
          </div>

          <div class="section-content">
            <a
              v-for="(experience, index) in person.experience"
              :key="index"
              class="section-content__item"
              :class="{ link: experience.website !== undefined}"
              :href="experience.website">

              <span class="section-content__header">{{ experience.position }}</span>
              <span class="section-content__subheader">
                {{ experience.company }}: {{ experience.location }} | {{ experience.timeperiod }}
              </span>

              <div class="section-content__subheader"><i>{{ experience.description }}</i></div>
              <span class="section-content__plain">
                <ul class="custom_indent">
                  <li v-for="(task) in experience.tasks">{{ task }}</li>
                </ul>
              </span>
            </a>
          </div>
        </div>

        <div class="section">
          <div class="section-headline">
            <i class="section-headline__icon material-icons">school</i>{{ lang.education }}
          </div>

          <div class="section-content">
            <a
              v-for="(education, index) in person.education"
              class="section-content__item"
              :key="index"
              :class="{ link: education.website !== undefined}"
              :href="education.website">

              <span class="section-content__header"> {{ education.school }} | {{ education.timeperiod }}</span>
              <span class="contrib-text">{{ education.degree }}</span>
              <span class="contrib-text"> {{ education.description }}</span>
            </a>
          </div>
        </div>

        <div
          v-if="person.contributions"
          class="section">
          <div class="section-headline">
            <i class="section-headline__icon material-icons">code</i>{{lang.contributions}}
          </div>

          <div class="section-content"><i>Open Source:</i></div>
          <div class="section-content-grid-contrib">
            <a
              v-for="(contribution, index) in person.contributions"
              class="section-content__item-grid"
              :key="index"
              :class="{ link: contribution.url !== undefined}"
              :href="contribution.url">
              <span class="contrib-text"><i class="section-headline__contrib_icon fa fa-code-fork"></i>{{ contribution.name }}</span>
            </a>
          </div>

          <div class="section-content"><hr></div>

          <div class="section-content"><i>Personal:</i></div>
          <div class="section-content-grid-contrib">
            <a
              v-for="(project, index) in person.projects" :key="index"
              class="section-content__item-grid"
              :class="{ link: project.url !== undefined}"
              :href="project.url">
              <span class="contrib-text"><i class="section-headline__contrib_icon fa fa-code-fork"></i>{{ project.name }}</span>
            </a>
          </div>

        </div>
      </div>
    </div>

    <img class="picture"/>
  </div>
</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';

const name = 'cool-logan';

export default Vue.component(name, getVueOptions(name));
</script>

<style lang="less" scoped>
@accent-color: #34495E;
@banner-color: #42b883;
@banner-height: 120px;
@picture-size: 130px;
@picture-offset: 35px;
@base-padding: 30px;
@left-column-width: 210px;

.link {
  color: inherit;
  cursor: pointer;
  text-decoration-line: none;

  &:visited {
    color: inherit;
  }
}

.resume {
  position: relative;
  font-family:'Roboto' !important;
  font-size: 0.9em;
}

.picture {
  position: absolute;
  // top: @banner-height - @picture-offset;
  // left: @left-column-width + @base-padding * 2 - @picture-size / 2;
  top: @picture-offset / 2;
  left: @left-column-width * 2 + @base-padding * 7;
  height: @picture-size;
  width: @picture-size;
  border-radius: 50%;
  border: 5px solid @accent-color;
  content: url('../../resume/id.jpg');
  z-index: 2;
}

.banner {
  width: calc(100% - @base-padding * 2);
  height: @banner-height;
  padding: @base-padding;
  background-color: @banner-color;
  /*
    background-image: url('../../resume/banner.png');
    background-repeat: no-repeat;
    background-size: cover;
  */
  color: white;

  &__fullname {
    font-size: 32px;
  }

  &__position {
    font-size: 16px;
  }

  &__location {
    font-size: 12px;
  }

  &__employer {
    font-size: 12px;
    // font-style: italic;
  }
}

.content {
  display: flex;
  width: 100%;
  height: 100%;

  &__left,
  &__right {
    height: 100%;
    padding: @base-padding;
  }

  &__left {
    width: @left-column-width;
    color: rgba(255, 255, 255, 0.59);
    background-color: @accent-color;

    .section-headline {
      color: white;
    }
  }

  &__right {
    flex: 1;
  }
}

.section {
  margin: 20px 0;
}

.section-link,
.section-headline {
  display: flex !important;
  align-items: center;
  color: @accent-color;
  display: inline-block;
  font-size: 1.2em;
  margin: 8px 0;

  &__icon {
    margin-right: 8px;
    font-size: 1.4em;
  }

  &__contrib_icon {
    margin-right: 4px;
    // font-size: 1.2em;
    font-size: 12px;
  }
}

.section-link {
  // font-size: 1.1em;
  font-size: 12px;
  color: rgba(255, 255, 255, 0.59) !important;

  &__icon {
    color: white;
  }
}

.section-content {
  margin-top: 5px;
  padding-left: 32px;
  font-size: 12px;

  &__item {
    display: block;
    margin-bottom: 5px;
  }

  &__header {
    display: block;
    font-size: 1.1em;
    font-weight: 500;
  }

  &__subheader {
    display: block;
    font-weight: 400;
  }

  &__plain,
  &__text {
    display: block;
    font-size: 12px;

    &--light {
      font-size: 12px;
    }
  }

  &__plain {
    display: inline;
    font-weight: 300;
  }

  &__item-grid {
    flex: 1 1 0;
    margin-bottom: 5px;
    padding-right: 5px;
  }

  &--plain {
    padding: 0;
  }
}

.contrib-text {
  display: block;
  font-size: 12px;
  font-weight: 300;
}

.section-content-grid {
  display: flex;
  flex-wrap: wrap;
  margin-top: 5px;
  margin-bottom: 5px;
}

.section-content-grid-contrib {
  display: flex;
  flex-wrap: wrap;
  margin-top: 5px;
  margin-bottom: 5px;
  padding-left: 32px;
  flex-direction: row;
  max-width: 300px;
}

.grid-item {
  padding-right: 5px;
}

.squarred-grid-item {
  display: block;
  border: 1px solid white;
  color: white;
  margin-top: 5px;
  padding: 5px;
  font-size: 12px;
}

ul.custom_indent {
    margin-top: 2px;
    margin-left: 15px;
    margin-right: 0px;
    padding-left: 15px;
    padding-right: 0px;
}

</style>
