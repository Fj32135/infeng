#include <iostream>
#include <vector>
#include <cmath>
#include <numeric>
unsigned GetNumberOfDigits (unsigned i)
{
    return i > 0 ? (int) log10 ((double) i) + 1 : 1;
}
class Student {
public:
    Student(std::string n,std::string m) {
            name_ = n;
            surname_ = m;
        }

    void set_index(int albnumber) { // setter
        if( GetNumberOfDigits(albnumber) == 5 || GetNumberOfDigits(albnumber)== 6)
        albnumber_ = albnumber;
        else
          std::cout << "Invalid number of digits" <<  std::endl;
    }
    int index() { // getter
        return albnumber_;
    }
    void set_grades(std::vector<float> grades)
    {
        for (std::vector<float>::iterator it = grades.begin() ; it != grades.end(); ++it)
            if(*it ==2 || *it == 3 || *it == 3.5 || *it == 4 || *it == 4.5 || *it == 5)
                    grades_.emplace_back(*it);
        else
                std::cout << "Invalid grade (" << *it <<  " )provided" << std::endl;

               }

    void add_grades(std::vector<float> grades)
    {
        for (std::vector<float>::iterator it = grades.begin() ; it != grades.end(); ++it)
            if(*it ==2 || *it == 3 || *it == 3.5 || *it == 4 || *it == 4.5 || *it == 5)
                    grades_.emplace_back(*it);
        else
                std::cout << "Invalid grade (" << *it <<  " )provided" << std::endl;

               }

    void add_grade(float grade){
        if(grade ==2 || grade == 3 || grade == 3.5 || grade == 4 || grade == 4.5 || grade == 5)
                grades_.emplace_back(grade);
    else
            std::cout << "Invalid grade (" << grade <<  " )provided" << std::endl;

           }

   void summary(Student s1)
   {
       std::cout << "Name: " <<  std::endl;
       std::cout << s1.name_ << std::endl;
       std::cout << "Surname: " <<  std::endl;
       std::cout << s1.surname_ << std::endl;
       std::cout << "Album number: " <<  std::endl;
       std::cout << s1.albnumber_ << std::endl;
       std::cout << "Grades: " << std::endl;
       for (std::vector<float>::iterator it = s1.grades_.begin() ; it != s1.grades_.end(); ++it)
           std::cout << " " <<  *it << std::endl;
   }
   void average() {
          float sum = std::accumulate(grades_.begin(), grades_.end(), 0.0f);
          average_ = sum/grades_.size();
         std::cout << "Student's average grade is " << average_ << std::endl;
      }
   void ifpassed()
   {
       int counter = 0;
       for (std::vector<float>::iterator it = grades_.begin() ; it != grades_.end(); ++it){
           if(*it == 2)
               counter++;}


       if(counter == 2)
           std::cout << "Student didn't pass the semester" << std::endl;
       else
           std::cout << "Student passed the semester" << std::endl;


   }

private:
    int albnumber_;
    std::string name_;
    std::string surname_;
    std::vector<float> grades_;
    float average_;
};



int main()
{
    Student s1("Filip", "Jankowiak");
    s1.set_index(147646);
    std::vector<float>grades = {2.0,3.5,4.0};
    s1.set_grades(grades);
    s1.add_grade(5);
    std::vector<float>add = {3,4};
    s1.add_grades(add);
    s1.summary(s1);
    s1.average();
    s1.ifpassed();

}
