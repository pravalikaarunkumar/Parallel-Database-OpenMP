# Parallel Database Architecture
This project demonstrates the use of **OpenMP** for achieving both **data parallelism** and **task parallelism** in a database-like operation involving employee records and their performance metrics. The solution leverages multi-threading to efficiently process large datasets by taking advantage of modern multi-core processor architectures.

## Key Concepts:

### Data Parallelism
Data parallelism is achieved in the `processEmployeesAndMetricsByDepartment` function, where tasks involving querying and processing employees based on their department are divided among multiple threads. 
- The `#pragma omp section` directive is used to parallelize the query of employee data, enabling each thread to operate on a different portion of the dataset.
- This approach allows multiple employees to be processed concurrently, resulting in faster query and processing times, particularly when dealing with large datasets.

### Task Parallelism / Query Parallelism
In addition to data parallelism, task parallelism is also applied within the `processEmployeesAndMetricsByDepartment` function, where different sections of the code are executed in parallel:
- Two sections are defined using the `#pragma omp parallel sections` directive.
    - The first section queries employees based on their department and populates the `departmentData` vector.
    - The second section processes the queried data, printing the details of each employee along with their performance metrics.

### Architecture Parallelism
OpenMP facilitates architecture parallelism by distributing the workload across multiple cores of the processor.
- The `#pragma omp parallel sections` directive divides the execution into multiple threads that run concurrently on different processor cores.
- Each thread operates on a separate section of the code, maximizing the utilization of multi-core architectures.

## Code Overview:

### Structures
- **Employee**: Holds the employee's data, including details such as name, ID, and department.
- **PerformanceMetrics**: Stores the performance metrics of an employee, like productivity score or performance rating.

### Functions
- **generateEmployeesWithPerformance(numEmployees)**:
    - Generates a dataset of employees and their corresponding performance metrics.
    - The dataset size is defined by the input `numEmployees`.

- **processEmployeesAndMetricsByDepartment(department)**:
    - Queries and processes employees belonging to a specified department.
    - Data parallelism is implemented in the employee querying step, and task parallelism is achieved by splitting the querying and processing tasks into different sections.
    - The results are printed, showing employee details and performance metrics.

### Main Function
- In the `main()` function:
    - A dataset of employees is generated using the `generateEmployeesWithPerformance()` function.
    - The `processEmployeesAndMetricsByDepartment()` function is then used to query and process employee data based on a department.

## Performance Metrics:
To analyze the performance of the code, you can measure execution times for different dataset sizes (number of employees) and varying numbers of threads (processing elements). Key metrics include:
- **Speedup**: The ratio of the time taken to execute the serial version of the code to the time taken to execute the parallel version with multiple threads.
- **Parallel Efficiency**: A measure of how effectively the parallelization process utilizes the available processing elements.

### Performance Evaluation
To evaluate performance:
1. Vary the number of employees (`numEmployees`) to test the scalability of the solution.
2. Adjust the number of processing elements (threads) by setting environment variables like `OMP_NUM_THREADS`.
3. Measure the execution time for different configurations and calculate the following:
4. To write the formulas for **Speedup** and **Parallel Efficiency** in a plain-text format for the README file, you can present them like this:
- **Speedup**:  
   Speedup is the ratio of the time taken by the serial execution to the time taken by the parallel execution. It is calculated as:

   ```
   Speedup = T_serial / T_parallel
   ```

   Where:
   - `T_serial`: Time taken by the serial execution.
   - `T_parallel`: Time taken by the parallel execution with multiple threads.

- **Parallel Efficiency**:  
   Parallel efficiency measures how well the processing power of multiple elements (threads) is utilized. It is calculated as:

   ```
   Efficiency = Speedup / Number of Processing Elements
   ```

   Where:
   - `Number of Processing Elements`: The number of threads used for parallel execution.

---

### Graphs
- **Graph 1**: Plot speedup with respect to the number of processing elements for different problem sizes (N).
- **Graph 2**: Plot speedup with respect to N (number of employees) for different numbers of processing elements.

## Conclusion
This project demonstrates the use of OpenMP to efficiently perform parallel data processing on employee records using data, task, and architecture parallelism. The use of multi-threading significantly improves the performance of database-like operations, especially for large datasets.

## Contributors:  
[Pravalika Arunkumar](https://github.com/pravalikaarunkumar)  
[Shruthi Mohan](https://github.com/shruthimohan03)
