# 피에조 스피커
피에조 효과(특정 물질에 전기적 신호 주면 수축 or 확장)를 이용해 판을 진동시켜 소리낸다

멜로디 출력하기
```java
/*
  Melody

 Plays a melody

 circuit:
 * 8-ohm speaker on digital pin 8

 created 21 Jan 2010
 modified 30 Aug 2011
 by Tom Igoe

This example code is in the public domain.
 //아래 사이트에서 음계코드 따오기
 http://arduino.cc/en/Tutorial/Tone

 */
 #include &quot;pitches.h&quot;

//노래의 음계순으로 배열에 담기
// notes in the melody:
int melody[] = {
  NOTE_C4, NOTE_G3,NOTE_G3, NOTE_A3, NOTE_G3,0, NOTE_B3, NOTE_C4};

//위의 각 음의 길이를 나타내는 배열
// note durations: 4 = quarter note, 8 = eighth note, etc.:
int noteDurations[] = {
  4, 8, 8, 4,4,4,4,4 };

void setup() {
  // iterate over the notes of the melody, 위의 배열을 순서대로 읽어라
  for (int thisNote = 0; thisNote &lt; 8; thisNote++) {

    // to calculate the note duration, take one second
    // divided by the note type.
    //e.g. quarter note = 1000 / 4, eighth note = 1000/8, etc.
    int noteDuration = 1000/noteDurations[thisNote];
    tone(8, melody[thisNote],noteDuration);
    // tone함수(핀번호,음주파수,음길이)= 음을 재생

    // to distinguish the notes, set a minimum time between them.
    // the note's duration + 30% seems to work well:
    int pauseBetweenNotes = noteDuration * 1.30;
    delay(pauseBetweenNotes);
    // stop the tone playing:
    noTone(8);  // 8번핀의 음을 멈춰라
  }
}

void loop() {
  // no need to repeat the melody.
}
```

피아노 건반
```java
#define NOTE_C4 262
#define NOTE_D4 294
#define NOTE_E4 330

int pins[] = {2,3,4};    //2,3,4번에 버튼 연결
int notes[] = {NOTE_E4, NOTE_D4, NOTE_C4};

void setup(){
  for (int i=0; i&lt;3; i++) {
    pinMode(pins[i],INPUT);
  }
}

void loop(){
  for (int i=0; i&lt;3; i++) {
    if (digitalRead(pins[i]) == HIGH) {
      tone(8, notes[i], 20);   //8번에 스피커 연결됨
    }
  }
}
```
