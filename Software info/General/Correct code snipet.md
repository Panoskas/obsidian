## Correct way of structuring if statements
```csharp
private static string GetAlias(ChangeProductDTO dto)
        {
            var alias = dto.Alias;
            if (alias.CheckValue() == null)
            {
                return  dto.Title.Slugify();
            }
            else
            {
                return dto.Alias.Slugify();
            }
            if (alias == string.Empty)
                alias = RandomString(4, true);
            return alias;
        }
```

**The second if is unreachable because after the return the function terminates**

*Correction of code *
```csharp
private static string GetAlias(ChangeProductDTO dto)
        {
            var alias = dto.Alias;
            if (alias.CheckValue() == null)
            {
                alias =  dto.Title.Slugify();
            }
            else
            {
                alias = dto.Alias.Slugify();
            }
            if (alias == string.Empty)
                alias = RandomString(4, true);
            return alias;
        }
```

**More compact way with `?` operator**
```csharp
private static string GetAlias(ChangeProductDTO dto)
        {
            var alias = dto.Alias.CheckValue() == null ? dto.Title.Slugify() : dto.Alias.Slugify();
            if (alias == string.Empty)
                alias = RandomString(4, true);
            return alias;
        }
```
In this version, the conditional operator is used to assign the appropriate value to `alias` based on the condition `alias.CheckValue() == null`. If `alias.CheckValue()` is `null`, it assigns `dto.Title.Slugify()`, otherwise it assigns `dto.Alias.Slugify()`. After that, the check for an empty `alias` and the assignment of a random string remain the same as in the previous version.