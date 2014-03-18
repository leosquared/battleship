from random import randint

board = []

#creates 5 x 5 board consisting of zeros
for x in range(5):
    board.append(["O"] * 5)
    
#organizes the boards so all rows are aligned together when printed
def print_board(board):
    for row in board:
        print " ".join(row)
#introduction to the game
print "Let's play Battleship!"
print "Pick a row (1-5) and pick a column (1-5). If you sink 10 ships in less than 20 turns, you win!"
print_board(board) 

#returns random choice for a row/col picking a number 0 - 4
def choose_row(board):
    return randint(0, len(board) - 1)
    
def choose_col(board):
    return randint(0, len(board) - 1)

new_list=[]

# To make ships we will tak a random list of 14 numbers that will be rows, and 14 numbers fo cols
# We turn these values into strings and them zip them, so that we can join them together into 1 string
# The list should now have a len of 10, we remove duplicates  
def make_the_ships(board):
	row_list =[]
	col_list =[]
 	i = 14
	while i>0:
		row_list.append(str(choose_row(board)))
		col_list.append(str(choose_col(board)))
		i-=1
	for x, y in zip(row_list, col_list):
		new_list.append(''.join(x+y))
	return list(set(new_list))
	
# new_board is the new list of point with duplicates removed
new_board = make_the_ships(board)

# makes sure there are 14 items in the list
while len(new_board)<14:
	new_board.append(''.join(str(choose_row(board))+str(choose_col(board))))
	list(set(new_board))

# how man times you have sunk the ship
sunk = 0

# for 20 turns, if you get 10 ships then you win
# Also checks to see that your guess is between 0, 4 and makes sure that to tell you if you've already guessed that spot
for turn in range(20):
	print "Turn", turn + 1
	guess_row = int(raw_input("Guess Row: "))-1
	guess_col = int(raw_input("Guess Col: "))-1
	guess = ''.join(str(guess_row)+str(guess_col))
	if guess in new_board:
		board[guess_row][guess_col] = "*"
		sunk += 1
		if turn==19:
			print "Game Over"
			break
		elif sunk == 10:
			print "You Win. All ships have sunk!"
			break
		else:
			print "Sunk {0}, {1} to go!".format(sunk, 10-sunk)
				
	else:
		if (guess_row < 0 or guess_row > 4) or (guess_col < 0 or guess_col > 4):
			print "Oops, that's not even in the ocean."
			if turn==19:
				print "Game Over"
		elif(board[guess_row][guess_col] == "X"):
			print "You guessed that one already."
			if turn==19:
				print "Game Over"
		else:
			print "You missed my battleship!"
			board[guess_row][guess_col] = "X"
			if turn==19:
				print "Game Over"
	print_board(board)

