[출처: https://medium.com/gitconnected/understanding-the-composite-pattern-in-flutter-ba1a3cddf5d]

Composite Pattern 한 그룹의 객체를 하나의 객체인 것처럼 사용

```dart
class Item {
  final String title;
  final String subtitle;

  Item({required this.title, required this.subtitle});
}

class ItemList extends StatelessWidget {
  final List<Item> items;

  ItemList({required this.items});

  @override
  Widget build(BuildContext context) {
    return ListView.builder(
      itemCount: items.length,
      itemBuilder: (context, index) {
        return ListTile(
          title: Text(items[index].title),
          subtitle: Text(items[index].subtitle),
        );
      },
    );
  }
}

class HomePage extends StatelessWidget {
  final List<Item> items = [
    Item(title: 'Item 1', subtitle: 'Subtitle 1'),
    Item(title: 'Item 2', subtitle: 'Subtitle 2'),
    Item(title: 'Item 3', subtitle: 'Subtitle 3'),
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Home Page'),
      ),
      body: Container(
        child: ItemList(items: items),
      ),
    );
  }
}
```

```dart
abstract class Component {
  void operation();
}

class Leaf extends Component {
  @override
  void operation() {
    print("Leaf operation performed.");
  }
} ❓이거랑 template method pattern 이랑 다른게 뭐지?

class Composite extends Component {
  List<Component> _children = [];

  void add(Component component) {
    _children.add(component);
  }

  void remove(Component component) {
    _children.remove(component);
  }

  @override
  void operation() {
    print("Composite operation performed.");
    for (var component in _children) {
      component.operation();
    }
  }
}

void main() {
  var leaf1 = Leaf();
  var leaf2 = Leaf();
  var leaf3 = Leaf();

  var composite1 = Composite();
  composite1.add(leaf1);
  composite1.add(leaf2);

  var composite2 = Composite();
  composite2.add(leaf3);
  composite2.add(composite1);

  composite2.operation();
}

```
