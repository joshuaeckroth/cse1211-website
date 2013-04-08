---
layout: post
title: "Lecture: Pong"
---

# Lecture: Pong

## Main file
{% highlight java %}
Game game;

void setup()
{
  size(800, 600, P3D);
  game = new Game();
}

void draw()
{
  background(255);
  game.update();
  game.display();
}

void keyPressed()
{
  game.handleKeyPress(key, keyCode);
}
{% endhighlight %}

## Ball class

{% highlight java %}
class Ball
{
  float x;
  float y;
  float sourceX;
  float sourceY;
  float distance;
  float angle;
  float speed;

  Ball()
  {
    sourceX = width/2;
    sourceY = height/2;
    speed = 3;
    angle = -PI/8;
    distance = 0;
  }

  void update()
  {
    distance += speed;

    pushMatrix();
    translate(sourceX, sourceY);
    rotate(angle);
    translate(distance, 0);
    x = modelX(0, 0, 0);
    y = modelY(0, 0, 0);
    popMatrix();
  }

  void bounceVertical()
  {
    sourceX = x;
    sourceY = y;
    angle = -angle;
    distance = 0;
  }
  
  void bounceHorizontal()
  {
    sourceX = x;
    sourceY = y;
    angle = -angle;
    speed = -speed;
    distance = 0;
  }

  void display()
  {
    pushMatrix();
    translate(x, y);
    fill(0, 0, 255);
    noStroke();
    ellipse(0, 0, 25, 25);
    popMatrix();
  }
}
{% endhighlight %}

## Player class

{% highlight java %}
class Player
{
  float y;
  float x;
  
  Player()
  {
    y = height/2.0;
    x = 50;
  }
  
  void handleKeyPress(int key, int keyCode)
  {
    if(key == CODED && keyCode == UP)
    {
      y -= 5;
    }
    else if(key == CODED && keyCode == DOWN)
    {
      y += 5;
    }
  }
  
  void display()
  {
    pushMatrix();
    translate(x, y);
    fill(0);
    noStroke();
    rect(0, 0, 20, 80);
    popMatrix();
  }
}
{% endhighlight %}

## ComputerPlayer class

{% highlight java %}
class ComputerPlayer
{
  float y;
  float x;
  Ball ball;
  
  ComputerPlayer(Ball ball_)
  {
    ball = ball_;
    y = height/2;
    x = 700;
  }
  
  void think()
  {
    if(ball.y > (y+2))
    {
      y += 2;
    }
    else if(ball.y < (y-2))
    {
      y -= 2;
    }
  }
  
  void display()
  {
    pushMatrix();
    translate(x, y);
    fill(0);
    noStroke();
    rect(0, 0, 20, 80);
    popMatrix();
  }
}
{% endhighlight %}

## Game class

{% highlight java %}
class Game
{
  Player player;
  Ball ball;
  ComputerPlayer computerPlayer;

  Game()
  {
    player = new Player();
    ball = new Ball();
    computerPlayer = new ComputerPlayer(ball);
  }

  void update()
  {
    ball.update();

    if (ball.y < 12.5 || ball.y > (height-12.5))
    {
      ball.bounceVertical();
    }
    if (abs(ball.x - computerPlayer.x) < 12.5 && ball.y > (computerPlayer.y-40) && ball.y < (computerPlayer.y + 40))
    {
      ball.bounceHorizontal();
    }
    if (abs(ball.x - (player.x+10)) < 12.5 && ball.y > (player.y-40) && ball.y < (player.y + 40))
    {
      ball.bounceHorizontal();
    }


    computerPlayer.think();
  }

  void display()
  {
    player.display();
    ball.display();
    computerPlayer.display();
  }

  void handleKeyPress(int key, int keyCode)
  {
    player.handleKeyPress(key, keyCode);
  }
}
{% endhighlight %}

