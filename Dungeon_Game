# Jeremiah Ransom
# project 2
# text based game

# A dictionary for the simplified text game
# The dictionary links a room to other rooms and also contains the items
rooms = {'Great Hall': {'West': 'Armory', 'East': 'Library', 'North': 'Sanctuary', 'item': None},
         'Armory': {'East': 'Great Hall', 'South': 'Forge', 'item': 'Cosmic Armor'},
         'Forge': {'North': 'Armory', 'item': 'Cosmic Sword'},
         'Library': {'West': 'Great Hall', 'South': 'Observatory', 'item': 'Meteor Scroll'},
         'Observatory': {'North': 'Library', 'item': 'Memory Orb'},
         'Sanctuary': {'South': 'Great Hall', 'North': 'Crystal Cavern', 'item': 'Mystic Cloak'},
         'Crystal Cavern': {'South': 'Sanctuary', 'North': 'Dark Lair', 'item': 'Cosmic Shield'},
         'Dark Lair': {'South': 'Crystal Cavern', 'item': None},
         }
# Inventory
inventory = []
#items required to defeat the Villan
required_items = ['Cosmic Armor', 'Cosmic Sword', 'Meteor Scroll', 'Memory Orb', 'Mystic Cloak', 'Cosmic Shield']


# function to display current status
def show_status():
    print('You are in the', current_room)
    print('Inventory:', inventory)

    if rooms[current_room]['item'] is not None:
        print('You see a', rooms[current_room]['item'])



# Starting Room
current_room = 'Great Hall'

# Gameplay loop
while current_room != 'exit':
    show_status()

    # Get User Input
    command = (input('Enter direction or Command(go North, go South, go East, go West or N/S/E/W), '
                     ' "get item" or "exit": ').lower().strip())

    # Exit game
    if command.lower() == 'exit':
        current_room = 'exit'
        print('Thanks for playing!')


    # Get Items
    elif command.startswith('get '):
            item_name = command[4:].title()

            if command == 'get item':
                print('You picked up', item_name)

                if rooms[current_room]['item'] is not None:
                    item = rooms[current_room]['item']
                    inventory.append(item)
                    rooms[current_room]['item'] = None
                    print(item, 'added to your inventory.')
                else:
                    print('There is no item here')

    else:
        #remove "go " if present
        if command.startswith('go '):
            command = command[3:]


        # Direction mapping
        direction = {'n': 'North', 's': 'South', 'e': 'East', 'w': 'West',
                     'north': 'North', 'east': 'East', 'west': 'West'}

        #validate  direction input

        if command in direction:
            direction = direction[command]
            # Entrance barrier
            if current_room == "Great Hall" and direction == "South":
                print('\nA powerful magical barrier blocks the exit!')
                print('You cannot escape the castle.')

            elif direction in rooms[current_room]:
                current_room = rooms[current_room][direction]
                print('You move to the', current_room)


                #!!!!win/lose check for boss fight!!!!
                if current_room == 'Dark Lair':

                    if all(item in inventory for item in required_items):
                        print('\nYou confront the Villain Garland fully equipped!')
                        print('You have defeated Garland! You win')
                    else:
                        print('\nYou have entered the Dark Lair unprepared...')
                        print('The Villain Garland cuts you in two. You lose.')
                        print('Better luck next time!, Please play again!')
                        current_room = 'exit'
            else:
                print('You cant go that way!')
        else:
            print('Invalid command!')