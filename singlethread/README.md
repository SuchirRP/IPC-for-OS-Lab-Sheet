We will define a variable called tid of the type pthread_t to store the thread identifier. A
thread identifier is a unique integer, that is, assigned to a thread in the system. Before
creating a thread, the message In main function is displayed on the screen. We will
create a thread and pass the identifier tid to the pthread_create function. The thread is
created with the default attributes, and the runThread function is set to execute to create
the thread.
In the runThread function, we will display the text message Running Thread to indicate
that the thread was created and is running. We will invoke a for loop to display the
sequence of numbers from 1 to 5 through the running thread. By invoking the
pthread_join method, we will make the main method wait until the thread completes its
task. It is essential to invoke the pthread_join here; otherwise, the main method will exit
without waiting for the completion of the thread.
