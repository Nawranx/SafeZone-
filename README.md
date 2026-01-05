# SafeZone

SafeZone is a real-time emergency response system designed for public safety. It allows users to broadcast their live geolocation via an SOS button and provides routing to the nearest hospitals or police stations. The system is built to handle high-stress scenarios and facilitates quick emergency response.

## Features

- **Real-time Location Tracking**: Users can share their live location in real-time.
- **Emergency SOS**: One-click emergency button to alert authorities with location data.
- **User Authentication**: Separate authentication for server administrators and client users.
- **Interactive Map**: Visual representation of user locations and emergencies using Leaflet maps.
- **Emergency Logs**: Server-side dashboard to view and manage emergency signals and user data.
- **Geolocation Routing**: Integration with mapping services for routing to emergency services.
- **IP Address Logging**: Tracks IP addresses for emergency signals for additional context.

## Technology Stack

- **Backend**: Node.js with Express.js
- **Real-time Communication**: Socket.io
- **Database**: SQLite (using better-sqlite3)
- **Frontend**: EJS templating engine, HTML, CSS, JavaScript
- **Mapping**: Leaflet.js with OpenStreetMap tiles
- **Authentication**: bcrypt for password hashing, express-session for session management

## Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd SafeZone--main
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Set up the database**:
   The application uses SQLite and creates the database file (`safe_zone.db`) automatically on first run. The schema includes tables for server users, client users, and emergency signals.

4. **Run the application**:
   ```bash
   node app.js
   ```

   The server will start on port 3030 and listen on all network interfaces.

## Usage

### For Server Administrators
1. Access the server login at `http://localhost:3030/server_login`.
2. On first run, sign up as a server user.
3. View the main dashboard at `http://localhost:3030/` to see user data and emergency signals.
4. Access logs at `http://localhost:3030/logs/view` to review emergency requests.

### For Client Users
1. Sign up or log in at `http://localhost:3030/emergency_login`.
2. Access the emergency dashboard at `http://localhost:3030/emergency_dashboard`.
3. Allow location sharing when prompted.
4. Press the SOS button to send an emergency signal with your current location.

### Real-time Features
- Locations are updated in real-time on the map.
- Emergency signals are broadcasted immediately to all connected clients and logged in the database.

## Project Structure

```
SafeZone--main/
├── app.js                 # Main application file
├── package.json           # Node.js dependencies and scripts
├── safe_zone.sql          # Database schema (MySQL format, but app uses SQLite)
├── public/
│   ├── css/               # Stylesheets
│   ├── images/            # Static images
│   └── js/
│       └── script.js      # Client-side JavaScript for map and socket handling
└── views/                 # EJS templates
    ├── index.ejs          # Server dashboard
    ├── dashboard.ejs      # Admin dashboard
    ├── emergency_dashboard.ejs  # Client emergency interface
    ├── logs.ejs           # Emergency logs view
    └── ...                # Other authentication pages
```

## API Endpoints

- `GET /` - Server dashboard (authenticated)
- `GET /server_login` - Server login page
- `POST /server_login` - Handle server login
- `GET /server_signup` - Server signup page
- `POST /server_signup` - Handle server signup
- `GET /emergency_login` - Client login page
- `POST /emergency_login` - Handle client login
- `GET /emergency_signup` - Client signup page
- `POST /emergency_signup` - Handle client signup
- `GET /emergency_dashboard` - Client dashboard (authenticated)
- `GET /logs/view` - View emergency logs (server authenticated)
- `GET /dashboard` - Admin dashboard (server authenticated)

## Socket Events

- `register-user` - Register user with socket
- `send-location` - Send user location
- `emergency` - Trigger emergency signal
- `receive-location` - Receive location updates
- `emergency-notification` - Emergency alert
- `update-emergency-location` - Update emergency location
- `client-disconnected` - Handle client disconnection

## Contributing

1. Fork the repository.
2. Create a feature branch.
3. Make your changes.
4. Test thoroughly.
5. Submit a pull request.

## License

This project is licensed under the ISC License.

## Notes

- The application uses SQLite for simplicity, but a `safe_zone.sql` file is provided in MySQL format for reference.
- Ensure geolocation permissions are granted in the browser for location tracking.
- The map is centered on a default location (Albukhary International University) but can be adjusted.
