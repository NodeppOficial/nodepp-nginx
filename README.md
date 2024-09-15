# NODEPP-NGINX

A Simple Reverse Proxy made with NodePP

## Dependencies
```bash
# ExpressPP
    💻: https://github.com/NodeppOficial/nodepp-express

# Nodepp
    💻: https://github.com/NodeppOficial/nodepp
```

## Build & Run
- 🪟: `g++ -o main main.cpp -I ./include -lz -lws2_32 -lssl -lcrypto ; ./main`
- 🐧: `g++ -o main main.cpp -I ./include -lz -lssl -lcrypto ; ./main`

## Usage

```cpp
#include <nodepp/nodepp.h>
#include <nginx/http.h>

using namespace nodepp;

void onMain() {
    
    auto app = nginx::http::add();

    app.add( "move", "/contact", object_t({
        { "href"   , "http://google.com" },
        { "timeout", 30000 }, { "limit", 25 },
    }));

    app.add( "pipe", "/blog", object_t({
        { "href"   , "http://localhost:8001/blog" },
        { "timeout", 30000 }, { "limit", 25 },
    }));

    app.add( "file", nullptr, object_t({
        { "path"   , "./www" },
        { "timeout", 30000 },{ "limit", 25 },
    }));

    app.add( "fssr", nullptr, object_t({
        { "path"   , "./www" },
        { "timeout", 30000 },{ "limit", 25 },
    }));

    app.listen( "0.0.0.0", 8000, []( ... ){
        console::log( "Listening -> http://localhost:3000" );
    });

}
```

## License

**Nodepp** is distributed under the MIT License. See the LICENSE file for more details.
