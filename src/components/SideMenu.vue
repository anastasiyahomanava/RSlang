<template>
  <div class="menu" :class="{ 'menu-open': isOpen, 'menu-close': !isOpen }">
    <div class="menu__logo">RSlang</div>
    <div class="menu__burger">
      <div
        class="menu__burger-wrapper"
        :class="{ 'menu__burger-wrapper_open': isOpen }"
        @click="openMenu"
      >
        <div class="menu__burger-line"></div>
      </div>
    </div>
    <div class="nav-wrapper">
      <nav class="menu__navigation">
        <router-link
          class="menu__link"
          v-for="item of menuItems"
          :key="item.name"
          :to="item.route"
          active-class="active-link"
          @click.native="close"
        >
          <IconBase :iconName="item.name" width="34px" height="34px" :viewBox="item.icon.viewbox">
            <component :is="`Icon${item.icon.name}`" />
          </IconBase>
          <transition name="fade">
            <p v-if="isOpen">{{ item.name }}</p>
          </transition>
        </router-link>
      </nav>
      <div class="menu__logout" @click="onLogout">
        <IconBase iconName="Log Out" width="34px" height="34px" viewBox="0 0 36 26">
          <IconLogOut />
        </IconBase>
        <p v-if="isOpen">Log Out</p>
      </div>
    </div>
  </div>
</template>

<script>
import IconBase from '@/components/IconBase.vue';
import IconLogOut from '@/components/icons/IconLogOut.vue';
import IconBurger from '@/components/icons/IconBurger.vue';
import IconDictionary from '@/components/icons/IconDictionary.vue';
import IconJoystick from '@/components/icons/IconJoystick.vue';
import IconBarChart from '@/components/icons/IconBarChart.vue';
import IconGroupOfMen from '@/components/icons/IconGroupOfMen.vue';
import IconSettings from '@/components/icons/IconSettings.vue';
import IconAudiobook from '@/components/icons/IconAudiobook.vue';
import routerConsts from '@/router/routerConsts';
import { mapActions, mapState, mapMutations } from 'vuex';

export default {
  name: 'SideMenu',
  components: {
    IconBase,
    IconLogOut,
    IconBurger,
    IconDictionary,
    IconJoystick,
    IconBarChart,
    IconGroupOfMen,
    IconSettings,
    IconAudiobook,
  },
  computed: {
    ...mapState('SideMenu', ['menuItems', 'isOpen']),
  },
  methods: {
    ...mapActions('Auth', ['logoutUser']),
    ...mapMutations('SideMenu', ['setIsOpen']),

    openMenu() {
      this.setIsOpen(!this.isOpen);
    },
    onLogout() {
      this.logoutUser();
      this.$router.push(routerConsts.welcomePage.path);
    },
    close() {
      this.setIsOpen(false);
    },
  },
};
</script>

<style scoped lang="scss">
.active-link {
  background-color: $color-prussian-blue;
  animation: fade-link 1s;

  g {
    color: $color-golden-dream;
  }
}

@keyframes fade-link {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
}

.menu {
  position: fixed;
  z-index: 15;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  height: 100%;
  min-height: 100vh;
  color: $color-white;
  text-align: center;
  background-color: $color-nile-blue;
  transition: width 0.5s;

  &__logo {
    display: flex;
    align-items: center;
    justify-content: center;
    min-height: 86px;
    font-size: 36px;
    font-weight: 800;
    background-color: $color-prussian-blue;
  }

  &__burger {
    position: absolute;
    top: 0;
    left: 0;
    z-index: 19;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 60px;
    min-height: 86px;
    color: $color-white;
    background-color: $color-prussian-blue;
  }

  &__burger-wrapper {
    position: relative;
    display: flex;
    align-items: center;
    width: 30px;
    height: 25px;
    cursor: pointer;

    &::before,
    &::after {
      position: absolute;
      content: '';
    }

    &::before {
      top: 0;
    }

    &::after {
      bottom: 0;
    }

    .menu__burger-line,
    &::before,
    &::after {
      width: 100%;
      height: 3px;
      background-color: $color-white;
      transition: transform 0.3s, background-color 0.3s, opacity 0.3s;
    }

    &_open {
      .menu__burger-line {
        height: 0;
      }

      &::before {
        top: 50%;
        opacity: 0.1;
        transform: rotate(45deg);
      }

      &::after {
        top: 50%;
        opacity: 0.1;
        transform: rotate(-45deg);
      }
    }
  }

  &__navigation {
    margin-top: 40px;
    font-size: 20px;
    font-weight: normal;
  }

  &__link {
    display: flex;
    align-items: center;
    padding: 15px;
    margin-bottom: 32px;
    margin-left: 60px;
    color: $color-white;
    text-decoration: none;
    cursor: pointer;
    border-radius: 50px 0 0 50px;
    transition: all 0.25s;

    p {
      margin-left: 10px;
    }
  }

  &__logout {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    min-height: 86px;
    font-size: 24px;
    font-weight: 500;
    color: $color-white;
    cursor: pointer;
    background: $color-prussian-blue;
    transition: color 0.5s;

    p {
      margin-left: 8px;
    }
  }
}

.nav-wrapper {
  z-index: 15;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
}

.menu-open {
  width: 300px;
}

.menu-close {
  width: 60px;

  .menu__link {
    padding-left: 15px;
    margin-left: 0;
  }

  .menu__logo {
    font-size: 0;
  }
}

@media screen and (max-width: $desktop-width) {
  .menu__navigation {
    margin-top: 12;
  }

  .menu__link {
    margin-bottom: 12px;
  }
}

@media screen and (max-width: $tablet-width) {
  .menu__navigation {
    margin-top: 10px;
  }
}

@media screen and (max-width: $mobile-big-width) {
  .menu__navigation {
    margin-top: 10px;
  }

  .menu__link {
    margin-bottom: 10px;
  }

  .menu-close {
    width: 0;

    .nav-wrapper {
      display: none;
    }
  }
}

@media (hover: hover) {
  .menu__burger-wrapper:hover {
    .menu__burger-line,
    &::before,
    &::after {
      background-color: $color-golden-dream;
      opacity: 1;
    }
  }

  .menu-open {
    .menu__link:hover {
      padding-left: 60px;
      background: $color-prussian-blue;

      g {
        color: $color-golden-dream;
      }
    }
  }

  .menu-close {
    .menu__link:hover {
      background: $color-prussian-blue;

      g {
        color: $color-golden-dream;
      }
    }
  }

  .menu__logout:hover {
    color: $color-golden-dream;
  }
}

@media screen and (max-width: $mobile-small-width) {
  .menu__navigation {
    margin-top: 6px;
  }

  .menu__link {
    padding: 12px;
    margin-bottom: 0;
  }
}
</style>
