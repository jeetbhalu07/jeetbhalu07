- 👋 Hi, I’m @jeetbhalu07
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

- Main.dart
import 'package:app3/data.dart';
import 'package:app3/level_page.dart';
import 'package:app3/start.dart';
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';
import 'package:shared_preferences/shared_preferences.dart';

void main() {
  runApp(MaterialApp(
    debugShowCheckedModeBanner: false,
    home: First(),
  ));
}

class First extends StatefulWidget {
  static SharedPreferences? prefer;

  @override
  State<First> createState() => _FirstState();
}

class _FirstState extends State<First> {
  void initState() {
    // TODO: implement initState
    super.initState();
    share_pefer();
  }

  share_pefer() async {
    First.prefer = await SharedPreferences.getInstance();
    int levelno=First.prefer!.getInt("levelNo")??0;
    l=List.filled(data.ans.length,"");
    for(int i=0;i<levelno;i++){
      l[i]=First.prefer!.getString("level_status$i")??"";
    }
    curren_lvl=First.prefer!.getInt("levelNo")??0;
  }
  List l=[];
  bool t = false;
  bool t1 = false;
  bool t2 = false;
  int ?curren_lvl;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: Container(
          decoration: BoxDecoration(
              image: DecorationImage(
                  fit: BoxFit.fill,
                  image: AssetImage("myasset/first/background.jpg"))),
          child: Column(
            children: [
              Row(
                children: [
                  Expanded(
                      child: Container(
                        margin: EdgeInsets.only(top: 20),
                        alignment: Alignment.center,
                        child: Text("Math Puzzles", style: TextStyle(color: Colors.blue, fontSize: 30)),
                      )),
                ],
              ),
              Expanded(
                flex: 7,
                child: Container(
                    margin: EdgeInsets.all(10),
                    height: double.infinity,
                    width: double.infinity,
                    decoration: BoxDecoration(image: DecorationImage(image: AssetImage(
                        "myasset/first/blackboard_main_menu.png"), fit: BoxFit.fill)),
                    child: Column(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          Row(
                            mainAxisAlignment: MainAxisAlignment.center,
                            children: [
                              GestureDetector(
                                onTapUp: (details) {
                                  t = false;
                                  Navigator.push(context, MaterialPageRoute(
                                    builder: (context) {
                                      return start();
                                    },
                                  ));
                                  setState(() {});
                                },
                                onTapDown: (details) {
                                  t = true;
                                  setState(() {});
                                },
                                onTapCancel: () {
                                  t = false;
                                  setState(() {});
                                },
                                child: Container(
                                  height: 50,
                                  width: 150,
                                  alignment: Alignment.center,
                                  decoration: BoxDecoration(
                                    borderRadius:
                                    BorderRadius.all(Radius.circular(10)),
                                    border: (t == true)
                                        ? Border.all(color: Colors.white)
                                        : null,
                                  ),
                                  child: Text("CONTINUE", style: TextStyle(fontSize: 25, fontFamily: "myfont",
                                      color: Colors.white),),
                                ),
                              )
                            ],
                          ),
                          Row(
                            mainAxisAlignment: MainAxisAlignment.center,
                            children: [
                              GestureDetector(
                                onTapUp: (details) {
                                  t1 = false;
                                  Navigator.push(context, MaterialPageRoute(
                                    builder: (context) {
                                      return level_page(l);
                                    },
                                  ));
                                  setState(() {});
                                },
                                onTapDown: (details) {
                                  t1 = true;
                                  setState(() {});
                                },
                                onTapCancel: () {
                                  t1 = false;
                                  setState(() {});
                                },
                                child: Container(
                                  height: 50,
                                  width: 150,
                                  alignment: Alignment.center,
                                  decoration: BoxDecoration(
                                    borderRadius:
                                    BorderRadius.all(Radius.circular(10)),
                                    border: (t1 == true)
                                        ? Border.all(color: Colors.white)
                                        : null,
                                  ),
                                  child: Text("PUZZLES", style: TextStyle(fontSize: 25, fontFamily: "myfont",
                                      color: Colors.white),),
                                ),
                              )
                            ],
                          ),
                          Row(
                            mainAxisAlignment: MainAxisAlignment.center,
                            children: [
                              GestureDetector(
                                onTapUp: (details) {
                                  t2 = false;
                                  // Navigator.push(context, MaterialPageRoute(
                                  //   builder: (context) {
                                  //     return start(curren_lvl);
                                  //   },
                                  // ));
                                  setState(() {});
                                },
                                onTapDown: (details) {
                                  t2 = true;
                                  setState(() {});
                                },
                                onTapCancel: () {
                                  t2 = false;
                                  setState(() {});
                                },
                                child: Container(
                                  height: 50,
                                  width: 150,
                                  alignment: Alignment.center,
                                  decoration: BoxDecoration(
                                    borderRadius:
                                    BorderRadius.all(Radius.circular(10)),
                                    border: (t2 == true)
                                        ? Border.all(color: Colors.white)
                                        : null,
                                  ),
                                  child: Text("BUY PR0", style: TextStyle(fontSize: 25, fontFamily: "myfont",
                                      color: Colors.white),),
                                ),
                              )
                            ],
                          ),
                        ])),
              ),
              Expanded(child: Text("")),
              Expanded(
                  child: Column(
                    children: [
                      Expanded(
                        child: Row(
                            mainAxisAlignment: MainAxisAlignment.end,
                            children: [
                              Container(
                                margin: EdgeInsets.all(5),
                                height: 50,
                                width: 50,
                                decoration: BoxDecoration(
                                  borderRadius:
                                  BorderRadius.all(Radius.circular(10)),
                                  image: DecorationImage(
                                      fit: BoxFit.fill,
                                      image:
                                      AssetImage("myasset/first/shareus.png")),
                                  gradient: LinearGradient(
                                      colors: [
                                        Colors.grey,
                                        Colors.white,
                                        Colors.grey
                                      ],
                                      begin: Alignment.center,
                                      end: Alignment.centerLeft),
                                ),
                              ),
                              Container(
                                margin: EdgeInsets.all(5),
                                height: 50,
                                width: 50,
                                decoration: BoxDecoration(
                                  borderRadius:
                                  BorderRadius.all(Radius.circular(10)),
                                  image: DecorationImage(
                                      fit: BoxFit.fill,
                                      image:
                                      AssetImage("myasset/first/emailus.png")),
                                  gradient: LinearGradient(
                                      colors: [
                                        Colors.grey,
                                        Colors.white,
                                        Colors.grey
                                      ],
                                      begin: Alignment.center,
                                      end: Alignment.centerLeft),
                                ),
                              )
                            ]),
                      ),
                    ],
                  ))
            ],
          ),
        ),
      ),
    );
  }
}
- start.dart
-
import 'package:app3/data.dart';
import 'package:app3/main.dart';
import 'package:app3/win.dart';
import 'package:flutter/material.dart';

class start extends StatefulWidget {
  int? ind;

  start([this.ind]);

  @override
  State<start> createState() => _startState();
}

class _startState extends State<start> {
  String str = "";
  int curren_lvl = 0;

  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    if (widget.ind != null) {
      curren_lvl = widget.ind!;
    } else {
      curren_lvl = First.prefer!.getInt("levelNo") ?? 0;
    }
    print("levelNno$curren_lvl");
    setState(() {});
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: WillPopScope(
        onWillPop: () async {
          showDialog(
            context: context,
            builder: (context) {
              return AlertDialog(
                title: Text("Exit Again"),
                actions: [
                  TextButton(
                      onPressed: () {
                        Navigator.pop(context);
                      },
                      child: Text("cancel")),
                  TextButton(
                      onPressed: () {
                        Navigator.pushReplacement(context, MaterialPageRoute(
                          builder: (context) {
                            return First();
                          },
                        ));
                      },
                      child: Text("ok"))
                ],
              );
            },
          );
          return true;
        },
        child: SafeArea(
            child: Container(
              decoration: BoxDecoration(
                  image: DecorationImage(
                      image: AssetImage("myasset/first/gameplaybackground.jpg"),
                      fit: BoxFit.fill)),
              child: Column(
                  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
                  children: [
                    Expanded(
                      flex: 2,
                      child: Row(
                        children: [
                          Expanded(
                              child: InkWell(
                                onTap: () {
                                  String st =
                                      First.prefer!.getString("skip_time") ?? "";
                                  if (st == "") {
                                    DateTime dt = DateTime.now();
                                    First.prefer!.setString("skip_time", dt.toString());
                                    First.prefer!
                                        .setString("level_status$curren_lvl", "no");
                                     curren_lvl++;
                                    First.prefer!.setInt("levelNo", curren_lvl);
                                  } else {
                                    DateTime cur_time = DateTime.now();
                                    DateTime skip_time = DateTime.parse(st);
                                    Duration dur = cur_time.difference(skip_time);
                                    int sec = dur.inSeconds;
                                    if (sec > 35) {
                                      First.prefer!
                                          .setString("skip_time", cur_time.toString());
                                      First.prefer!
                                          .setString("level_status$curren_lvl", "no");
                                      curren_lvl++;
                                      First.prefer!.setInt("levelNo", curren_lvl);
                                    } else {
                                      showDialog(
                                        context: context,
                                        builder: (context) {
                                          return AlertDialog(
                                            title: Text("U Can Skip After 35 Second"),
                                            actions: [
                                              TextButton(
                                                  onPressed: () {
                                                    Navigator.pop(context);
                                                  },
                                                  child: Text(
                                                    "OK",
                                                    style: TextStyle(fontSize: 25),
                                                  ))
                                            ],
                                          );
                                        },
                                      );
                                    }
                                  }
                                  setState(() {});
                                },
                                child: Container(
                                  height: 50,
                                  width: 50,
                                  decoration: BoxDecoration(
                                      image: DecorationImage(
                                          image: AssetImage("myasset/first/skip.png"))),
                                ),
                              )),
                          Expanded(
                              child: Container(
                                alignment: Alignment.center,
                                height: 100,
                                width: double.infinity,
                                decoration: BoxDecoration(
                                    image: DecorationImage(
                                        image: AssetImage(
                                            "myasset/first/level_board.png"))),
                                child: Text(
                                  "Puzzle ${curren_lvl + 1}",
                                  style: TextStyle(fontSize: 15, fontFamily: "myfont"),
                                ),
                              )),
                          Expanded(
                              child: Container(
                                height: 50,
                                width: 50,
                                decoration: BoxDecoration(
                                    image: DecorationImage(
                                        image: AssetImage("myasset/first/hint.png"))),
                              )),
                        ],
                      ),
                    ),
                    Expanded(
                        flex: 11,
                        child: Row(
                          children: [
                            Expanded(
                              child: Container(
                                margin: EdgeInsets.only(
                                    bottom: 200, right: 10, left: 10),
                                height: double.infinity,
                                width: double.infinity,
                                decoration: BoxDecoration(
                                    image: DecorationImage(
                                        image:
                                        AssetImage("${data.level[curren_lvl]}"),
                                        fit: BoxFit.fill)),
                              ),
                            ),
                          ],
                        )),
                    Expanded(child: Text("")),
                    Expanded(
                      flex: 3,
                      child: Container(
                        height: double.infinity,
                        width: double.infinity,
                        decoration: BoxDecoration(
                          color: Colors.black,
                          borderRadius: BorderRadius.all(Radius.circular(10)),
                          border: Border.all(color: Colors.black, width: 3),
                        ),
                        child: Column(
                          children: [
                            Row(
                              children: [
                                Expanded(
                                  flex: 3,
                                  child: Container(
                                    alignment: Alignment.centerLeft,
                                    child: Text("$str"),
                                    margin: EdgeInsets.all(10),
                                    height: 50,
                                    width: 100,
                                    decoration: BoxDecoration(
                                      color: Colors.white,
                                      borderRadius:
                                      BorderRadius.all(Radius.circular(10)),
                                      border:
                                      Border.all(color: Colors.black, width: 3),
                                    ),
                                  ),
                                ),
                                Expanded(
                                    child: InkWell(
                                      onTap: () {
                                        if (str != "") {
                                          str = str.substring(0, str.length - 1);
                                        }
                                        setState(() {});
                                      },
                                      child: Container(
                                        margin: EdgeInsets.all(10),
                                        height: 50,
                                        width: 50,
                                        decoration: BoxDecoration(
                                            image: DecorationImage(
                                              image: AssetImage("myasset/first/delete.png"),
                                            )),
                                      ),
                                    )),
                                Expanded(
                                    child: InkWell(
                                      onTap: () {
                                        if (str == "${data.ans[curren_lvl]}") {
                                          if (widget.ind == null) {
                                            First.prefer!.setString(
                                                "level_status$curren_lvl", "yes");
                                            curren_lvl++;
                                            First.prefer!.setInt("levelNo", curren_lvl);
                                            str = "";
                                            Navigator.push(context, MaterialPageRoute(
                                              builder: (context) {
                                                return win(curren_lvl);
                                              },
                                            ));
                                          } else {
                                            str = "";
                                            First.prefer!.setString(
                                                "level_status$curren_lvl", "yes");
                                            curren_lvl++;
                                            Navigator.push(context, MaterialPageRoute(
                                              builder: (context) {
                                                return win(curren_lvl,true);
                                              },
                                            ));
                                          }
                                        } else {
                                          ScaffoldMessenger.of(context).showSnackBar(
                                              SnackBar(
                                                  content: Text("Answer is wrong")));
                                        }
                                        setState(() {});
                                      },
                                      child: Container(
                                        alignment: Alignment.center,
                                        margin: EdgeInsets.all(10),
                                        height: 50,
                                        width: 100,
                                        decoration: BoxDecoration(
                                            color: Colors.black26,
                                            borderRadius: BorderRadius.circular(10)),
                                        child: Text(
                                          "SUBMIT",
                                          style: TextStyle(
                                              fontSize: 20, color: Colors.white),
                                        ),
                                      ),
                                    )),
                              ],
                            ),
                            Row(
                              children: [
                                Expanded(
                                  child: InkWell(
                                    onTap: () {
                                      str += '1';
                                      setState(() {});
                                    },
                                    child: Container(
                                      margin: EdgeInsets.only(left: 2, right: 2),
                                      decoration: BoxDecoration(
                                          border: Border.all(
                                              color: Colors.white, width: 2)),
                                      alignment: Alignment.center,
                                      child: Text("1",
                                          style: TextStyle(color: Colors.white)),
                                    ),
                                  ),
                                ),
                                Expanded(
                                  child: InkWell(
                                    onTap: () {
                                      str += '2';
                                      setState(() {});
                                    },
                                    child: Container(
                                      margin: EdgeInsets.only(left: 2, right: 2),
                                      decoration: BoxDecoration(
                                          border: Border.all(
                                              color: Colors.white, width: 2)),
                                      alignment: Alignment.center,
                                      child: Text("2",
                                          style: TextStyle(color: Colors.white)),
                                    ),
                                  ),
                                ),
                                Expanded(
                                  child: InkWell(
                                    onTap: () {
                                      str += '3';
                                      setState(() {});
                                    },
                                    child: Container(
                                      margin: EdgeInsets.only(left: 2, right: 2),
                                      decoration: BoxDecoration(
                                          border: Border.all(
                                              color: Colors.white, width: 2)),
                                      alignment: Alignment.center,
                                      child: Text("3",
                                          style: TextStyle(color: Colors.white)),
                                    ),
                                  ),
                                ),
                                Expanded(
                                  child: InkWell(
                                    onTap: () {
                                      str += '4';
                                      setState(() {});
                                    },
                                    child: Container(
                                      margin: EdgeInsets.only(left: 2, right: 2),
                                      decoration: BoxDecoration(
                                          border: Border.all(
                                              color: Colors.white, width: 2)),
                                      alignment: Alignment.center,
                                      child: Text("4",
                                          style: TextStyle(color: Colors.white)),
                                    ),
                                  ),
                                ),
                                Expanded(
                                  child: InkWell(
                                    onTap: () {
                                      str += '5';
                                      setState(() {});
                                    },
                                    child: Container(
                                      margin: EdgeInsets.only(left: 2, right: 2),
                                      decoration: BoxDecoration(
                                          border: Border.all(
                                              color: Colors.white, width: 2)),
                                      alignment: Alignment.center,
                                      child: Text("5",
                                          style: TextStyle(color: Colors.white)),
                                    ),
                                  ),
                                ),
                                Expanded(
                                  child: InkWell(
                                    onTap: () {
                                      str += '6';
                                      setState(() {});
                                    },
                                    child: Container(
                                      margin: EdgeInsets.only(left: 2, right: 2),
                                      decoration: BoxDecoration(
                                          border: Border.all(
                                              color: Colors.white, width: 2)),
                                      alignment: Alignment.center,
                                      child: Text("6",
                                          style: TextStyle(color: Colors.white)),
                                    ),
                                  ),
                                ),
                                Expanded(
                                  child: InkWell(
                                    onTap: () {
                                      str += '7';
                                      setState(() {});
                                    },
                                    child: Container(
                                      margin: EdgeInsets.only(left: 2, right: 2),
                                      decoration: BoxDecoration(
                                          border: Border.all(
                                              color: Colors.white, width: 2)),
                                      alignment: Alignment.center,
                                      child: Text("7",
                                          style: TextStyle(color: Colors.white)),
                                    ),
                                  ),
                                ),
                                Expanded(
                                  child: InkWell(
                                    onTap: () {
                                      str += '8';
                                      setState(() {});
                                    },
                                    child: Container(
                                      margin: EdgeInsets.only(left: 2, right: 2),
                                      decoration: BoxDecoration(
                                          border: Border.all(
                                              color: Colors.white, width: 2)),
                                      alignment: Alignment.center,
                                      child: Text("8",
                                          style: TextStyle(color: Colors.white)),
                                    ),
                                  ),
                                ),
                                Expanded(
                                  child: InkWell(
                                    onTap: () {
                                      str += '9';
                                      setState(() {});
                                    },
                                    child: Container(
                                      margin: EdgeInsets.only(left: 2, right: 2),
                                      decoration: BoxDecoration(
                                          border: Border.all(
                                              color: Colors.white, width: 2)),
                                      alignment: Alignment.center,
                                      child: Text("9",
                                          style: TextStyle(color: Colors.white)),
                                    ),
                                  ),
                                ),
                                Expanded(
                                  child: InkWell(
                                    onTap: () {
                                      str += '0';
                                      setState(() {});
                                    },
                                    child: Container(
                                      margin: EdgeInsets.only(left: 2, right: 2),
                                      decoration: BoxDecoration(
                                          border: Border.all(
                                              color: Colors.white, width: 2)),
                                      alignment: Alignment.center,
                                      child: Text("0",
                                          style: TextStyle(color: Colors.white)),
                                    ),
                                  ),
                                ),
                              ],
                            ),
                          ],
                        ),
                      ),
                    ),
                    //Expanded(child: Text(""),),
                  ]),
            )),
      ),
    );
  }
}

<!---

jeetbhalu07/jeetbhalu07 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

-WIN.DART

import 'package:app3/main.dart';
import 'package:app3/start.dart';
import 'package:flutter/material.dart';

class win extends StatefulWidget {
  int curren_lvl;
  bool ?is_skip;
  win(this.curren_lvl,[this.is_skip]);

  @override
  State<win> createState() => _winState();
}

class _winState extends State<win> {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: Container(
          decoration: BoxDecoration(
              image: DecorationImage(
                  fit: BoxFit.fill,
                  image: AssetImage("myasset/first/background.jpg"))),
          child: Column(
            children: [
              Container(
                  margin: EdgeInsets.only(top: 30),
                  child: Text("Puzzle ${widget.curren_lvl} Completed", style: TextStyle(fontSize: 25),)),
              Expanded(
                flex: 2,
                child: Container(
                  height: 250,
                  width:double.infinity,
                  decoration: BoxDecoration(
                      image: DecorationImage(image: AssetImage("myasset/first/trophy.png"))),
                ),
              ),

              Expanded(
                child: Column(children: [
                  Expanded(
                    child: InkWell(onTap: () {
                      if(widget.is_skip==true){
                        Navigator.push(context, MaterialPageRoute(builder: (context) {
                          return start(widget.curren_lvl);
                        },));
                      }
                      else{
                        Navigator.push(context, MaterialPageRoute(builder: (context) {
                          return start();
                        },));
                      }
                    },
                      child: Container(
                        margin: EdgeInsets.all(5),
                        alignment: Alignment.center,
                        height:100,
                        width: 150,
                        child: Text("Continue",style: TextStyle(fontSize: 25,),),
                        decoration: BoxDecoration(
                            gradient: LinearGradient(
                                colors: [Colors.grey, Colors.white, Colors.grey], begin: Alignment.center,
                                end: Alignment.centerLeft),
                            borderRadius: BorderRadius.circular(10),border: Border.all(color: Colors.black,width: 3)),
                      ),
                    ),
                  ),
                  Expanded(
                    child: InkWell(onTap: () {
                      Navigator.push(context, MaterialPageRoute(builder: (context) {
                        return First();
                      },));
                    },
                      child: Container(
                        margin: EdgeInsets.all(5),
                        alignment: Alignment.center,
                        height:150,
                        width: 150,
                        child: Text("Main Menu",style: TextStyle(fontSize: 25,),),
                        decoration: BoxDecoration(
                            gradient: LinearGradient(
                                colors: [Colors.grey, Colors.white, Colors.grey], begin: Alignment.center,
                                end: Alignment.centerLeft),
                            borderRadius: BorderRadius.circular(10),border: Border.all(color: Colors.black,width: 3)),
                      ),
                    ),
                  ),
                  Expanded(
                    child: Container(
                      margin: EdgeInsets.all(5),
                      alignment: Alignment.center,
                      height:50,
                      width: 150,
                      child: Text("Buy Pro",style: TextStyle(fontSize: 25,),),
                      decoration: BoxDecoration(
                          gradient: LinearGradient(
                              colors: [Colors.grey, Colors.white, Colors.grey], begin: Alignment.center,
                              end: Alignment.centerLeft),
                          borderRadius: BorderRadius.circular(10),border: Border.all(color: Colors.black,width: 3)),
                    ),
                  ),],),
              ),
              Expanded(child: Text("")),
            ],
          ),
        ),
      ),
    );
  }
}
-level_page.dart
import 'package:app3/data.dart';
import 'package:app3/main.dart';
import 'package:app3/start.dart';
import 'package:flutter/material.dart';



class level_page extends StatefulWidget {
  List l;
  level_page(this.l);

  @override
  State<level_page> createState() => _level_pageState();
}

class _level_pageState extends State<level_page> {
  int levelNo = 0;

  @override
  void initState() {
    // TODO: implement initState
    super.initState();
    share_pefer();
  }

  share_pefer() {
    levelNo = First.prefer!.getInt("levelNo") ?? 0;
    setState(() {});
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(

        child: Column(children: [
          Container(
            alignment: Alignment.center,
            child: Text("Select puzzle", style: TextStyle(fontSize: 35, color: Colors.blueAccent),),
          ),
          Expanded(
            child: GridView.builder(
              itemCount: data.ans.length,
              gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
                  crossAxisCount: 4, mainAxisSpacing: 10, crossAxisSpacing: 10),
              itemBuilder: (context, index) {
                return InkWell(
                  onTap: () {
                   if(levelNo>index){
                     Navigator.push(context, MaterialPageRoute(
                       builder: (context) {
                         return start(index);
                       },
                     ));
                   }
                  },
                  child: Container(
                    alignment: Alignment.center,
                    child: (index < levelNo) ? Text("${index + 1}", style:
                    TextStyle(fontSize: 40, fontFamily: "myfont"),) : null,
                    decoration: BoxDecoration(
                        image: (index < levelNo)
                            ? (widget.l[index] == "yes")
                            ? DecorationImage(image: AssetImage("myasset/first/tick.png")) : null
                            : DecorationImage(image: AssetImage("myasset/first/lock.png")),
                        borderRadius: BorderRadius.circular(10),border: Border.all(width: 3)),
                  ),
                );
              },
            ),
          ),
        ]),
      ),
    );
  }
}



-data.dart
class data
{
  static List  level=[
    "myasset/first/p1.png",
    "myasset/first/p2.png",
    "myasset/first/p3.png",
    "myasset/first/p4.png",
    "myasset/first/p5.png",
    "myasset/first/p6.png",
    "myasset/first/p7.png",
    "myasset/first/p8.png",
    "myasset/first/p9.png",
    "myasset/first/p10.png",
    "myasset/first/p11.png",
    "myasset/first/p12.png",
    "myasset/first/p13.png",
    "myasset/first/p14.png",
    "myasset/first/p15.png",
    "myasset/first/p16.png",
    "myasset/first/p17.png",
    "myasset/first/p18.png",
    "myasset/first/p19.png",
    "myasset/first/p20.png",

  ];
  static List ans=[
    "1","2","3","4","5","6","7","8","9","10"
    ,"11","12","13","14","15","16","17","18","19","20"
  ];
}
