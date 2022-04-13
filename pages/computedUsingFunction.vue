<template>
  <div>
    <TheHeader />
    <h1>Computed using a function internally</h1>

    <ComputedUsingFunction />
    <hr style="margin-top: 15px">
    <span>
      Le code:<br>
      <pre>
    sqrt (val: number) {
      console.log('sqrt function')
      return val ** 0.5
    }

    get squareRoot () {
      console.log('sqrt computed')
      const toDisplay = this.sqrt(this.variable)
      return toDisplay
    }
    </pre>
      - Même comportement que sur une computed simple. On voit passer les 2 logs à chaque invalidation du cache, ie à chaque changement de `this.variable` (que le getter soit affiché ou non)

      <br>
      <br>
      Conclusion:
      <br>
      - Utiliser une fonction dans un getter fonctionne comme on s'y attendrait.

    </span>
  </div>
</template>
