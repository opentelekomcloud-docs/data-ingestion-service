:original_name: dis_01_0052.html

.. _dis_01_0052:

Event Notification Overview
===========================

Overview
--------

DIS uses Simple Message Notification (SMN) to send notifications of DIS events. In a subscription, you need to specify one or more event filtering conditions. When an event that matches all filtering conditions occurs, DIS sends a notification based on the subscription. The filter conditions include the **Event Type** (for example, **Management**, **Monitoring**, or **Security**), **Event Level** (for example, **Normal** or **Warning**), and **Event Source** (for example, **Stream**, **Dump task**, or **User**).

Supported Event Types and Events
--------------------------------

Events are records of changes in the tenant's stream status. It can be triggered by a user operation (for example, an audit event), or may be caused by a stream status change (for example, a dump task is abnormal or a dump task is recovered). The following tables list the events and event types supported by DIS:

-  The following table lists the events whose **Event Source** is **Stream**.

   .. table:: **Table 1** Events whose **Event Source** is **Stream**

      ============ =========== ==================================
      Event Source Event Level Event
      ============ =========== ==================================
      Stream       Warning     Traffic limited
      Stream       Warning     Automatic stream scaling succeeded
      Stream       Warning     Automatic stream scaling failed
      Stream       Warning     Stream traffic abnormal
      Stream       Warning     Stream traffic restored
      ============ =========== ==================================

-  The following table lists the events whose **Event Source** is **Event**.

   .. table:: **Table 2** Events whose **Event Source** is **User**

      ============ =========== ==================
      Event Source Event Level Event
      ============ =========== ==================
      User         Warning     Quota insufficient
      ============ =========== ==================

-  The following table lists the events whose **Event Source** is **Dump task**.

   .. table:: **Table 3** Events whose **Event Source** is **Dump task**

      ============ =========== ==================
      Event Source Event Level Event
      ============ =========== ==================
      Dump task    Normal      Dump task restored
      Dump task    Warning     Dump task abnormal
      ============ =========== ==================
