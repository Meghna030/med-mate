<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>MedMate</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding-top: 70px; /* Prevent content from hiding behind fixed navbar */
      background-image: url('https://images.unsplash.com/photo-1576671081837-49000212a370?q=80');
      background-size: cover;
      background-repeat: no-repeat;
      background-attachment: fixed;
      background-position: center;
      color: #000;
    }

    header {
      background-color: rgba(0, 0, 0, 0.85);
      color: #fff;
      padding: 1em 0;
      text-align: center;
      position: fixed;
      top: 0;
      width: 100%;
      z-index: 999;
    }

    nav ul {
      list-style: none;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      gap: 2em;
    }

    nav a {
      color: #fff;
      text-decoration: none;
      font-weight: bold;
    }

    main {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 2em;
    }

    section {
      background-color: rgba(255, 255, 255, 0.85);
      padding: 1.5em;
      margin: 1.5em 0;
      width: 85%;
      max-width: 700px;
      border-radius: 10px;
      box-shadow: 0 0 12px rgba(0,0,0,0.2);
    }

    h1, h2 {
      margin-top: 0;
    }

    label {
      display: block;
      margin-top: 10px;
    }

    input, select, textarea, button {
      width: 100%;
      padding: 0.5em;
      margin-top: 5px;
      box-sizing: border-box;
    }

    button {
      background-color: #4CAF50;
      color: white;
      border: none;
      cursor: pointer;
      margin-top: 10px;
      border-radius: 5px;
    }

    button:hover {
      background-color: #45a049;
    }

    #reminders-list {
      list-style: none;
      padding: 0;
      margin-top: 1em;
    }

    #reminders-list li {
      padding: 10px;
      border-bottom: 1px solid #ccc;
    }

    .medicine-name {
      color: #007bff;
      cursor: pointer;
      text-decoration: underline;
    }

    #pharmacy-results {
      padding: 10px;
      margin-top: 1em;
    }

    ul {
      padding-left: 20px;
    }

    ul li {
      margin-bottom: 0.5em;
    }

    #home {
      text-align: center;
    }

    footer {
      background-color: rgba(0, 0, 0, 0.85);
      color: #fff;
      text-align: center;
      padding: 1em;
    }
  </style>
</head>
<body>
  <header>
    <nav>
      <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#reminders">Reminders</a></li>
        <li><a href="#pharmacy">Pharmacy</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section id="home">
      <h1>Welcome to MedMate</h1>
      <p>Your smart health companion! MedMate helps you manage your medications effortlessly, sending you reminders and locating nearby pharmacies with just a few clicks. Stay healthy, stay on track — MedMate has you covered!</p>
    </section>

    <section id="reminders">
      <h1>Medicine Reminders</h1>
      <form id="reminder-form">
        <label for="medicine-name">Medicine Name:</label>
        <input type="text" id="medicine-name" required>
        <label for="dosage">Dosage:</label>
        <input type="text" id="dosage" required>
        <label for="frequency">Frequency:</label>
        <select id="frequency" required>
          <option value="daily">Daily</option>
          <option value="weekly">Weekly</option>
          <option value="monthly">Monthly</option>
        </select>
        <button type="submit" id="add-reminder">Add Reminder</button>
      </form>
      <ul id="reminders-list"></ul>
    </section>

    <section id="pharmacy">
      <h1>Nearest Pharmacy</h1>
      <form id="pharmacy-form">
        <label for="pharmacy-medicine-name">Medicine Name:</label>
        <input type="text" id="pharmacy-medicine-name" required>
        <button type="submit" id="find-pharmacy">Find Pharmacy</button>
      </form>
      <div id="pharmacy-results"></div>
    </section>

    <section id="about">
      <h1>About MedMate</h1>
      <p><strong>MedMate</strong> is your intelligent health companion — designed to simplify your medication routine and help you stay on track.</p>
      <ul>
        <li>💊 Easy-to-set medication reminders (Premium Feature)</li>
        <li>📍 Quickly locate nearby pharmacies</li>
        <li>🔔 Smart notification alerts</li>
        <li>📱 Mobile-friendly</li>
        <li>🗂 Stores your medication history</li>
      </ul>
    </section>

    <section id="contact">
      <h1>Contact Us</h1>
      <form id="contact-form">
        <label for="name">Full Name:</label>
        <input type="text" id="name" required>

        <label for="email">Email Address:</label>
        <input type="email" id="email" required>

        <label for="message">Your Message:</label>
        <textarea id="message" rows="5" required></textarea>

        <button type="submit">Submit</button>
      </form>

      <hr style="margin: 2em 0;">

      <h2>Premium Membership</h2>
      <p>Get access to premium features like setting medicine reminders, smart notifications, and more.</p>

      <form id="premium-form">
        <label for="premium-name">Full Name:</label>
        <input type="text" id="premium-name" required>

        <label for="premium-email">Email Address:</label>
        <input type="email" id="premium-email" required>

        <label for="payment-method">Payment Method:</label>
        <select id="payment-method" required>
          <option value="">Select a method</option>
          <option value="credit">Credit Card</option>
          <option value="paypal">PayPal</option>
          <option value="upi">UPI</option>
        </select>

        <button type="submit">Purchase Membership</button>
      </form>
    </section>
  </main>

  <footer>
    © 2025 MedMate. All rights reserved.
  </footer>

  <script>
    const remindersList = document.getElementById('reminders-list');
    const reminderForm = document.getElementById('reminder-form');
    const pharmacyForm = document.getElementById('pharmacy-form');
    const pharmacyResults = document.getElementById('pharmacy-results');

    const medicineToPharmacies = {
      "Paracetamol": ["PharmaPlus", "HealthHub"],
      "Ibuprofen": ["WellCare", "PharmaPlus"],
      "Aspirin": ["MediStore", "HealthHub"],
      "Amoxicillin": ["WellCare", "CureWell"],
    };

    reminderForm.addEventListener('submit', (e) => {
      e.preventDefault();
      alert("To set medicine reminders, you must have a Premium Membership.");
      reminderForm.reset();
    });

    pharmacyForm.addEventListener('submit', (e) => {
      e.preventDefault();
      const medicine = document.getElementById('pharmacy-medicine-name').value;
      pharmacyResults.innerHTML = `<p>Searching for pharmacies with "${medicine}"...</p>`;
      setTimeout(() => {
        const pharmacies = medicineToPharmacies[medicine] || ["No pharmacy found"];
        pharmacyResults.innerHTML = `<strong>Available at:</strong><ul>` +
          pharmacies.map(pharmacy => `<li>${pharmacy}</li>`).join('') +
          `</ul>`;
      }, 1000);
      pharmacyForm.reset();
    });

    document.getElementById('contact-form').addEventListener('submit', (e) => {
      e.preventDefault();
      alert("Thank you for contacting us!");
      e.target.reset();
    });

    document.getElementById('premium-form').addEventListener('submit', (e) => {
      e.preventDefault();
      alert("Thank you for purchasing Premium Membership!");
      e.target.reset();
    });
  </script>
</body>
</html>
