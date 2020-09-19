# Tic-Tac-Toe
```python


class game:
    __board = ["_" for x in range(0, 9)]
    __coordinate = {
        (1, 3): 0,
        (2, 3): 1,
        (3, 3): 2,
        (1, 2): 3,
        (2, 2): 4,
        (3, 2): 5,
        (1, 1): 6,
        (2, 1): 7,
        (3, 1): 8
    }

    def __init__(self):
        count = 0
        while True:
            self.__draw_board()
            if count % 2 == 0:
                self.__input_into_board("X")
            else:
                self.__input_into_board("O")
            count += 1
            if count > 4:
                player_x = self.__check_win("X")
                player_y = self.__check_win("O")
                if player_x:
                    self.__draw_board()
                    print("X wins")
                    break
                elif player_y:
                    self.__draw_board()
                    print("O wins")
                    break
            if count >= 9:
                self.__draw_board()
                print("Draw")
                break

    def __draw_board(self):
        print('---------')
        for i in range(3):
            print('|', self.__board[0+i*3],
                  self.__board[1+i*3], self.__board[2+i*3], "|")
        print('---------')

    def __input_into_board(self, player_symbols):

        while True:

            player_input = input("Enter the coordinates: ")
            player_input = player_input.split()
            try:
                player_input = [int(item) for item in player_input]
                if player_input[0] > 3 or player_input[1] > 3:
                    print("Coordinates should be from 1 to 3!")
                else:
                    index = self.__coordinate.get(tuple(player_input))
                    if self.__board[index] == "X" or self.__board[index] == 'O':
                        print("This cell is occupied! Choose another one!")
                    else:
                        self.__board[index] = player_symbols
                        break
            except:
                print("You should enter numbers!")

    def __check_win(self, player_symbols):
        if self.__board[0] == player_symbols:
            if self.__board[1] == player_symbols and self.__board[2] == player_symbols:
                return True
            elif self.__board[4] == player_symbols and self.__board[8] == player_symbols:
                return True
            elif self.__board[3] == player_symbols and self.__board[6] == player_symbols:
                return True
        if self.__board[1] == player_symbols:
            if self.__board[4] == player_symbols and self.__board[7] == player_symbols:
                return True
        if self.__board[2] == player_symbols:
            if self.__board[5] == player_symbols and self.__board[8] == player_symbols:
                return True
            elif self.__board[4] == player_symbols and self.__board[6] == player_symbols:
                return True
        if self.__board[3] == player_symbols:
            if self.__board[4] == player_symbols and self.__board[5] == player_symbols:
                return True
        if self.__board[6] == player_symbols:
            if self.__board[7] == player_symbols and self.__board[8] == player_symbols:
                return True
        return False


if __name__ == "__main__":
    game()



```
