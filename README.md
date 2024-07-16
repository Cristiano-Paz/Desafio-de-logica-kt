# Desafio-de-logica-kt

enum class Nivel { Junior, Pleno, Senior }

data class Usuario(val nome: String, val email: String)

data class ConteudoEstudo(var nome: String, val duracao: Int = 60, val nivel: Nivel)

data class Formacao(val nome: String, var conteudos: List<ConteudoEstudo>) {
    val inscritos = mutableListOf<Usuario>()
    
    fun matricular(usuario: Usuario) {
        inscritos.add(usuario)
        println("${usuario.nome} foi matriculado na formação $nome.")
    }
}

fun main() {
    // Criando usuários
    val usuario1 = Usuario("Cristiano", "cristiano@example.com")
    val usuario2 = Usuario("Gabriel", "gabriel@example.com")
    
    // Criando conteúdo de nivel
    val conteudo1 = ConteudoEstudo("Kotlin Junior", 95, Nivel.Junior)
    val conteudo2 = ConteudoEstudo("Kotlin Senior", 150, Nivel.Senior)
    
    // formação de conteúdos
    val formacao = Formacao("Formação Kotlin", listOf(conteudo1, conteudo2))
    
    // Matriculando usuários 
    formacao.matricular(usuario1)
    formacao.matricular(usuario2)
    
    // Informações da formação
    println("Formação: ${formacao.nome}")
    println("Conteúdos:")
    formacao.conteudos.forEach { println("- ${it.nome} (${it.duracao} minutos, Nível: ${it.nivel})") }
    
    println("Inscritos:")
    formacao.inscritos.forEach { println("- ${it.nome} (${it.email})") }
}
