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


**Samples**

```cpp
#include "myhtml2/myhtml.h"


int main(int argc, char** argv) {
    HtmlObject* doc = HtmlReadObjectFromFile("sample.html");

    // == print html title ==
    HtmlObject* tagTitle = HtmlFindObject(doc, "title");
    printf("title: %s\n", HtmlGetObjectInnerText(tagTitle);   // 

    // == iterate all <img> ==
    HtmlSelect select = HtmlCreateSelect(doc, "img");

    printf("founded <img> href:\n");
    HtmlForeachSelect(select, tag) {
        printf("  %s\n", HtmlGetObjectAttrValue(tag, "href"));

        // you can stop finding to reduce finding unuse object
        // break;
    }
    putchar('\n');

    HtmlDestroySelect(&select);  // destroy select task

    // == find all objects ==
    HtmlArray result = HtmlFindAllObjects(doc, "link");

    printf("all links\n");
    for (int i = 0; i < result.length; i++) {
        printf("  %s\n", HtmlWriteObjectToString(result.objects[i]));
        // the string to unview memory: tagTitle->name + strlen(tagTitle->name) + 1
    }

    HtmlDestroyArray(&result); // destroy array


    // == write html (optional) ==
    HtmlWriteHtmlToFile(doc, "output.html");

    // == destroy doc/objects ==
    HtmlDestroyObject(doc);

    return 0;
}

```

- myhtml2-c++ coming soon


---

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


#include "game.cpp"  // game.cpp for skip many defines, not actually program

GameObject* mob1 = NULL;
GameObject* mob2 = NULL;

int main(int argc, char** argv) {
    // only class maked with TwoLinkable can be its object
    game_init();

    // == init list ==
    TwoLinkableList<GameObject> objectList;

    mob1 = objectList.tlAddObject(new GameObject(0, 0, texture_mob1));
    mob2 = objectList.tlAddObject(new GameObject(0, 0, texture_mob2));

    // == loop game ==

    while (game_running) {
        game_loop_start();

        // delete object
        if (game_is_delete_mob1) {
            delete mob1;   // direct deleting O(1), also mob1 removed from objectList
         }

        // foreach objects
        for (GameOject* object : objectList) {
            object->draw(game_renderer);
        }

        game_loop_end();
    }

    // objectList actully destroy autoly
    objectList.tlClear();

    game_quit();
    return 0;
}

```