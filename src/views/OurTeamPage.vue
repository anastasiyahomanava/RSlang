<template>
  <div class="our-team">
    <div class="our-team__wrapper">
      <div class="our-team__card" v-for="man in people" :key="man.name">
        <img :src="man.image" alt="img" class="our-team__img" />
        <div class="our-team__information">
          <h3 class="our-team__name">{{ man.name }}</h3>
          <h5 class="our-team__major">{{ man.major }}</h5>
          <p class="our-team__my-work">
            Тут мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения. Тут
            мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения
          </p>
          <div class="our-team__contacts">
            <span class="icon-circle icon-circle_blue">
              <IconBase width="19" height="16" viewBox="0 0 19 16" icon-color="white">
                <IconTelegram />
              </IconBase>
            </span>
            <span class="icon-circle icon-circle_blue">
              <IconBase width="15" height="16" viewBox="0 0 15 17" icon-color="white">
                <IconLinkedin />
              </IconBase>
            </span>
            <span class="icon-circle icon-circle_blue">
              <span class="icon">
                <IconBase width="20" height="19" viewBox="0 0 20 15" icon-color="white">
                  <IconDiscord />
                </IconBase>
              </span>
            </span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import IconBase from '@/components/IconBase.vue';
import IconTelegram from '@/components/icons/IconTelegram.vue';
import IconLinkedin from '@/components/icons/IconLinkedin.vue';
import IconDiscord from '@/components/icons/IconDiscord.vue';

const SOFTWARE_ENGINEER = 'Software engineer';
export default {
  name: 'OurTeamPage',
  data() {
    return {
      people: [
        {
          image: require('../assets/img/Oleg.png'),
          name: 'Oleg Rashinskiy',
          major: SOFTWARE_ENGINEER,
          myWork:
            'Тут мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения. Тут мы рассказывае какие мы молодцы и какой вклад внесли в разработку приложения',
        },
        {
          image: require('../assets/img/Andrey.png'),
          name: 'Andrei Karol',
          major: SOFTWARE_ENGINEER,
          myWork:
            'Тут мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения. Тут мы расскаваем, какие мы молодцы и какой вклад внесли в разработку приложения',
        },
        {
          image: require('../assets/img/Yaroslav.png'),
          name: 'Yaroslav Denisyuk',
          major: SOFTWARE_ENGINEER,
          myWork:
            'Тут мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения. Т мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения',
        },
        {
          image: require('../assets/img/Dzianis.png'),
          name: 'Dzianis Puchko',
          major: 'Team Lead',
          myWork:
            'Тут мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения. Тут мы рассказываем, кие мы молодцы и какой вклад внесли в разработку приложения',
        },
        {
          image: require('../assets/img/Vasiliy.png'),
          name: 'Vasiliy Sukhavenka',
          major: SOFTWARE_ENGINEER,
          myWork:
            'Тут мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения. Тут мы рссказываем, какие мы молодцы и какой вклад внесли в разработку приложения',
        },
        {
          image: require('../assets/img/Dzhangar.png'),
          name: 'Dzhangar Zolvanov',
          major: SOFTWARE_ENGINEER,
          myWork:
            'Тут мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения. Тут м рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения',
        },
        {
          image: require('../assets/img/Ruslan.png'),
          name: 'Ruslan Bobreshov',
          major: SOFTWARE_ENGINEER,
          myWork:
            'Тут мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения. Ту мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения',
        },
        {
          image: require('../assets/img/Anastasiya.png'),
          name: 'Anastasiya Homanava',
          major: 'Experience Designer',
          myWork:
            'Тут мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения. Тт мы рассказываем, какие мы молодцы и какой вклад внесли в разработку приложения',
        },
      ],
    };
  },
  components: {
    IconBase,
    IconTelegram,
    IconLinkedin,
    IconDiscord,
  },
};
</script>

<style scoped lang="scss">
.our-team {
  background-color: $color-ghost;

  &__wrapper {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    max-width: $content-width;
    margin: auto;
  }

  &__card {
    display: inline-flex;
    width: 545px;
    height: 275px;
    margin: 6px 0;
    background-color: $color-white;
    border-radius: 25px;
  }

  &__img {
    width: 187px;
    height: 275px;
  }

  &__information {
    width: 310px;
    height: 199px;
    margin-top: 35px;
    margin-left: 24px;
  }

  &__name {
    margin-bottom: 5px;

    @include font($size: 18px, $height: 22px);
  }

  &__major {
    margin-bottom: 8px;

    @include font($size: 16px, $height: 18px, $weight: 300);

    color: $color-ghost;
  }

  &__my-work {
    margin-bottom: 17px;
  }
}

.icon-circle {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 36px;
  height: 36px;
  margin-right: 8px;
  cursor: pointer;
  border-radius: 25px;

  &_blue {
    background-color: $color-cornflower-blue;
  }
}
</style>