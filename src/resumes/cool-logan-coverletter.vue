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
          <div class="section-headline">Personal Info</div>
          <hr>

          <div class="section-content section-content--plain">
            <span class="section-subheadline">Address<br/></span>
            <span>{{ person.contact.street }}<br/>{{ person.contact.city }}</span>
            <br/><br/>

            <span class="section-subheadline">Phone<br/></span>
            <span> {{ person.contact.phone }}</span>
            <br/><br/>

            <span class="section-subheadline">Email<br/></span>
            <span>{{ person.contact.email }}</span>
            <br/><br/>

            <span class="section-subheadline">LinkedIn<br/></span>
            <span>linkedin.com/in/logan-thomas</span>
            <br/><br/>

            <span class="section-subheadline">GitHub<br/></span>
            <span>github.com/loganthomas</span>
          </div>

        </div>
      </div>

      <div class="content__right">
        <span class="section-content__plain">
          <br/>
          November 14, 2020
          <br/>
          <br/>
          Dear Hiring Manager,
          <br/>
          <br/>

          I am writing to you out of interest for the position of Software Developer: Scientific Applications that I found
          on the Enthought careers web-page.

          <br/>
          <br/>

          I have extensive work experience in the fields of project management, data science, and machine learning.
          Through the <i>Emerging Leaders Program</i> at Nielsen, I was taught to spearhead new ideas, implement solutions based on
          client needs, and deliver on key performance indicators. While serving as a Senior and Lead Data Scientist,
          I was able to develop in-depth expertise with data mining, modeling, and artificial intelligence techniques.

          <br/>
          <br/>

          Over the past year, I have served as a Senior Data Scientist at an engineering consultancy.
          Being the first true data scientist hired at Protection Engineering Consultants, I have paved the way for the company
          to break into the data science landscape. I have been an advocate for writing clean code that is version controlled and
          unit tested. One of the first action steps I took after being hired was setting up an extensive continuous integration and
          continuous delivery pipeline architecture for all internal projects. I also created a repository template to ensure consistent
          project structure across all internal efforts and to remove the start-up barrier for non-technical users desiring to create
          a new project repository.

          <br/>
          <br/>

          I enjoy teaching others and sharing my knowledge with those that are interested in bolstering their data science skills.
          I currently mentor three recent graduates and provide guidance on their journey to becoming data scientists.
          My aptitude for collaborative software development can be displayed through my contributions on GitHub and the fact that
          I serve as a core developer for the <i>pyjanitor</i> library.
          I have also served as a Python Technical Curriculum Developer for DataCamp and currently maintain the <i>Writing Efficient Python Code</i>
          course available on their online platform.

          <br/>
          <br/>

          Through years of developing my data science and machine learning skill set, I have become passionate about software development
          and coding best practices. If you are looking for a "scientist who codes", I am confident that I am a solid candidate for this role.

          <br/>
          <br/>

          Please find my resume attached if you’d like more details. I look forward to speaking with you during an interview.
          Please feel free to contact me at (321) 961-9107 anytime during the day. Thank you once again for your time and consideration.
          <br/>
          <br/>
          Respectfully yours,
          <br/>
          Logan Thomas
        </span>
      </div>
    </div>

    <img class="picture"/>
  </div>
</template>

<script>
import Vue from 'vue';
import { getVueOptions } from './options';

const name = 'cool-logan-coverletter';

export default Vue.component(name, getVueOptions(name));
</script>

<style lang="less" scoped>
@accent-color: #34495E;
@banner-color: #42b883;
@banner-height: 120px;
@picture-size: 130px;
@picture-offset: 35px;
@base-padding: 30px;
@left-column-width: 165px;

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
  // left: @left-column-width * 2 + @base-padding * 7;
  left: 630px;
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
    padding-top: 0px;
  }

  &__left {
    width: @left-column-width;
    color: rgba(255, 255, 255, 0.59);
    background-color: @accent-color;

    .section-headline {
      color: white;
    }

    .section-subheadline {
      color: white;
      font-size: 12px;
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
