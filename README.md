

import 'package:flutter/material.dart';

void main() {
  runApp(const AmarByabshaApp());
}

class AmarByabshaApp extends StatelessWidget {
  const AmarByabshaApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'আমার ব্যবসা',
      theme: ThemeData(
        primarySwatch: Colors.green,
        scaffoldBackgroundColor: const Color(0xFFF5F8F5),
        useMaterial3: true,
      ),
      home: const DashboardPage(),
    );
  }
}

class DashboardPage extends StatelessWidget {
  const DashboardPage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        backgroundColor: Colors.white,
        title: const Text(
          'আমার ব্যবসা',
          style: TextStyle(
            color: Color(0xFF147D45),
            fontWeight: FontWeight.bold,
          ),
        ),
        actions: const [
          Icon(Icons.notifications_none, color: Colors.green),
          SizedBox(width: 16),
        ],
      ),
      body: SingleChildScrollView(
        padding: const EdgeInsets.all(16),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            const Text(
              'স্বাগতম!',
              style: TextStyle(
                fontSize: 25,
                fontWeight: FontWeight.bold,
              ),
            ),
            const SizedBox(height: 5),
            const Text(
              'আপনার ব্যবসার সম্পূর্ণ হিসাব রাখুন এক জায়গায়।',
              style: TextStyle(color: Colors.black54),
            ),
            const SizedBox(height: 20),

            Container(
              width: double.infinity,
              padding: const EdgeInsets.all(20),
              decoration: BoxDecoration(
                color: const Color(0xFF147D45),
                borderRadius: BorderRadius.circular(18),
              ),
              child: const Column(
                crossAxisAlignment: CrossAxisAlignment.start,
                children: [
                  Text(
                    'আজকের মোট বিক্রি',
                    style: TextStyle(color: Colors.white70),
                  ),
                  SizedBox(height: 8),
                  Text(
                    '₹ 0.00',
                    style: TextStyle(
                      color: Colors.white,
                      fontSize: 32,
                      fontWeight: FontWeight.bold,
                    ),
                  ),
                  SizedBox(height: 8),
                  Text(
                    'আপনার ব্যবসার আজকের হিসাব',
                    style: TextStyle(color: Colors.white70),
                  ),
                ],
              ),
            ),

            const SizedBox(height: 22),
            const Text(
              'ব্যবসার হিসাব',
              style: TextStyle(
                fontSize: 20,
                fontWeight: FontWeight.bold,
              ),
            ),
            const SizedBox(height: 12),

            GridView.count(
              crossAxisCount: 2,
              shrinkWrap: true,
              physics: const NeverScrollableScrollPhysics(),
              crossAxisSpacing: 12,
              mainAxisSpacing: 12,
              childAspectRatio: 1.3,
              children: const [
                DashboardCard(
                  icon: Icons.shopping_cart,
                  title: 'বিক্রি',
                  value: '₹ 0',
                ),
                DashboardCard(
                  icon: Icons.inventory_2,
                  title: 'স্টক',
                  value: '0 পণ্য',
                ),
                DashboardCard(
                  icon: Icons.people,
                  title: 'কাস্টমার',
                  value: '0 জন',
                ),
                DashboardCard(
                  icon: Icons.money_off,
                  title: 'খরচ',
                  value: '₹ 0',
                ),
                DashboardCard(
                  icon: Icons.local_shipping,
                  title: 'সাপ্লায়ার',
                  value: '0 জন',
                ),
                DashboardCard(
                  icon: Icons.bar_chart,
                  title: 'রিপোর্ট',
                  value: 'দেখুন',
                ),
              ],
            ),
          ],
        ),
      ),
      bottomNavigationBar: const NavigationBar(
        selectedIndex: 0,
        destinations: [
          NavigationDestination(
            icon: Icon(Icons.home_outlined),
            label: 'হোম',
          ),
          NavigationDestination(
            icon: Icon(Icons.receipt_long),
            label: 'লেনদেন',
          ),
          NavigationDestination(
            icon: Icon(Icons.inventory),
            label: 'পণ্য',
          ),
          NavigationDestination(
            icon: Icon(Icons.settings),
            label: 'সেটিংস',
          ),
        ],
      ),
    );
  }
}

class DashboardCard extends StatelessWidget {
  final IconData icon;
  final String title;
  final String value;

  const DashboardCard({
    super.key,
    required this.icon,
    required this.title,
    required this.value,
  });

  @override
  Widget build(BuildContext context) {
    return Container(
      padding: const EdgeInsets.all(14),
      decoration: BoxDecoration(
        color: Colors.white,
        borderRadius: BorderRadius.circular(16),
        boxShadow: [
          BoxShadow(
            color: Colors.black.withValues(alpha: 0.04),
            blurRadius: 8,
          ),
        ],
      ),
      child: Column(
        crossAxisAlignment: CrossAxisAlignment.start,
        mainAxisAlignment: MainAxisAlignment.center,
        children: [
          Icon(icon, color: const Color(0xFF147D45), size: 28),
          const SizedBox(height: 9),
          Text(
            title,
            style: const TextStyle(fontWeight: FontWeight.bold),
          ),
          const SizedBox(height: 4),
          Text(value, style: const TextStyle(color: Colors.black54)),
        ],
      ),
    );
  }
}
