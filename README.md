# GstreamerVideo
Модуль работы с видеопотоком(прием) с использованием rtcp протокола и gstreamer'a 
## Import
Чтобы импортировать данный модуль необходимо в файле программы ввести
```
import RTCVideo
```
## Связь
Т.к. видео передается через rtpcp, необходимо указать ip(передающего устройства) и порты для связи
```
IP = '127.0.0.1'
RTP_RECV_PORT0 = 5000
RTCP_RECV_PORT0 = 5001
RTCP_SEND_PORT0 = 5005
```
## Video 
Класс предоставляющий методы для работы с видеопотоком. В качастве параметров передаются ip и порты
```
video = RTCvideo.Video(IP, RTP_RECV_PORT0, RTCP_RECV_PORT0, RTCP_SEND_PORT0)
```
**P.S.** Кроме этих 4х параметров можно передать 5й - **overlay**. Этот параметр представляет собой ф-ию,             
которая позволяет рисовать поверх экрана при помощи OpenGL(пример в самом модуле, т.к. там есть ф-ия по умолчанию)                 
**P.P.S** Контекст OpenGL должен быть инициализирован внутри ф-ии                         
## Методы
### StandartOverlay
Чтобы нарисовать текстуру поверх экрана необходимо вызвать метод         
```
video.drawOverlay("ring.png", x = 0, y = 0, scaleX = 0.3, scaleY = 0.2, fullScreen = True)
```
Первый параметр - путь до изображения, которое нужно наложить                                                          
x и y - координаты изображения на экране                                                               
scaleX и scaleY  - масштабирующие параментры, на которые умножаются координаты(соответственно уменьшается изображение)                      
fullScreen - в положении True растягивает изображение на весь экран, игнорируя предыдущие 4 параметра.                          
### video pipeline
Запуск видео
```
video.start()
```
Пауза
```
video.paused()
```
Остановка метода с освобождением контекста
```
video.stop()
```
Пример работы с видео в файле testVideo.py                                      