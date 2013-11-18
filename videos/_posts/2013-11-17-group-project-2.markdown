---
layout: post
title: "Video: Lecture about group project 2"
---

# Video: Lecture about group project 2

<div style="text-align: center">
<iframe src="http://player.vimeo.com/video/79564060?title=0&amp;byline=0&amp;portrait=0&amp;color=ffffff" width="800" height="600" frameborder="0" webkitAllowFullScreen mozallowfullscreen allowFullScreen></iframe>
</div>

## Code

### main file

{% highlight java %}
char c1;
int x1, y1;
int rate;
int score;
boolean lost;
boolean disappearing;
float theta;
int alpha;
ScoreList scoreList;

void setup()
{
  size(800, 600);
  restartGame();
  scoreList = new ScoreList();
}

void draw()
{
  background(255);

  if (y1 > height)
  {
    lost = true;
  }

  if (lost)
  {
    textSize(50);
    fill(255, 0, 0);
    text("You lost.", 300, 300);
    scoreList.displayScores();
    noLoop();
  }
  else
  {
    textSize(40);
    if (disappearing)
    {
      fill(0, 0, 0, alpha);
      pushMatrix();
      translate(x1, y1);
      rotate(theta);
      text(c1, 0, 0);
      popMatrix();
      alpha -= 3;
      theta += 0.1;
      if (alpha < 0)
      {
        disappearing = false;
        c1 = char(int(random(65, 91)));
        x1 = int(random(20, width-20));
        y1 = int(random(20, 100));
      }
    }
    else
    {
      fill(0);
      text(c1, x1, y1);

      y1 += rate;
    }
  }

  textSize(20);
  fill(0, 0, 255);
  text("Score: " + score, 50, 50);
}

void restartGame()
{
  c1 = char(int(random(65, 91)));
  x1 = int(random(20, width-20));
  y1 = 20;
  lost = false;
  disappearing = false;
  rate = 1;
  score = 0;
  theta = 0;
  alpha = 255;
  loop();
}

void keyPressed()
{
  if (lost) {
    if (key == 'r') {
      restartGame();
    }
  }
  else if (key <= 'z' && key >= 'a') {
    if (key == (c1 + 32))
    {
      disappearing = true;
      alpha = 255;
      theta = 0;
      score++;

      if (score % 5 == 0 && score > 0) {
        rate += 2;
      }
    }
    else
    {
      lost = true;
      // record score...
      scoreList.saveScore(score);
    }
  }
}
{% endhighlight %}

### ScoreList class

{% highlight java %}
class ScoreList
{
  int[] scores;
  
  ScoreList()
  {
    scores = new int[0];
  }
  
  void saveScore(int score)
  {
    // put score in array
    scores = expand(scores, scores.length + 1);
    scores[scores.length-1] = score;
  }
  
  void displayScores()
  {
    textSize(32);
    fill(0, 0, 255);
    for(int i = 0; i < scores.length; i++)
    {
      text(scores[i], 100, 100 + i*50);
    }
  }
}
{% endhighlight %}


