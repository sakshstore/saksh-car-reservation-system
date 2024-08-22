
# Saksh Car Reservation System

A Node.js package for managing car reservations, including functionalities for adding cars, making reservations, canceling reservations, modifying reservations, and adding reviews.

## Installation

To install the package, use npm:




```bash
npm install saksh-car-reservation-system
```



###  Class: SakshCarReservationSystem
- Constructor: constructor(dbUri)
- Parameters: dbUri (String) - The MongoDB connection URI.
- Description: Initializes the reservation system, connects to MongoDB, and initializes the review system.

Method: sakshConnect()
- Description: Connects to the MongoDB database using the provided URI.

Method: sakshAddCar(make, model, year)
- Parameters:

- make (String) - The make of the car.
- model (String) - The model of the car.
- year (Number) - The year of the car.
- Description: Adds a new car to the system.

Method: sakshListAvailableCars()
- Description: Lists all available cars in the system.

Method: sakshMakeReservation(carId, userId, customerName, startDate, endDate, bookingCharge)
- Parameters:

- carId (String) - The ID of the car to be reserved.

- userId (String) - The ID of the user making the reservation.

- customerName (String) - The name of the customer.

- startDate (Date) - The start date of the reservation.

- endDate (Date) - The end date of the reservation.

- bookingCharge (Number) - The booking charge for the reservation.

- Description: Makes a reservation for a car.

Method: sakshCancelReservation(reservationId)
- Parameters: reservationId (String) - The ID of the reservation to be canceled.

- Description: Cancels a reservation if it hasn't started yet.

Method: sakshModifyReservation(reservationId, newStartDate, newEndDate)
- Parameters:

- reservationId (String) - The ID of the reservation to be modified.

- newStartDate (Date) - The new start date for the reservation.

- newEndDate (Date) - The new end date for the reservation.

- Description: Modifies an existing reservation if there are no conflicting reservations.

Method: sakshListReservations()
- Description: Lists all reservations in the system.

Method: sakshGetReservationHistory(userId)
- Parameters: userId (String) - The ID of the user.

- Description: Gets the reservation history for a specific user.

Method: sakshUpdatePaymentStatus(reservationId, status)
- Parameters:

- reservationId (String) - The ID of the reservation.

- status (String) - The new payment status.

- Description: Updates the payment status of a reservation.

Method: sakshSearchReservations(filters)
- Parameters: filters (Object) - The filters to apply when searching for reservations.

- minCharge (Number) - The minimum booking charge.

- maxCharge (Number) - The maximum booking charge.

- carType (String) - The type of car.

- startDate (Date) - The start date for the search.

- endDate (Date) - The end date for the search.

- location (String) - The location of the car.

- Description: Searches for reservations based on the provided filters.

Method: sakshAddReview(reservationId, carId, userId, rating, comment)
- Parameters:

- reservationId (String) - The ID of the reservation.

- carId (String) - The ID of the car.

- userId (String) - The ID of the user.

- rating (Number) - The rating given by the user.

- comment (String) - The comment provided by the user.

- Description: Adds a review to a reservation.

Method: sakshListReviews(reservationId, carId)
- Parameters:

- reservationId (String) - The ID of the reservation (optional).

- carId (String) - The ID of the car (optional).

- Description: Lists reviews for a specific reservation or car.

Class: ReviewSystem
Method: sakshAddReview(reservationId, carId, userId, rating, comment)
- Parameters:

- reservationId (String) - The ID of the reservation.

- carId (String) - The ID of the car.

- userId (String) - The ID of the user.

- rating (Number) - The rating given by the user.

- comment (String) - The comment provided by the user.

- Description: Adds a review to a reservation.

Method: sakshListReviews(reservationId, carId)
- Parameters:

- reservationId (String) - The ID of the reservation (optional).

- carId (String) - The ID of the car (optional).

- Description: Lists reviews for a specific reservation or car.

This detailed description should help users understand the purpose and usage of each function in the saksh-car-reservation-system module. Let me know if you need any further assistance!





Usage
Importing the Package
```
const SakshCarReservationSystem = require('saksh-car-reservation-system');
```

Connecting to MongoDB
```
const dbUri = 'your_mongodb_uri';
const reservationSystem = new SakshCarReservationSystem(dbUri);
```

Adding a New Car
```
await reservationSystem.sakshAddCar('Toyota', 'Camry', 2021);
```

Listing All Available Cars
```
const availableCars = await reservationSystem.sakshListAvailableCars();
console.log(availableCars);
```

Making a Reservation
```
const reservation = await reservationSystem.sakshMakeReservation(
'carId123',
'userId123',
'John Doe',
'2024-09-01',
'2024-09-10',
100
);
console.log(reservation);
```


Canceling a Reservation
```
const canceledReservation = await reservationSystem.sakshCancelReservation('reservationId123');
console.log(canceledReservation);

Modifying a Reservation
const modifiedReservation = await reservationSystem.sakshModifyReservation(
'reservationId123',
'2024-09-05',
'2024-09-15'
);
console.log(modifiedReservation);
```



Listing All Reservations
```
const reservations = await reservationSystem.sakshListReservations();
console.log(reservations);
```



Getting Reservation History for a User
```
const userReservations = await reservationSystem.sakshGetReservationHistory('userId123');
console.log(userReservations);
```



Updating Payment Status of a Reservation
```
const updatedReservation = await reservationSystem.sakshUpdatePaymentStatus('reservationId123', 'paid');
console.log(updatedReservation);
```


Searching for Reservations
```
const filters = {
minCharge: 50,
maxCharge: 150,
carType: 'Sedan',
startDate: '2024-09-01',
endDate: '2024-09-30',
location: 'New York'
};

const searchResults = await reservationSystem.sakshSearchReservations(filters);
console.log(searchResults);

```


Adding a Review to a Reservation
```
const review = await reservationSystem.sakshAddReview(
'reservationId123',
'carId123',
'userId123',
5,
'Great experience!'
);
console.log(review);
```


Listing Reviews for a Reservation or Car
```
const reviews = await reservationSystem.sakshListReviews('reservationId123', 'carId123');
console.log(reviews);
```


Example
Here's an example to help you get started:

```
const SakshCarReservationSystem = require('saksh-car-reservation-system');

// MongoDB connection URI
const dbUri = 'your_mongodb_uri';

// Initialize the reservation system
const reservationSystem = new SakshCarReservationSystem(dbUri);

// Connect to MongoDB
reservationSystem.sakshConnect().then(async () => {
try {
// Add a new car
await reservationSystem.sakshAddCar('Toyota', 'Camry', 2021);
console.log('Car added successfully');

// List all available cars
const availableCars = await reservationSystem.sakshListAvailableCars();
console.log('Available Cars:', availableCars);

// Make a reservation
const reservation = await reservationSystem.sakshMakeReservation(
availableCars[0]._id,
'userId123',
'John Doe',
'2024-09-01',
'2024-09-10',
100
);
console.log('Reservation made:', reservation);

// Add a review to the reservation
const review = await reservationSystem.sakshAddReview(
reservation._id,
availableCars[0]._id,
'userId123',
5,
'Great experience!'
);
console.log('Review added:', review);

// List reviews for the car
const reviews = await reservationSystem.sakshListReviews(null, availableCars[0]._id);
console.log('Reviews for the car:', reviews);

// Modify the reservation
const modifiedReservation = await reservationSystem.sakshModifyReservation(
reservation._id,
'2024-09-05',
'2024-09-15'
);
console.log('Reservation modified:', modifiedReservation);

// Cancel the reservation
const canceledReservation = await reservationSystem.sakshCancelReservation(reservation._id);
console.log('Reservation canceled:', canceledReservation);

// List all reservations
const reservations = await reservationSystem.sakshListReservations();
console.log('All Reservations:', reservations);

// Get reservation history for a user
const userReservations = await reservationSystem.sakshGetReservationHistory('userId123');
console.log('User Reservation History:', userReservations);

// Update payment status of a reservation
const updatedReservation = await reservationSystem.sakshUpdatePaymentStatus(reservation._id, 'paid');
console.log('Payment status updated:', updatedReservation);

// Search for reservations based on filters
const filters = {
minCharge: 50,
maxCharge: 150,
carType: 'Sedan',
startDate: '2024-09-01',
endDate: '2024-09-30',
location: 'New York'
};
const searchResults = await reservationSystem.sakshSearchReservations(filters);
console.log('Search Results:', searchResults);

} catch (error) {
console.error('Error:', error);
}
});
```


### License
This project is licensed under the MIT License.

#support

susheel2339 @ gmail.com
