<script lang="ts">
  import Footer from '$lib/components/Footer.svelte';
    import Section from '$lib/components/home/Section.svelte';
  import { onMount, onDestroy } from 'svelte';
  import Typewriter from 'typewriter-effect/dist/core';

  let greetingElement: HTMLElement;
  let typewriterExecuted = false;

  onMount(() => {
    if (!greetingElement) return;

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting && !typewriterExecuted) {
          // 2度目の実行を制御
          typewriterExecuted = true;

          const typewriter = new Typewriter(greetingElement, {
            loop: false,
            delay: 75
          });

          typewriter
            .typeString('Hello World.')
            .start();

          observer.unobserve(greetingElement);
        }
      });
    }, {
      // ビューポートの指定領域と1pxでも交差すれば発火
      root: null,
      rootMargin: '-20% 0px -20% 0px',
      threshold: 0
    });

    observer.observe(greetingElement);

    onDestroy(() => {
      observer.disconnect();
    });
  });
</script>

<svelte:head>
  <meta name="description" content="Flatbozu">
  <meta property="og:url" content="https://flatbozu.com/">
  <meta property="og:type" content="website">
  <meta property="og:title" content="Flatbozu">
  <meta property="og:description" content="やりたいことを、やりたいときに、やりたいように、やる。">
  <meta property="og:image" content="https://flatbozu.com/assets/img/og.png">
  <meta property="og:site_name" content="Flatbozu">
  <meta property="og:locale" content="ja">
  <title>Flatbozu</title>
</svelte:head>

<div class="wrapper">
  <header>
    <h1 class="logo">Flat<wbr />bozu</h1>
    <p class="info">since May 8, 2025</p>
  </header>

  <main>
    <section class="section" data-color-theme="negative">
      <h2>Profile</h2>

      <div class="contentWrapper">
        <p bind:this={greetingElement} class="greeting" id="greeting">
          &nbsp;
        </p>

        <Section
          heading={'Who'}
          data={[
            '私のハンドルネームは「Flatbozu」（日本語表記は「フラット坊主」）です。',
            'Flat（フラット）には「やりたいことを、やりたいときに、やりたいように、やる」という心の有り様を含ませています。確たる目的を持たず、何にも縛られず、その時々の何となくの感覚を大事にします。'
          ]}
        />

        <Section
          heading={'Work'}
          data={[
            '私の仕事は「デザイナーが制作したwebサイトのデザインを形にすること」です。',
            'そのデザインが解決したい課題を理解して、課題解決に最大限貢献することを意識しながら、実装・提案をおこないます。'
          ]}
        />
      </div>
    </section>

    <section class="section" data-color-theme="positive">
      <h2>Contents</h2>

      <div class="contentWrapper">
        <p>
          まだ何も無いです。
        </p>
      </div>
    </section>
  </main>

  <Footer />
</div>

<style lang="scss">
  header {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 24px;
    height: 100dvh;
    padding-left: 24px;
    padding-right: 24px;
    background-color: #fff;
  }

  .logo {
    font-size: 12vw;
    font-weight: bold;
    line-height: 1;
    letter-spacing: 0.1em;
    text-align: center;
    word-break: auto-phrase;

    @media (max-width: 800px) {
      font-size: 24vw;
    }
  }

  .info {
    font-size: max(1.8vw, 1.6rem);
    line-height: 1;

    @media (max-width: 800px) {
      font-size: max(2.8vw, 1.6rem);
    }
  }

  .section {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100svh;
    padding: 80px 0;
    overflow: hidden;
    will-change: transform;

    &[data-color-theme="positive"] {
      color: var(--color-main);
      background-color: #fff;
    }

    &[data-color-theme="negative"] {
      color: #fff;
      background-color: var(--color-main);
    }

    h2 {
      position: absolute;
      left: -0.1em;
      top: -0.1em;
      display: flex;
      align-items: center;
      height: 120px;
      font-size: 8.0rem;
      letter-spacing: 0.1em;
      line-height: 1;
      writing-mode: vertical-rl;
      opacity: 0.1;
    }
  }

  .contentWrapper {
    display: flex;
    flex-direction: column;
    gap: 80px;
    max-width: 720px;
    margin: 0 auto;
    padding: 0 32px;
  }

  .greeting {
    font-size: 5.6rem;
    line-height: 1;
  }
</style>
