# Spring Style guide

This is in addition to our [Java style guide](https://project-books.github.io/docs/development/styleguides/java-styleguide/).

## Lombok

- Explicitly exclude (or only manually include) all lazy loaded fields in JPA entities
- Ensure @NoArgsConstructor is used if @AllArgsConstructor is used, as entities need a public or protected no-arg constructor
- Do not the @EqualsAndHashCode annotation as we don't want Lombok to generate equals() and hashCode() methods for JPA entities
- Do not use the @Data annotation for the same reason as above
 
For more information, read this [article on some Lombok pitfalls](https://www.jpa-buddy.com/blog/lombok-and-jpa-what-may-go-wrong/).