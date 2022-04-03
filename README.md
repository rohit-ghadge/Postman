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

## Pass data inside Body
![Get](https://user-images.githubusercontent.com/57706022/161421478-3e918cee-afa5-4083-8746-43f8d828be23.png)


## Controller
```
     @PostMapping("/flight/book/verify")
    public String showVerifyBookingPageResult(@RequestParam("flightId") long flightId,
                                              @RequestParam("passengerId") long passengerId,
                                              Model model)
    {

        Flight flight = flightService.getFlightById(flightId);
    }	
```

## Pass data inside Params
![Get](https://user-images.githubusercontent.com/57706022/161421894-7a0bb94a-bfed-451a-8fff-b7d1452d2e5e.png)

## Controller
```   
public class TestController 
{
    private final ServerServiceImpl serverService;

    @PostMapping("/save")
    public ResponseEntity<Response> saveServer(@RequestBody @Valid Server server) 
    {
         serverService.create(server));
    }
}

```
