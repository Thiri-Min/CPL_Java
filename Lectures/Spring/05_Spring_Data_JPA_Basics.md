# Spring Data JPA Basics Notes

## 🔗 JPA - Hibernate - Spring Data JPA
- **JPA (Java Persistence API)**: Standard specification for object-relational mapping (ORM).
- **Hibernate**: Popular JPA implementation, provides ORM features.
- **Spring Data JPA**: Abstraction layer on top of JPA/Hibernate, simplifies repository and query handling.

---

## 🏷️ Entity Mapping
- Entities represent database tables.
- Annotated with `@Entity`.
- Fields mapped to columns using `@Column`.
- Relationships:
  - `@OneToOne`
  - `@OneToMany`
  - `@ManyToOne`
  - `@ManyToMany`

Example:
```
@Entity
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    private String name;
    private String email;
}
```

## Repository Abstraction
- Spring Data JPA provides JpaRepository and CrudRepository.

- Eliminates boilerplate DAO code.
```
public interface UserRepository extends JpaRepository<User, Long> {
    List<User> findByName(String name);
}
```

## CRUD Operations
- Create → save(entity)

- Read → findById(id), findAll()

- Update → save(entity) (if entity exists)

- Delete → delete(entity), deleteById(id)

## Transaction Basics
- Transactions ensure atomicity and consistency.

- Managed by Spring with @Transactional.

- Rollback on exceptions.

```
@Service
public class UserService {
    @Transactional
    public void registerUser(User user) {
        userRepository.save(user);
    }
}
```

## Pagination
Spring Data JPA supports pagination via Pageable.

```
Page<User> users = userRepository.findAll(PageRequest.of(0, 10));
```

