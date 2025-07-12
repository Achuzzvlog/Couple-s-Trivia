💖 Brew-Studios Presents: Couple's Trivia 💖

A fun, real-time, web-based multiplayer trivia game designed for couples! Test your knowledge about each other and general fun facts in an engaging, interactive experience.
✨ Features

    Multiplayer: Play simultaneously with your partner in a shared game room.

    Real-time Updates: Powered by Firebase Firestore for instant synchronization of questions, answers, and scores.

    Static Trivia Questions: A curated list of fun and lighthearted questions specifically for couples.

    Dynamic Game States: Manages game flow from waiting for players, to question display, answer submission, and revealing answers.

    User-Friendly Interface: Simple and intuitive design with a focus on a smooth user experience.

    Mobile-Responsive: Designed to look great and be playable on various screen sizes.

    Free to Play: Built with technologies that allow for free usage.

🚀 Technologies Used

    HTML5: Structure of the game.

    CSS3: Styling and animations for a pleasant visual experience.

    JavaScript (ES6+): Game logic and interactivity.

    Firebase Firestore: Real-time NoSQL cloud database for game state management and synchronization.

    Firebase Authentication: Anonymous authentication for easy user identification without sign-ups.

🎮 How to Play

    Enter Your Name: Upon opening the game, enter your name and click "Start Game."

    Create or Join a Game:

        Create New Game: Click "Create New Game." Your unique User ID will be displayed. This ID also serves as your game room ID. Share this ID with your partner.

        Join Game: If your partner has already created a game, ask for their User ID. Enter it into the "Enter partner's User ID to join" field and click "Join Game."

    Start the Game:

        Once both players are in the same game room, Player 1 (the one who created the game) will see a "Start Game" button. Click it to fetch the first trivia question.

    Answer Questions:

        Both players will see the same question. Type your answer in the input field and click "Submit Answer."

        Once both players have submitted their answers, the answers will be revealed on screen.

    Next Question:

        Player 1 is responsible for advancing the game. Click "Next Question" to get the next trivia question and update scores. Scores are incremented for each player who submits an answer.

    End Game:

        The game continues through the list of questions. You can choose to leave the game at any time.

    Leave Game: Click the "Leave Game" button to exit the current game. If Player 1 leaves, the game room will be deleted. If Player 2 leaves, their slot becomes available for another player.

⚙️ Setup for Development & Deployment

To get this game running locally or deploy it yourself, you'll need a Firebase project.
Prerequisites

    A modern web browser.

    A text editor (like VS Code).

    A Firebase account.

Local Setup

    Clone the Repository (or save the file):

    git clone https://github.com/your-username/couples-trivia-game.git
    cd couples-trivia-game

    (If you just have the index.html file, simply save it to a folder on your computer.)

    Open index.html:
    Open the index.html file in your web browser. The game will load, but Firebase functionality won't work until configured.

Firebase Configuration (Crucial!)

The game uses Firebase Firestore for real-time data and Firebase Authentication for anonymous user IDs. You need to set up your own Firebase project:

    Create a Firebase Project:

        Go to the Firebase Console.

        Click "Add project" and follow the prompts to create a new project.

    Enable Firestore Database:

        In your Firebase project, navigate to "Firestore Database" from the left menu.

        Click "Create database." Choose "Start in test mode" for quick setup during development (you can refine security rules later). Select a location for your database.

    Enable Anonymous Authentication:

        In your Firebase project, navigate to "Authentication" from the left menu.

        Go to the "Sign-in method" tab.

        Find "Anonymous" and enable it.

    Register a Web App and Get Your Firebase Config:

        In your Firebase project, go to "Project settings" (the gear icon next to "Project overview").

        Under the "General" tab, scroll down to "Your apps" and click the web icon (</>) to "Add app to get started."

        Follow the steps to register your web app.

        Firebase will provide you with a firebaseConfig object. It will look like this:

        const firebaseConfig = {
            apiKey: "YOUR_API_KEY",
            authDomain: "YOUR_AUTH_DOMAIN",
            projectId: "YOUR_PROJECT_ID",
            storageBucket: "YOUR_STORAGE_BUCKET",
            messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
            appId: "YOUR_APP_ID"
        };

        Copy this entire firebaseConfig object.

    Update index.html with Your Firebase Config:

        Open your index.html file in a text editor.

        Find the <script type="module"> block near the end of the <body>.

        Locate the initializeFirebase function.

        Replace the placeholder lines for appId and firebaseConfig with your actual Firebase configuration:

        // Replace with your actual Firebase config from the Firebase Console
        const firebaseConfig = {
            apiKey: "YOUR_ACTUAL_API_KEY_FROM_FIREBASE",
            authDomain: "YOUR_AUTH_DOMAIN_FROM_FIREBASE",
            projectId: "YOUR_PROJECT_ID_FROM_FIREBASE",
            storageBucket: "YOUR_STORAGE_BUCKET_FROM_FIREBASE",
            messagingSenderId: "YOUR_MESSAGING_SENDER_ID_FROM_FIREBASE",
            appId: "YOUR_APP_ID_FROM_FIREBASE"
        };
        const appId = firebaseConfig.appId; // Use the appId from your config

        // Replace the authentication block with:
        await signInAnonymously(auth); // Sign in anonymously for game functionality

        Save your index.html file.

    Set Firestore Security Rules:

        In your Firebase Console, go to "Firestore Database" -> "Rules."

        Replace the default rules with the following to allow authenticated users to read and write to your public game data:

        rules_version = '2';
        service cloud.firestore {
          match /databases/{database}/documents {
            // Allow authenticated users to read and write to public game data
            // Ensure 'appId' matches your Firebase project's appId if you modify the path
            match /artifacts/{appId}/public/data/coupleGames/{gameId} {
              allow read, write: if request.auth != null;
            }
          }
        }

        Click "Publish" to apply these rules.

Deployment

Once your index.html file is updated with your Firebase configuration, you can deploy it to any static site hosting service.
🤝 Contributing

Feel free to fork this repository, suggest improvements, or add new features!
💡 Future Improvements

    Add a timer for answering questions.

    Implement a scoring system based on correct answers (if questions had predefined answers).

    Allow players to submit their own custom questions.

    Add more diverse question categories.

    Implement a "rematch" or "play again" feature.

    Enhance UI/UX with more animations and feedback.

📄 License

This project is licensed under the MIT License - see the LICENSE file for details (if you create one, otherwise omit this section).
🎮 Credits

Developed by Brew-Studios.
