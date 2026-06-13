# Mock Airbnb

A robust RESTful API built with Django and Django REST Framework that powers an Airbnb-like property booking platform. This project handles user authentication, property management, reservations, commenting systems, and a real-time notification service.

## 🚀 How to Run the Project

To set up and run the application locally, navigate to the project root folder and execute the provided shell scripts.

**Prerequisites:** * You must have `sudo` privileges on your machine to install necessary dependencies.
* *Note: If the `apt install` step fails during startup, run `sudo apt-get update` first.*

# 1. Install dependencies and setup the environment
sh startup.sh

# 2. Run the Django development server
sh run.sh
🗄️ Database Models
The platform's data layer is structured around several key relational models:

MyUser (Custom User Model): Extends Django's AbstractUser. Uses email for authentication. Stores user details like phone_number (requires xxx-xxx-xxxx format), avatar, self_intro, and auto-calculates host/guest ratings.

Property: Stores property listings, including location data, default price, amenities, capacity, and the host (Foreign Key to MyUser).

Preview: Handles property image uploads.

Availability: Manages available dates (start_date, end_date) and custom pricing for a property. Prevents overlapping booking dates.

Rev (Reservation): Manages booking states between a host, guest, and property. Tracks the reservation lifecycle (pending, approved, denied, canceled, terminated).

Ntf (Notification): A messaging system that triggers automated alerts to users when a reservation status changes.

Comment: Utilizes Django's ContentType (Generic Relations) to allow comments/ratings to be attached to both Users and Properties. Supports nested comments (replies).

📡 API Endpoints
The API uses SimpleJWT for token-based authentication. Most endpoints (except Register, Login, and Property Index) require a valid JWT token in the authorization header.

👤 Accounts
Endpoint	Method	Description
/accounts/register/	POST	Register a new user (email, phone, password, name).
/accounts/login/	POST	Authenticate and receive JWT tokens.
/accounts/profile/update/	PUT/PATCH	Update authenticated user's profile info.
/accounts/home/	GET	View the authenticated user's own profile.
/accounts/<pk>/profile/	GET	View a specific user's public profile.
🏠 Properties & Availabilities
Endpoint	Method	Description
/property/index/	GET	Browse properties (Supports search, filters, ordering, & pagination).
/property/<pk>/detail/	GET	View details of a specific property.
/property/add/	POST	Create a new property listing (Host only).
/property/<pk>/update/	PUT	Update an existing property.
/property/<pk>/delete/	DELETE	Delete a property.
/property/preview/<pk>/delete/	DELETE	Delete a specific preview image.
/property/<prop_pk>/availability/add/	POST	Add available dates to a property.
/property/availability/<pk>/update/	PUT	Update available dates.
/property/availability/<pk>/delete/	DELETE	Remove an availability slot.
📅 Reservations
Endpoint	Method	Description
/revs/create/<pid>/	POST	Create a reservation request for a property.
/revs/list/<user_id>/	GET	List user's reservations (Supports user_type & status filters).
/revs/action/<reservation_id>/<action>/	PUT/PATCH	Update reservation status (actions: approve, deny, request_cancel, terminate).
💬 Comments & Ratings
Endpoint	Method	Description
/comment/create/myuser/<user_id>/<parent_id>/	POST	Leave a comment/rating for a user.
/comment/property/<property_id>/<parent_id>/	POST	Leave a comment/rating for a property.
/comment/update/<pk>/	PUT/PATCH	Edit a comment or reply to an existing comment.
/comment/list/user/<pk>/	GET	Get all comments for a specific user.
/comment/list/property/<pk>/	GET	Get all comments for a specific property.
🔔 Notifications
Endpoint	Method	Description
/notifications/<user_id>/list/	GET	Get a list of the user's notifications.
/notifications/<user_id>/<notification_id>/details/	GET	View a notification (marks it as if_read: true).
🛠️ Built With
Django & Django REST Framework (DRF)

SimpleJWT for Authentication

SQLite/PostgreSQL (Database)

i want readme in md format

🗄️ Database Models
The platform's data layer is structured around several key relational models:

MyUser (Custom User Model): Extends Django's AbstractUser. Uses email for authentication. Stores user details like phone_number (requires xxx-xxx-xxxx format), avatar, self_intro, and auto-calculates host/guest ratings.

Property: Stores property listings, including location data, default price, amenities, capacity, and the host (Foreign Key to MyUser).

Preview: Handles property image uploads.

Availability: Manages available dates (start_date, end_date) and custom pricing for a property. Prevents overlapping booking dates.

Rev (Reservation): Manages booking states between a host, guest, and property. Tracks the reservation lifecycle (pending, approved, denied, canceled, terminated).

Ntf (Notification): A messaging system that triggers automated alerts to users when a reservation status changes.

Comment: Utilizes Django's ContentType (Generic Relations) to allow comments/ratings to be attached to both Users and Properties. Supports nested comments (replies).

📡 API Endpoints
The API uses SimpleJWT for token-based authentication. Most endpoints (except Register, Login, and Property Index) require a valid JWT token in the authorization header.

👤 Accounts
Endpoint	Method	Description
/accounts/register/	POST	Register a new user (email, phone, password, name).
/accounts/login/	POST	Authenticate and receive JWT tokens.
/accounts/profile/update/	PUT/PATCH	Update authenticated user's profile info.
/accounts/home/	GET	View the authenticated user's own profile.
/accounts/<pk>/profile/	GET	View a specific user's public profile.
🏠 Properties & Availabilities
Endpoint	Method	Description
/property/index/	GET	Browse properties (Supports search, filters, ordering, & pagination).
/property/<pk>/detail/	GET	View details of a specific property.
/property/add/	POST	Create a new property listing (Host only).
/property/<pk>/update/	PUT	Update an existing property.
/property/<pk>/delete/	DELETE	Delete a property.
/property/preview/<pk>/delete/	DELETE	Delete a specific preview image.
/property/<prop_pk>/availability/add/	POST	Add available dates to a property.
/property/availability/<pk>/update/	PUT	Update available dates.
/property/availability/<pk>/delete/	DELETE	Remove an availability slot.
📅 Reservations
Endpoint	Method	Description
/revs/create/<pid>/	POST	Create a reservation request for a property.
/revs/list/<user_id>/	GET	List user's reservations (Supports user_type & status filters).
/revs/action/<reservation_id>/<action>/	PUT/PATCH	Update reservation status (actions: approve, deny, request_cancel, terminate).
💬 Comments & Ratings
Endpoint	Method	Description
/comment/create/myuser/<user_id>/<parent_id>/	POST	Leave a comment/rating for a user.
/comment/property/<property_id>/<parent_id>/	POST	Leave a comment/rating for a property.
/comment/update/<pk>/	PUT/PATCH	Edit a comment or reply to an existing comment.
/comment/list/user/<pk>/	GET	Get all comments for a specific user.
/comment/list/property/<pk>/	GET	Get all comments for a specific property.
🔔 Notifications
Endpoint	Method	Description
/notifications/<user_id>/list/	GET	Get a list of the user's notifications.
/notifications/<user_id>/<notification_id>/details/	GET	View a notification (marks it as if_read: true).
🛠️ Built With
Django & Django REST Framework (DRF)

SimpleJWT for Authentication

SQLite/PostgreSQL (Database)
"""

with open("README.md", "w", encoding="utf-8") as f:
f.write(markdown_content)

print("Markdown file generated.")


```text?code_stdout&code_event_index=1
Markdown file generated.

Your README.md file is ready for download.
MD icon
README
 MD 
Open

You can drop this directly into your GitHub repository's root directory.




Gemini is AI and can make mistakes.

# Mock Airbnb API

A robust RESTful API built with Django and Django REST Framework that powers an Airbnb-like property booking platform. This project handles user authentication, property management, reservations, commenting systems, and a real-time notification service.

## How to Run the Project

To set up and run the application locally, navigate to the project root folder and execute the provided shell scripts.

**Prerequisites:** 
* You must have `sudo` privileges on your machine to install necessary dependencies.
* *Note: If the `apt install` step fails during startup, run `sudo apt-get update` first.*

```bash
# 1. Install dependencies and setup the environment
sh startup.sh

# 2. Run the Django development server
sh run.sh
```

## Database Models

The platform's data layer is structured around several key relational models:

* **MyUser (Custom User Model):** Extends Django's `AbstractUser`. Uses `email` for authentication. Stores user details like `phone_number` (requires `xxx-xxx-xxxx` format), `avatar`, `self_intro`, and auto-calculates host/guest `ratings`.
* **Property:** Stores property listings, including location data, default `price`, `amenities`, `capacity`, and the `host` (Foreign Key to MyUser). 
* **Preview:** Handles property image uploads.
* **Availability:** Manages available dates (`start_date`, `end_date`) and custom pricing for a property. Prevents overlapping booking dates.
* **Rev (Reservation):** Manages booking states between a `host`, `guest`, and `property`. Tracks the reservation lifecycle (`pending`, `approved`, `denied`, `canceled`, `terminated`).
* **Ntf (Notification):** A messaging system that triggers automated alerts to users when a reservation status changes.
* **Comment:** Utilizes Django's `ContentType` (Generic Relations) to allow comments/ratings to be attached to both **Users** and **Properties**. Supports nested comments (replies).

## 📡 API Endpoints

The API uses **SimpleJWT** for token-based authentication. Most endpoints (except Register, Login, and Property Index) require a valid JWT token in the authorization header.

### 👤 Accounts
| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/accounts/register/` | `POST` | Register a new user (email, phone, password, name). |
| `/accounts/login/` | `POST` | Authenticate and receive JWT tokens. |
| `/accounts/profile/update/` | `PUT/PATCH` | Update authenticated user's profile info. |
| `/accounts/home/` | `GET` | View the authenticated user's own profile. |
| `/accounts/<pk>/profile/` | `GET` | View a specific user's public profile. |

### 🏠 Properties & Availabilities
| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/property/index/` | `GET` | Browse properties (Supports search, filters, ordering, & pagination). |
| `/property/<pk>/detail/` | `GET` | View details of a specific property. |
| `/property/add/` | `POST` | Create a new property listing (Host only). |
| `/property/<pk>/update/` | `PUT` | Update an existing property. |
| `/property/<pk>/delete/` | `DELETE`| Delete a property. |
| `/property/preview/<pk>/delete/`| `DELETE`| Delete a specific preview image. |
| `/property/<prop_pk>/availability/add/`| `POST` | Add available dates to a property. |
| `/property/availability/<pk>/update/`| `PUT` | Update available dates. |
| `/property/availability/<pk>/delete/`| `DELETE`| Remove an availability slot. |

### Reservations
| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/revs/create/<pid>/` | `POST` | Create a reservation request for a property. |
| `/revs/list/<user_id>/` | `GET` | List user's reservations (Supports `user_type` & `status` filters). |
| `/revs/action/<reservation_id>/<action>/`| `PUT/PATCH`| Update reservation status (actions: `approve`, `deny`, `request_cancel`, `terminate`). |

### Comments & Ratings
| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/comment/create/myuser/<user_id>/<parent_id>/` | `POST` | Leave a comment/rating for a user. |
| `/comment/property/<property_id>/<parent_id>/` | `POST` | Leave a comment/rating for a property. |
| `/comment/update/<pk>/` | `PUT/PATCH` | Edit a comment or reply to an existing comment. |
| `/comment/list/user/<pk>/` | `GET` | Get all comments for a specific user. |
| `/comment/list/property/<pk>/` | `GET` | Get all comments for a specific property. |

### Notifications
| Endpoint | Method | Description |
| :--- | :--- | :--- |
| `/notifications/<user_id>/list/` | `GET` | Get a list of the user's notifications. |
| `/notifications/<user_id>/<notification_id>/details/`| `GET` | View a notification (marks it as `if_read: true`). |

## Built With
* **Django** & **Django REST Framework (DRF)**
* **SimpleJWT** for Authentication
* **SQLite/PostgreSQL** (Database)
README.md
Displaying README.md.
