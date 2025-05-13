# football-
پیشبینی نتایج فوتبال
import 'package:flutter/material.dart';

void main() {
  runApp(PishbinFootballApp());
}

class PishbinFootballApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'پیش‌بین فوتبال',
      theme: ThemeData(primarySwatch: Colors.blue),
      home: HomePage(),
    );
  }
}

class HomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('لیگ‌های فوتبال')),
      body: ListView(
        children: <Widget>[
          LeagueCard(leagueName: 'لیگ برتر انگلیس'),
          LeagueCard(leagueName: 'لالیگا اسپانیا'),
          LeagueCard(leagueName: 'بوندس‌لیگا آلمان'),
          LeagueCard(leagueName: 'سری آ ایتالیا'),
          LeagueCard(leagueName: 'لیگ ۱ فرانسه'),
        ],
      ),
    );
  }
}

class LeagueCard extends StatelessWidget {
  final String leagueName;

  LeagueCard({required this.leagueName});

  @override
  Widget build(BuildContext context) {
    return Card(
      child: ListTile(
        title: Text(leagueName),
        onTap: () {
          Navigator.push(
            context,
            MaterialPageRoute(builder: (context) => MatchListPage(leagueName: leagueName)),
          );
        },
      ),
    );
  }
}

class MatchListPage extends StatelessWidget {
  final String leagueName;

  MatchListPage({required this.leagueName});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('$leagueName - پیش‌بینی‌ها')),
      body: ListView(
        children: <Widget>[
          MatchCard(team1: 'تیم 1', team2: 'تیم 2'),
          MatchCard(team1: 'تیم 3', team2: 'تیم 4'),
          // Add more matches here
        ],
      ),
    );
  }
}

class MatchCard extends StatelessWidget {
  final String team1;
  final String team2;

  MatchCard({required this.team1, required this.team2});

  @override
  Widget build(BuildContext context) {
    return Card(
      child: ListTile(
        title: Text('$team1 vs $team2'),
        subtitle: Text('پیش‌بینی: گل‌های تیم‌ها و مجموع کرنرها'),
        onTap: () {
          Navigator.push(
            context,
            MaterialPageRoute(builder: (context) => PredictionPage(team1: team1, team2: team2)),
          );
        },
      ),
    );
  }
}

class PredictionPage extends StatelessWidget {
  final String team1;
  final String team2;

  PredictionPage({required this.team1, required this.team2});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('$team1 vs $team2 - پیش‌بینی')),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text('نتیجه نهایی: ۲ - ۱'),
            Text('مجموع کرنرها: ۱۰'),
            ElevatedButton(
              onPressed: () {
                Navigator.pop(context);
              },
              child: Text('بازگشت'),
            ),
          ],
        ),
      ),
    );
  }
}
