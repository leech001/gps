# STM32 HAL library for GPS module NEO-6M

## English note
A simple C library (STM32 HAL) for working with the GPS module NEO-6M
https://ru.aliexpress.com/wholesale?trafficChannel=main&d=y&CatId=0&SearchText=neo-6m&ltype=wholesale&SortType=total_tranpro_desc&groupsort=1&page=1

Configure STM32CubeMX by setting "General peripheral Initalizion as a pair of '.c / .h' file per peripheral" in the project settings.

Add NVIC global interrupt for UART

Copy the library header and source file to the appropriate project directories (Inc, Src).

Config you GPS module UART and if need DEBUG over USB on gps.h file
```
#define GPS_DEBUG	0
#define	GPS_USART	&huart2
```
In the head file of your project (main.c), include the header file
```
/ * USER CODE BEGIN Includes * /
#include "gps.h"
/ * USER CODE END Includes * /
```
add UART call back
```
/* USER CODE BEGIN 0 */
void HAL_UART_RxCpltCallback(UART_HandleTypeDef *huart)
{
	if(huart == &huart2) GPS_UART_CallBack();
}
/* USER CODE END 0 */
```
add in main function section for initial initialization of the GPS module NEO-6M
```
/* USER CODE BEGIN 2 */
  GPS_Init();
/* USER CODE END 2 */
```
On this project setup is ready.
After starting the program, information from the GPS module NEO-6M will be available through the GPS structure
```
GPS.dec_latitude
GPS.dec_longitude
...
```

## Russian note
Простая библиотека на С (STM32 HAL) для работы с GPS модулем module NEO-6M
https://ru.aliexpress.com/wholesale?trafficChannel=main&d=y&CatId=0&SearchText=neo-6m&ltype=wholesale&SortType=total_tranpro_desc&groupsort=1&page=1

Сконфигурируйте STM32CubeMX установив "General peripheral Initalizion as a pair of '.c/.h' file per peripheral" в настройках проекта.

Незабудьте включить глобальные прерывания для вашего UART.

Скопируйте заголовочный и исходный файл библиотеки в соотвесвтующие директории проекта (Inc, Src).

Сконфигурируйте UART порт куда подключен ваш модуль и вуключите если необходимо отладку через USB в gps.h file
```
#define GPS_DEBUG	0
#define	GPS_USART	&huart2
```
В головном файл вашего проекта (main.c) подключите заголовочный файл
```
/ * USER CODE BEGIN Includes * /
#include "gps.h"
/ * USER CODE END Includes * /
```
добавьте функцию вызова по прерыванию UART
```
/* USER CODE BEGIN 0 */
void HAL_UART_RxCpltCallback(UART_HandleTypeDef *huart)
{
	if(huart == &huart2) GPS_UART_CallBack();
}
/* USER CODE END 0 */
```
добавьте в секцию функции main(void) код инициализации модуля
```
/* USER CODE BEGIN 2 */
  GPS_Init();
/* USER CODE END 2 */
```
На этом настройка проекта готова. После запуска программы информация от вашего GPS модуля будет доступна через структуру GPS
```
GPS.dec_latitude
GPS.dec_longitude
...
```