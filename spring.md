@SpringBootApplication:
  - @ComponentScan (сканирование пакетов вокруг класса)
  - @SpringBootConfiguration = @Configuration
  - @EnableAutoConfiguration (использование стартеров вместо конфигурации)
  
@Configuration (загружается с приложением) - суть спринг бута

@Conditional (условия для загрузки конфигурации) может быть на классе и на методе
 - базируется на имплементации функционального интерфейса Condition с методом boolean matches(), если возвращает true, то конфигурация будет загружена
 
@Profile тоже включает @Conditional и в зависимости от профиля загружает нужные конфиги

Так, например, JpaRepositoriesAutoConfiguration загружается тогда, когда у нас есть класс JpaRepository, DataSource, Property 'spring.data.jpa.repositories'

-------------------------------------------------------

- @Autowired -использует AutowiredAnnotationBeanPostProcessor для инъекции (пакет спринга), есть required атрибут, есть @Qualifier. По умолчанию: singleton
- @Inject - использует AutowiredAnnotationBeanPostProcessor для инъекции (JSR-330 - стандарт инъекций Java), есть @Named. По умолчанию: prototype
- @Resource - использует CommonAnnotationBeanPostProcessor для инъекции

-------------------------------------------------------

JPA

Repository<T,ID> - базовый интерфейс JPA, в котором нет методов
CrudRepository<T,ID>
PagingAndSortingRepository<T,ID>
JpaRepository<T,ID>
