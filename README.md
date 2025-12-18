# Implementation Steps of Dynamic Pipeline To fetch All files in Github and stored into Azure DataLake Gen2:

1-Web Activity for Metadata Retrieval
Begin by creating a Web Activity to retrieve metadata from GitHub containing the URLs of the source files.

2-Set Variable Activity
Add a Set Variable Activity to store the Web Activity response.
Assign the variable value using:
@activity('WebGithubMetadata').output.response

3-Validation Activity
Configure a Validation Activity to ensure that the required file (netflix_titles.csv) exists in the raw container.
The pipeline proceeds only if the validation condition is satisfied.

4-ForEach Activity for File Processing
Use a ForEach Activity to iterate over a parameterized array containing GitHub file metadata (such as file name and folder name).
Pass the array dynamically to the ForEach activity.

5-Copy Activity Inside ForEach
Within the ForEach loop:
Source: Configure the GitHub HTTP connection with a parameterized file name to dynamically fetch each file.
Sink: Configure Azure Data Lake Storage with two parameters—fileName and folderName—to dynamically store the files in the appropriate location.
Enable sequential execution if required.
Within the ForEach loop, use a Copy Activity to fetch and load each file individually into the Data Lake.


<img width="1907" height="815" alt="image" src="https://github.com/user-attachments/assets/bbdfcff9-783a-4d19-b297-9dd2650c277e" />


