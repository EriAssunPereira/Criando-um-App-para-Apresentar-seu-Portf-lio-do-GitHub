# Criando-um-App-para-Apresentar-seu-Portf-lio-do-GitHub

Criar um aplicativo Android para apresentar um portfólio no GitHub é uma ótima maneira de mostrar nossos projetos de forma profissional. Vou detalhar o processo em módulos e fornecer exemplos práticos usando Kotlin.

### Módulo 1: Configuração Inicial
- **Instalação do Android Studio**: Instale a última versão do Android Studio.
- **Configuração do Projeto**: Crie um novo projeto Kotlin com uma Activity principal.

### Módulo 2: Integração com a API do GitHub
- **Retrofit**: Adicione Retrofit para fazer chamadas de rede.
- **Coroutines**: Use Coroutines para chamadas assíncronas.
- **Gson**: Utilize Gson para converter JSON em objetos Kotlin.

### Módulo 3: Interface do Usuário
- **Layouts**: Crie layouts XML para suas telas.
- **Data Binding**: Use Data Binding para conectar os dados aos layouts.
- **Navigation Component**: Implemente a navegação entre telas.

### Módulo 4: Exibição de Repositórios
- **RecyclerView**: Use RecyclerView para listar os repositórios.
- **Adapter**: Crie um Adapter personalizado para o RecyclerView.
- **ViewModel**: Gerencie os dados da UI com ViewModel.

### Módulo 5: Detalhes do Repositório
- **Fragment**: Use um Fragment para exibir detalhes de um repositório.
- **LiveData**: Atualize a UI com LiveData observando mudanças nos dados.

### Módulo 6: Testes e Manutenção
- **JUnit**: Escreva testes unitários com JUnit.
- **Espresso**: Utilize Espresso para testes de interface.
- **ProGuard/R8**: Configure o ProGuard ou R8 para ofuscação de código.

Aqui está um exemplo de código para o **Módulo 2**, mostrando como configurar o Retrofit para consumir a API do GitHub:

```kotlin
import retrofit2.Retrofit
import retrofit2.converter.gson.GsonConverterFactory
import retrofit2.http.GET
import retrofit2.http.Path

object RetrofitClient {
    private const val BASE_URL = "https://api.github.com/"

    val instance: GitHubService by lazy {
        Retrofit.Builder()
            .baseUrl(BASE_URL)
            .addConverterFactory(GsonConverterFactory.create())
            .build()
            .create(GitHubService::class.java)
    }
}

interface GitHubService {
    @GET("users/{user}/repos")
    suspend fun listRepos(@Path("user") user: String): List<Repo>
}

data class Repo(val name: String, val description: String)
```

Este código define um cliente Retrofit para a API do GitHub e uma função para listar os repositórios de um usuário. Lembre-se de que este é um exemplo simplificado e você precisará adaptar o código conforme necessário para o seu aplicativo.

https://github.com/EzequielMessore/app-repositories
