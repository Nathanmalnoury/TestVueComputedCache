<template>
  <div>
    <TheHeader />
    <h1>Computed wrapping around a computed returning a callable </h1>

    <ComputedReturnCallableWithWrapper />
    <span>
      Le code:<br>
      <pre>
      // balise template
           Double: { doubleOfVariable }
      // fin balise template

      get double() {
          console.log("double getter")
          return (num) => {
            console.log("inner function of getter")
            return num * 2;
          }
        }
      get doubleOfVariable () {
        console.log('Getter wrapping Double for variable')
        return this.double(this.variable)
      }
    </pre>
      - Au premier affichage, on passe dans "double of variable" puis dans "double" et dans la fonction interne.
      - Comme dans "computed returning a callable"; on ne revoit jamais "double getter". Le cache du getter double consistant en un pointeur vers sa fonction interne, qui n'est jamais invalidé
      <br>
      - Tant que `variable` ne change pas, le cache de "doubleOfVariable" est valide, donc on profite bien du cache.
      <br>
      - Si la valeur de "variable" change, on repasse dans "doubleOfVariable" qui utilise la valeur cachée de "double" qui est un pointeur vers sa fonction interne; la fonction interne est alors executée.
      <br>
      <br>
      Conclusion:
      <br>
      - Rien de très étonnant finalement. En revanche cette technique est je pense à éviter, car au final la technique de "Computed using a function" est aussi performante et plus lisible.
    </span>
  </div>
</template>

<style scoped>

</style>
