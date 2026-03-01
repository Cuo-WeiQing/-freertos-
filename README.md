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
    启动通讯-Si24R1模块自检-若正常-开启接收模式

    <img width="868" height="227" alt="image" src="https://github.com/user-attachments/assets/b34f0591-dbaf-4684-a04d-e497db10a6ff" />

    创建启动任务——启动任务负责创建所有任务
    vTaskStartScheduler();
    调用freertos任务调度器，开始调度任务，此时创建了一个任务，开始执行启动任务-创建所有任务
 1.电源任务：
    
 <img width="1112" height="753" alt="image" src="https://github.com/user-attachments/assets/2af717eb-c302-4d82-a875-e8bebe83efc5" />

    使用xTaskGetTickCount，计算精确延时，这里预留了一段代码，但并未使用

    if(ulTaskNotifyTake(pdTRUE, POWER_EXEC_CYCLE))
    程序阻塞，等待任务通知，等到了关机通知则关机，否则等待POWER_EXEC_CYCLE进入else分支
2.灯控任务：







