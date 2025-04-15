
## Coding Guidelines ##
### Local variables ###
Use <code>var</code> when the return type can be derived by the compiler. Use the type when creating an instance.
<pre>  
  // Correct
  var userId = BusinessEnvironment.Instance.CurrentContext.UserId;
  
  // Wrong. Guid is unambiguous
  Guid? userId = BusinessEnvironment.Instance.CurrentContext.UserId;

  // Preferred
  UserRoles userRoles = new()
  {
    RoleId = role.Id,
    UserId = userId?.ToString()
  }
  
  // Not preferred
  var userRoles = new UserRoles()
  {
    RoleId = role.Id,
    UserId = userId?.ToString()
  }
</pre>

### Commments ###
Should have space after the two slashes and start with capital letter. No final period needed
<pre>
// Project should be unique for each company
</pre>

### Fields ###
Use underscores for private fields
<pre>
private readonly IAccessHelper _accessHelper;
</pre>

### String type ###
Prefer <code>string</code> over <code>String</code>.

### Closing brackets ###
Always leave a blank line after a closing bracket, except when the next line is also a closing bracket or an <code>else</code>, <code>catch</code> statement.
<pre>
  if (doesProjectExistForOtherTenant)
  {
      return Forbidden<InitializationResponse>(ErrorConstants.PROJECT_ALREADY_EXISTS_WITH_OTHER_TENANT);
  }

   return Success<InitializationResponse>(Constants.INIT_PERFORMED_SUCCESSFULLY);
</pre>
