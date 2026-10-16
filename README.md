# Adapter

A small Java demo of the **Adapter design pattern**. A central unit (`UniteCentre`) only knows how to output through a legacy **VGA** interface, while some display devices (a TV) only accept **HDMI**. An adapter bridges the two.

## Structure

```
src/main/java
├── Test.java                       # Demo entry point
├── computer/
│   ├── UniteCentre.java            # Client: prints via a Vga device
│   ├── Vga.java                    # Target interface
│   ├── Hdmi.java                   # Adaptee interface
│   ├── Ecran.java                  # Native VGA display
│   ├── VideoProjecteur.java        # Native VGA projector
│   ├── TV.java                     # HDMI-only display
│   └── SuperVP.java                # Projector supporting both VGA and HDMI
└── adapter/
    ├── HdmiVgaAdapter.java         # Object adapter (composition)
    └── HdmiVgaAdapterH.java        # Class adapter (inheritance, extends TV)
```

## Adapter variants

- **Object adapter** – `HdmiVgaAdapter` implements `Vga` and holds an `Hdmi` device (set with `setHdmi`). It converts the message to bytes and forwards it to `hdmi.view(...)`.
- **Class adapter** – `HdmiVgaAdapterH` extends `TV` and implements `Vga`, reusing the TV's `view` method through inheritance.

## Requirements

- JDK 26 (see `maven.compiler.source` in `pom.xml`)
- Maven

## Build and run

```bash
mvn compile
```

`Test.java` contains the demo; run it from your IDE (IntelliJ project files are included).

## License

No license specified.
