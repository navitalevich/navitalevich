# How to Manage User Roles in WorkflowEngine?

You can use BasicPlugin.

## Сontent
1. [How to manage](#How-to-manage)
    1. [Predefined actors](#Predefined-actors)
    2. [UsersInRoleAsync and checkRole](#UsersInRoleAsync-and-checkRole)
2. [How it use](#How-it-use)

## How to manage

### Predefined actors

```csharp
private static WorkflowRuntime InitWorkflowRuntime()
{
    ...

    var basicPlugin = new OptimaJet.Workflow.Core.Plugins.BasicPlugin();
    basicPlugin.CheckPredefinedActorAsync = CheckPredefinedActorAsync;
    basicPlugin.GetPredefinedIdentitiesAsync = GetPredefinedIdentitiesAsync;

    basicPlugin.WithActors(new List<string>() {"Manager", "Author"});

    var runtime = new WorkflowRuntime()
    ...
    .WithPlugin(basicPlugin)
    .Start();
    ...

    return runtime;
}

async Task<bool> CheckPredefinedActorAsync(ProcessInstance processInstance, WorkflowRuntime runtime, string parameter, string identityId)
{

  //Example: проверка что пользователь с указанными Id является менеджером
  if (parameter == "Manager")
  {
      if (identityId == myManagerId)
          return true;
      else
          return false;
  }

  return false;
}

async Task<IEnumerable<string>> GetPredefinedIdentitiesAsync(ProcessInstance processInstance, WorkflowRuntime runtime, string parameter)
{
  //Example: вернуть id всех пользователей являющимися менеджерами
  if (parameter == "Manager")
  {
      return new List<string>() {myManagerId1, myManagerId2};
  }

  return new List<string>();
}
```

### UsersInRoleAsync and CheckRole

 To implement this, subscribe for the `UsersInRoleAsync` delegate:
```csharp
private static WorkflowRuntime InitWorkflowRuntime()
{
    ...

    var basicPlugin = new OptimaJet.Workflow.Core.Plugins.BasicPlugin();
    basicPlugin.UsersInRoleAsync = UsersInRoleAsync;

    var runtime = new WorkflowRuntime()
    ...
    .WithPlugin(basicPlugin)
    .Start();
    ...

    return runtime;
}

public static async Task<IEnumerable<string>> UsersInRoleAsync(string roleName, Guid? processId = null)
{
    //TODO return all identityIds (userId) for this roleName
    return new List<string>() {"identity1",  "identity2", "identity3"};
}
```

Then, the *CheckRole* method becomes available in the WorkflowDesigner. 

In the Actors section, add the following roles:

![Actors](/documentation/assets/images/faq/roles-actors.png)

- *Name* – the Actor name to be used in the workflow scheme
- *Rule* – set the *CheckRole* from the BasicPlugin
- *Parameter* – the role name to be used when calling `UsersInRoleAsync`, it will be passed in the delegate function as the `roleName` parameter.


## How it use

Next, you can limit access to Transitions, using Actors:

![Transition](/documentation/assets/images/faq/roles-transition.png)

When invoking [basic operations](/documentation/main-terms/basic-operations/), you specify the *identityId* parameter. This is the identifier of the user, who has initiated the operation (for example, the operation of obtaining a list of available commands). When checking the user’s access to commands, in case the Workflow Engine meets Actor with *CheckRole* Rule in the scheme, the BasicPlugin calls `UsersInRoleAsync`. It checks if the *identityId* parameter is contained in the array returned by `UsersInRoleAsync`. If so, then the command that launches Transition (see picture above) becomes available to the user; and, the user becomes able to execute this command and start the transitional process.


**If your system is heavily loaded, and the performance is critical for you, then we recommend creating a separate IWorkflowRuleProvider with the RuleGet and RuleCheck methods that check user roles. You can read more [here](/documentation/scheme/rules/)**