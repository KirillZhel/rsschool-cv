# KIRILL ZHELTYSHEV #
*Saint-Petersburg, Russia*
## Contact ##

- **Mobile:** 8(911)-718-47-60
- **EMail:**  zheltyshev.kirill@gmail.com
- **Telegram:** [kiryazh](https://t.me/kiryazh)
- **GitHub:** [KirillZhel](https://github.com/KirillZhel)

## Summary ##

My goal is to get a new modern profession of a programmer and further professional growth. I am stress-resistant, assiduous, ready to learn new things and am not afraid of sudden changes.

## Skills ##

- Basic knowledge of C++, C#, JS, HTML5, CSS3, GIT.
- Basic knowledge of IDE Visual Studio.

## Code Example ##

```
#include <iostream>
#include <fstream>
#include <cmath>
#include "functions.h"

double integrand(double t)
{
    double rez = sin (t * t);
    return rez;
}

double lagrange1(double* x, double* y, int n, double _x)
{
    double result = 0.0;

    for (int i = 0; i < n; i++)
    {
        double P = 1.0;

        for (int j = 0; j < n; j++)
            if (j != i)
                P *= (_x - x[j]) / (x[i] - x[j]);

        result += P * y[i];
    }

    return result;
}

int main()
{
    int i;
    double x[7];

    for (i = 0; i < 7; i++)
    {
        x[i] = 1.5 + 0.2 * i;
    }

    double abserr = 0.001;
    double relerr = 0.001;
    double result = 0.0, errest = 0.0;
    int nofun = 0, flag = 0;
    double posn = 0.0;

    double function[7];

    std::cout << std::endl;
    std::cout << " Number" << "\t" << "x[i]" << "\t" << "function[i]" << std::endl;
    std::cout << std::endl;

    for (i = 0; i < 7; i++)
    {
        quanc8(integrand, 0, x[i],
               abserr, relerr,
               &result, &errest,
               &nofun,
               &posn, &flag);

        function[i] = result;
        std::cout << " " << i << "\t" << x[i] << "\t" << function[i] << std::endl;
    }

    std::cout << std::endl;

    /*----------1 часть (Лагранж)----------*/

    std::cout << "----------1 chast'----------" << std::endl;
    std::cout << std::endl;

    std::cout << " Number" << "\t" << "x[i]" << "\t" << "function[i]" << std::endl;
    std::cout << std::endl;

    const int n = 6;

    int k = 0;
    double x_k[n];
    double arr_lagrange[6];

    for (k = 0; k < 6; k++)
    {
        x_k[k] = 1.6 + 0.2 * k;
        arr_lagrange[k] = lagrange1(x, function, 7, x_k[k]);

        std::cout << " " << k << "\t" << x_k[k] << "\t" << lagrange1(x, function, 7, x_k[k]) << std::endl;
    }
 
    /*----------2 часть (Сплайн)----------*/

    std::cout << std::endl;
    std::cout << "----------2 chast'----------" << std::endl;
    std::cout << std::endl;

    int end1 = 0, end2 = 0;
    double slope1 = 0, slope2 = 0;
    double b[n], c[n], d[n];
    int iflag;

    spline(n, end1, end2, slope1, slope2,
           x, function, b, c, d, &iflag);

    int nk = 6;
    double u;
    int last = -1;
    
    double arr_spline[6];

    for (k = 0; k < 6; k++)
    {
        arr_spline[k] = seval(nk, x_k[k], x, function, b, c, d, &last);

        std::cout << " " << k << "\t" << x_k[k] << "\t" <<
        seval(nk, x_k[k], x, function, b, c, d, &last) << std::endl;
    }

    /*----------3 часть (QUANC8 для x_k)----------*/

    std::cout << std::endl;
    std::cout << "----------3 chast'----------" << std::endl;
    std::cout << std::endl;

    double function_k[6];
    double arr_quanc8[6];

    for (k = 0; k < 6; k++)
    {
        quanc8(integrand, 0, x_k[k],
            abserr, relerr,
            &result, &errest,
            &nofun,
            &posn, &flag);

        function_k[k] = result;
        arr_quanc8[k] = function_k[k];

        std::cout << " " << k << "\t" << x_k[k] << "\t" << function_k[k] << std::endl;
    }

    std::cout << std::endl;
    std::cout << " " << "N" << "\t" << "x[k]" << "\t" << "Lagrange" << "\t" << "Spline" << "\t" << "QUANC8" << std::endl;
    std::cout << std::endl;

    for (k = 0; k < 6; k++)
    {
        std::cout << " " << k << "\t" << x_k[k] << "\t" << arr_lagrange[k] << "\t" << arr_spline[k] << "\t" << arr_quanc8[k] <<  std::endl;
    }
}
```

## Education ##

- Master's degree in "design and technological support of machine-building industries" in the direction of "metalworking machines and complexes".
- half-education in "computer engineering".

## English ##

- Pre-Intermediate
