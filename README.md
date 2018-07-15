# go-clash

API bindings for the public Clash Royale API, for Go.

https://developer.clashroyale.com/#/documentation

## Usage

```
client := clash.NewClient("Your bearer token"),

player := client.Player("9PLJLPQ8G") // "#9PLJLPQ8G" is also fine

chests, _ := player.UpcomingChests()

for _, chest := range chests.Items {
    fmt.Printf("Chest %s is %d drops away!\n", chest.Name, chest.Index)
}
```

## Error handling

Any issues with HTTP transport or response codes >=400 will be reflected in the returned error.

Cast the error to an API error structure. If casting wasn't successful, the error must be from net/http.

```
if err, ok := err.(clash.APIError); ok {
    // handle a clash API error response
}
```