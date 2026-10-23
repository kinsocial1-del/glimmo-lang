# Glimmo

**Glimmo is a programming language that reads like plain English and explains its own mistakes.** It is built for people writing their first program, and it has the features experienced coders expect.

Glimmo was called Lumo until October 2026. Programs saved as `.lumo` files still run.

```
set name to ask "What's your name?"
say "Hello, {name}!"

repeat 3 times
    say "Glimmo is fun!"
end
```

**Try it in your browser at [glimmo-lang.vercel.app](https://glimmo-lang.vercel.app).** Nothing to install. The playground has 10 short lessons for complete beginners, every example, a Variables tab that shows every value as your program runs, a Tidy button, and a Share button that makes a link to your program, so you can post your games anywhere.

## Why Glimmo?

- **Reads like English.** `if score is more than 10`, `add "apple" to fruits`, `repeat 3 times`, `count i from 1 to 10`.
- **Errors that explain themselves.** Glimmo names the line, points at the exact spot, says what's wrong in plain words, and often guesses the fix:

  ```
  Oops! There's a problem on line 3 of mistakes.glimmo:

    3 | say "Hi " + nmae
                    ^

    I don't know what 'nmae' is.
    Hint: Did you mean 'name'?
  ```

  Habits from other languages get a friendly nudge too. Writing `print` tells you Glimmo uses `say`, and writing `def` tells you about `make`.
- **Math that does what you expect.** `0.1 + 0.2` is `0.3`, not `0.30000000000000004`, and comparisons ignore that rounding noise too.
- **Asking a question is one line.** `set age to ask "Age?"` gives you a number if someone types a number, so there's no `int(input(...))` to remember.
- **Counts from 1, like people do.** `fruits[1]` is the first item and `fruits[-1]` is the last.
- **Capital letters don't trip you up.** `Say` and `say` are the same, and `"YES" is "yes"` is true. Use `is exactly` when capitals matter.
- **Fast.** Glimmo turns each program into JavaScript before running it, so it runs on the same engine as Chrome and Node.js. `fib(30)`, which makes 1.3 million function calls, takes about 0.02 seconds.
- **Make games.** Draw shapes and emoji, move them with the keyboard and mouse, and play sounds. `glimmo build` turns a game into one web page you can send to anyone.
- **Ready for real projects.** Read and write files, work with JSON data, download from the web, run a website, and take command-line inputs. Error handling (`try` / `otherwise` / `fail`), built-in tests (`check`), closures, and splitting code into files (`use`) are all built in.
- **Easy to share.** `glimmo build app.glimmo` makes one `app.js` file that runs on any computer with Node.js, without installing Glimmo.
- **Tiny and portable.** The whole language is one JavaScript file with no dependencies. The same file runs in a terminal and in a web page.

## Glimmo next to Python

| Task | Glimmo | Python |
|---|---|---|
| Ask for a number | `set age to ask "Age?"` | `age = int(input("Age? "))` |
| Show a value in text | `say "Hi {name}"` | `print(f"Hi {name}")` |
| Count to 10 | `count i from 1 to 10` | `for i in range(1, 11):` |
| First item of a list | `fruits[1]` | `fruits[0]` |
| Add to a total | `add 5 to score` | `score += 5` |
| Compare | `if age is at least 18` | `if age >= 18:` |
| Handle a problem | `try ... otherwise ... end` | `try: ... except Exception as e: ...` |
| Read a file | `read_file("notes.txt")` | `open("notes.txt").read()` |
| Run a website | `serve(home, 8080)` | install a framework such as Flask, then about 6 lines |

## Getting started

Open the **[Glimmo playground](https://glimmo-lang.vercel.app)**, type a program and press Run. It works on computers, tablets and phones.

### Examples

These programs are in the [`examples`](examples) folder, and every one of them is also in the playground.

| File | What it shows |
|---|---|
| `examples/hello.glimmo` | Asking questions and showing answers |
| `examples/guess.glimmo` | A number guessing game with loops and decisions |
| `examples/fizzbuzz.glimmo` | The classic FizzBuzz puzzle |
| `examples/bank.glimmo` | Records, functions, `try`, `fail`, `check` and `map` |
| `examples/todo.glimmo` | A to-do app that saves tasks in a file: `glimmo examples/todo.glimmo add Buy milk` |
| `examples/website.glimmo` | A small website. Run it and open http://localhost:8080 |
| `examples/speed.glimmo` | How fast Glimmo is |
| `examples/drawing.glimmo` | A picture made of shapes and emoji |
| `examples/bounce.glimmo` | An animation: a bouncing ball you click to recolor |
| `examples/catch.glimmo` | A complete game: catch falling stars with the arrow keys |
| `examples/space.glimmo` | A space shooter built with kinds, with phone buttons |
| `examples/maze.glimmo` | A maze drawn from rows of text, with animated coins |
| `examples/pets.glimmo` | Kinds: pets with their own data and actions |
| `examples/countdown.glimmo` | Timers: a countdown with `every` and `after` |
| `examples/tour.glimmo` | Every feature, one after another |
| `examples/mistakes.glimmo` | How Glimmo explains a mistake |

To write your own program, open the playground and start typing.


---

## The language guide

### Saying things

```
say "Hello!"
say "You can say", 3, "things at once"
```

Put `{ }` around anything inside text to show its value. Write `\{` for a real brace.

```
set name to "Sam"
say "Hi {name}, 2 + 2 is {2 + 2}"
```

Anything after a `#` is a note for humans, and Glimmo skips it.

### Variables

```
set score to 10
set score to score + 1
add 5 to score          # same as: set score to score + 5
score = 20              # this works too
```

### Asking questions

```
set name to ask "What's your name?"
set age to ask "How old are you?"
say "Next year you'll be {age + 1}"
```

### Kinds of values

| Kind | Examples |
|---|---|
| number | `42`, `3.14`, `-7`, `1_000_000` |
| text | `"hello"`, `'hi'` |
| true/false | `true`, `false` |
| nothing | `nothing` |
| list | `[1, 2, 3]`, `["red", "green"]` |
| record | `{name: "Biscuit", age: 3}` |

### Math

`+  -  *  /` work as usual. `^` is power (`2 ^ 3` is 8), and `mod` (or `%`) gives the remainder. `"ha" * 3` is `"hahaha"`, and `+` joins text together.

### Comparing

| Write | Meaning |
|---|---|
| `a is b` | equal (ignores capital letters in text) |
| `a is not b` | not equal |
| `a is exactly b` | equal, and capital letters must match |
| `a is more than b` | `>` |
| `a is less than b` | `<` |
| `a is at least b` | `>=` |
| `a is at most b` | `<=` |
| `n is even`, `n is odd` | even or odd number |
| `list is empty` | has nothing in it |
| `list contains x`, `x is in list` | x is inside (works for text too) |

Combine conditions with `and`, `or`, `not`. The symbols `== != < > <= >=` also work.

### Making decisions

```
if score is more than 90
    say "Amazing!"
else if score is more than 50
    say "Nice!"
otherwise
    say "Keep practising!"
end
```

`else` and `otherwise` mean the same thing. A short `if` fits on one line with `then`:

```
if score is 100 then say "Perfect score!"
```

### Loops

```
repeat 3 times
    say "Hip hip hooray!"
end

count i from 1 to 10
    say i
end

count i from 10 to 0 by -2
    say i
end

for each fruit in ["apple", "banana"]
    say "I like {fruit}"
end

while score is less than 100
    add 10 to score
end

repeat forever
    set answer to ask "Say 'bye' to stop:"
    if answer is "bye" then stop
end
```

Use `stop` to leave a loop early, and `skip` to jump to its next round.

### Lists

```
set fruits to ["apple", "banana"]
add "cherry" to fruits
remove "apple" from fruits
say fruits[1]                # first item
say fruits[-1]               # last item
say fruits.length, fruits.first, fruits.last
set fruits[1] to "mango"
```

### Records

A record keeps named pieces of information together:

```
set pet to {name: "Biscuit", kind: "dog", age: 3}
say pet.name
set pet.age to 4
if pet contains "age" then say "We know the age"
```

### Functions

Make your own commands with `make`, and send an answer back with `give back`:

```
make greet with person
    give back "Hello, {person}!"
end

make area with width and height
    give back width * height
end

say greet("Ada")
say area(3, 4)
```

You can use a function before the line that makes it. Functions are values, so you can hand them to other functions:

```
make double with n
    give back n * 2
end
say map([1, 2, 3], double)       # [2, 4, 6]
```

For a short function, write it right where you need it with `gives`:

```
say map([1, 2, 3], n gives n * 2)                  # [2, 4, 6]
say filter(scores, s gives s is at least 50)
set add to (a, b) gives a + b
say sort_by(people, p gives p.age)                 # youngest first
say sort_by(people, p gives [p.age, p.name])       # by age, then by name
say any(people, p gives p.age is less than 10)     # true or false
```

**Where names live.** A name set inside `make` belongs to that function, unless the top of the program also sets it. Then the function changes the shared one:

```
set score to 0

make win
    add 10 to score       # changes the score above
    set bonus to 5        # only exists inside win
end
```

Functions made inside other functions remember the names around them:

```
make counter
    set n to 0
    make next
        add 1 to n
        give back n
    end
    give back next
end

set tick to counter()
say tick(), tick(), tick()       # 1 2 3
```

### Kinds

A kind is a recipe for making things that have their own data and actions, like the player and enemies in a game. Other languages call these classes.

```
make kind Pet with name, animal
    set hunger to 5
    set tricks to []

    make feed
        set hunger to max(0, hunger - 3)
    end

    make learn with trick
        add trick to tricks
    end

    make describe
        give back "{name} the {animal} knows {length(tricks)} tricks."
    end
end

set rex to Pet("Rex", "dog")
rex.learn("sit")
rex.feed()
say rex.describe()       # Rex the dog knows 1 tricks.
say rex.hunger           # 2
say rex                  # pet {name: "Rex", animal: "dog", hunger: 2, tricks: ["sit"]}
```

Everything a kind sets becomes a field of the thing it makes, and the kind's own `make` blocks can read and change those fields. Inside them, `me` is the whole thing. `type(rex)` gives `"pet"`.

**One name, one meaning.** Glimmo doesn't care about capital letters, so `Pet` and `pet` are the same name. Once you make a function or kind, its name can't be used for anything else, so `set pet to Pet("Rex")` gives a friendly error. Use names like `my_pet`, or `for each p in pets`.

### Handling problems

`try` runs some code, and if a problem happens, `otherwise` runs instead. The variable `problem` holds what went wrong. Use `fail` to signal a problem yourself.

```
make withdraw with amount
    if amount is more than balance then fail "Not enough money"
    set balance to balance - amount
end

try
    withdraw(500)
otherwise
    say "That didn't work: {problem}"
end
```

### Testing with check

`check` makes sure something is true. If it isn't, Glimmo stops and shows both sides:

```
check area(3, 4) is 12
check fruits contains "apple"
```

```
  This check failed: the left side is 11, the right side is 12.
```

### Using other files

`use` runs another Glimmo file once, so you can share functions between programs:

```
use "helpers.glimmo"
say shout("hi")
```

`use` also loads Glimmo files from the web, which is how people share libraries. Put a `.glimmo` file online (for example on GitHub), and anyone can use it in one line:

```
use "https://raw.githubusercontent.com/someone/glimmo-tools/main/tools.glimmo"
```

A file loaded from the web can `use` other files next to it, written as plain names like `use "more.glimmo"`. Only load code from people you trust, because it runs just like your own code. This works in the playground too.

### Remembering things

`remember` keeps a value after the program ends, and `recall` gets it back the next time. It's perfect for high scores and settings.

```
set best to recall("best_score", 0)     # 0 the very first time
set score to 37
if score is more than best
    remember("best_score", score)
    say "New best score!"
end
```

`recall` gives back the second value (or `nothing`) when nothing was remembered yet, and `forget("best_score")` throws a value away. Lists and records can be remembered too.

On a website, values are kept in that browser, and every Glimmo program on the same site shares them, so pick names that belong to your program, like `"catch_best"`. On a computer, they're kept in a file called `memory.json`, in a `.glimmo` folder inside your user folder.

### Timers

`every` runs a function again and again, and `after` runs one once, later. The rest of the program keeps going while they wait, which makes them good for clocks, countdowns and reminders.

```
set seconds_left to 5

make tick
    say "{seconds_left}..."
    add -1 to seconds_left
    if seconds_left is 0
        cancel(countdown)
        say "Liftoff!"
    end
end

make halfway
    say "(Halfway there!)"
end

set countdown to every(1, tick)      # every second
after(2.5, halfway)                  # once, in 2.5 seconds
```

`cancel(countdown)` stops a timer. A program keeps running while it has timers, so on a computer press Ctrl+C to stop one that never cancels.

### Files

File names are relative to the folder your program is in.

```
write_file("notes.txt", "Remember the milk")
add_to_file("notes.txt", "\nAnd the bread")
say read_file("notes.txt")

if file_exists("notes.txt") then say "Saved!"
say list_files()
delete_file("notes.txt")
```

### Data (JSON)

`to_json` turns lists and records into JSON text, and `from_json` turns JSON text back into lists and records. Together with files, that's an easy way to save a program's data:

```
set settings to {volume: 7, theme: "dark"}
write_file("settings.json", to_json(settings))

set loaded to from_json(read_file("settings.json"))
say loaded.volume
```

### The internet

`fetch` downloads a web page or an API's answer as text:

```
set answer to from_json(fetch("https://api.github.com/repos/nodejs/node"))
say "Node.js has {answer.stargazers_count} stars"
```

### Websites

`serve` runs a website. Your function gets each request (with its `path`, `method`, `query` and `body`) and gives back the page. Text starting with `<` is sent as HTML. Lists and records are sent as JSON. To choose the status code, give back a record like `{status: 404, body: "Not found"}`.

```
make home with request
    if request.path is "/"
        give back "<h1>Hello from Glimmo!</h1>"
    end
    give back {status: 404, body: "No page here"}
end

serve(home, 8080)
```

### Drawing

Drawing happens on a screen. In the playground it appears above the output. On your computer, `glimmo picture.glimmo` opens it in your web browser.

Positions are measured from the top-left corner: `x` goes right and `y` goes down.

```
screen(600, 400)                         # 600 wide, 400 tall (640 by 480 if you skip this)
background("sky blue")
circle(500, 80, 50, "gold")              # center x, center y, radius, color
rectangle(0, 300, 600, 100, "green")     # left, top, width, height, color
line(0, 0, 600, 400, "white", 3)         # from, to, color, thickness
triangle(130, 180, 370, 180, 250, 90, "brown")
draw_text("Hello!", 20, 20, 28, "white") # text, left, top, size, color
sprite("🐱", 300, 200, 64)               # any emoji, centered, with a size
```

Colors can be names like `"red"` or `"sky blue"`, codes like `"#ff8800"`, or `rgb(255, 136, 0)`. A color Glimmo doesn't know gets a friendly error.

Pictures work too. Keep the file in the same folder as your program, or use a web address:

```
picture("cat.png", 300, 200)          # centered at 300, 200, at its own size
picture("cat.png", 300, 200, 120)     # 120 wide (the height keeps its shape)
```

In the playground, use the **Add picture** button first. When you `glimmo build` a game, its pictures go inside the `.html` file, so it still works when you send it to someone.

### Games

A game sets things up once at the top. Then Glimmo runs three functions, if you make them:

| Make this | And Glimmo runs it |
|---|---|
| `make draw` | 60 times a second, on every screen. Clear the screen and draw the next picture here |
| `make key_pressed with key` | each time a key is pressed. `key` is `"left"`, `"right"`, `"up"`, `"down"`, `"space"`, `"enter"`, or a letter like `"a"` |
| `make clicked with x and y` | each time the screen is clicked or tapped |

Inside them you can check:

| Function | Gives |
|---|---|
| `key_down("left")` | true while that key is held down. Best for smooth movement |
| `mouse_x()`, `mouse_y()`, `mouse_down()` | where the mouse is, and whether it's pressed |
| `distance(x1, y1, x2, y2)` | how far apart two things are. Handy for checking if they touch |
| `beep(440, 0.2)` | plays a note: 440 vibrations a second, for 0.2 seconds |
| `stop_game()` | stops the game |

A rocket you steer with the arrow keys:

```
set x to 300

make draw
    background("black")
    if key_down("left") then add -5 to x
    if key_down("right") then add 5 to x
    sprite("🚀", x, 350, 48)
end
```

**Levels made of text.** Draw a level as rows of text, one symbol for each tile. `draw_tiles` turns each symbol into a color, an emoji, or a picture file. Symbols that aren't in the record are left empty, so use a space or a dot for open ground:

```
set level to [
    "##########",
    "#..*...*.#",
    "#..####..#",
    "##########",
]
set looks to {"#": "brown", ".": "sky blue", "*": "⭐"}

make draw
    draw_tiles(level, 40, looks)             # each tile is 40 by 40
end
```

`tile_at(level, x, y, 40)` gives the symbol at a spot on the screen, like `"#"`, or `""` outside the level. Check it before moving, so walls stop the player:

```
if tile_at(level, x + 5, y, 40) is not "#" then add 5 to x
```

To scroll a level bigger than the screen, give both the same left and top: `draw_tiles(level, 40, looks, -camera_x, 0)` and `tile_at(level, x, y, 40, -camera_x, 0)`.

**Animation.** `frame(list, per_second)` gives the picture to show right now, moving through the list that many times a second. Use it anywhere a picture goes:

```
sprite(frame(["🐤", "🐥"], 4), x, y, 48)
picture(frame(["run1.png", "run2.png", "run3.png"], 10), x, y)
```

The Maze game (`examples/maze.glimmo`) uses all three.

**Phones and tablets.** On a touch screen, a game shows big on-screen buttons for the keys it uses, like ◀ ▶ and Space. You don't need to do anything: Glimmo works out which keys your game listens for.

To share a game, run `glimmo build mygame.glimmo`. You get `mygame.html`, one file that anyone can open in a browser to play, with nothing to install.

### Long text

Text inside `"""` can cover many lines. The indent shared by every line is removed, so it can line up with your code:

```
make page with name
    give back """
        <h1>Hello, {name}!</h1>
        <p>Welcome to my site.</p>
        """
end
```

### Command-line inputs

Anything typed after the file name goes into the list `arguments`. Inputs that look like numbers become numbers.

```
# glimmo greet.glimmo Ada 3
repeat arguments[2] times
    say "Hi {arguments[1]}!"
end
```

### Built-in functions

| Function | What it does |
|---|---|
| `length(x)` | how many letters or items |
| `upper(t)`, `lower(t)`, `trim(t)` | change text |
| `replace(t, old, new)` | swap words in text |
| `split(t, sep)`, `join(list, sep)` | text to list and back |
| `starts_with(t, s)`, `ends_with(t, s)` | check the start or end of text |
| `number(x)`, `text(x)` | change a value's kind |
| `round(n, places)`, `floor(n)`, `ceil(n)`, `abs(n)`, `sqrt(n)` | number tools |
| `random(6)`, `random(1, 100)`, `random(list)` | random numbers, or a random item from a list |
| `shuffle(x)` | the same items, or letters, in a random order: `shuffle(["A", "K", "Q"])` |
| `min(...)`, `max(...)`, `sum(list)`, `average(list)` | number lists |
| `sin(d)`, `cos(d)`, `tan(d)`, `pi` | angles, in degrees |
| `sort(list)`, `reverse(x)`, `unique(list)`, `range(1, 5)`, `find(list, x)` | list tools |
| `slice(x, from, to)` | part of a list or text: `slice([10, 20, 30], 2)` is `[20, 30]` |
| `map(list, f)`, `filter(list, f)` | run a function on every item |
| `sort_by(list, f)`, `any(list, f)`, `all(list, f)` | sort by something, or check the items |
| `keys(record)`, `values(record)` | record tools |
| `type(x)` | `"number"`, `"text"`, `"list"`... |
| `today()`, `time()`, `now()` | the date, the time, and seconds since 1970 (for timing) |
| `read_file`, `write_file`, `add_to_file`, `file_exists`, `list_files`, `delete_file` | files |
| `to_json(x)`, `from_json(t)` | JSON data |
| `fetch(url)` | download from the web |
| `serve(f, port)` | run a website |
| `screen`, `background`, `circle`, `rectangle`, `line`, `triangle`, `draw_text`, `sprite`, `picture` | drawing |
| `key_down`, `mouse_x`, `mouse_y`, `mouse_down`, `beep`, `stop_game`, `distance`, `rgb` | games |
| `draw_tiles`, `tile_at`, `frame` | levels made of text, and animation |
| `arguments` | the command-line inputs |
| `every(seconds, f)`, `after(seconds, f)`, `cancel(timer)` | timers |
| `remember(name, value)`, `recall(name, fallback)`, `forget(name)` | keep values for next time |
| `wait(seconds)` | pause (on a computer; in a web page, use timers or a game's `draw` instead) |
| `clear()` | wipe the screen |

Files and `serve` work when Glimmo runs on a computer, but not in the browser playground. `fetch` works in both, but in a web page only for websites that allow other pages to read them (many data services do). Drawing and games work in a browser, so on a computer `glimmo` opens them in yours.

### Special words

These words are part of the language, so they can't be used as names:
`say set to if then else otherwise end repeat while for in make with give return stop skip and or not is true false nothing ask contains from`

---

## About this repository

This repository holds Glimmo's guide and example programs. The Glimmo language itself is not open source.

Copyright © 2026 kinsocial1. All rights reserved. See [LICENSE](LICENSE).
