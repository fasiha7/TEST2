# TEST2
import 'package:flutter/material.dart';

void main() {
  runApp(TaekwondoTrainingApp());
}

// Main App Widget
// This widget initializes the app and sets up the theme and home screen
class TaekwondoTrainingApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Taekwondo Training',
      theme: ThemeData(primarySwatch: Colors.blue), // Set primary color theme
      debugShowCheckedModeBanner: false, // Hide the debug banner
      home: HomeScreen(), // Set the home screen as the entry point
    );
  }
}

// Home Screen Widget
// This is the first screen the user sees when they open the app
class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Taekwondo Training'), // Title of the app bar
      ),
      body: Center(
        child: Padding(
          padding: const EdgeInsets.all(16.0),
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: [
              // Display an image to represent Taekwondo training
              Image.asset('assets/taekwondo3.jpg',
                  height: 200), // Replace with your own image asset
              SizedBox(height: 20),
              Text(
                'Welcome to Taekwondo Training!',
                style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
                textAlign: TextAlign.center, // Center align the text
              ),
              SizedBox(height: 10),
              Text(
                '"Taekwondo basics are the first steps to strength and discipline."',
                style: TextStyle(fontSize: 14),
                textAlign: TextAlign.center, // Center align the text
              ),
              SizedBox(height: 30),
              // Button to start training, which navigates to the training screen
              ElevatedButton(
                onPressed: () {
                  Navigator.push(
                    context,
                    MaterialPageRoute(builder: (context) => TrainingScreen()),
                  );
                },
                child: Text('Start Training'),
              ),
            ],
          ),
        ),
      ),
    );
  }
}

// Training Screen Widget
// This screen displays a list of training steps with their descriptions and icons
class TrainingScreen extends StatelessWidget {
  // List of training steps with titles, subtitles, icons, and colors for each step
  final List<Map<String, dynamic>> trainingSteps = [
    {
      'title': 'Warm-Up',
      'subtitle': 'Start with basic stretching to loosen your muscles.',
      'icon': Icons.sports_martial_arts,
      'color': Colors.blue,
    },
    {
      'title': 'Basic Stance',
      'subtitle': 'Learn the fighting stance to maintain balance.',
      'icon': Icons.sports_martial_arts,
      'color': Colors.green,
    },
    {
      'title': 'Front Kick',
      'subtitle': 'Practice the front kick with controlled power.',
      'icon': Icons.sports,
      'color': Colors.orange,
    },
    {
      'title': 'Basic Punch',
      'subtitle': 'Work on your straight punches with focus.',
      'icon': Icons.sports_mma,
      'color': Colors.red,
    },
    {
      'title': 'Side Kick',
      'subtitle': 'Perform side kicks to improve leg strength.',
      'icon': Icons.directions_run,
      'color': Colors.purple,
    },
    {
      'title': 'Strength Training',
      'subtitle': 'Focus on exercises to build your core strength.',
      'icon': Icons.fitness_center,
      'color': Colors.teal,
    },
    {
      'title': 'Meditation',
      'subtitle': 'End the session with meditation to calm your mind.',
      'icon': Icons.self_improvement,
      'color': Colors.pink,
    },
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Training Steps'), // Title of the training screen
      ),
      body: Column(
        children: [
          // Expanded widget ensures the list of training steps takes available space
          Expanded(
            child: Padding(
              padding: const EdgeInsets.all(16.0),
              child: ListView.builder(
                itemCount: trainingSteps.length, // Count of training steps
                itemBuilder: (context, index) {
                  final step = trainingSteps[index]; // Get the current training step
                  return Padding(
                    padding: const EdgeInsets.symmetric(vertical: 8.0),
                    child: Container(
                      padding: EdgeInsets.all(16),
                      decoration: BoxDecoration(
                        color: Colors.white,
                        borderRadius: BorderRadius.circular(12),
                        boxShadow: [
                          BoxShadow(
                            color: Colors.grey.withOpacity(0.3),
                            blurRadius: 5,
                            spreadRadius: 2,
                          ),
                        ],
                      ),
                      child: Row(
                        children: [
                          // Icon representing the training step
                          Icon(step['icon'], color: step['color']),
                          SizedBox(width: 16),
                          Expanded(
                            child: Column(
                              crossAxisAlignment: CrossAxisAlignment.start,
                              children: [
                                // Title of the training step
                                Text(
                                  step['title'],
                                  style: TextStyle(
                                      fontSize: 18,
                                      fontWeight: FontWeight.bold),
                                ),
                                SizedBox(height: 4),
                                // Subtitle providing a description of the step
                                Text(step['subtitle']),
                              ],
                            ),
                          ),
                        ],
                      ),
                    ),
                  );
                },
              ),
            ),
          ),
          // Button to go back to the home screen
          Padding(
            padding: const EdgeInsets.all(16.0),
            child: ElevatedButton(
              onPressed: () {
                Navigator.pop(context); // Navigate back to the home screen
              },
              child: Text('Back to Home'),
              style: ElevatedButton.styleFrom(
                minimumSize: Size(double.infinity, 50), // Full-width button
              ),
            ),
          ),
        ],
      ),
    );
  }
}
