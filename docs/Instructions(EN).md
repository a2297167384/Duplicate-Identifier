# Duplicate Data Identifier User Manual
v1.0 (August 2024)

## 1. Overview
### 1.1 Software Name
Duplicate Data Identifier

### 1.2 Software Introduction
Duplicate Data Identifier is a desktop application developed based on Python Pandas, used to identify and process duplicate data in Excel files. It allows users to process single files or batch files and outputs consolidated files containing duplicate and non-duplicate data.
This software is suitable for data cleaning and data management scenarios, especially when deduplication of large amounts of data is required.

### 1.3 Software Features
- Process duplicate data in a single Excel file
- Batch process duplicate data in multiple Excel files
- Automatically classify and output duplicate and non-duplicate data based on the unique identifier column name specified by the user
- Supports custom naming for processed results

## 2. Functional Description
### 2.1 Main Menu Interface
Function: Provides an entry point for users to choose between processing a single file or batch files.
- Process Single File: Enters the single file processing interface.
- Process Batch Files: Enters the batch file processing interface.

![png1](png1.png)

### 2.2 Single File Processing Module Interface Introduction
Function: After the user selects the primary file, supporting file, and configures relevant parameters, the program automatically identifies duplicate data in the primary file and generates processed results.
- **Back**: Returns to the main menu.
- **Select Primary File**: User selects the primary Excel file to be processed.
- **Select Supporting File**: User selects the supporting Excel file used for comparison.
- **Select Output Folder Path**: User selects the folder path for the output results.
- **Header Row Number**: User inputs the row number of the header row in the Excel file, default is 1.
- **Update Column Names**: Extracts all column names from the primary file for the user to select the unique identifier column.
- **Unique Identifier Column Name**: User selects a column as the unique identifier for identifying duplicate data.
- **Output Filename Prefix**: User sets a prefix for the generated result files; the program will generate files with "_repeat.xlsx" and "_non_repeat.xlsx" suffixes.
- **Run**: Executes the identification and classification of duplicate data, generating Excel files containing duplicate and non-duplicate data.

![png2](png2.png)

### 2.3 Batch File Processing Module Interface Introduction
Function: After the user selects multiple folders and configures relevant parameters, the program automatically batch identifies duplicate data in the files and generates processed results.
- **Back**: Returns to the main menu.
- **Select Primary Folder**: User selects the folder containing the primary Excel files.
- **Select Supporting Folder**: User selects the folder containing the supporting Excel files.
- **Select Output Folder Path**: User selects the folder path for the output results.
- **Select Sample File**: User selects a sample file to extract column names.
- **Header Row Number**: User inputs the row number of the header row, default is 1.
- **Update Column Names**: Extracts column names from the sample file for the user to select the unique identifier column.
- **Filename List**: User inputs the list of filenames to be processed, separated by commas.
- **Duplicate Filename Prefix/Suffix**: User sets the prefix and suffix for the resulting duplicate data files.
- **Non-duplicate Filename Prefix/Suffix**: User sets the prefix and suffix for the resulting non-duplicate data files.
- **Duplicate Data Summary Filename**: User sets the Excel filename for the summary of all duplicate data.
- **Non-duplicate Data Summary Filename**: User sets the Excel filename for the summary of all non-duplicate data.
- **Run**: Executes batch file duplicate data identification and classification, generating processed results for each file and summary files.

![png3](png3.png)

## 3. Operating Guide
### 3.1 Single File Processing Workflow
When processing a single file,
First, click the 'Select Primary File' button to choose the path of the Excel file to be processed.
When selecting the supporting file, click the 'Select Supporting File' button to choose the path of the supporting file used to help identify duplicate/non-duplicate content.
Click the 'Select Output Folder Path' button to choose the save location for the finally generated duplicate/non-duplicate files.

![png4](png4.png)

As shown in the Excel file below, since the header row containing information in this table is located at row 8, enter '8' in the 'Header Row Number' box and click 'Update Column Names'.

![png5](png5.png)

This operation will read the name of each column in the selected row (row 8 here) and display them in the 'Unique Identifier Column Name' dropdown list. The user needs to select the unique identifier column name option for filtering. In this case, 'Student Code' is selected as the unique identifier column name for filtering the two tables, meaning the software will filter out duplicate and non-duplicate students for the ACC202 course in 2022 and 2023 based on the Student Code in both files.

![png6](png6.png)

Next, enter your custom content in the 'Output Filename Prefix' box. As shown in the figure, if the prefix 'ACC202' is entered, the resulting filenames will be as shown.

![png7](png7.png)

Processing successful. The figure below shows the output filenames and table content.

![png8](png8.png)

Non-duplicate content Excel for a pair of files (ACC202):

![png9](png9.png)

Duplicate content Excel for a pair of files (ACC202):

![png10](png10.png)

### 3.2 Batch File Processing Workflow
When processing multiple files,
First, click the 'Select Primary Folder' button to choose the path of the folder containing Excel files to be processed.
When selecting the supporting files, click the 'Select Supporting Folder' button to choose the path of the folder containing supporting files used to help identify duplicate/non-duplicate content.
Click the 'Select Output Folder Path' button to choose the save location for the finally generated duplicate/non-duplicate files.
Then, click the 'Select Sample File' button to choose a sample file.

![png11](png11.png)

The sample file is as shown in the Excel file below. Since the header row containing information in this table is located at row 8, enter '8' in the 'Header Row Number' box and click 'Update Column Names'.

![png12](png12.png)

This operation will read the name of each column in the selected row (row 8 here) and display them in the 'Unique Identifier Column Name' dropdown list. The user needs to select the unique identifier column name option for filtering.
In this case, 'Student Code' is selected as the unique identifier column name for filtering. This means the software will filter out duplicate and non-duplicate students for the ACC202 and ACC206 courses in 2022 and 2023 based on the Student Code in the Excel files within the two folders.

![png13](png13.png)

After selecting the unique identifier column name, since this is batch processing (multiple file pairs), you need to enter the list of filenames in the box to the right of 'Filename List'. For example, in this process, you need to enter 'ACC202, ACC206'.
Finally, when processing batch files, the software also supports custom prefixes and suffixes for duplicate and non-duplicate filenames, and will automatically merge and generate summary files based on the individual duplicate/non-duplicate files. Similarly, the names of the summary files can also be customized.
As shown below:

![png14](png14.png)

Click Run, displays processing complete.

![png15](png15.png)

Processing successful. The figure below shows the output filenames and table content.
ACC202, ACC206 Duplicate Information Summary Table. Duplicate information from two different file pairs is merged into one table, and a 'file' column is added to the far right, showing the source filename of the information.
ACC202, ACC206 Non-duplicate Information Summary Table. Non-duplicate information from two different file pairs is merged into one table, and a 'file' column is added to the far right, showing the source filename of the information.
Non-duplicate content Excel for a pair of Excel files (ACC206):
At this point, the specific steps for processing single/batch files have been fully presented.

## 4. Error Handling
### 4.1 Input Validation
Before running the process, the system checks if all required fields have been filled. If any are missing, an error message will be displayed.

### 4.2 File and Path Selection
The system requires the user to select valid file paths and output folder paths. If an incorrect selection is made, the system will display an error message.

### 4.3 Data Processing Exceptions
During the processing, if any exceptions occur (e.g., file format issues, column name problems, etc.), the system will catch the error and display a message to guide the user in making corrections.

## 5. Data Structure and Storage
### 5.1 Data Structure
- **Primary and Supporting Files**: Contain paths to Excel files and columns from the data tables.
- **Processing Results**: Two output Excel files, containing duplicate data and non-duplicate data respectively.

### 5.2 Storage
The processed results will be saved in the specified output folder according to the filename prefix and suffix set by the user.