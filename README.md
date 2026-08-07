# Roguelike BSP

## SP25

[Länk till credits](https://github.com/Timearchitect/frontend-22-VC-/wiki/Credits)

## Om projektet

Detta är ett repository för ett [examensarbete](https://docs.google.com/document/d/1SZkBWDGFPLLa5hlYZZjIUfqgCwMHedp7lyt50gcwKqM/edit?tab=t.0) där fokus ligger på procedural generation. detta projekt använder Binary Space Partitioning för att generera en map. 

# Om metoden
Metoden som användes för att generera kartan var Binary Space Overlap (BSP) och valdes ut som ett effektivt sätt att generera en karta som är annorlunda varje gång man genererar den. 
Detta uppnåddes genom att skapa "rum" som först delas upp i två delar som sen används för att delas ytterligare en gång. Processen fortsätter sedan tills området består av mindre sektioner som kan användas för rum.

![image1](https://github.com/0DevinN/Roguelike-BSP/blob/main/Screenshot%202026-08-07%20234527.png)

```c#
public class BSPNode
{
    public RectInt rect;
    public BSPNode left;
    public BSPNode right;
    public Room room;

    public BSPNode(RectInt rect) { this.rect = rect; }

    public bool IsLeaf => left == null && right == null;
}

```

Klassen för rum som finns under BinarySpacePartitioning.cs: 

```c#
public class Room
{
    public int x, y, width, height;

    public Room(int x, int y, int width, int height)
    {
        this.x = x; this.y = y; this.width = width; this.height = height;
    }

    public Vector2Int Center => new Vector2Int(
        x + width / 2,
        y + height / 2);

    public Vector3 CenterWorld => new Vector3(Center.x, Center.y, 0);
}

```

