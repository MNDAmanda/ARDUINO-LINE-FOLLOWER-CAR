# cod-follower-line-car
// Motor A 
int ligaA = 9;
int gira1 = 8;
int gira2 = 7;
// Motor B
int ligaB = 3;
int gira3 = 5;
int gira4 = 4;
//Sensores
int ldre = A0;
int ldrd = A1;
int valorldre = 0;
int valorldrd = 0;
 
 
void setup() {
	pinMode(ligaA, OUTPUT);
	pinMode(ligaB, OUTPUT);
	pinMode(gira1, OUTPUT);
	pinMode(gira2, OUTPUT);
	pinMode(gira3, OUTPUT);
	pinMode(gira4, OUTPUT);
  	pinMode(ldre, INPUT);
  	pinMode(ldrd, INPUT);
	digitalWrite(gira1, LOW);
	digitalWrite(gira2, LOW);
	digitalWrite(gira3, LOW);
	digitalWrite(gira4, LOW);
  	Serial.begin(9600);
}
 
void loop() {
   valorldre = analogRead (ldre);
   Serial.print("Ldr Esquerda: ");
   Serial.println(valorldre);
   valorldrd = analogRead (ldrd);
   Serial.print("Ldr Direita: ");
   Serial.println(valorldrd);
  if((valorldre) < 500 && (valorldrd) < 500){ 
    pararTudo();
  }  
  else if ((valorldre) < 500 && (valorldrd) >= 500){ 
	paraRodaDireita();
  }
    else if ((valorldre) >= 500 && (valorldrd) < 500){ 
    	paraRodaEsquerda();
	}
      else { 
        moveParaFrente();
      }
}
 
 
void moveParaFrente(){
	analogWrite(ligaA, 255);
	analogWrite(ligaB, 255);
 
	digitalWrite(gira1, HIGH);
	digitalWrite(gira2, LOW);
	digitalWrite(gira3, HIGH);
	digitalWrite(gira4, LOW);
}
 
void paraRodaDireita(){
  	analogWrite(ligaA, 255);
	analogWrite(ligaB, 0);
	digitalWrite(gira1, HIGH);
	digitalWrite(gira2, LOW);
	digitalWrite(gira3, LOW);
	digitalWrite(gira4, LOW);
}
 
void paraRodaEsquerda(){ 
  	analogWrite(ligaA, 0);
	analogWrite(ligaB, 255);
	digitalWrite(gira1, LOW);
	digitalWrite(gira2, LOW);
	digitalWrite(gira3, HIGH);
	digitalWrite(gira4, LOW);
}
 
void pararTudo(){
    analogWrite(ligaA, 0);
	analogWrite(ligaB, 0);
	digitalWrite(gira1, LOW);
	digitalWrite(gira2, LOW);
	digitalWrite(gira3, LOW);
	digitalWrite(gira4, LOW);
}
