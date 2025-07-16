
# 📦 Belvedere Booking System

## 🧩 Overview
This project is a **Google-based booking system** for the Belvedere Family Community center.  
It allows community members to **book indoor spots**, optionally request AV services, and automatically receive a "Booking Summary" PDF by email.

The system is fully powered by:
- Google Apps Script (backend logic)
- Google Sheets (data storage and admin interface)
- Google Drive (spot images and logo)
- Google Calendar (bookings calendar)
- Google Sites (public website embedding the Web App)

---

## ✅ Key Features

### Frontend (Google Sites + Web App)
- Public Google Sites page: "Book a Spot"
- Header with image and contact info:  
  ```
  Belvedere Family  
  723 South Broadway, Tarrytown, NY 10592  
  adminbelvedere
  ```
- Display categories and spots with images (indoor spots only):  
  - Agora  
  - White House  
  - Training Center  
  - Main Room  
  - Lounge  
  - Kitchen  
  - CSW Prayer Hall  
  - Room A  
  - Room D  
  - Room G  
  - Baby Room A  
  - Baby Room B  
  - Belvedere Estate  

- Clicking a spot opens a dynamic booking form with:  
  - Date picker  
  - Time range (start & end time)  
  - Name, email, phone  
  - Notes  
  - Booking frequency (one-time, weekly, monthly)  
  - Checkbox for AV needs with detailed options and pricing:  
    - Multiple microphones – $50  
    - Video projection – $50  
    - Video recording – $50  
    - Live stream – TBD  
    - Number of technicians (0 to 3)  

- Real-time cost calculation shown before submitting  
- "Reserve" button submits the booking

---

## ⚙️ Backend & Admin

### Google Sheets as backend
- Stores booking data organized by month (12 tabs: January to December)
- Contains admin columns: comments, approved/rejected by, invoice sent status

### Admin Panel for Configuration
- Instead of direct cell editing, there is a **custom sidebar/modal panel** in Google Sheets accessible via a custom menu (e.g. `Config > Rules`)
- This panel allows the admin to:  
  - Set operating hours (time range picker)  
  - Select allowed weekdays (checkboxes)  
  - Set minimum advance booking days  
  - Manage holiday blocks (date pickers)  
  - Update AV pricing and base booking price  
- On clicking "Save" in this panel, all configuration values are saved internally (in a hidden config sheet or PropertiesService)  
- These rules **automatically update the validation logic and the booking frontend** on the Web App side — so changes take effect immediately without manual code updates or republishing

### Booking Workflow
- On booking submission:  
  - Validate input against current rules  
  - Save booking to correct monthly sheet tab  
  - Create calendar event in Google Calendar  
  - Generate PDF invoice ("Booking Summary") including logo and booking details  
  - Send confirmation email with PDF to user  
  - Notify booking manager via email with full booking info  

### Booking Approval
- Admin reviews bookings in Google Sheets  
- Uses a button (Apps Script-driven) to approve/reject  
- Sends customizable approval/rejection emails (templates editable via admin panel)

---

## 📂 Assets
All spot images and logo are stored in Google Drive with these public links:

| Spot             | Image Link                                                                                  |
|------------------|---------------------------------------------------------------------------------------------|
| White House      | https://drive.google.com/file/d/1_AYp3OOfCP9vG5pYnJ8gFvIaTLKaU_fh/view?usp=drive_link       |
| Training Center  | https://drive.google.com/file/d/19Gl4PmAZe-7OJENWgNn5_4UFzESeSWYD/view?usp=drive_link       |
| Room D          | https://drive.google.com/file/d/1ayjzPz0hRVp9pmye54wJbHVwHcNgIKvW/view?usp=drive_link       |
| Room A          | https://drive.google.com/file/d/1Y1Io8q3-Jed791F3bJS826FOl-_IjvpT/view?usp=drive_link       |
| Main Room       | https://drive.google.com/file/d/1XqbddGKfMIxtaYcRoP0Ccu_m9jjGNIIy/view?usp=drive_link       |
| Lounge          | https://drive.google.com/file/d/1q9T8Ru5_03g3Rvtc5_76I6Hsj4s-WaYo/view?usp=drive_link       |
| Kitchen         | https://drive.google.com/file/d/1NyGBvfODklKFIUC2-M2DABoY6dZt_tB-/view?usp=drive_link       |
| CSW Prayer Hall | https://drive.google.com/file/d/1qH-dySVtUUA04Lbcgrqnmqkk6MkVtEgM/view?usp=drive_link       |
| Belvedere Estate| https://drive.google.com/file/d/1XVcl9hfohZ5mdrQvAkTcPthjhT5JhLlU/view?usp=drive_link       |
| Baby Room B     | https://drive.google.com/file/d/1_sWFD-7dIqaiGSD-DPiXJit8tLAdfys-/view?usp=drive_link       |
| Baby Room A     | https://drive.google.com/file/d/1wz_xCsQquODgKyJjSFCokoCaKHHawEKS/view?usp=drive_link       |
| Agora           | https://drive.google.com/file/d/1ZCgGgcbROgd2F4md6al8WzaDMOWjTxMP/view?usp=drive_link       |
| Room G          | https://drive.google.com/file/d/1bI6um4gogML55y-YkD_cc-6_LD8ZDTNi/view?usp=drive_link       |

Logo:  
https://drive.google.com/file/d/1cPFtapkjnouUvVxSz3xOROo5GLMwQlz3/view?usp=sharing

---

## 📧 Email & PDF
- Sender email: `adminbelvedere`  
- PDF invoice name: **Booking Summary**  
- PDF includes: logo, spot, date/time, AV options and costs, total cost

---

## 💰 Pricing
- Only FFPU pricing for now:  
  - Base spot price: $240 per half day  
  - AV options and technicians as listed in frontend  
- Pricing configurable via admin panel

---

## 🚀 Usage & Automation
- Setup functions to create Google Sheets structure, config panel, and initialize default rules/prices
- Web App dynamically loads rules and updates form validation and options accordingly
- Any config change made via admin panel sidebar is reflected immediately across system (frontend, validation, emails, calendar)
- Google Sites embeds the Web App via URL (iframe), ensuring the latest version is always displayed without manual re-pasting

---

## 🎯 Goals
By running the setup and deploying the Web App, the admin will have a fully dynamic, easy-to-configure, robust booking system powered by Google tools, which minimizes manual intervention and scales well.

---
