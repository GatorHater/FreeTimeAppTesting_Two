Vacation Planner App Workflow
This document outlines the workflow for the Vacation Planner app, which helps users plan their trips by guiding them through a series of selections and storing their preferences.


App Navigation Flow
The app follows this general navigation pattern:
"Login → Options → Free Time Selection → Date Range → Planner Type → Vacation Type → 
People Count → Destination → Budget → Lodging → Transportation → Vacation Summary → 
Plan Vacation (Activities, Lodging, Transportation)"

Key Components
SelectionViewModel
This ViewModel stores user selections throughout the app:


previousSelection: Tracks what type of activity the user is planning (vacation, daycation, etc.)
plannerTypeSelected: Whether planning is solo/couple or group decision
destinations: List of destinations the user wants to visit
leaving: Departure location
transportNeeded: Whether transportation is needed
peopleSelected: Number of people (individual or group)
budget: User's budget for the trip
vacationTypeSelected: Type of vacation (family, romantic, etc.)
startDate and endDate: Trip dates
Screen-by-Screen Workflow
Login Screen


Enter username and password to access the app
Credentials are validated against properties file
Options Screen


Choose between "Set Your Free Time" and "View your Play Time"
Free Time Screen


Select type of activity (Vacation, Daycation, Organization, etc.)
Selection is stored in the ViewModel
Date Range Screen


Enter event details (summary, location, description)
Select start and end dates
Creates event in Google Calendar
Planner Screen


Choose between "Solo or Couple" and "Group Decides"
Selection determines planning approach
Vacation Type Screen


Select vacation category (Family, Romantic, Girls Trip, etc.)
People Count Screen


Choose between "Individual" or "Group"
Destination Screen


Add one or more destinations
Can add multiple destinations as needed
Budget Screen


Enter budget amount (optional)
App will track spending against budget
Lodging Screen


Select lodging preference (Hotel, B&B, Home Rental, etc.)
Transportation Screen


Indicate if transportation is needed
Enter departure location
Vacation Summary Screen


Review all selections made
Proceed to detailed planning
Plan Vacation Screen


Access tools for specific planning needs:
Things to Do
Lodging
Flight or Car Rental
Activity Screens


Things To Do: Search activities, access Groupon and TripAdvisor
Lodging Page: Browse accommodations, access Airbnb
Flight/Car Rental: Links to booking.com services
External Integrations
The app integrates with:


Google Calendar for scheduling
Groupon for activity deals
TripAdvisor for attractions and reviews
Booking.com for flights and car rentals
Airbnb for lodging options
Development Notes
When extending the app:


Add new screens to the NavHost in MainActivity
Add relevant state properties to SelectionViewModel
Ensure proper navigation between screens
Update summary screen to display new information
For API integrations, replace mock functions with actual API calls to services like Booking.com and Groupon.
