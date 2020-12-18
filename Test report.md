Краткое описание
================================
Установить и проверить работу программы IntelliJ IDEA с разными тестовыми данными 

Дата начала: 17.12.2020  
Дата окончания: 17.12.2020  
На тестирование затрачено: 2 часа

#### В результате тестирования выявлены следующие дефекты:

•	Карты Diners Club - Carte Blanche,  Diners Club - International, American Express (AMEX) невалидны   
•	Программа не считает валидными номера банковских карт свыше 16 знаков

Описание процесса тестирования:
=====================================
#### В процессе тестирования использовались следующие артефакты:

•	Программа IntelliJ IDEA   
•	Код написанный предыдущим программистом  
•	В строку < String number = "номер карты" > подставлять тестовые номера карт, фиксируя результат проверки 
``` java
public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```
#### В качестве тестовых данных использовались номера карт c сервиса [www.freeformatter.com](https://www.freeformatter.com/credit-card-number-generator-validator.html)

![SKRINSOT-17-12-2020-110142.jpg](https://ia.wampi.ru/2020/12/18/SKRINSOT-17-12-2020-110142.jpg)

### Ожидаемый результат тестирования:  
Result is OK

### Фактический результат тестирования:  
![SKRINSOT-18-12-2020-105001.jpg](https://ia.wampi.ru/2020/12/18/SKRINSOT-18-12-2020-105001.jpg)

### Тестирование производилось в следующем окружении:  
•	Windows 7 Professional, x64  
•	версия Java 11.0.9.1  
•	браузер Google Chrome версия 87.0.4280.88 (Официальная сборка), (64 бит)  

