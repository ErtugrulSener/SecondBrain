```Java
@Configuration
public class SecurityConfig {
	@Bean
	public SecurityFilterChain filterChain(HttpSecurity http) {
		http.authorizeHttpRequests((authz) -> authz.requestMatchers("/admin/**").hasRole("ADMIN"));
	}

	@Bean
	public InMemoryUserDetailsService userDetailsService() {
	
	}
```

## Eine Resource nicht sichern
```Java
@Bean
public WebSecurityCustomizer webSecurityCustomizer() {
    return (web) -> web.ignoring().requestMatchers("/ignore1", "/ignore2");
}
```