LCD-Code
========

//This code scrolls a line of text up to 32 characters in length

#include <LiquidCrystal.h>


const int numRows = 2;
const int numCols = 16;
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);

void setup()
{
  lcd.begin(numCols,numRows);
  
}

void loop()
{
 marquee("This took in more than 3 hours to do");
 delay(1000);
 lcd.clear();
}
void marquee( char *text)
{
  int length = strlen(text);
  if(length<numCols)
  lcd.print(text);
  else
  {
    int pos;
    for(pos = 0; pos< numCols; pos++)
    lcd.print(text[pos]);
    delay(1000);
    while(pos<length)
    {lcd.scrollDisplayLeft();
    lcd.print(text[pos]);
    pos = pos +1;
    delay(300);
    }}}
