# TRACKMATE-IOT-Based-Wearable-Device-for-Rehabilitation-Monitoring
An IoT device for monitoring patients with walking disabilities, featuring pedometer and fall detection algorithms using MPU9250 and ESP32 C3. Implements TensorFlow Lite LSTM models for 96% accurate walking pattern recognition, with real-time alerts via Firebase and MQTT.

# Patient Monitoring Dashboard  

This guide walks you through setting up and running the **Patient Monitoring Dashboard**. Follow these step-by-step instructions to ensure proper configuration and operation.  

---

## Requirements  
- **ESP32-C3 Dev Kit 2**  
- **MPU9250 Sensor**  
- **Personal Computer (PC)** with Windows/Linux/macOS  
- **Node.js** and **npm** (for running the server)  
- **Wi-Fi connection**  

---

## Step 1: Preparing the ESP32 Firmware  
1. **Install Arduino IDE**  
   - Download and install the Arduino IDE from [arduino.cc](https://www.arduino.cc/).  
   - Open the Arduino IDE after installation.  

2. **Install ESP32 Board Support**  
   - Open Arduino IDE, go to `File > Preferences`.  
   - In the "Additional Boards Manager URLs" field, add:  
     ```
     https://dl.espressif.com/dl/package_esp32_index.json
     ```  
   - Go to `Tools > Board > Board Manager`. Search for "ESP32" and install the "esp32" package by Espressif Systems.  

3. **Install Required Libraries**  
   - Go to `Sketch > Include Library > Manage Libraries`.  
   - Search and install the following libraries:  
     - **WiFi** (pre-installed)  
     - **MPU9250_asukiaaa**  
     - **HTTPClient**  

4. **Write Code to ESP32**  
   - Open the Arduino IDE and copy the modified code.  
   - Replace placeholders:  
     ```c
     const char* ssid = "your_wifi_ssid";
     const char* password = "your_wifi_password";
     const char* serverName = "http://yourserver.com/data";
     ```  
   - Connect your ESP32-C3 to your computer via USB.  
   - In Arduino IDE, go to `Tools > Board` and select **"ESP32C3 Dev Module"**.  
   - Under `Tools > Port`, select the port for the ESP32.  
   - Click **Upload** to flash the code to the ESP32.  

---

## Step 2: Setting Up the Node.js Server  
1. **Install Node.js and npm**  
   - Download and install Node.js from [nodejs.org](https://nodejs.org/).  
   - Verify installation:  
     ```bash
     node -v
     npm -v
     ```  

2. **Create a Project Directory**  
   - Create a folder named `patient-dashboard-server` and navigate to it:  
     ```bash
     cd path/to/patient-dashboard-server
     ```  

3. **Initialize Node.js Project**  
   - Run:  
     ```bash
     npm init -y
     ```  

4. **Install Dependencies**  
   - Install required packages:  
     ```bash
     npm install express ws body-parser
     ```  

5. **Create the Server Script**  
   - In the folder, create a file named `server.js` and paste the server code into it.  

6. **Create Public Directory for Dashboard**  
   - Create a folder named `public` and add an `index.html` file inside it.  
   - Paste the dashboard HTML code into `index.html`.  

---

## Step 3: Running the Server  
1. **Start the Server**  
   - Navigate to the project folder and run:  
     ```bash
     node server.js
     ```  
   - You should see output like:  
     ```
     Server is listening on port 3000
     ```  

2. **Access the Dashboard**  
   - On a device connected to the same network, open a browser and go to:  
     ```
     http://<your-server-ip>:3000/
     ```  
   - Replace `<your-server-ip>` with your server's IP (e.g., 192.168.1.100).  

3. **Test ESP32 Communication**  
   - Ensure the ESP32 is powered on and connected to Wi-Fi.  
   - Verify data like step count and gyroscope values update in real-time on the dashboard.  

---

## Step 4: Improving the Dashboard  
1. **Customize CSS**  
   - Edit the `<style>` section in `index.html` to modify the dashboard's appearance.  

2. **Add Animations**  
   - Use CSS keyframes or JavaScript for interactive elements.  

---

## Step 5: Optional Enhancements  
1. **Using PM2 for Server Management**  
   - Install PM2 for persistent server management:  
     ```bash
     npm install -g pm2
     pm2 start server.js
     pm2 save
     pm2 startup
     ```  

2. **Remote Access**  
   - Set up port forwarding or use [ngrok](https://ngrok.com/) for external access.  

---

## Troubleshooting  
1. **Wi-Fi Issues**  
   - Double-check SSID, password, and signal strength.  

2. **ESP32 Not Connecting**  
   - Verify the server is running and the IP in the ESP32 code matches the server's IP.  

3. **Dashboard Not Loading**  
   - Ensure the server is running and accessible. Check firewall settings.  

---




