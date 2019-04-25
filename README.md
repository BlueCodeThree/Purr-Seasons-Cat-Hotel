# 🐱 PURR SEASONS

## Ruby Terminal App

by Carlie Hamilton and Natalie Sargent

![Purr Seasons Terminal App](./docs/purr.gif)

Link to the repository - [https://github.com/natkat9/terminal-app](https://github.com/natkat9/terminal-app "Our Github Repository")

## ℹ️ About the App

### Description

This app is a MVP of a Cat Hotel Booking System for the Purr Seasons Cat Hotel. The aim of this MVP was to create a booking system that allows one cat to create one booking, with a choice of several rooms in a seven day period.

### Functionality

![Purr Seasons Welcome](./docs/welcome.jpg "Welcome to the Purr Seasons")

On commencing the application, the user is prompted to enter their cat's name. From there they are presented with a menu prompt where they can select to make a new booking, view an existing booking, view room types, view information about the hotel, or to exit the app.

![menu](./docs/menu.jpg "Main Menu")

When making a new booking the user is given the option to select one of 3 room types.  They are then prompted to select what days they would like to stay, from the available days.  The booking is created and displayed for the user.  The user is then prompted to press any key to return to the main menu.

![creating a booking](./docs/2019-04-24-app-example.jpg "Creating a booking")

If the user has created a booking they can select to view an existing booking, and their booking will be displayed.  Otherwise, they are advised that they do not yet have a booking and they will be prompted to return to the main menu.

![room information](./docs/room.jpg "Room Information")

The user is able to see information about each room type, as well as details about the hotel. The room information page shows the availability of the room, which changes once a user has booked into the room.

![exit](./docs/exit.jpg "Exit Message")

The app will display a personalised message on exit, depending on if you have made a booking or not.

### Instructions for Installation and Use

1. You will need ruby installed on your computer. [Download ruby here](https://www.ruby-lang.org/en/).
2. You will also need the Bundler gem installed. It comes with the main ruby installation, but if you do not have it on your machine, you can install it with the following command:

`gem install bundler`

3. Fork or clone this repository down to your local computer
4. To install the gem(s) required, navigate to the location of the `/src` folder in repostitory on your computer, and use the command:

`bundle install`

5. Run the app with:

`ruby main.rb`

## 📝 Design & Planning Process

When planning this application, we brainstormed a couple of ideas. We initially thought of a medication tracking app, but we felt that it was important to keep that app simple so that it would be accessible for it's target audience - and because of this we wouldn't have an opportunity to have some fun.

![brainstorming](./docs/planning.jpg "Brainstorming")

We decided to settle on the Cat Hotel Booking System as we felt that we could be creative with it.

### Initial Flow Chart

This was our initial flow chart and structure ideas for app.

![flow chart](./docs/flow-chart.png)

### Timeline

#### Day 0

Together we brainstormed app ideas and worked on potential structure and flow of these ideas, before settling on the Cat Hotel Booking System. 

#### Day 1

We worked together with pair programming to create the basic structure of the app. We utilized a gem TTY-Prompt for the menus so that our user can easily select multiple items at once. As we went along we tested our app with each new feature.

#### Day 2

In the morning we worked on finalising the functionality of the app as well as commenting, the look of the app, and cleaning up code. We implemented a stretch goal to include activities to book into.

In the afternoon we worked on documentation for the app. We ran out of time to complete the activities extension, so the extra code was archived.

## 💻 App Creation

### Collaboration

We used VS Code Live Share to work together. We commited to git regularly to back up our code. We also had a slack channel to communicate together.

![slack](./docs/2019-04-24-Slack.jpg "Slack")

#### Trello

We used Trello to organise what we needed to do. We had user stories to drive what features we needed to implement. We used custom fields to estimate the sizing (how long a feature would take) as well as the priority of the feature (low, med and high priority). We had labels for future enhancement ideas (stretch goals) as well as for any bugs we encountered.

We ended up not assigning tasks to people in trello as we did a lot of pair programing together.

Below are some examples of our Trello board at various points in our development.

Day 1
Includes user stories:
![trello day 1](./docs/2019-04-23-Trello.jpg "Trello Day 1")

![trello end day 1](./docs/2019-04-23-End-Day-Trello.jpg "End Day 1 Trello")

Day 2
![trello day 2](./docs/2019-04-24-Trello01.jpg "Trello Day 2")

### ✔️ Testing

We tested our code at every stage of the process, and recorded our tests in a spreadsheet.

![tests1](./docs/tests1.jpg "test spreadsheet")
![tests2](./docs/tests2.jpg "test spreadsheet")
![tests3](./docs/tests3.jpg "test spreadsheet")

### Code Structure

- `main.rb` is the main document that controls the flow of the program.

- `classes/hotel.rb` holds the Hotel class and represents the hotel. This class holds the information of the hotel, such as the address and phone number. It also holds a list of the rooms in the hotel. It is used for methods that show the rooms all together.

- `classes/room.rb` holds the Room super class, as well as it's sub classes (which represents different types of rooms). This class deals with methods that pertain to a room, such as showing the availability of a room.

- `classes/cat.rb` holds the cat class. The cat class represents the user, and holds the details of the cat as well as a booking that is associated with the cat when it (the booking) is created. The booking is initialized with the cat as "nil" - this is used during the main flow of the program, as different menus show different things depending on if there is a booking or not.

- `classes/booking.rb` is initialized once the user has selected a room and days. It represents the booking. The methods display the booking and it also calculates the total price of the booking.

- `methods/headers.rb` is a file that holds some methods to make the main flow of the program look pretty, including fancy headers.

### Gem 💎 TTY-Prompt

We chose to use the TTY-Prompt gem, as this cuts out user error when accessing the menus. The user can not input incorrect information, but instead selects from a list.

One difficulty with using this gem is we had to change our data (such as a room's availability that is stored in a hash) to a format that the menu recognizes.  We believe that it is worth this extra step in the code, as we do not have to worry about incorrect user input, it makes navigating the application easier, and also because the menu is formatted nicely.

We could have captured the original data so that is matched the requirements of the gem, but we thought that the code would be more extensible for future changes if we kept it as is, and changed to specifically for the menu. 

It is recommended to use a font that supports unicode for this gem to look extra pretty.

#### Corner Cases - Some Examples

- If the cat name is accidentally not given, we implemented a loop so that the user has the opportunity to write in the cat's name. If the user does not enter anything after three tries, it creates a cat object named "The Cat Without A Name." In future extensions we could implement the program so that a cat is created only when making a booking, or have the input of only being accepted with certain characters in a certain format with regex.

- We avoided many corner cases by having our navigation through the TTY-Prompt. One challenge using this gem was to format our data for the prompt, and also getting the correct data we want back from the menu (such as changing a string to a symbol, to update our availability hash). However, using this meant that we could avoid a user inputting an invalid option.

- There was the possibility of the user selecting "view booking" if a booking hadn't been booked in yet. We set the status of a booking to nil inside the cat class when it is initialized so that we could create an if statement around if there was a booking or not. This way, if the user tries to view a booking that doesn't exist, they will see a friendly error message.

- At the moment if you select the days out of order, it will display them out of order in the booking. The user can also miss a day (for instance, books into a Monday, then Wednesday). A future extension could be to make it so that the user can only book into consecutive days, by implementing a "start date" and "end date" for the booking.

#### Future Extensions

The code has been designed to be modular and DRY as possible, with thought toward how the app could be modified in the future.

Some possible future implementations include:

- A user is able to go to a previous screen during the booking process if they made a mistake.
- Display unicode "X" on the room information page when a day is booked out.
- Currently the app does not save the booking in any way. We would implement saving the booking and also sending a copy of the booking to the user's email.
- A user will be able to log in with a password, store all their bookings and see past bookings.
- The user will be able to pay for the booking using a credit card.
- Allow the user to booking into more than just one week but any date for any amount of time.
- Allow the app to accept multiple cats, and multiple bookings, and be able to implement multiple hotels (such as hotels in different locations).
- Get the cat's age and recommend certain rooms or activities based on their age.
- Allow the user to enter information regarding special considerations for their cat, for example if their cat has any behavioural, medical or dietary concerns.
- Style the colours of the app using the gem [pastel](https://github.com/piotrmurach/pastel)

We tried to implement a future extension - adding activities to the order. Code for this can be viewed in the folder `./archive-activities` - this is just a copy of where the app was at when the extension was abandoned. This would have used an activity class and added the activities to the booking in a similar way to the rooms being added. We just ran out of time to implement it the way we would have liked.

![extension - activities](./docs/2019-04-24-activities.jpg)

## 🌏 Impact

### Accessibility

The app has clear instructions for screen readers, however to make the app more accessible to the vision impaired we could implement a text-to-speech gem in the future.

The app is able to be navigated using only the keyboard, and the text colour and size has not been manually changed - so the user can set their own peferred colours and font size with their terminal.

The TTY-Prompt gem has made the app more accessible for a command line interface, as the user doesn't have to type in their desired choice. This also makes it harder for the user to input an incorrect response that may bring up an error.

### Potential Ethical, Legal and Broader Societal Implications

In a future extensions we will have to consider the legal and ethical ramifications of storing user data and taking money online from the user. If this was a business they would also have to consider having a disclaimer that the user would agree to with the conditions of making a booking and using the app.

The hotel must consider the safety and wellbeing of their cat guests.  In a future extension, we would add the facility for user to record any special needs requests, for example if their cat has any medical, dietary or behavioural concerns that the hotel may need to accommodate.

(Tongue in cheek:) Dogs may feel discriminated against for not being allowed in the Purr Seasons, but for the health and safety of our guests, this is a dog-free hotel.

Apart from only allowing cats at the hotel, we did not discover any other political, cultural, racial or gender issues with this app. After all, everyone likes cat videos.