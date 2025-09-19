+-------------------+
|     TravelService  |  <<Service Layer>>
+-------------------+
| - flightRepo: FlightRepository
| - hotelRepo: HotelRepository
| - bookingRepo: BookingRepository
+-------------------+
| +searchFlights()
| +searchHotels()
| +bookFlightHotel()
+-------------------+
          |
          |
          v
+-------------------+          +-------------------+          +-------------------+
|   Flight          |  <<Elasticsearch Document>>  |   Hotel           |  <<Elasticsearch Document>>  |   Booking         |  <<Database Entity>> |
+-------------------+          +-------------------+          +-------------------+
| - id: String      |          | - id: String      |          | - id: Long        |
| - airline: String |          | - name: String    |          | - userId: String  |
| - source: String  |          | - city: String    |          | - flightId: String|
| - destination: String|       | - stars: int      |          | - hotelId: String |
| - departureTime: String|     | - pricePerNight: double |     | - bookingDate: String |
| - price: double   |          | - amenities: String[] |      |                   |
+-------------------+          +-------------------+          +-------------------+
          ^                            ^
          |                            |
          |                            |
+-------------------+          +-------------------+
| FlightRepository   |  <<ElasticsearchRepository>>  | HotelRepository  |  <<ElasticsearchRepository>> |
+-------------------+          +-------------------+
| +findBySourceAndDestination()|  | +findByCityAndStars()  |
|                             |  | +findByAmenitiesContaining() |
+-------------------+          +-------------------+
