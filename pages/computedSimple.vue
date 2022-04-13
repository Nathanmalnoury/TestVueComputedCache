<template>
  <div>
    <TheHeader />
    <h1>Computed Simple</h1>

    <ComputedSimple />

    <hr style="margin-top: 15px">
    <span>
      Le code:<br>
      <pre>
      get square() {
        console.log('square')
        return this.variable ** 2
      }
    </pre>
      - Au 1er affichage; on calcule la valeur du getter et on crée notre cache<br>
      - Si on toggle `show computed`; le cache est utilisé et on ne recalcule pas le getter.<br>
      - Si on hide; puis change la valeur; puis show; la valeur est recalculée et le cache mis-à-jour<br>
      - Mais si on hide, puis on change la valeur et on la remet sur la valeur originale (par ex. on increase de 1
      puis decrease de 1); alors <strong>le cache n'est pas utilisé</strong>. <br>=>Il semble que le cache soit invalidé dès
      lors que la valeur de la propriété réactive sur laquelle la computed se base change.

      <br><br>
      Conclusion:
      <br>
      - Les computed sont "Lazy": <strong>leurs valeurs ne sont calculées que quand elles deviennent nécessaire à l'affichage.</strong>
      <br>
      - <strong>Le cache des computed est invalidé à chaque fois changement de valeur de leur propriété réactive</strong>, sans rapport aucun avec leur affichage.

    </span>
  </div>
</template>

<script>
