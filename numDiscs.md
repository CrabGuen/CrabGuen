fun hanoiTower(numDiscs: Int, fromTower: Char, auxTower: Char, toTower: Char) {
    if (numDiscs == 1) {
        println("Move disk 1 from $fromTower to $toTower")
    } else {
        hanoiTower(numDiscs - 1, fromTower, toTower, auxTower)
        println("Move disk $numDiscs from $fromTower to $toTower")
        hanoiTower(numDiscs - 1, auxTower, fromTower, toTower)
    }
}

fun main() {
    val numDiscs = 3
    hanoiTower(numDiscs, 'A', 'B', 'C')
}
