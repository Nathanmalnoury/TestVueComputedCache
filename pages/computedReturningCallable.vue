<template>
  <div>
    <TheHeader/>
    <h1>Computed returning a callable</h1>

    <ComputedReturnCallable/>
    <hr style="margin-top: 15px">
    <span>
      Le code:<br>
      <pre>
      // balise template
           Double: { double(variable) }  // <- utilisée comme ceci
      // fin balise template

      get double() {
          console.log("double getter")
          return (num) => {
            console.log("inner function of getter")
            return num * 2;
          }
        }
    </pre>
      - Au premier affichage, on passe dans `double` et dans la fonction interne.
      <br>
      - <strong>Meme sans changement de la variable on repasse dans la fonction interne</strong> (vérifier en togglant plusieurs fois l'affichage sans changer la valeur de la variable)
      <br>
      - La valeur de ce qui est caché n'est pas la valeur de retour de la fonction; mais le pointeur vers cette fonction. Pour tous les appels suivants, on ne revoit jamais passer `double getter`, car rien n'a invalidé ce cache.
      <br>
      <br>
      Conclusion:
      <br>
        - Un getter qui renvoie une fonction n'a aucun bénéfice de cache, et est en revanche moins lisible qu'une fonction classique.
    </span>
  </div>
</template>

<style scoped>

</style>
