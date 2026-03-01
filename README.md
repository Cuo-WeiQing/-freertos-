# -freertos-
尚硅谷freertos无人机解析

所有代码来自尚硅谷，作者看过全套视频教程，秉持学习和记录的想法对无人机项目freertos部分进行解析，若有侵权，联系删除

FLY-HAL部分
<img width="713" height="176" alt="image" src="https://github.com/user-attachments/assets/6ea7ab87-f457-455f-a98d-03f92878e0c3" />
代码将freertos调度器函数封装

    debug_start(); 
    经过嵌套和重定义，初始化了串口重定义
    
    debug_printfln("尚硅谷无人机项目--飞控");
    将printf函数重定义为debug_printfln

    App_Flight_Start();
    初始化电机、MPU6050、激光测距

    App_Communication_Start();



