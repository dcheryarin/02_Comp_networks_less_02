# Урок 2. Физический и канальный уровень. Технология Ethernet. Часть 2
Работа в CPT. Скачать приложенный файл.

## 1. Исправить проблемы с линками на всех хостах.

ВЫПОЛНЕНИЕ:

Результирующая схема сохранена и выложена в файле HW_lesson2.pkt.

* Восстановление линка (Switch1 10.0.1.101) - (PC-PT 10.0.1.2)
   - на (Switch1 10.0.1.101) включен порт интерфейса FastEthernet0/1 (изменена настройка port status на on)
   ![](/1_1.PNG)
   - проверка
   ![](/1_3.PNG)
* Восстановление линка (Switch2 10.0.1.102) - (PC-PT 10.0.1.4)
   - на (Switch2 10.0.1.102) изменена настройка на duplex auto интерфейса FastEthernet0/1;
    ![](/1_2.PNG)
    ![](/1_4.PNG)
    - проверка
    ![](/1_5.PNG)

## 2. Настроить сетевые интерфейсы на всех хостах и менеджмент на свитчах, используя только консольный кабель.

ВЫПОЛНЕНИЕ:

Результирующая схема сохранена и выложена в файле HW_lesson2.pkt.

* Выполнена настройка хостов;

   - Настройка (Switch0 10.0.1.100) был настроен.
   ```
      switch0>ping 10.0.1.1

      Type escape sequence to abort.
      Sending 5, 100-byte ICMP Echos to 10.0.1.1, timeout is 2 seconds:
      !!!!!
      Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/0 ms
   ```
   - Настройка (Switch1 10.0.1.101)

   ```
      Switch(config-if)#exit
      Switch(config)#int vlan1
      Switch(config-if)#ip address 10.0.1.101 255.255.255.0
      Switch(config-if)#no shutdown
      Switch(config-if)#do write
      vSwitch(config-if)#do ping 10.0.1.1

      Type escape sequence to abort.
      Sending 5, 100-byte ICMP Echos to 10.0.1.1, timeout is 2 seconds:
      !!!!!
      Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/0 ms
   ```
   Консоль коммутатора находилась в привелегированном режиме + был осуществлен переход в режим конфигурирования интерфейса FastEthernet0/1. После исправлений - сохранил конфигурацию.
   ![](/2_1.PNG)

    - Настройка (Switch2 10.0.1.102)
   ```
      Switch#en
      Switch#conf t
      Switch(config)#int vlan1
      Switch(config-if)#ip address 10.0.1.102 255.255.255.0
      Switch(config-if)#no shutdown
      Switch(config-if)#do write
      Switch(config-if)#do ping 10.0.1.1

      Type escape sequence to abort.
      Sending 5, 100-byte ICMP Echos to 10.0.1.1, timeout is 2 seconds:
      !!!!!
      Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms
   ```
   После исправлений - сохранил конфигурацию.
   ![](/2_2.PNG)

    - Настройка(Switch3 10.0.1.103)
   ```
      Switch#en
      Switch#conf t
      Switch(config)#int vlan1
      Switch(config-if)#ip address 10.0.1.103 255.255.255.0
      Switch(config-if)#no shutdown

      Switch(config-if)#
      Switch(config-if)#do write
      Switch(config-if)#do ping 10.0.1.1

      Type escape sequence to abort.
      Sending 5, 100-byte ICMP Echos to 10.0.1.1, timeout is 2 seconds:
      !!!!!
      Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/1 ms
   ```
   После исправлений - сохранил конфигурацию.
   ![](/2_3.PNG)

   Проверка:
   ![](/3_1.PNG)
   ![](/3_2.PNG)
   ![](/3_3.PNG)


## 3. Обвести синим цветом все широковещательные домены, а красным все домены коллизий. (см. картинку в методичке)

Результирующая схема - 4_domens.png
![](/4_domens.png)
