# Deadlocking

We will first define a macro called **max** of the value **10**, along with an array stack of the size **max**. Then, we will define two mutex objects with the names **pop_mutex** and **push_mutex**. To use the **stack**, we will initialize the value of **top** to **-1**. We will also define two variables of the type **pthread_t**, with the names **tid1** and **tid2**, to store two thread identifiers.

We will invoke the **pthread_create** function to create the first thread, and we will assign the identifier returned by the function to the variable **tid1**. The thread will be created with the default attributes, and we will execute the push function to create this thread.

We will invoke the **pthread_create** function again to create the second thread, and we will assign the identifier returned by the function to the variable **tid2**. This thread is also created with the default attributes, and we will execute the **pop** function to create this thread. On the screen, we will display the message **Both threads are created**.

In the **push** function, we will invoke the **pthread_mutex_lock** method and pass the **mutex** object **push_mutex** to it to lock it. Now, if any other thread asks for the **push_mutex** object, it will need to wait until the object is unlocked.

Then, the **mutex** object **pop_mutex** will be locked by the first thread. We will be asked to enter the value to be pushed to the stack. The entered value will be assigned to the variable **n**. The value of **top** will be incremented to **0**. The value that we enter will be pushed to the location **stack[0]**.

Next, we will invoke the **pthread_mutex_unlock** and pass the **mutex** object **pop_mutex** to it to unlock it. Also, the mutex object **push_mutex** will be unlocked. At the bottom of the **push** function, we will display the message **Value is pushed to stack**.
