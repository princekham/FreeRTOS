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
