<script lang="ts">
  import { Localized } from "@nubolab-ffwd/svelte-fluent"
  import { assets } from "$app/paths"
  import { t } from "../store/locale"
  import Window from "./Window.svelte"
  import { utmSource } from "../utils/constants"
</script>

<Window title={$t("partners--title")}>
  <h3 class="title"><Localized id="partners--sponsors" /></h3>

  <div class="grid grid-sponsors">
    <a href={`https://contaaberta.info/?${utmSource}`} target="_blank" rel="noopener">
      <img src={`${assets}/conta-aberta.png`} alt="Conta Aberta" />
    </a>
  </div>

  <h3 class="title"><Localized id="partners--supporters" /></h3>

  <div class="grid grid-partners">
    <a href={`https://symcomp.ime.usp.br/?${utmSource}`} target="_blank" rel="noopener">
      <img src={`${assets}/symcomp.png`} alt="SymComp" />
    </a>

    <a href={`https://www.tempest.com.br/?${utmSource}`} target="_blank" rel="noopener">
      <img src={`${assets}/tempest.svg`} alt="Tempest" />
    </a>

    <a href={`https://elixiremfoco.com/?${utmSource}`} target="_blank" rel="noopener">
      <img src={`${assets}/elixir-em-foco.png`} alt="Elixir em foco" />
    </a>

    <a href={`https://www.meteor.com/?${utmSource}`} target="_blank" rel="noopener">
      <img src={`${assets}/meteor.png`} alt="Meteor" />
    </a>

    <Localized id="partners--become-a-partner" args={{ assets }} let:attrs>
      <a href={attrs.href.replace(/\p{C}/gu, "")} target="_blank" rel="noopener">
        <img src={attrs.src.replace(/\p{C}/gu, "")} alt={attrs.alt} />
      </a>
    </Localized>
  </div>
</Window>

<style>
  .title {
    padding: 10px 25px;
    margin: 0;
  }

  .grid {
    display: grid;
    justify-items: center;
    gap: 25px;

    padding: 25px;
  }

  .grid img {
    height: 175px;
    transition: filter 0.75s;
    filter: grayscale(1);
    max-width: 100%;
    max-height: 100%;
    object-fit: contain;
  }

  .grid img:hover {
    filter: grayscale(0);
  }

  .grid-sponsors {
    grid-template-columns: repeat(1, 1fr);
  }

  .grid-sponsors img {
    height: 100px;
  }

  .grid-partners {
    grid-template-columns: repeat(2, 1fr);
  }

  @media screen and (min-width: 768px) {
    .grid-partners {
      grid-template-columns: repeat(3, 1fr);
    }
  }
</style>
