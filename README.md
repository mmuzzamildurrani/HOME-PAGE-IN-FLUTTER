import 'package:flutter/material.dart';

void main() {
  runApp(const MyWebsite());
}

class MyWebsite extends StatelessWidget {
  const MyWebsite({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: HomePage(),
    );
  }
}

class HomePage extends StatefulWidget {
  const HomePage({super.key});

  @override
  State<HomePage> createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  int selectedIndex = 0;

  final List<Widget> pages = const [
    PortfolioBody(),
    ProjectsSection(),
    ContactSection(),
  ];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: pages[selectedIndex],
      bottomNavigationBar: Container(
        margin: const EdgeInsets.all(12),
        decoration: BoxDecoration(
          color: Colors.white,
          borderRadius: BorderRadius.circular(25),
          boxShadow: [
            BoxShadow(
              color: Colors.black.withOpacity(0.1),
              blurRadius: 20,
              spreadRadius: 5,
            ),
          ],
        ),
        child: ClipRRect(
          borderRadius: BorderRadius.circular(25),
          child: BottomNavigationBar(
            currentIndex: selectedIndex,
            onTap: (index) {
              setState(() {
                selectedIndex = index;
              });
            },
            backgroundColor: Colors.white,
            selectedItemColor: Colors.indigo,
            unselectedItemColor: Colors.grey,
            type: BottomNavigationBarType.fixed,
            items: const [
              BottomNavigationBarItem(
                icon: Icon(Icons.home),
                label: "Home",
              ),
              BottomNavigationBarItem(
                icon: Icon(Icons.work),
                label: "Projects",
              ),
              BottomNavigationBarItem(
                icon: Icon(Icons.contact_mail),
                label: "Contact",
              ),
            ],
          ),
        ),
      ),
    );
  }
}

/// Portfolio Body
class PortfolioBody extends StatelessWidget {
  const PortfolioBody({super.key});

  @override
  Widget build(BuildContext context) {
    return const SingleChildScrollView(
      child: Column(
        children: [
          SizedBox(height: 80),
          HeroSection(),
          SizedBox(height: 80),
          SkillsSection(),
          SizedBox(height: 80),
          TechImageSection(),
          SizedBox(height: 80),
          FooterSection(),
        ],
      ),
    );
  }
}

/// Hero Section
class HeroSection extends StatelessWidget {
  const HeroSection({super.key});

  @override
  Widget build(BuildContext context) {
    return Column(
      children: const [
        Text(
          "Hi, I'm Muzzamil",
          style: TextStyle(
            fontSize: 32,
            fontWeight: FontWeight.bold,
          ),
        ),
        SizedBox(height: 10),
        Text(
          "Flutter & ASP.NET Developer",
          style: TextStyle(fontSize: 18, color: Colors.grey),
        ),
      ],
    );
  }
}

/// Skills Section
class SkillsSection extends StatelessWidget {
  const SkillsSection({super.key});

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        const Text(
          "My Skills",
          style: TextStyle(fontSize: 24, fontWeight: FontWeight.bold),
        ),
        const SizedBox(height: 20),
        Wrap(
          spacing: 20,
          runSpacing: 20,
          alignment: WrapAlignment.center,
          children: const [
            SkillCard(title: "Flutter"),
            SkillCard(title: "Dart"),
            SkillCard(title: "ASP.NET"),
            SkillCard(title: "C#"),
          ],
        ),
      ],
    );
  }
}

class SkillCard extends StatelessWidget {
  final String title;

  const SkillCard({super.key, required this.title});

  @override
  Widget build(BuildContext context) {
    return Card(
      elevation: 5,
      child: Padding(
        padding: const EdgeInsets.all(20),
        child: Text(
          title,
          style: const TextStyle(fontSize: 18),
        ),
      ),
    );
  }
}

/// Tech Image Section
class TechImageSection extends StatelessWidget {
  const TechImageSection({super.key});

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Image.network(
          "https://flutter.dev/assets/homepage/carousel/slide_1-layer_0-7e5f6d.png",
          height: 200,
        ),
        const SizedBox(height: 20),
        const Padding(
          padding: EdgeInsets.symmetric(horizontal: 40),
          child: Text(
            "I have learned modern technologies including Flutter for cross-platform app development and ASP.NET for powerful backend systems. "
            "I focus on building responsive, scalable, and clean applications.",
            textAlign: TextAlign.center,
            style: TextStyle(fontSize: 16, color: Colors.grey),
          ),
        ),
      ],
    );
  }
}

/// Projects Section Placeholder
class ProjectsSection extends StatelessWidget {
  const ProjectsSection({super.key});

  @override
  Widget build(BuildContext context) {
    return const Center(
      child: Text(
        "Projects Page",
        style: TextStyle(fontSize: 24, color: Colors.black87),
      ),
    );
  }
}

/// Contact Section Placeholder
class ContactSection extends StatelessWidget {
  const ContactSection({super.key});

  @override
  Widget build(BuildContext context) {
    return const Center(
      child: Text(
        "Contact Page",
        style: TextStyle(fontSize: 24, color: Colors.black87),
      ),
    );
  }
}

/// Professional Footer
class FooterSection extends StatelessWidget {
  const FooterSection({super.key});

  @override
  Widget build(BuildContext context) {
    return Container(
      width: double.infinity,
      padding: const EdgeInsets.symmetric(vertical: 50, horizontal: 20),
      decoration: const BoxDecoration(
        gradient: LinearGradient(
          colors: [
            Color(0xff0f172a),
            Color(0xff1e293b),
          ],
          begin: Alignment.topLeft,
          end: Alignment.bottomRight,
        ),
      ),
      child: Column(
        children: [
          /// Top Footer Content
          Wrap(
            alignment: WrapAlignment.spaceEvenly,
            runSpacing: 40,
            children: [
              Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: const [
                  Text(
                    "Muzzamil",
                    style: TextStyle(
                        fontSize: 22,
                        fontWeight: FontWeight.bold,
                        color: Colors.white),
                  ),
                  SizedBox(height: 10),
                  SizedBox(
                    width: 250,
                    child: Text(
                      "Passionate Flutter & ASP.NET Developer focused on building modern, scalable and responsive applications.",
                      style: TextStyle(color: Colors.white70),
                    ),
                  ),
                ],
              ),
              Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: const [
                  Text(
                    "Quick Links",
                    style: TextStyle(
                        fontSize: 18,
                        fontWeight: FontWeight.bold,
                        color: Colors.white),
                  ),
                  SizedBox(height: 12),
                  Text("Home", style: TextStyle(color: Colors.white70)),
                  SizedBox(height: 6),
                  Text("Projects", style: TextStyle(color: Colors.white70)),
                  SizedBox(height: 6),
                  Text("Contact", style: TextStyle(color: Colors.white70)),
                ],
              ),
              Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: const [
                  Text(
                    "Contact",
                    style: TextStyle(
                        fontSize: 18,
                        fontWeight: FontWeight.bold,
                        color: Colors.white),
                  ),
                  SizedBox(height: 12),
                  Text("Email: muzzamil@email.com",
                      style: TextStyle(color: Colors.white70)),
                  SizedBox(height: 6),
                  Text("Location: Pakistan",
                      style: TextStyle(color: Colors.white70)),
                ],
              ),
            ],
          ),
          const SizedBox(height: 50),
          const Divider(color: Colors.white24),
          const SizedBox(height: 20),

          /// Social Icons
          Row(
            mainAxisAlignment: MainAxisAlignment.center,
            children: const [
              Icon(Icons.facebook, color: Colors.white70),
              SizedBox(width: 20),
              Icon(Icons.linked_camera, color: Colors.white70),
              SizedBox(width: 20),
              Icon(Icons.code, color: Colors.white70),
            ],
          ),
          const SizedBox(height: 20),

          /// Copyright
          const Text(
            "© 2026 Muzzamil. All Rights Reserved.",
            style: TextStyle(color: Colors.white54),
          ),
        ],
      ),
    );
  }
}
