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

<H4>Counting Semaphore</H4>
used for 
- Counting events
- Resource management

<H4>xSemaphoreCreateCounting()</H4>
SemaphoreHandle_t xSemaphoreCreateCounting( <br>
     UBaseType_t uxMaxCount, <br>
      UBaseType_t uxInitialCount); <br>
 <H4>Priority Inversion</H4>
 Higher priority task waiting for a lower priority task inherently assumes <br>
 the priority of the lower priority task.<br>
 <H4>Deadlock</H4>
 Deadlock occurs when two tasks cannot<br>
 proceed because they are both waiting for a resource<br>
 that is held by the other.<br>
 <H4>Priority Inheritance</H4>
 Temporarily raising the priority of the resource holder<br>
 to the priority of the highest priority task waiting for the resource. <br>
 
 <H3>Gatekeeper</H3>
 <H4> Using TICK_HOOK function </H4>
 we need to go to FreeRTOSConfig.h <br>
 and set #define configUSE_TICK_HOOK to 1 <br>
 
 - OS moves thread from Run State to Ready Stat
-  Preemption is needed to guarantee fairness
- Preemption needs a interrupts
 - Preemption helps meet deadlines

<H3>Interrupts on Arduino</H3>

void InterruptInit(void) 
{
  noInterrupts(); // disable global interrupt <br>
  TCCR1A =0; // <br>
  TCCR1B =0; // <br>
 timer1_counter = 34286; // <br>

 TCNT1  = timer1_counter; //preload the counter timer <br>
  TCCR1B |= (1 << CS12);  // <br>
 TIMSK1 |= (1 << TOIE1); // enable Timer overflower interupt
 interrupts(); //enable global interrupt
  
}

