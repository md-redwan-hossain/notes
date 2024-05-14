### Claims-based authentication with cookie

The first thing we do is build up a list of claims, populating each with a string for its name, a string for its value, and optional `Issuer` and `ClaimValueType` fields. The `ClaimType` class is a helper which exposes a number of common claim types.

Once you have built up your claims you can create a new `ClaimsIdentity`, passing in your claim list, and specifying the `AuthenticationType` (to ensure that your identity has IsAuthenticated=true). Finally you can create a new `ClaimsPrincipal` using your identity and sign the user in. In this case we are telling the AuthenticationManager to use the `CookieAuthenticationDefaults.AuthenticationScheme` authentication handler, which we must have configured as part of our middleware pipeline.

To sign in, `SignInAsync(HttpContext, String, ClaimsPrincipal, AuthenticationProperties)` extension method is used. The `string` param is for specifying scheme.

If the payload of the cookie is very large, aspnetcore will automatically spplit it.

For the conversion of `ClaimsPrincipal` to Cookie, a mechanism with scheme is needed as shown in the code `.AddAuthentication().AddCookie()`.

`UseAuthentication` middleware will pick up the cookie, open and read it using the cookie handler which is added in `AddAuthentication`.

```cs
using System.Security.Claims;
using Microsoft.AspNetCore.Authentication;
using Microsoft.AspNetCore.Authentication.Cookies;


var builder = WebApplication.CreateBuilder(args);

builder.Services.AddEndpointsApiExplorer();

builder.Services
    .AddAuthentication()
    .AddCookie(CookieAuthenticationDefaults.AuthenticationScheme);

var app = builder.Build();

app.MapGet("/cookie-auth", (HttpContext context) =>
{
    var userId = context.User.FindFirst(ClaimTypes.NameIdentifier)?.Value;
    return Results.Ok(userId ?? "User id not found");
});


app.MapPost("/cookie-auth", async (HttpContext context, [FromQuery] bool persist) =>
{
    var claim = new Claim(ClaimTypes.NameIdentifier, Guid.NewGuid().ToString(), ClaimValueTypes.String);
    var userIdentity = new ClaimsIdentity([claim], CookieAuthenticationDefaults.AuthenticationScheme);
    var claimsPrincipal = new ClaimsPrincipal(userIdentity);
    var authenticationProperties = new AuthenticationProperties { IsPersistent = persist };

    await context.SignInAsync(
        CookieAuthenticationDefaults.AuthenticationScheme,
        claimsPrincipal,
        authenticationProperties
    );
});


app.UseAuthentication();
app.Run();
```
