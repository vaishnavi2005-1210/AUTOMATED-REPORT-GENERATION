# AUTOMATED-REPORT-GENERATION
#COMPANY:CODETECH IT SOLUTIONS

#NAME:BEHARA VAISHNAVI PATNAIK

#INTERN ID:CT04DF34

#DOMAIN:PYTHON PROGRAMMING

#DURATION:4 WEEKS

#MENTOR:NEEELA SANTOSH

Problem statement:DEVELOP A SCRIPT THAT READS DATA FROM
A FILE, ANALYZES IT, AND GENERATES A
FORMATTED PDF REPORT USING LIBRARIES
LIKE FPDF OR REPORTLAB.

📌Objective:This project demonstrates how to automate the process of reading student data from a CSV file, performing basic data analysis, and generating a visually appealing PDF report using Python libraries. 
The report includes summary statistics, class-wise averages, and visual charts like bar graphs and pie charts to help easily understand student performance metrics.

📌Tools and Libraries Used:

Python 3.x: Programming language.

pandas: For CSV reading and data analysis.

matplotlib: For creating charts and graphs.

fpdf2: To create and format the PDF report.

Optional: PyCharm IDE for development.

📌Step-by-Step Code Explanation:

➤Step 1: Import required libraries

        import pandas as pd

        import matplotlib.pyplot as plt

        from fpdf import FPDF

        from fpdf.enums import XPos, YPos

pandas to load and analyze data.

matplotlib to create charts.

fpdf to create the PDF.

Enums from fpdf help avoid deprecated parameters for line breaks.

➤Step 2: Load CSV data

       df = pd.read_csv("STUDENTMARKSDETAILS.csv")

Reads the CSV file into a DataFrame df.

Assumes columns like Name, Class, Marks.

➤Step 3: Analyze data

      total_students = len(df)
      
      average_marks = df['Marks'].mean()
      
      class_averages = df.groupby('Class')['Marks'].mean()
      
      class_counts = df['Class'].value_counts()
      
Calculate total students.

Calculate overall average marks.

Calculate average marks by class using groupby.

Count students per class.

➤Step 4: Create charts

     plt.figure(figsize=(6,4))

    class_averages.plot(kind='bar', color='yellow')

    plt.title("Average Marks by Class")

    plt.ylabel("Average Marks")

    plt.xlabel("Class")

    plt.tight_layout()

    plt.savefig("bar_chart.png")

    plt.close()

Plots a bar chart.

Saves it as "bar_chart.png" for embedding in PDF.

➤Step 5: Initialize PDF

    pdf = FPDF()
    
    pdf.add_page()
    
    pdf.set_font("Helvetica", 'B', 16)

Create PDF object.

Add a page.

Set font to Helvetica, bold, size 16.

➤Step 6: Add Title and summary

    pdf.cell(0, 10, "Student Performance Report", align='C', new_x=XPos.LMARGIN, new_y=YPos.NEXT)
    
    pdf.set_font("Helvetica", '', 12)
    
    pdf.cell(0, 10, f"Total Students: {total_students}", new_x=XPos.LMARGIN, new_y=YPos.NEXT)
    
    pdf.cell(0, 10, f"Average Marks: {average_marks:.2f}", new_x=XPos.LMARGIN, new_y=YPos.NEXT)
    
Adds centered report title.

Adds total students and average marks info.

➤Step 7: Insert charts:

    pdf.set_font("Helvetica", 'B', 12)
    
    pdf.cell(0, 10, "Visualizations:", new_x=XPos.LMARGIN, new_y=YPos.NEXT)
    

    pdf.image("bar_chart.png", x=10, y=pdf.get_y(), w=90)
    
    pdf.image("pie_chart.png", x=110, y=pdf.get_y() - 60, w=90)
    
    pdf.ln(65)
    
Adds heading.

Inserts saved bar chart and pie chart images side-by-side.

Moves cursor down to avoid overlapping.

➤Step 8: Add detailed student data table

    pdf.set_font("Helvetica", 'B', 12)
    
    pdf.cell(0, 10, "Student Details", new_x=XPos.LMARGIN, new_y=YPos.NEXT)


    pdf.set_font("Helvetica", 'B', 11)
    
    pdf.cell(60, 10, "Name", border=1)
    
    pdf.cell(40, 10, "Class", border=1)
    
    pdf.cell(40, 10, "Marks", border=1, new_x=XPos.LMARGIN, new_y=YPos.NEXT)
    
    pdf.set_font("Helvetica", '', 11)

      for _, row in df.iterrows():
    
        pdf.cell(60, 10, str(row['Name']), border=1)
    
        pdf.cell(40, 10, str(row['Class']), border=1)
    
        pdf.cell(40, 10, str(row['Marks']), border=1, new_x=XPos.LMARGIN, new_y=YPos.NEXT)

Prints table header with borders.

Loops through each student record and prints row-wise data.

➤Step 9: Save PDF

    pdf.output("student_marks_deatils_fpdf.pdf")

Writes the PDF to disK

📌Sample Output:

  'student_marks_details_fpdf.pdf' created successfully.

📌Summary:

➤Import libraries	      -         Load needed tools for data, charts, PDF

➤Read CSV	              -         Load student data

➤Analyze	                -         Compute summary statistics

➤Plot charts	            -         Create visual summaries saved as PNGs

➤Prepare PDF	            -         Set fonts, add text and images

➤Insert table	          -         Add detailed student data

➤Save PDF                -       	Output the report file

#OUTPUT:



