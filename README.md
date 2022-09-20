# blackjack-card-game
import random
from replit import clear
def deal_card():
  """Returns a random card from deck"""
  cards=[11,2,3,4,5,6,7,8,9,10,10,10,10]
  random_card=random.choice(cards) 
  return random_card
def calc_score(cards):
  if 11in cards and 10 in cards and len(cards)==2:
    return 0
  if 11 in cards and sum(cards)>21:
    cards.remove(11)
    cards.append(10)
  return sum(cards)
def compare(user_score,computer_score):
  if user_score==computer_score:
    return "draw"
  elif computer_score==0:
   return "Lose,opponent has blackjack"
  elif user_score==0:
    return "Win.with a blackjack"
  elif computer_score>21:
    return "oppponent went over 21, You win"
  elif user_score > computer_score:
    return "you win"
  else:
    return "You lose"
def play_game():
  print(
 """
.------.            _     _            _    _            _    
|A_  _ |.          | |   | |          | |  (_)          | |   
|( \/ ).-----.     | |__ | | __ _  ___| | ___  __ _  ___| | __
| \  /|K /\  |     | '_ \| |/ _` |/ __| |/ / |/ _` |/ __| |/ /
|  \/ | /  \ |     | |_) | | (_| | (__|   <| | (_| | (__|   < 
`-----| \  / |     |_.__/|_|\__,_|\___|_|\_\ |\__,_|\___|_|\_\\
      |  \/ K|                            _/ |                
      `------'                           |__/           
"""
                   


    
  )
  user_card=[]
  computer_card=[]
  is_game_over=False
  for i in range(2):
    user_card.append(deal_card())
    computer_card.append(deal_card())
  while not is_game_over:
    user_score=calc_score(user_card)
    computer_score=calc_score(computer_card)
    print(f"user:{user_score}, comp_score:{computer_score}")
    print(f"comp first card{computer_card[0]}")
    if user_score==0 or computer_score==0 or user_score>21:
      is_game_over=True
    else:
      user_continue=input("type 'y' to get another card, type'n' to pass: ")
      if user_continue=='y':
        user_card.append(deal_card())
      else:
        is_game_over=True
  
  while computer_score !=0 and computer_score<17:
    computer_card.append(deal_card())
    computer_score= calc_score(computer_card)  
  print(compare(user_score,computer_score))
  print(f"user_final hand:{user_card},final score:{user_score}")
  print(f"Computer final hand:{computer_card},final score:{computer_score}")

while input("Do you wantto play a game of Blackjack? type'y' or 'n'")=="y":
  clear()
  play_game()
  
