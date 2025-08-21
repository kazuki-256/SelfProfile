# Yoshihara Kazuki

## Overview

- Languages:

  - C/C++: 4 years as primary language, mastering memory control, effectively and readable

  - Python: 5 years as secondary language, used its interpreter, OpenCV, networking, etc...

  - Basic proficiency in: Lua, Json, html, JavaScript, Java, SQL

- Skills:
  - Networking: client by libcurl + myhtml2-c, server by SocketTCP (structed socket)

  - Image process: OpenCV2, sdb-image

  - language translation: googletrans (private c program reamke of googletrans-python)

  - Game development: mygame3 (pricate api structed SDL2)

  - data science: dataframe-cpp (under developing)

- Maintainer of several public C/C++ libraries on GitHub including

  - [myhtml2-c](https://github.com/kazuki-256/myhtml2)

  - [linkable](https://github.com/kazuki-255/linkable)

  - [dataframe c++](https://github.com/kazuki-256/dataframe-cpp) (on developing)



---

## Contact

- 🔗 GitHub: [Fuuki255](https://github.com/Fuuki255)
- 📧 Email: luy18667@gmail.com



---

## Featured Projects

### 💡 myhtml2-c

C program fast html api to parse/make html:

- Clean, readable and easy using

- Full NULL debugging

- Robust error recovery, inspired by BeautifulSoup4

- Benchmarks show:
  - 17x faster parsing than BeautifulSoup4
  - 20x faster selection than BeautifulSoup4

### 🔗 linkable

c++ two linkable structure basic, free object with full control destruction unlike std::list


**Sample**

```cpp
#include "linkable.hpp"
#include <SDL2/SDL.h>
#include <string>

class GameObject : public TwoLinkable {
    SDL_Texture* texture;
    
    float x, y;
public:
    GameObject(SDL_Texture* texture, float x, float y);

    void draw(SDL_Renderer* renderer);
};


#include "games.cpp"

int main(int argc, char** argv) {
    // only class maked with TwoLinkable can be its object
    game_init();

    TwoLinkableList<GameObject> objectList;

    object.tlAddObject(new GameObject(0, 0, texture_background));


    while (game_running) {
        game_basic_handle_event();

        SDL_RenderClear(game_renderer);
        for (GameOject* object : objectList) {
            object->draw(game_renderer);
        }
        SDL_RenderPresent(game_renderer);

        SDL_Delay(1000 / 60);
    }

    game_quit();
    // objectList actully destroy autoly
    objectList.tlClear();
    return 0;
}

```