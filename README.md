# Grade-Classification
A Program which allows you to check your assignment score and check the classification you have got

#include <iostream>
#include <iomanip>

using namespace std;

int main()
{
	double totalMarks, achievedMarks;
	double percentageAchieved;
	char answer;
	
	bool markValidity(double&, double&);

	bool isValid = false;
	
	void calculatePercentage(double&, double&, double&);

	void checkGradeClass(double&);

	do
	{
		do
		{
			isValid = markValidity(totalMarks, achievedMarks);
		}	while (!isValid);

			calculatePercentage(totalMarks, achievedMarks, percentageAchieved);

			checkGradeClass(percentageAchieved);

			cout << endl << endl << endl;

			cout << "Another Result? (Y/N)";
			cin >> answer;
			cout << "______________________________________" << endl << endl;
	} while (!(tolower(answer) == 'n'));
	
	return(0);
}

bool markValidity(double& totalMarks, double& achievedMarks)
{
	cout << "Acheived Marks: ";
	cin >> achievedMarks;
	cout << endl << "Total Marks: ";
	cin >> totalMarks;
	if ((totalMarks <= 0 || achievedMarks < 0) || (achievedMarks > totalMarks))
	{
	cout << endl << "Enter valid marks!" << endl << endl;
		return false;
	}

	totalMarks = totalMarks;
	achievedMarks = achievedMarks;
	return true;
}

void calculatePercentage(double& totalMarks, double& achievedMarks, double& percentageAchieved)
{
	percentageAchieved = achievedMarks / totalMarks * 100;
	cout << "Your overall percentage is: " << fixed << setprecision(2) << percentageAchieved << "%" << endl << endl;
}

void checkGradeClass(double& percentageAchieved)
{
	int gradePercentage = percentageAchieved;
	if (gradePercentage < 30)
	{
		cout << "You have Failed!";
	}
	else if ((gradePercentage >= 30) && (gradePercentage < 40))
	{
		cout << "You have Passed!";
	}
	else if ((gradePercentage >= 40) && (gradePercentage < 50))
	{
		cout << "You have a Third Class honours!";
	}
	else if ((gradePercentage >= 50) && (gradePercentage < 60))
	{
		cout << "You have got a 2:2!";
	}
	else if ((gradePercentage >= 60) && (gradePercentage < 70))
	{
		cout << "You have got a 2:1!";
	}
	else
	{
		cout << "You have a First Class Honours!";
	}
}
