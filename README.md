# startup_3
کد فلاتر نمونه اولیه ای اپلیکیشن
import 'package:flutter/material.dart';

void main() {
  runApp(const DarShahrApp());
}

class DarShahrApp extends StatelessWidget {
  const DarShahrApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'در شهر',
      theme: ThemeData(
        primarySwatch: Colors.blue,
        fontFamily: 'IranSans',
      ),
      home: const MainMenu(),
    );
  }
}

class MainMenu extends StatefulWidget {
  const MainMenu({super.key});

  @override
  // ignore: library_private_types_in_public_api
  _MainMenuState createState() => _MainMenuState();
}

class _MainMenuState extends State<MainMenu> {
  int _selectedIndex = 0;

  final List<Widget> _pages = [
    const HomePage(),
    const BusinessesPage(),
    const SearchPage(),
    const ProfilePage(),
    const MapPage(),
  ];

  void _onItemTapped(int index) {
    setState(() {
      _selectedIndex = index;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: _pages[_selectedIndex],
      bottomNavigationBar: BottomNavigationBar(
        type: BottomNavigationBarType.fixed,
        currentIndex: _selectedIndex,
        onTap: _onItemTapped,
        items: const [
          BottomNavigationBarItem(
            icon: Icon(Icons.home),
            label: 'خانه',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.business),
            label: 'کسب و کارها',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.search),
            label: 'جستجو',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.person),
            label: 'پروفایل',
          ),
          BottomNavigationBarItem(
            icon: Icon(Icons.map),
            label: 'نقشه',
          ),
        ],
      ),
    );
  }
}

// صفحات اصلی

class HomePage extends StatelessWidget {
  const HomePage({super.key});

  @override
  Widget build(BuildContext context) {
    // تعریف لیست کسب و کارها
    final List<Map<String, String>> businesses = [
      {
        'name': ' رستوران قیصر ',
        'type': 'رستوران',
        'address': 'تهران، خیابان ولیعصر',
      },
      {
        'name': 'کافه علی بابا',
        'type': 'کافه',
        'address': 'تهران، میدان تجریش',
      },
      {
        'name': ' پارک نوری تهران',
        'type': 'پارک',
        'address': 'تهران',
      },
      {
        'name': 'فست فود زارع',
        'type': 'فست فود',
        'address': 'تهران، میدان گل سرخ',
      },
      // می‌توانید کسب و کارهای بیشتری اضافه کنید
    ];

    return Scaffold(
      appBar: AppBar(
        title: const Text('خانه'),
        centerTitle: true,
        actions: [
          IconButton(
            icon: const Icon(Icons.search),
            onPressed: () {
              // کد جستجو را اینجا پیاده‌سازی کنید
            },
          ),
        ],
      ),
      body: Padding(
        padding: const EdgeInsets.all(8.0),
        child: Column(
          children: [
            // اضافه کردن TextField برای جستجو
            TextField(
              decoration: const InputDecoration(
                labelText: 'جستجو...',
                border: OutlineInputBorder(),
              ),
              onChanged: (query) {
                // کد جستجو را اینجا پیاده‌سازی کنید
              },
            ),
            const SizedBox(height: 8),
            Expanded(
              child: ListView.builder(
                itemCount: businesses.length,
                itemBuilder: (context, index) {
                  final business = businesses[index];
                  return Card(
                    margin: const EdgeInsets.symmetric(vertical: 8),
                    child: ListTile(
                      title: Text(business['name']!),
                      subtitle: Text(business['type']!),
                      trailing: Text(business['address']!),
                      onTap: () {
                        // اینجا می‌توانید به صفحه جزئیات کسب و کار بروید
                      },
                    ),
                  );
                },
              ),
            ),
          ],
        ),
      ),
    );
  }
}

class BusinessesPage extends StatelessWidget {
  const BusinessesPage({super.key});

  @override
  Widget build(BuildContext context) {
    // تعریف لیست کسب و کارها
    final List<Map<String, String>> businesses = [
      {
        'name': 'رستوران قیصر',
        'type': 'رستوران',
        'address': 'تهران، خیابان ولیعصر',
      },
      {
        'name': 'کافه علی بابا',
        'type': 'کافه',
        'address': 'تهران، میدان تجریش',
      },
      {
        'name': ' پارک نوری تهران',
        'type': 'پارک',
        'address': 'تهران',
      },
      {
        'name': 'فست فود زارع',
        'type': 'فست فود',
        'address': 'تهران، میدان گل سرخ',
      },

      // می‌توانید کسب و کارهای بیشتری اضافه کنید
    ];

    return Scaffold(
      appBar: AppBar(
        title: const Text('کسب و کارها'),
        centerTitle: true,
      ),
      body: Padding(
        padding: const EdgeInsets.all(12.0),
        child: ListView.builder(
          itemCount: businesses.length,
          itemBuilder: (context, index) {
            final business = businesses[index];
            return Card(
              margin: const EdgeInsets.symmetric(vertical: 8),
              child: ListTile(
                title: Text(business['name']!),
                subtitle: Text(business['type']!),
                trailing: Text(business['address']!),
                onTap: () {
                  // اینجا می‌توانید به صفحه جزئیات کسب و کار بروید
                },
              ),
            );
          },
        ),
      ),
    );
  }
}

class SearchPage extends StatelessWidget {
  const SearchPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('جستجو'),
        centerTitle: true,
      ),
      body: Padding(
        padding: const EdgeInsets.all(12.0),
        child: Column(
          children: [
            TextField(
              decoration: const InputDecoration(
                labelText: 'عبارت جستجو...',
                border: OutlineInputBorder(),
              ),
              onChanged: (query) {
                // کد جستجو را اینجا پیاده‌سازی کنید
              },
            ),
            const SizedBox(height: 12),
            Expanded(
              child: ListView.builder(
                // اینجا می‌توانید لیست نتایج جستجو را نمایش دهید
                itemCount: 0, // تعداد نتایج جستجو
                itemBuilder: (context, index) {
                  // اینجا باید نمای هر نتیجه جستجو را بسازید
                  return Card(
                    margin: const EdgeInsets.symmetric(vertical: 8),
                    child: ListTile(
                      title: const Text('نتیجه جستجو'),
                      onTap: () {
                        // اینجا می‌توانید به صفحه جزئیات بروید
                      },
                    ),
                  );
                },
              ),
            ),
          ],
        ),
      ),
    );
  }
}

class ProfilePage extends StatelessWidget {
  const ProfilePage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('پروفایل'),
        centerTitle: true,
      ),
      body: Container(
        decoration: BoxDecoration(
          gradient: LinearGradient(
            colors: [Colors.blue.shade300, Color.fromARGB(255, 172, 203, 230)],
            begin: Alignment.topLeft,
            end: Alignment.bottomRight,
          ),
        ),
        child: ListView(
          padding: const EdgeInsets.all(20),
          children: [
            const SizedBox(height: 20),
            const CircleAvatar(
              radius: 70,
              backgroundImage:
                  AssetImage('assets/profile_picture.png'), // تصویر پروفایل
            ),
            const SizedBox(height: 16),
            const Text(
              'نام و نام خانوادگی',
              style: TextStyle(
                  fontSize: 24,
                  fontWeight: FontWeight.bold,
                  color: Colors.white),
              textAlign: TextAlign.center,
            ),
            const SizedBox(height: 8),
            const Text(
              'ایمیل: example@example.com',
              style: TextStyle(fontSize: 16, color: Colors.white),
              textAlign: TextAlign.center,
            ),
            const SizedBox(height: 8),
            const Text(
              'شماره تماس: 0912-345-6789',
              style: TextStyle(fontSize: 16, color: Colors.white),
              textAlign: TextAlign.center,
            ),
            const SizedBox(height: 24),
            ElevatedButton(
              onPressed: () {
                // کد برای ویرایش پروفایل
              },
              style: ElevatedButton.styleFrom(primary: Colors.white),
              child: const Text('ویرایش پروفایل',
                  style: TextStyle(color: Colors.blue)),
            ),
            const SizedBox(height: 16),
            ElevatedButton(
              onPressed: () {
                // کد برای خروج
              },
              style: ElevatedButton.styleFrom(primary: Colors.red),
              child: const Text('خروج از حساب کاربری',
                  style: TextStyle(color: Colors.white)),
            ),
          ],
        ),
      ),
    );
  }
}

class MapPage extends StatelessWidget {
  const MapPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('نقشه'),
        centerTitle: true,
      ),
      body: const Center(
          child: Text('حوصلم نمیشد کتابخونه های نقشه رو اضافه کنم')),
    );
  }
}
