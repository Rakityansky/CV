**Problem Title: Process Hierarchy Creation with fork()**

**Objective:**  
Demonstrate understanding of process creation, hierarchy management, and proper synchronization using `fork()` and `wait()` system calls in C.

---

**Problem Statement:**  
Write a C program that creates a process hierarchy as follows:  
1. The parent process creates **two child processes** (Child1 and Child2).  
2. **Each child process** then creates **one grandchild process** (Grandchild1 and Grandchild2).  
3. The parent must wait for **both child processes** to terminate.  
4. Each child process must wait for **its respective grandchild** to terminate.  

Each process must print the following information in the specified format:  
- **Parent Process**: `"Parent Process: PID = <pid>, Parent PID = <ppid>"`  
- **Child Process**: `"Child Process: PID = <pid>, Parent PID = <ppid>"`  
- **Grandchild Process**: `"Grandchild Process: PID = <pid>, Parent PID = <ppid>"`  

**Requirements:**  
1. Use `fork()` to create the processes.  
2. Use `wait()` (or `waitpid()`) to ensure processes terminate in the correct order.  
3. Handle errors for **all** `fork()` calls. If a `fork()` fails:  
   - Print `"Error: fork() failed."`  
   - Exit with status code `1`.  

---

**Example Output:**  
The output will vary due to dynamic PIDs, but the hierarchy should be clear. Example:  
```
Parent Process: PID = 5000, Parent PID = 3000  
Child Process: PID = 5001, Parent PID = 5000  
Child Process: PID = 5002, Parent PID = 5000  
Grandchild Process: PID = 5003, Parent PID = 5001  
Grandchild Process: PID = 5004, Parent PID = 5002  
```  
*Note:* The order of lines might differ slightly due to process scheduling, but grandchildren should always appear after their respective parents.

---

**Hints:**  
1. Use `getpid()` and `getppid()` to retrieve process IDs.  
2. The parent must call `fork()` twice (once for each child).  
3. Each child process should call `fork()` once to create its grandchild.  
4. Use `wait()` in the parent to wait for its children, and in the children to wait for their grandchildren.  

---

**Submission Instructions:**  
Submit your C code with comments explaining key steps. Ensure your program compiles and runs on a UNIX system (test with `gcc`).  

---

**Learning Outcomes:**  
- Mastery of multi-level process creation with `fork()`.  
- Understanding hierarchical process synchronization using `wait()`.  
- Proper error handling for system calls.  
- Insight into UNIX process relationships and IDs.  

**Difficulty:** Medium  
**Time Estimate:** 45–60 minutes