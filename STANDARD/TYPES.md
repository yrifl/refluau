# Type Cheatsheets

## Implementation

```luau
type AccountImpl = {
    _index: AccountImpl,
    new: (name: string, balance: number) -> Account,
    deposit: (self: Account, credit: number) -> ()
}
```

## Generics

```luau
function isOk<T>(wrapper: (T) -> ()): T

end
```
