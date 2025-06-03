<script lang="ts">
  interface Props {
    heading: string;
    data: string[];
  }

  let {heading, data}: Props = $props()
</script>

<section class="section">
  <h3>{heading}</h3>

  {#each data as row}
    <p>
      {row}
    </p>
  {/each}
</section>

<style lang="scss">
  .section {
    display: flex;
    flex-direction: column;
    gap: 32px;

    h3 {
      font-size: 4.0rem;
      font-weight: normal;
      letter-spacing: 0.1em;
      line-height: 1.4;
    }

    p {
      letter-spacing: 0.1em;
      line-height: 2.0;
      word-break: auto-phrase;
    }
  }
</style>
