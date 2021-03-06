# NFC Client
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Ftaglme%2Fnfc-goclient.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Ftaglme%2Fnfc-goclient?ref=badge_shield)


Open-Source Go library for quick and efficient work with NFC REST API.

### Installation

``` go get github.com/taglme/nfc-client ```

### Usage

```Go
import "github.com/taglme/nfc-client/pkg"

url := "http://127.0.0.1:3011" // url of the hosted API
locale := "en" // preferred locale to be set on the BE side
client := client.New(url, locale)

// Request to get About info
about, err := client.About.Get()
if err != nil {
    fmt.Println(err) // handle an error
    return
}

fmt.Printf(about.Name) // Print received About.Name
```

#### WS

WS connection is a part of the library functionality via which you are able to receive Events.

```Go
// Initialize the  WS connection
defer func () {
    err = ws.Disconnect() 
    if err != nil {} // handle an error on disconnect
}()

err := client.Ws.Connect()
if err != nil {} // handle an error on init


eHandler := func(e models.Event) {
    // handle the received event
}

client.Ws.OnEvent(eHandler)
```

Also you are able to handle errors in a similar manner

```Go
errHandler := func(e error) {
    // handle the received error
}

client.Ws.OnError(eHandler)
```

## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Ftaglme%2Fnfc-goclient.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2Ftaglme%2Fnfc-goclient?ref=badge_large)