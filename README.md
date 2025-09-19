classDiagram
    class TravelService {
        - FlightRepository flightRepo
        - HotelRepository hotelRepo
        - BookingRepository bookingRepo
        + List~Flight~ searchFlights(String source, String destination)
        + List~Hotel~ searchHotels(String city, int stars)
        + Booking bookFlightHotel(Booking booking)
    }

    class Flight {
        - String id
        - String airline
        - String source
        - String destination
        - String departureTime
        - double price
    }

    class Hotel {
        - String id
        - String name
        - String city
        - int stars
        - double pricePerNight
        - String[] amenities
    }

    class Booking {
        - Long id
        - String userId
        - String flightId
        - String hotelId
        - String bookingDate
    }

    class FlightRepository {
        + List~Flight~ findBySourceAndDestination(String source, String destination)
    }

    class HotelRepository {
        + List~Hotel~ findByCityAndStars(String city, int stars)
        + List~Hotel~ findByAmenitiesContaining(String amenity)
    }

    class BookingRepository {
        + Booking save(Booking booking)
    }

    TravelService --> FlightRepository
    TravelService --> HotelRepository
    TravelService --> BookingRepository

    FlightRepository --> Flight
    HotelRepository --> Hotel
    BookingRepository --> Booking

