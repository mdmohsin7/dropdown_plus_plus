# dropdown_plus_plus

Simple and easy to use Dropdown in forms with search, keyboard navigation, offiline data source, remote data source and easy customization.

A maintained fork of [dropdown_plus](https://pub.dev/packages/dropdown_plus) with a lot more customisations.

## Getting Started

Simple Text Dropdown.

<img src="https://github.com/mdmohsin7/dropdown_plus_plus/blob/master/screenshots/screen1.png?raw=true"  width="35%" height="17%">
<img src="https://github.com/mdmohsin7/dropdown_plus_plus/blob/master/screenshots/screen2.png?raw=true"  width="35%" height="17%">


```
TextDropdownFormField(
  options: ["Male", "Female"],
  decoration: InputDecoration(
      border: OutlineInputBorder(),
      suffixIcon: Icon(Icons.arrow_drop_down),
      labelText: "Gender"),
  cursorColor: Colors.green,
  dropdownItemColor: Colors.red,
),
```

## Install

##### packages.yaml
```
dropdown_plus_plus: <lastest version>
```

## Customizable Example
 
<img src="https://github.com/mdmohsin7/dropdown_plus_plus/blob/master/screenshots/screen4.png?raw=true"  width="35%" height="17%">
<img src="https://github.com/mdmohsin7/dropdown_plus_plus/blob/master/screenshots/screen5.png?raw=true"  width="35%" height="17%">

```

 final List<Map<String, dynamic>> _roles = [
    {"name": "Super Admin", "desc": "Having full access rights", "role": 1},
    {
      "name": "Admin",
      "desc": "Having full access rights of a Organization",
      "role": 2
    },
    {
      "name": "Manager",
      "desc": "Having Magenent access rights of a Organization",
      "role": 3
    },
    {
      "name": "Technician",
      "desc": "Having Technician Support access rights",
      "role": 4
    },
    {
      "name": "Customer Support",
      "desc": "Having Customer Support access rights",
      "role": 5
    },
    {"name": "User", "desc": "Having End User access rights", "role": 6},
  ];


// ...
// ...

DropdownFormField<Map<String, dynamic>>(
    onEmptyActionPressed: () async {},
    dropdownItemSeparator: Divider(
      color: Colors.black,
      height: 1,
      ),
    decoration: InputDecoration(
        border: OutlineInputBorder(),
        suffixIcon: Icon(Icons.arrow_drop_down),
        labelText: "Access"),
    onSaved: (dynamic str) {},
    onChanged: (dynamic str) {},
    validator: (dynamic str) {},
    displayItemFn: (dynamic item) => Text(
    item['name'] ?? '',
    style: TextStyle(fontSize: 16),
    ),
    findFn: (dynamic str) async => _roles,
    filterFn: (dynamic item, str) =>
        item['name'].toLowerCase().indexOf(str.toLowerCase()) >= 0,
    dropdownItemFn: (dynamic item, position, focused,
            dynamic lastSelectedItem, onTap) =>
        ListTile(
    title: Text(item['name']),
    subtitle: Text(
        item['desc'] ?? '',
    ),
    tileColor:
        focused ? Color.fromARGB(20, 0, 0, 0) : Colors.transparent,
    onTap: onTap,
    ),
),
```

## Options

```
final bool autoFocus;
final bool Function(dynamic item, String str)? filterFn;
final bool Function(dynamic item1, dynamic item2)? selectedFn;
final Future<List<dynamic>> Function(String str) findFn;

final ListTile Function(
  dynamic item,
  int position,
  bool focused,
  bool selected,
  Function() onTap,
) dropdownItemFn;

final Widget Function(dynamic item) displayItemFn;
final InputDecoration? decoration;
final Color? dropdownColor;
final Color? cursorColor;
final DropdownEditingController<T>? controller;
final void Function(dynamic item)? onChanged;
final void Function(dynamic)? onSaved;
final String? Function(T?)? validator;
final double? dropdownHeight;
final TextStyle? searchTextStyle;
final String emptyText;
final String emptyActionText;
final Future<void> Function()? onEmptyActionPressed;
final Widget? dropdownItemSeparator;

```