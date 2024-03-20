# EEPROM_Comfort
Набор функций для удобного чтения и записи в ЭСППЗУ (EEPROM) для МК ESP8266 в среде Arduino, скорее всего будет работать и на других платформах.

Работает с целыми числами, числами с плавающей занятой и текстовыми строками (Float,Int,Float,String).

Для числовых значений можно задать минимальное и максимальное значение, если считанная информация не укладывается в лимиты - будет присвоено стандартное значение.
Для строки так же можно задать стандартное значение и ее максимальную длину. Все, что не укладывается в максимальную длину - не будет записано.

Функции записи проверяют правильность записанных данных их чтением и сравнением полученных значений. Если данные сходятся - возвращается 'true', если нет - 'false'.

Параметр StartCell - первая ячейка В ПЗУ для чтения/записи. Данные разных типов имеют разную длину:
float: 4 байта,

int: 2 байта,

long: 4 байта,

string: MaxLength + 1 байт.
Это необходимо учитывать при записи/чтении данных. Т.е. если необходимо записать переменную float, то следующую переменную можно записать только через 4 байта.

Функции
------------------

float EepromReadFloat (int StartCell, float MinValue, float MaxValue, float StandartValue)

int EepromReadInt (int StartCell, int MinValue, int MaxValue, int StandartValue)

long EepromReadLong (int StartCell, long MinValue, long MaxValue, long StandartValue)

String EepromReadString (int StartCell, String StandartValue, int MaxLength)

bool EepromSaveFloat (int StartCell, String SaveValue)

bool EepromSaveInt (int StartCell, String SaveValue)

bool EepromSaveLong (int StartCell, String SaveValue)

bool EepromSaveString (int StartCell, String SaveValue, int MaxLength)
