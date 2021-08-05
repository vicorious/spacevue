<template>
  <footer class="footer container">
    <hr class="footer__divider" />
    <div class="footer__bar">
      <div class="footer__logo">
        <Logo />
      </div>
      <div class="footer__copyright">
        &copy; Alejandro Lindarte Castro {{ new Date().getFullYear() }}
      </div>
      <div class="footer__social">        
        <a href="https://github.com/vicorious" target="_blank">
          <img
            src="../../../assets/images/social-icons/github.svg"
            alt="Github Logo"
          />
        </a>
        <a href="https://twitter.com/" target="_blank">
          <img
            src="../../../assets/images/social-icons/twitter.svg"
            alt="Twitter Logo"
          />
        </a>
      </div>
    </div>
  </footer>
</template>

<script>
import Logo from '../Logo.vue'
export default {
  components: { Logo }
}
</script>

<style lang="scss" scoped>
.footer {
  &__bar {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
    align-items: center;
    justify-content: space-between;
    padding: 1rem 0;
    text-align: center;

    @include mq(mobile) {
      flex-direction: row;
    }
  }

  &__social {
    display: flex;
    gap: 0.5rem;

    img {
      height: 20px;
      filter: invert(100%);
    }
  }

  &__divider {
    border: 1px solid $gray;
  }
}
</style>
