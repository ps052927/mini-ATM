# mini-ATM
this is my first project in c language <br>

#include <stdio.h>
#include <stdlib.h>
#include <windows.h>

void typeEffect(const char *text, int delay)
{
    while (*text)
    {
        printf("%c", *text);
        fflush(stdout);
        Sleep(delay);
        text++;
    }
}

int main()
{
    system("color 0A");
    long long n;
    int num1, num2;
    char ACname = 'A';
    int pin = 1234;
    int balance = 10000;
    int amount;
    int attempts = 3;
    long long AC = 12345678910;
    long long mob = 1234567890;
    int otp = 123456;

    typeEffect("\nWELCOME TO MINI ATM \nchoose your preference\n\n", 54);
    typeEffect("1- withdraw\n2- check balance\n3- change pin\n", 50);
    scanf("%lld", &n);

    switch (n)
    {
        case 1:
            typeEffect("enter PIN: ", 50);
            scanf("%lld", &n);
            if (pin == n)
            {
                typeEffect("enter amount: ", 50);
                scanf("%d", &amount);
                if (balance >= amount)
                {
                    typeEffect("wait and collect your CASH: ", 50);
                    Sleep(3000);
                    printf("%d rupees\n", amount);
                    typeEffect("would you like to print RECEIPT\n1- yes\n2- no\n", 50);
                    scanf("%lld", &n);
                    if (n == 1)
                    {
                        typeEffect("RECEIPT is printing please wait\n", 50);
                        Sleep(2000);
                        printf("RECEIPT\n");
                    }
                    else
                    {
                        typeEffect("thanks for using ATM\n", 50);
                    }
                }
                else
                {
                    typeEffect("insufficient balance\n", 50);
                }
            }
            else
            {
                typeEffect("incorrect pin, please enter correct pin\n", 50);
            }
            break;

        case 2:
            typeEffect("enter PIN: ", 50);
            scanf("%d", &num1);
            if (num1 == pin)
            {
                printf("your balance is: %d\n", balance);
                typeEffect("would you like to print receipt\n1- yes \n2- no\n", 50);
                scanf("%lld", &n);
                if (n == 1)
                {
                    typeEffect("please wait receipt is printing\n", 50);
                    Sleep(3000);
                    printf("RECEIPT\n");
                }
                else
                {
                    typeEffect("thanks for using ATM\n", 50);
                }
            }
            else
            {
                attempts--;
                printf("incorrect pin, only %d attempts left\n", attempts);
            }
            break;

        case 3:
            typeEffect("enter 11 digit account number: ", 50);
            scanf("%lld", &n);
            if (n == AC)
            {
                typeEffect("enter registered mobile number: \n", 50);
                scanf("%lld", &n);
                if (n == mob)
                {
                    typeEffect("enter 6 digit OTP sent to your registered mobile number: ", 50);
                    scanf("%lld", &n);
                    if (n == otp)
                    {
                        typeEffect("enter new pin: ", 50);
                        scanf("%d", &num1);
                        typeEffect("re-enter new pin: ", 50);
                        scanf("%d", &num2);
                        if (num1 == num2)
                        {
                            pin = num1;
                            printf("your new pin: %d\n", pin);
                        }
                        else
                        {
                            typeEffect("entered pin does not match, please enter carefully\n", 50);
                        }
                    }
                    else
                    {
                        typeEffect("entered OTP is incorrect, please try again\n", 50);
                    }
                }
                else
                {
                    typeEffect("incorrect mobile number, please try again\n", 50);
                }
            }
            else
            {
                typeEffect("incorrect account number, please try again\n", 50);
            }
            break;

        default:
            typeEffect("invalid input, please try again\n", 50);
    }

    return 0;
}

