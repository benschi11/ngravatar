NGravatar module for Orchard CMS
=================

To Use:

1. Initialize the module
2. Then modify your view within your theme.... Here is an example of mine... Parts.Common.Metadata.cshtml


```
@using NGravatar.Html
@using Orchard.Security

@{
    IUser user = (IUser)Model.ContentPart.Owner;
    var gravatarUrl = Url.Gravatar(string.IsNullOrWhiteSpace(user.Email) ? "dummy@foobar.com" : user.Email, 50);
}

<span class="author">
    @if (!string.IsNullOrWhiteSpace(gravatarUrl)) {
        <img src="@gravatarUrl" alt="" title="@user.UserName" />
    }
    @T("By {0}", user.UserName)@T(",")
</span>
<span class="published">@Display.PublishedState(createdDateTimeUtc: Model.ContentPart.CreatedUtc, publisheddateTimeUtc: Model.ContentPart.PublishedUtc)</span>
```



The module mearly provides HTML and URL Extension for you.
