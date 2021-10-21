#include <iostream>
#include<fstream>
#include <clocale>

using namespace std;

class Password
{
public:

    int Entrance()
    {
        string login = "login.txt";
        string password = "password.txt";

        fstream log;
        fstream pass;

        log.open(login, fstream::in | fstream::out | fstream::app);
        pass.open(password, fstream::in | fstream::out | fstream::app);

        if (!log.is_open() && !pass.is_open())
        {
            cout << "Ошибка!" << endl;
        }
        
        else
        {
            string log_chek;
            string pass_chek;

            while (!log.eof())  
            {
                log_chek = "";
                log >> log_chek; 
            }
            while (!pass.eof()) 
            {
                pass_chek = "";
                pass >> pass_chek; 
            }

            string login_correct;
            string pass_correct;

            cout << "Введите свой логин, пожалуйста: ";
            cin >> login_correct;
            cout << endl;
            cout << "Введите свой пароль,пожалуйста: "; 
            cin >> pass_correct;

            if (login_correct != log_chek && pass_correct != pass_chek)
            {
                cout << "Пароль или логин введен неправильно!" << endl;
            }
            else
            {
                cout << "Выполняется вход" << endl;
            }
            return 0;
        }
    }
    int Sign_up()
    {
        string login = "login.txt";
        string password = "password.txt";

        fstream log;
        fstream pass;

        log.open(login, fstream::in | fstream::out | fstream::app);
        pass.open(password, fstream::in | fstream::out | fstream::app);

        if (!log.is_open() && !pass.is_open())
        {
            cout << "Данные неверны!" << endl;
        }
        else
        {
            string log_chek;
            string pass_chek;
            cout << "Введите свой логин,пожалуйста: "; 
            cin >> log_chek;
            cout << endl;
            cout << "Введите свой пароль,пожалуйста: "; 
            cin >> pass_chek;

            log << log_chek;
            pass << pass_chek;

            cout << "Регистрация прошла успешно!" << endl;

            return 0;

        }
    }

};
class SignUp
{
public:

    int WorkSignUp()
    {
        int choice;
        cout << "Добро пожаловать!" << endl;
        cout << "1.Войти" << endl;
        cout << "2.Зарегистрироваться" << endl;
        cin >> choice;

        switch (choice)
        {
            case 1:
            Password pass;
            pass.Entrance();
            break;
            case 2:
            Password pass;
            pass.Sign_up();
            break;
            default:
            cout << "Вы ничего не выбрали" << endl;
        }
        return 0;
    }
};

int main()
{
    setlocale(LC_ALL, "rus");

    SignUp SignUp;

    SignUp.WorkSignUp();

    return 0;
}
