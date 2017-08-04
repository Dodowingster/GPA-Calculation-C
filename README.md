# GPA-Calculation-C
A programme I made that could calculate The GPA of students according to their Credits, Total Marks and also Grade Points.

#include <stdio.h>
#include <stdlib.h>

void main()
{

    int stnum, courses, arr[100];
    float arr2[6], arr3[20];
    int counter, counter2, id, sum=0, sum2=0;
    float gpa, gp, gpch;
    char grd;

    //Receiving the number of students to be calculated
     printf("Please enter the number of student: ");
     scanf("%d", &stnum);

     //Guaranteeing the maximum(above 20) and minimum(below 0) number of students
     if(stnum>20 || stnum<0)
                {
                    printf("Invalid user input. Please enter from 1-20. Thank you");
                }else
                {
                    printf("How many courses does each student(s) register?: ");
                    scanf("%d", &courses);

                //Guaranteeing the minimum(below 0) number of courses taken
                if(courses<=0)
                {
                    printf("Invalid user input. Please enter a valid number.");
                }else
                {

                //Asking for the student's respective details
                for(counter2=1; counter2<=stnum; counter2++)
                    {
                        printf("\nStudent %d:\n\n", counter2);


                        printf("Please enter the student ID: ");
                        scanf("%d", &id);

                        for(counter=0; counter<courses; counter++)
                        {

                        printf("Please enter credit hour for course %d: ", counter+1);
                        scanf("%f", &arr2[counter]);
                        printf("Please enter total mark for course %d: ", counter+1);
                        scanf("%d", &arr[counter]);


                        //arr[counter] = Total Marks of the course //arr2[counter] = Credit Hour
                        //Converting the Total Mark(arr[x]) into Grades
                        if(arr[counter]>=85&&arr[counter]<=100)
                        {
                            grd = 'A';
                            gp = 4.00;
                        }
                        else if(arr[counter]>80&&arr[counter]<84)
                        {
                            grd = 'A-';
                            gp = 3.70;
                        }
                        else if(arr[counter]>=75&&arr[counter]<=79)
                        {
                            grd = 'B+';
                            gp = 3.30;
                        }
                        else if(arr[counter]>=70&&arr[counter]<=74)
                        {
                            grd = 'B';
                            gp = 3.00;
                        }
                        else if(arr[counter]>=65&&arr[counter]<=69)
                        {
                            grd = 'B-';
                            gp = 2.70;
                        }
                        else if(arr[counter]>=60&&arr[counter]<=64)
                        {
                            grd = 'C+';
                            gp = 2.30;
                        }
                        else if(arr[counter]>=55&&arr[counter]<=59)
                        {
                            grd = 'C';
                            gp = 2.00;
                        }
                        else if(arr[counter]>=50&&arr[counter]<=54)
                        {
                            grd = 'C-';
                            gp = 1.70;
                        }
                        else if(arr[counter]>=45&&arr[counter]<=49)
                        {
                            grd = 'D+';
                            gp = 1.30;
                        }
                        else if(arr[counter]>=40&&arr[counter]<=44)
                        {
                            grd = 'D';
                            gp = 1.00;
                        }
                        else if(arr[counter]<40)
                        {
                            grd = 'E';
                            gp = 0.00;
                        }

                        //Setting every Grade Point * Credit Hour for EVERY course
                        arr3[counter] = arr2[counter] * gp;

                        //Setting the total Credit Hours for ONE STUDENT
                        sum = sum + arr2[counter];

                        //Setting the total of Grade Point * Credit Hour for EVERY student
                        sum2 = sum2 + arr3[counter];

                    }

                }

            }

            printf("RESULT INFO:\n");
            printf("============\n\n");


            printf("Student Id\tCourse\tCredit Hour\tMark\tGrade\tGrade Point\tGP*CH\n");


                    for(counter=1; counter<=stnum; counter++)
                    {

                    printf("\t%d", counter);
                    printf("\t %d\t %f\t %d\t %c\t %f\t %f\n", courses, arr2[counter], arr[counter], grd, gp, arr3[counter]);

            }


     }
}
