# Programação Dinâmica 
Implementações dos exemplos comentados nesse artigo:  
* [Programação Dinâmica vs Memoization]()

### Função fibonacci
Complexidade: O(2^n)
```kotlin
fun fib(num: Int): Int {
    return if (num < 2)
        num
    else
        fib(num-1) + fib(num - 2)
}
```

### Função fibonacci + memoization
Complexidade: O(n)
```kotlin
val cache = mutableMapOf<Int, Int>()

fun fibMemo(num: Int): Int {
    if (num < 2) return num
    if (!cache.containsKey(num)) {
        cache[num] = fibMemo(num-1) + fibMemo(num - 2)
    }
    return cache[num]!!
}
```

### Função fibonacci + tabulation
Complexidade: O(n)
```kotlin
val tab = mutableMapOf<Int, Int>()

fun fibTab(num: Int): Int {
    tab[0] = 0
    tab[1] = 1
    for (i in 2..num) {
        tab[i] = tab[i-2]!! + tab[i-1]!!
    }
    return tab[num]!!
}
```

### Comparativo de eficiencia
```kotlin
fun main() {
    val num = 45

    val time1 = measureTimeMillis { fibTab(num) }
    println("Tabulation: $time1 ms")

    val time2 = measureTimeMillis { fibMemo(num) }
    println("Memoization: $time2 ms")

    val time3 = measureTimeMillis { fib(num) }
    println("Fib sem otimização: $time3 ms")
}
```
Se quiser rodar pelo browser: https://pl.kotl.in/in0uQ_i3l