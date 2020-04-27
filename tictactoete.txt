
def display_board(board):
    print(' | | ')
    print(board[9]+'|'+board[8]+'|'+board[7])
    print('_|_|_')
    print(' | | ')
    print(board[6]+'|'+board[5]+'|'+board[4])
    print('_|_|_')
    print(' | | ')
    print(board[3]+'|'+board[2]+'|'+board[1])
    print(' | | ')

def player_input():
    marker=''
    while marker!='x' and marker!='o':
        marker=input('Player 1 choose x or o :  ')
    player1=marker
    if player1=='x':
        player2='o'
    else:
        player2='x'
    return (player1,player2)

def placemarker(board,marker):
    posi=int(input("Enter position: "))
    if board[posi]=='x' or board[posi]=='o':
        print("\nPlease enter valid position\n")
        placemarker(board,marker)
    board[posi]=marker
    display_board(board)
    return board

def check(b,mark):
    if b[1]==b[2]==b[3]==mark or b[1]==b[4]==b[7]==mark or b[1]==b[5]==b[9]==mark or b[2]==b[5]==b[8]==mark or b[3]==b[6]==b[9]==mark or  b[4]==b[5]==b[6]==mark or  b[5]==b[3]==b[7]==mark or  b[7]==b[8]==b[9]==mark:
        return 1
    else:
        return 0

status=input('Do you want to play tic-tac-toa? Y/N: ')
while status=='Y':
    test_board=[' ','1','2','3','4','5','6','7','8','9']
    display_board(test_board)
    p1,p2=player_input()
    for i in range(0,9):
        if i%2==0:
            print('Player2 ')
            test_board=placemarker(test_board,p2)
            win=check(test_board,p2)
            if win==1:
                print("Player 2 won")
                break;
            else:
                continue
        else:
            print('Player1 ')
            test_board=placemarker(test_board,p1)
            win=check(test_board,p1)
            if win==1:
                print("Player 1 won")
                break;
            else:
                continue
    if win!=1:
            print("It is a tie")
        
    status=input('Do you want to play tic-tac-toa? Y/N: ')