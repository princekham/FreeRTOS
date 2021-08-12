# FreeRTOS

QueueHandle_t xQueueCreate (UBaseType_t uxQueueLength, UBaseType_t uxItemSize);

Three API

xQueueSend(), sQueueSendToFront(), xQueueSendToBack()

BaseType_t xQueueSend (QueueHandle_t xQueue, const *_pvItemToQueue, TickType_t xTickToWait);


<H3> Queue Set</H3>
xQueueAddToSet() <br>
Base_Type xQueueAddToSet( QueueSetMemberHandle_t xQueueOrSemaphore, QueueSetHandle_t xQueueSet) <br>

QueueSetMemberHandle_t xQueueSelectFromSet (QueueSetHandle_t xQueueSet, const TickType_t xTicksToWait); <br>

<H3>Software Timer</H3>
void ATimerCallback (TimerHandle_t xTimer);
<H4>Type of Software Timer</H4>
One-Shot - manual retart<br> 
Auto-reload - auto restart<br>

<H4>Timer Management Functions</H4>
xTimerCreate
TimerHandle_t xTimerCreate(
                          const char *const pcTimerName, <br>
                          TickType_t uTimerPeriodInTicks, <br>
                          UBaseType_t uxAutoReload, <br>
                          void *pvTimerID, <br>
                          TimerCallbackFunction_t pxCallbackFunction <br>
                          ); <br>
                          
<H4>xTimerStart()</H4>
BaseType_t xTimerStart (TimerHandle_t xTimer,<br>
TickType_tx TicksToWait);

<H4>The Timer ID </H4>
void vTimerSetTimerID (const TimerHandle_t xTimer,<br>
void *pvNewID); <br>
void *pvTimerGetTimerID (TimerHandle_t xTimer);
<H4>Changing the time period</H4>
BaseType_t xTimerChangePeriod( <br>
TimerHandle_t xTimer,<br>
TickType_t xNewTimerPeriodInTicks,<br>
TickType_t xTicksToWait <br>
);

<H3>Semaphore</H3>
<H4>xSemaphoreCreateBinary()</H4>
SemaphoreHandle_t xSemaphoreCreateBinary( void); // to create binary semaphore <br>
<H4>xSemaphoreTake()</H4>
BaseType_t xSemaphoreTake ( <br>
    SemaphoreHandle_t xSemaphore, <br>
    TickType_t xTicksToWait); // သူ မရမချင်းစောင့်တဲ့ အချိန်လို့ နားလည်တယ်။<br>
<H4>xSemaphoreGive</H4>
BaseType_t xSemaphoreGive(SemaphoreHandle_t xSemaphore);
<H4> xSemaphoreGiveFromISR() </Hr>
BaseType_t xSemaphoreGiveFromISR( SemaphoreHandle_t xSemaphore, <br>
        BaseType_t *pxHigherPriorityTaskWoken);

