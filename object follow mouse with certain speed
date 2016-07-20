#include "Game.h"
#include <QGraphicsRectItem>
#include <QGraphicsScene>
#include <QMouseEvent>
#include <QTimer>
 
Game::Game(): QGraphicsView()
{
    // set size/disable scroll bars
    setFixedSize(800,600);
    setVerticalScrollBarPolicy(Qt::ScrollBarAlwaysOff);
    setHorizontalScrollBarPolicy(Qt::ScrollBarAlwaysOff);
 
    // create a scene
    QGraphicsScene* scene = new QGraphicsScene(this);
    scene->setSceneRect(0,0,800,600);
    setScene(scene);
 
    // create someItem_
    someItem_ = new QGraphicsRectItem();
    someItem_->setRect(0,0,50,50);
    scene->addItem(someItem_);
    QTimer* timer = new QTimer();
    QObject::connect(timer,SIGNAL(timeout()),this,SLOT(moveTowardsMouse()));
    timer->start(300);
 
    // allow this QWidget to recieve events when the mouse is moved
    setMouseTracking(true);
}
 
void Game::mouseMoveEvent(QMouseEvent *event)
{
    // update the mousePos_ attribute
    mousePos_ = event->pos();
 
}
 
void Game::moveTowardsMouse()
{
    // moves someItem_ 1 step closer to the mouse
 
    int STEP_SIZE = 50;
 
    // create a line from someItem_'s current pos to mousePos
    QLineF line(someItem_->pos(),mousePos_);
    line.setLength(STEP_SIZE);
 
    // move by the dx and dy of this line
    someItem_->moveBy(line.dx(),line.dy());
 
}
