# FreeRTOS

QueueHandle_t xQueueCreate (UBaseType_t uxQueueLength, UBaseType_t uxItemSize);

Three API

xQueueSend(), sQueueSendToFront(), xQueueSendToBack()

BaseType_t xQueueSend (QueueHandle_t xQueue, const *_pvItemToQueue, TickType_t xTickToWait);


<H3> Queue Set</H3>
xQueueAddToSet() <br>
Base_Type xQueueAddToSet( QueueSetMemberHandle_t xQueueOrSemaphore, QueueSetHandle_t xQueueSet) <br>

QueueSetMemberHandle_t xQueueSelectFromSet (QueueSetHandle_t xQueueSet, const TickType_t xTicksToWait); <br>


