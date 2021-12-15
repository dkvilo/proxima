# FMeta Spec 0.1
FMeta is a Domain-specific language to serialize Game-Level data. It was designed for my upcoming puzzle game.

# Specification overview


### "Hello, World" example with standard output 

```julia
#pragma *MAIN |std_out;
@message &str: "Hello, World";
> message;
#end;
```

### Break down

```julia

! MAIN section
! Which also is a default starting point for the program
#pragma *MAIN |std_out;

! Variable declaration
@message &str: "Hello, World";

! Standard output
> message;

! End of the scope
#end;
```


### Level Data Serialization

```julia
#pragma *META_DATA |...;

@name &str: "Level 1";
@screenshot &ref<Image>: preview.png

@unit &ref<Unit>: Pixel;

@frame_width &int: 500;
@frame_height &int: 500;
#end;

! Represent 4x4 Identity Matrix
#pragma *DATA | 4,4;
+ 1, 0, 0, 0
+ 0, 1, 0, 0
+ 0, 0, 1, 0
+ 0, 0, 0, 1
#end;
```

## Data Types

- int
- float
- str
- ref

## Compile-time generated types
```julia
#pragma *GAME_STATE |...;
@game_difficulty &ref<Difficulty>: HARD; 
#end;
```

In the compiler side, You need to create corresponding enum
```C++
typedef enum { EASY, MEDIUM, HARD  } Difficulty; 
```





