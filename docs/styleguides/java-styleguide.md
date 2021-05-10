# Java Style guide

Please also ensure that you remain familiar with this document as it may change from time to time.

We have adopted [Google's Java style guide](https://google.github.io/styleguide/javaguide.html). In addition, we have listed our own rules below.

All source files should start with our copyright notice attached verbatim. This copyright notice can be found at the root of the respective repository.

## JUnit tests

### Use AssertJ

For assertions and assumptions, we're using AssertJ. We find this to be more readable (it flows nicer as it reads like a sentence) and it's easier to have a consistent team style.

### Given/when/then pattern
The pattern we follow for JUnit tests are given/when/then. For example, given some input some setup, when an action occurs, then assert as desired. Concrete example:

```java
    @Test
    void errorShownWhenEmailInUse() {
        // given
        userRepository.save(VALID_TEST_USER);
        EmailField emailField = _get(EmailField.class, spec -> spec.withId("email"));

        // when
        _setValue(emailField, VALID_TEST_USER.getEmail());

        // then
        assertThat(emailField.getErrorMessage()).isNotBlank();
    }
```

In general, we add comments to separate out the given, when and then sections. We find that this greatly improves readability.

### Assert all for multiple assertions

If a test method needs multiple assertions, `assertSoftly()` should be used. Otherwise, lazy evaluation is used. For example, if you had two assertions, and both assertions fail, you will not know about the second assertion failing until you have fixed the first assertion.
