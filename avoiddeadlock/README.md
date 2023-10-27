We will start by defining a macro called max of the value 10. Then, we will define an
array stack of the size max. We will define two mutex objects with the names pop_mutex
and push_mutex.
To use the stack, the value of top will be initialized to -1. We will define two variables of
the type pthread_t, with the names tid1 and tid2, to store two thread identifiers.
We will invoke the pthread_create function to create the first thread and assign the
identifier returned by the function to the variable tid1. The thread will be created with the
default attributes, and the push function will be executed to create this thread.
We will invoke the pthread_create function a second time to create the second thread,
and we'll assign the identifier returned by the function to the variable tid2. The thread will
be created with the default attributes and the pop function will be executed to create this
thread. On the screen, we will display the message Both threads are created.
In the push function, the pthread_mutex_lock method is invoked, and the mutex
object push_mutex is passed to it to lock it. Now, if any other thread asks for
the pop_mutex object, it will need to wait until the object is unlocked. After a sleep of 2
seconds, the mutex object pop_mutex is locked by the first thread.
We will be prompted to enter the value to be pushed to the stack. The entered value will be
assigned to the variable n. The value of top will increment to 0. The value that we enter
will be pushed to the location stack[0]. Now, the pthread_mutex_unlock will be
invoked, and the mutex object pop_mutex will be passed to it to unlock it. Also, the mutex
object push_mutex will be unlocked. At the bottom of the push function, the message
Value is pushed to stack will be displayed.
In the pop function, it will try to lock the mutex object push_mutex, but because it is
already locked by the first thread, this thread will be asked to wait. After a sleep or delay of
5 seconds, it will also try to lock the pop_mutex object. The value in the stack, that is,
pointed at by the pointer top will be popped. Because the value of top is 0, the value at
stack[0] is picked up and assigned to the variable k. Thereafter, the value of top will
decrement by 1 to make it -1 again. The value, that is, popped from the stack will be
displayed on the screen. Then, the mutex object pop_mutex will be unlocked, followed by
the push_mutex object.
In the main function, the pthread_join method is invoked twice, and the tid1 and tid2
thread identifiers are passed to it. The pthread_join is invoked to make the two threads
and the main method wait until both of the threads have completed their tasks.
Here, we avoided a deadlock because the locking and unlocking of the mutex objects was
done in a sequence. In the push function, the first thread locked the push_mutex object and
tried to get a lock on the pop_mutex object. The pop_mutex was kept free because the
second thread in the pop function first tried to lock the push_mutex object, followed by the
pop_mutex object. Since the first thread had already locked the push_mutex object, the
second thread was asked to wait. Consequently, both of the mutex objects, push_mutex
and pop_mutex, were in an unlocked state, and the first thread was able to easily lock both
of the mutex objects and use the common resource. After finishing its task, the first thread
will unlock both of the mutex objects, enabling the second thread to lock both of the mutex
objects and access the common resource thread.
