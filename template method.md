``` dart
abstract class Game {
  void initialize();
  void startPlay();
  void endPlay();

   void play() {
      initialize();
      startPlay();
      endPlay();
  }
}

class Chess extends Game {
  @override
  void endPlay() {
    print("Chess Game Finished!");
  }

  @override
  void initialize() {
    print("Chess Game Initialized! Start playing.");
  }

  @override
  void startPlay() {
    print("Chess Game Started. Enjoy the game!");
  }
}

void main() {
  Game game = Chess();
  game.play();
}



```
