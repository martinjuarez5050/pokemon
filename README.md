# Pokémon API Client con Spring WebClient

Este proyecto es un cliente en Java que consume la [PokéAPI](https://pokeapi.co/) para obtener información de Pokémon usando **Spring WebClient**. 

---

## Tecnologías usadas

- Java 17+
- Spring Boot 
- Spring WebClient
- Spring Web MVC / REST

---

## Funcionalidad principal

- Consulta dinámica de Pokémon por nombre usando WebClient.

---

## Uso

### Método para obtener Pokémon

```java
public infopokemon getPokemon(String name) {
    try {
        return webClient.get()
            .uri("/" + name)
            .retrieve()
            .bodyToMono(infopokemon.class)
            .block();
    } catch (WebClientResponseException.NotFound ex) {
        throw new ResponseStatusException(HttpStatus.NOT_FOUND, "Pokemon no encontrado");
    }
}
