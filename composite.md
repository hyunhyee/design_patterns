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
