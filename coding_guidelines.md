
## Style ##
### Local variables ###
Use <code>var</code> when the return type can be derived by the compiler. Use the type when creating an instance.
<pre>
  var userId = BusinessEnvironment.Instance.CurrentContext.UserId;

  UserRoles userRoles = new()
  {
    RoleId = role.Id,
    UserId = userId?.ToString()
  }
</pre>

## Formatting ##
## Commments ##
Should have space after the two slashes and start with capital letter. No final period needed
<pre>
// Project should be unique for each company
</pre>

### Fields ###
Use underscores for private fields
<pre>
    private readonly IAccessHelper _accessHelper;
</pre>

## Types ##
### String ###
Prefer <code>string</code> over <code>String</code>.
