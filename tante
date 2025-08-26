#include
#include
LiquidCrystal_I2C lcd(0x27, 16, 2);
const char* lyrics[] = {
"Sudah", "terbiasa", "terjadi", "tante",
"Teman", "datang", "ketika", "lagi",
"butuh", "saja", "Coba", "kalo",
"lagi", "susah", "Mereka", "semua",
"Menghilaaangg^_^"
};
const int delays[] = {
500, 500, 500, 1000,
500, 500, 500, 400,
500, 1000, 500, 500,
500, 1000, 500, 500,
6000
};
const int wordCount = sizeof(lyrics) / sizeof(lyrics[0]);
int typingDelay = 200;
const char* promoPairs[] = {
"", "Apakah", "spek standar",
"seperti ini", "yang para", "pemirsa inginkan?"
};
const int promoPairCount = sizeof(promoPairs) / sizeof(promoPairs[0]);
const int promoDisplayInterval = 2;
void setup() {
lcd.init();
lcd.backlight();
lcd.clear();
Serial.begin(9600);
}
void loop() {
for (int i = 0; i < wordCount; i++) {
int row = i % 2;
lcd.setCursor(0, row);
lcd.print(" ");
if (i == wordCount - 1) {
const char* word = lyrics[i];
int len = strlen(word);
int totalSteps = promoPairCount * promoDisplayInterval;
if (totalSteps < len) totalSteps = len;
for (int j = 0; j <= totalSteps; j++) {
lcd.setCursor(0, row);
lcd.print(" ");
lcd.setCursor(0, row);
for (int k = 0; k < j && k < len; k++) {
lcd.print(word[k]);
}
int promoIndex = j / promoDisplayInterval;
if (promoIndex < promoPairCount) {
lcd.setCursor(0, 1);
lcd.print(" ");
lcd.setCursor(0, 1);
lcd.print(promoPairs[promoIndex]);
}
delay(typingDelay);
}
delay(delays[i]);
} else {
const char* word = lyrics[i];
int startPos = (16 - strlen(word)) / 2;
if (startPos < 0) startPos = 0;
lcd.setCursor(startPos, row);
lcd.print(word);
delay(delays[i]);
}
if (row == 1 || i == wordCount - 1) {
delay(300);
lcd.clear();
}
}
while (true);
}
