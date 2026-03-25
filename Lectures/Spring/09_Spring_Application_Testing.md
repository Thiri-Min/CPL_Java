# Spring Application Testing
## 1. Unit vs Integration Tests
- Unit Tests

    - Test individual components (e.g., service methods).

    - Use mocking frameworks like Mockito to isolate dependencies.

    - Fast and lightweight.
```
@SpringBootTest
class UserServiceTest {

    @Mock
    private UserRepository userRepository;

    @InjectMocks
    private UserService userService;

    @Test
    void testGetUserById() {
        when(userRepository.findById(1L)).thenReturn(Optional.of(new User(1L, "Alice")));
        User user = userService.getUserById(1L);
        assertEquals("Alice", user.getName());
    }
}
```

- Integration Tests

    - Test multiple layers working together (Controller → Service → Repository).

    - Often use embedded databases (H2) or test containers.

    - Slower but ensure system correctness.

## 2. @SpringBootTest
- Annotation that boots the entire Spring context for testing.

- Useful for integration tests.

- Can be combined with @AutoConfigureMockMvc for web layer testing.
```
@SpringBootTest
@AutoConfigureMockMvc
class UserControllerIntegrationTest {

    @Autowired
    private MockMvc mockMvc;

    @Test
    void testGetUser() throws Exception {
        mockMvc.perform(get("/api/users/1"))
               .andExpect(status().isOk())
               .andExpect(jsonPath("$.name").value("Alice"));
    }
}
```

## 3. MockMvc Basics

- MockMvc allows testing controllers without starting a full server.

- Provides fluent API for request building and response assertions.

```
@SpringBootTest
@AutoConfigureMockMvc
class ProductControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @Test
    void testGetProducts() throws Exception {
        mockMvc.perform(get("/api/products"))
               .andExpect(status().isOk())
               .andExpect(jsonPath("$[0].name").value("Laptop"));
    }
}
```

