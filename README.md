# DBML Viewer

DBML Viewer is a Visual Studio Code extension that allows you to visualize your DBML (Database Markup Language) files directly within the editor.

## Features

- Visualize DBML files as SVG graphs
- Save DBML content as SVG files
- Automatically update visualization when DBML files are changed
- Navigate through tables, enums, and references in DBML files

## Installation

1. Install Visual Studio Code.
2. Go to the Extensions view by clicking the Extensions icon in the Activity Bar on the side of the window or by pressing `Ctrl+Shift+X`.
3. Search for "DBML Viewer" and click Install.

## Usage

1. Open a `.dbml` file in Visual Studio Code.
2. Use the Command Palette (`Ctrl+Shift+P`) to run the command `Generate DBML Graph` to visualize the DBML content.
3. To save the visualization as an SVG file, use the command `Save DBML as SVG`.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request on GitHub.

## Maintainer

This project is now maintained by [JakeMofa](https://github.com/JakeMofa). I will be updating, adding new features, and addressing issues. Contributions and feedback are always welcome.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE.txt) file for details.

## Updates

### Version 0.1.2

#### New Features and Improvements

- **Live Rendering**: Visualize your DBML files as SVG graphs directly within VS Code.
- **Save as SVG**: Save the rendered DBML content as an SVG file.
- **File System Watcher**: Automatically update the visualization when DBML files are changed.
- **Document Symbol Provider**: Navigate through tables, enums, and references in your DBML files.
- **Support for Latest DBML Syntax**: Compatible with the latest DBML syntax from dbdiagram.io, including:
  - Project Definition
  - Schema Definition
  - Public Schema
  - Table Definition
  - Table Alias
  - Table Notes
  - Table Settings
  - Column Definition
  - Column Settings
  - Default Value
  - Index Definition
  - Index Settings
  - Relationships & Foreign Key Definitions
  - Relationship settings
  - Many-to-many relationship
  - Enum Definition
  - Note Definition
  - Project Notes
  - Table Notes
  - Column Notes
  - TableGroup Notes
  - Sticky Notes
  - TableGroup
  - TableGroup Notes
  - TableGroup Settings
  - Multi-line String
  - Comments
  - Syntax Consistency

#### Known Issues and Future Improvements

- The live parser that generates the SVG may not handle very large DBML files efficiently. Future updates may focus on improving performance for larger files.
- Consider making the extension more interactive and live, similar to dbdiagram.io, allowing users to code directly in VS Code without needing to copy and paste into dbdiagram.io.

## Supported Syntax

The DBML Viewer now supports both the current syntax and the syntax used on dbdiagram.io.

### Example

```dbml
table user {
    id uuid pk
    name text unique
    verbandsschlüssel char(1)
}
```

or

```dbml
table user {
    id uuid [pk]
    name text [unique]
    verbandsschluessel char(1)
}
```

## Table Definitions

To create tables and fields, use the Table definition syntax.

### Example

```dbml
Table users {
  id int [PK]
  email varchar
  gender varchar
  relationship varchar
  dob datetime
  country int
}

Table countries {
  code int [PK]
  name varchar
  continent_name varchar
}
```

## Relationships

We support 2 ways of creating relationships:

1. Typing DBML code
2. Interacting directly on the diagrams itself, by dragging from field to field.

### Example

The below defines a 1-n relationship between `countries.code` to `users.country`.

```dbml
Ref: countries.code < users.country;
```

or use inline relationships:

```dbml
Table users {
  id int [primary key]
  country int [ref: > countries.code] // many-to-one
  ...
}
```

## Schemas

You can define the tables with full schema names:

```dbml
Table ecommerce.order_items {
  ...
}
```

Moreover, you can make cross-schemas relationships and use enums from different schemas:

```dbml
Table orders {
  id int [pk, ref: < ecommerce.order_items.order_id]
  status core.order_status
  ...
}

Enum core.order_status {
  ...
}
```

## Roadmap

-   [x] ~Live preview (eye icon in the top right corner / command palette)~
-   [x] ~Download SVG (in command palette)~
-   [x] ~Code Structure with layout of code~
-   [ ] Light/dark mode toggle
-   [ ] Zooming in/out
-   [ ] Change the ugly logo

## Demo

![Demo](./dbml-demo.gif)

## Appendix

This extension is a perfect complement to [vscode-dbml](vscode:extension/matt-meyers.vscode-dbml) (color syntaxing and SQL export commands).

## References

Here are some related projects used in this extension

[@softwaretechnik-berlin/dbml-renderer](https://github.com/softwaretechnik-berlin/dbml-renderer/)

## Authors

-   Previous author: [@Durandal14](https://www.github.com/durandal14)
-   Current maintainer: [@JakeMofa](https://github.com/JakeMofa)
