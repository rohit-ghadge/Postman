# Postman Request different optoins

## Pass data inside Header
![Get](https://user-images.githubusercontent.com/57706022/151702664-33fb9e35-3018-4290-a7c5-9c19dfe92f18.png)


## Controller
```
  // Check Token is Valid or Not
    @Override
    protected void doFilterInternal(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, FilterChain filterChain) throws       ServletException, IOException 
    {
    	// Header Key Muse be = "Authorization"
        String authorization = httpServletRequest.getHeader("Authorization");
        String token = null;
        String userName = null;

        // Check Header Value start with "Bearer "
        if(null != authorization && authorization.startsWith("Bearer "))
        {
            token = authorization.substring(7);
            userName = jwtUtility.getUsernameFromToken(token);
        }

```

-- Pass data inside body

http://localhost:8080//api/test/save
    
Body 
{
  "id" : 7,
  "imageUrl" : "http://localhost:8080/server/image/server1.png",
  "ipAddress" : "64.233.191.255",
  "memory" : "128",
  "name" : "Google",
  "status" : "SERVER_UP",
  "type": "7"
}
    
@RestController
@RequiredArgsConstructor
@RequestMapping("/api/test")
public class TestController 
{
	
    private final ServerServiceImpl serverService;
    
    @PostMapping("/save")
    public ResponseEntity<Response> saveServer(@RequestBody @Valid Server server) 
    {
       serverService.create(server)))
    }
}    
------------------------------------------------------------------------------------------------------------------------


