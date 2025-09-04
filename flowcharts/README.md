# Flowcharts - Airbnb Clone Backend

This directory contains flowcharts that illustrate key backend workflows of the **Airbnb Clone Project**.

---

## 📌 Property Booking Flowchart

The **Property Booking Flowchart** maps out the end-to-end process a user follows when booking a property:

1. **User Login** → User logs into the system.  
2. **Search Property** → User searches for available properties.  
3. **Check Availability** → System verifies if the property is available.  
   - ❌ If not available → Process ends.  
   - ✅ If available → User proceeds.  
4. **Enter Booking Details** → User provides check-in/check-out dates and guest details.  
5. **Confirm Booking** → User confirms the booking request.  
6. **Process Payment** → Payment is processed through the gateway.  
   - ❌ If payment fails → Process ends.  
   - ✅ If payment succeeds → System saves booking.  
7. **Save Booking** → Booking information is stored in the database.  
8. **Send Confirmation** → Notification service sends booking confirmation.  
9. **Cancel Booking (Optional)** → User may cancel a booking, triggering a refund process.  
10. **Leave Review** → After the stay, the user can leave a review for the property.  
11. **End** → Workflow completes.  

---

## 📂 File Details
- **`data-flow-diagram.png`** → Exported PNG version of the Property Booking Flowchart.  
- **`property-booking-flowchart.drawio`** → Editable Draw.io source file.  

---

## 🔗 How to View
- Open the `.drawio` file in [Draw.io](https://app.diagrams.net) for editing.  
- The PNG can be previewed directly in the repository.  
