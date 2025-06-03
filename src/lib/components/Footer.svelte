<footer>
  <div class="links">
    <a href="https://bsky.app/profile/flatbozu.bsky.social" target="_blank">
      <img src="/assets/img/Bluesky_Logo.svg" alt="Bluesky">
    </a>

    <a href="https://github.com/flatbozu" target="_blank">
      <img src="/assets/img/github-mark.svg" alt="GitHub">
    </a>
  </div>

  <small>
    © 2025 Flatbozu
  </small>
</footer>

<style lang="scss">
  footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    min-height: 64px;
    padding-left: 24px;
    padding-right: 24px;
    color: #fff;
    background-color: var(--color-main);
  }

  .links {
    display: flex;
    align-items: center;
    gap: 16px;

    a {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      width: 40px;
      height: 40px;

      &::before {
        position: absolute;
        left: 50%;
        top: 50%;
        content: '';
        width: 0;
        height: 0;
        border: 1px solid transparent;
        border-radius: 50%;
        transform: translate(-50%, -50%);
      }

      @media (hover) {
        &::before {
          transition-property: border-color, height, width;
          transition-duration: 0.2s;
        }

        &:hover {
          &::before {
            width: 100%;
            height: 100%;
            border-color: #fff;
          }
        }
      }

      img {
        max-width: 20px;
        filter: brightness(0) invert(1);
      }
    }
  }
</style>
