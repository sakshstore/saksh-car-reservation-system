
# Saksh Car Reservation System

A Node.js package for managing car reservations, including functionalities for adding cars, making reservations, canceling reservations, modifying reservations, and adding reviews.

## Installation

To install the package, use npm:




```bash
npm install saksh-car-reservation-system
```





 Here’s your code with GitHub-flavored Markdown formatting added for better readability:

```markdown
## Function: `sakshConnect()`
- **Description**: Connects to the MongoDB database using the provided URI.
- **Usage**:
  ```javascript
  await reservationSystem.sakshConnect();
  ```

## Function: `sakshAddCar(make, model, year)`
- **Parameters**:
  - `make` (String) - The make of the car.
  - `model` (String) - The model of the car.
  - `year` (Number) - The year of the car.
- **Description**: Adds a new car to the system.
- **Usage**:
  ```javascript
  await reservationSystem.sakshAddCar('Toyota', 'Camry', 2021);
  ```

## Function: `sakshListAvailableCars()`
- **Description**: Lists all available cars in the system.
- **Usage**:
  ```javascript
  const availableCars = await reservationSystem.sakshListAvailableCars();
  console.log(availableCars);
  ```

## Function: `sakshMakeReservation(carId, userId, customerName, startDate, endDate, bookingCharge)`
- **Parameters**:
  - `carId` (String) - The ID of the car to be reserved.
  - `userId` (String) - The ID of the user making the reservation.
  - `customerName` (String) - The name of the customer.
  - `startDate` (Date) - The start date of the reservation.
  - `endDate` (Date) - The end date of the reservation.
  - `bookingCharge` (Number) - The booking charge for the reservation.
- **Description**: Makes a reservation for a car.
- **Usage**:
  ```javascript
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

## Function: `sakshCancelReservation(reservationId)`
- **Parameters**:
  - `reservationId` (String) - The ID of the reservation to be canceled.
- **Description**: Cancels a reservation if it hasn't started yet.
- **Usage**:
  ```javascript
  const canceledReservation = await reservationSystem.sakshCancelReservation('reservationId123');
  console.log(canceledReservation);
  ```

## Function: `sakshModifyReservation(reservationId, newStartDate, newEndDate)`
- **Parameters**:
  - `reservationId` (String) - The ID of the reservation to be modified.
  - `newStartDate` (Date) - The new start date for the reservation.
  - `newEndDate` (Date) - The new end date for the reservation.
- **Description**: Modifies an existing reservation if there are no conflicting reservations.
- **Usage**:
  ```javascript
  const modifiedReservation = await reservationSystem.sakshModifyReservation(
    'reservationId123',
    '2024-09-05',
    '2024-09-15'
  );
  console.log(modifiedReservation);
  ```

## Function: `sakshListReservations()`
- **Description**: Lists all reservations in the system.
- **Usage**:
  ```javascript
  const reservations = await reservationSystem.sakshListReservations();
  console.log(reservations);
  ```

## Function: `sakshGetReservationHistory(userId)`
- **Parameters**:
  - `userId` (String) - The ID of the user.
- **Description**: Gets the reservation history for a specific user.
- **Usage**:
  ```javascript
  const userReservations = await reservationSystem.sakshGetReservationHistory('userId123');
  console.log(userReservations);
  ```

## Function: `sakshUpdatePaymentStatus(reservationId, status)`
- **Parameters**:
  - `reservationId` (String) - The ID of the reservation.
  - `status` (String) - The new payment status.
- **Description**: Updates the payment status of a reservation.
- **Usage**:
  ```javascript
  const updatedReservation = await reservationSystem.sakshUpdatePaymentStatus('reservationId123', 'paid');
  console.log(updatedReservation);
  ```

## Function: `sakshSearchReservations(filters)`
- **Parameters**:
  - `filters` (Object) - The filters to apply when searching for reservations.
    - `minCharge` (Number) - The minimum booking charge.
    - `maxCharge` (Number) - The maximum booking charge.
    - `carType` (String) - The type of car.
    - `startDate` (Date) - The start date for the search.
    - `endDate` (Date) - The end date for the search.
    - `location` (String) - The location of the car.
- **Description**: Searches for reservations based on the provided filters.
- **Usage**:
  ```javascript
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

## Function: `sakshAddReview(reservationId, carId, userId, rating, comment)`
- **Parameters**:
  - `reservationId` (String) - The ID of the reservation.
  - `carId` (String) - The ID of the car.
  - `userId` (String) - The ID of the user.
  - `rating` (Number) - The rating given by the user.
  - `comment` (String) - The comment provided by the user.
- **Description**: Adds a review to a reservation.
- **Usage**:
  ```javascript
  const review = await reservationSystem.sakshAddReview(
    'reservationId123',
    'carId123',
    'userId123',
    5,
    'Great experience!'
  );
  console.log(review);
  ```

## Function: `sakshListReviews(reservationId, carId)`
- **Parameters**:
  - `reservationId` (String) - The ID of the reservation (optional).
  - `carId` (String) - The ID of the car (optional).
- **Description**: Lists reviews for a specific reservation or car.
- **Usage**:
  ```javascript
  const reviews = await reservationSystem.sakshListReviews('reservationId123', 'carId123');
  console.log(reviews);
  ```

## Function: `sakshGenerateDailyReservationReport()`
- **Description**: Generates a report of daily reservations, including the total number of reservations and details of each reservation.
- **Usage**:
  ```javascript
  const dailyReport = await reservationSystem.sakshGenerateDailyReservationReport();
  console.log(dailyReport);
  ```

## Function: `sakshGenerateCarUtilizationReport()`
- **Description**: Generates a report on car utilization, including the total days each car was reserved and the utilization rate.
- **Usage**:
  ```javascript
  const utilizationReport = await reservationSystem.sakshGenerateCarUtilizationReport();
  console.log(utilizationReport);
  ```

## Function: `sakshGenerateUserActivityReport()`
- **Description**: Generates a report on user activity, including the total number of reservations made by each user and their average rating.
- **Usage**:
  ```javascript
  const userActivityReport = await reservationSystem.sakshGenerateUserActivityReport();
  console.log(userActivityReport);
  ```



This formatting uses headings, bullet points, and code blocks to clearly present the functions, their parameters, descriptions, and usage examples.





 
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

        // Generate daily reservation report
        const dailyReport = await reservationSystem.sakshGenerateDailyReservationReport();
        console.log('Daily Reservation Report:', dailyReport);

        // Generate car utilization report
        const utilizationReport = await reservationSystem.sakshGenerateCarUtilizationReport();
        console.log('Car Utilization Report:', utilizationReport);

        // Generate user activity report
        const userActivityReport = await reservationSystem.sakshGenerateUserActivityReport();
        console.log('User Activity Report:', userActivityReport);

    } catch (error) {
        console.error('Error:', error);
    }
});
```
 
 
## Explanation

1. **Connecting to MongoDB**:
   - The `sakshConnect` function is called to connect to the MongoDB database using the provided URI.

2. **Adding a New Car**:
   - The `sakshAddCar` function is used to add a new car to the system.

3. **Listing All Available Cars**:
   - The `sakshListAvailableCars` function lists all available cars in the system.

4. **Making a Reservation**:
   - The `sakshMakeReservation` function makes a reservation for a car.

5. **Adding a Review**:
   - The `sakshAddReview` function adds a review to a reservation.

6. **Listing Reviews**:
   - The `sakshListReviews` function lists reviews for a specific reservation or car.

7. **Modifying a Reservation**:
   - The `sakshModifyReservation` function modifies an existing reservation.

8. **Canceling a Reservation**:
   - The `sakshCancelReservation` function cancels a reservation if it hasn't started yet.

9. **Listing All Reservations**:
   - The `sakshListReservations` function lists all reservations in the system.

10. **Getting Reservation History**:
    - The `sakshGetReservationHistory` function gets the reservation history for a specific user.

11. **Updating Payment Status**:
    - The `sakshUpdatePaymentStatus` function updates the payment status of a reservation.

12. **Searching for Reservations**:
    - The `sakshSearchReservations` function searches for reservations based on the provided filters.

13. **Generating Reports**:
    - The `sakshGenerateDailyReservationReport`, `sakshGenerateCarUtilizationReport`, and `sakshGenerateUserActivityReport` functions generate various reports.




 
 
# saksh-car-reservation-system Events

The `saksh-car-reservation-system` module emits several events that can be used to handle notifications, logging, or other custom actions. Here are the details about each event:

## Events Emitted

1. **reservationMade**
   - **Description**: Emitted when a new reservation is successfully made.
   - **Payload**: The reservation object.
   - **Usage**:
     ```javascript
     reservationSystem.on('reservationMade', (reservation) => {
       console.log('New reservation made:', reservation);
       // Handle notification or other actions here
     });
     ```

2. **reservationCanceled**
   - **Description**: Emitted when a reservation is successfully canceled.
   - **Payload**: The canceled reservation object.
   - **Usage**:
     ```javascript
     reservationSystem.on('reservationCanceled', (reservation) => {
       console.log('Reservation canceled:', reservation);
       // Handle notification or other actions here
     });
     ```

3. **reservationModified**
   - **Description**: Emitted when a reservation is successfully modified.
   - **Payload**: The modified reservation object.
   - **Usage**:
     ```javascript
     reservationSystem.on('reservationModified', (reservation) => {
       console.log('Reservation modified:', reservation);
       // Handle notification or other actions here
     });
     ```

4. **paymentStatusUpdated**
   - **Description**: Emitted when the payment status of a reservation is updated.
   - **Payload**: The updated reservation object.
   - **Usage**:
     ```javascript
     reservationSystem.on('paymentStatusUpdated', (reservation) => {
       console.log('Payment status updated:', reservation);
       // Handle notification or other actions here
     });
     ```

## Example: Handling Events

Here's an example of how you can handle these events to send notifications or perform other actions:

```javascript
const SakshCarReservationSystem = require('saksh-car-reservation-system');

// MongoDB connection URI
const dbUri = 'your_mongodb_uri';

// Initialize the reservation system
const reservationSystem = new SakshCarReservationSystem(dbUri);

// Connect to MongoDB
reservationSystem.sakshConnect().then(async () => {
  try {
    // Event listeners
    reservationSystem.on('reservationMade', (reservation) => {
      console.log('New reservation made:', reservation);
      // Send notification to the user
      sendNotification(reservation.userId, 'Your reservation has been made successfully.');
    });

    reservationSystem.on('reservationCanceled', (reservation) => {
      console.log('Reservation canceled:', reservation);
      // Send notification to the user
      sendNotification(reservation.userId, 'Your reservation has been canceled.');
    });

    reservationSystem.on('reservationModified', (reservation) => {
      console.log('Reservation modified:', reservation);
      // Send notification to the user
      sendNotification(reservation.userId, 'Your reservation has been modified.');
    });

    reservationSystem.on('paymentStatusUpdated', (reservation) => {
      console.log('Payment status updated:', reservation);
      // Send notification to the user
      sendNotification(reservation.userId, 'The payment status of your reservation has been updated.');
    });

    // Example functions to demonstrate usage
    await reservationSystem.sakshAddCar('Toyota', 'Camry', 2021);
    const availableCars = await reservationSystem.sakshListAvailableCars();
    const reservation = await reservationSystem.sakshMakeReservation(
      availableCars[0]._id,
      'userId123',
      'John Doe',
      '2024-09-01',
      '2024-09-10',
      100
    );

  } catch (error) {
    console.error('Error:', error);
  }
});

// Example notification function
function sendNotification(userId, message) {
  // Implement your notification logic here (e.g., email, SMS, push notification)
  console.log(`Notification sent to user ${userId}: ${message}`);
}
```

## Summary of Events

- **reservationMade**: Triggered when a new reservation is made.
- **reservationCanceled**: Triggered when a reservation is canceled.
- **reservationModified**: Triggered when a reservation is modified.
- **paymentStatusUpdated**: Triggered when the payment status of a reservation is updated.

These events allow you to hook into the reservation system's lifecycle and perform custom actions such as sending notifications, logging activities, or updating other systems. Let me know if you need any further assistance!
 

 

 
### License
This project is licensed under the MIT License.

### support

susheel2339 @ gmail.com
