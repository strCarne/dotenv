# How to link **<dotenv.h>** with your project
## 1 step
### Clone the library repo
```sh
cd ${YOUR_PROJECT_LOCATION}
git clone https://github.com/strCarne/dotenv
```
## 2 step
### Add next lines into your main CMakeLists.txt
```
add_subdirectory(dotenv)
include_directories(dotenv)
target_link_libraries(${PROJECT_NAME} dotenv)
```

---

# How to use **<dotenv.h>** in your code
```c
#include <dotenv.h>
#include <stdio.h>
#include <stdlib.h>

int main() {
    if (dotenv_load(".env") != 0) {
        fprintf(stderr, "couldn't load .env file\n");
        return EXIT_FAILURE;
    }

    char *test_variable = getenv("TEST_VARIABLE");
    if (test_variable == NULL) {
        fprintf(stderr, "TEST_VARIABLE must be set\n");
        return EXIT_FAILURE;
    }

    fprintf(stdout, "TEST_VARIABLE=%s\n", test_variable);

    return EXIT_SUCCESS;
}


```
