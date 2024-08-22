
# Saksh Car Reservation System

A Node.js package for managing car reservations, including functionalities for adding cars, making reservations, canceling reservations, modifying reservations, and adding reviews.

## Installation

To install the package, use npm:

```bash
npm install saksh-car-reservation-system
```


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
```


Modifying a Reservation
```
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

Searching for Reservations
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

Listing Reviews for a Reservation or Car
const reviews = await reservationSystem.sakshListReviews('reservationId123', 'carId123');
console.log(reviews);

Example
Here's an example to help you get started:

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
### support

for anything contact susheel2339 @ gmail.com

### License
This project is licensed under the MIT License.
