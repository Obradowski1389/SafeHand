# SafeHand
SafeHand is application created for hackaton Tech says NO. It is designed to assist women who are victims of physicall or verbal abuse by allowing them to send an emergency alert to their loved ones. It is based around the concept of having a concealed physicall device that can be operated easily in time of need, by simply pressing a button 3 times in a row. When button gets pressed emergency contacts will get a whatsapp message, additionaly a push notification if they are users of our platform, that will lead them to victims location.

<img src="https://github.com/Obradowski1389/tech_says_no/blob/master/documentation/home.jpg" alt="app homepage" height="500"/>

## Prerequisites
Before running this application, ensure you have the following installed:

 - [Flutter SDK](https://docs.flutter.dev/get-started/install)
 - Docker
 - RaspberryPI and a button
 - CallMeBot (it requires number registration since we are in developing environment)

<img src="https://github.com/Obradowski1389/tech_says_no/blob/master/documentation/callmebot.jpg" alt="callmebot" height="500"/>

## Setup
### Docker Configuration:
Docker configuration files are provided in the tech_says_no_flask/ directory.
Build the Docker image using 
```
docker-compose build
```
Run the Docker container using 
```
docker-compose up
```

### IP configuration
- Run this command in CMD to obtain your machine's IPv4 address:
```
ipconfig
```
- Search for '192.168.0' in project and change it for local IPv4 address.

### RaspberryPI Configuration
- Follow the wiring diagram from the picture
![wiring](https://github.com/Obradowski1389/tech_says_no/blob/master/documentation/2-pin-button.png)
- Power on your PI
- Enter the following command to copy the script and dependency requirements to the PI:
```
scp -r python {username}@{raspberry_ip}:~/path/to/target/directory
```
- SSH yourself to the PI
- Position yourself to target directory and run the following commands
```
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
sudo python main.py
```

### Flutter Setup:
- Clone this repository.
- Navigate to the tech_says_no_flutter/ directory and run the following command to fetch the project dependencies:
```
flutter pub get
```

### Google Maps Setup:
- Obtain a Google maps API key
- Follow further [instructions](https://codelabs.developers.google.com/codelabs/google-maps-in-flutter#3) for setup.

### Firebase Admin SDK Setup
- Download the service account JSON file from Firebase project settings and add it to tech_says_no_flask/ directory.
- Update the path to JSON in tech_says_no_flask/app.py:
```
cred = credentials.Certificate("path/to/techsaysno-firebase-adminsdk-tnj21-d26f5188f5.json")
```
  

## Usage
After setting up Firebase and configuring the Flutter app, you can run the app on your local development environment using 
```
flutter run
```

## Acknowledgments
- Inspiration for this project came from the need to provide a quick and discreet way for women to alert their loved ones in case of emergency.
- Special thanks to the open-source community for the tools and libraries that made this project possible as well as already existing software that inspired us to make newest implementation with latest technologies.
