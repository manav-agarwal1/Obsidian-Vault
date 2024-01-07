- Simple problem on multiples of $3$ or $5$.
```1
void helper(){
    int res = 0;
    int vec[3] = {3, 5, 15};
    size_t n = sizeof(vec)/sizeof(vec[0]);
    for (size_t i = 0; i < n; i++) {
        for (int j = vec[i]; j < 1000; j+=vec[i]) {
            if (vec[i] != 15)
                res += j;
            else
                res -= j;
        }
    }
    cout << res << '\n';
}
```
- Sum of even valued fibonacci numbers with some bound.
```2
void helper(){
    int a_i_m_2 = 1;
    int a_i_m_1 = 2;
    int a_i = a_i_m_1 + a_i_m_2;
    int res = a_i_m_1;
    for (; a_i < 4'000'000; a_i = a_i_m_1 + a_i_m_2) {
        if ((a_i&1) == 0) {
            res += a_i;
        }
        a_i_m_2 = a_i_m_1;
        a_i_m_1 = a_i;
    }
    cout << res << '\n';
}
```
- Largest prime factor of a very large number. [[Integer Factorization]]
```
/*

There can be atmost one prime factor greater than sqrt(n).

All primes are of the form 2, 3 or 6n-1 or 6n+1

6n-1 + 2 = 6n+1

*/

void helper(){

    int64_t n = 600851475143;

    int64_t pf = 0ll;

    while (n % 2 == 0ll) {

        pf = 2ll;

        n /= 2ll;

    }

    while (n % 3 == 0ll) {

        pf = 3ll;

        n /= 3ll;

    }

  

    // rest of the primes are off the form

    for (int64_t i = 5ll; i*i <= n; i+=6ll) {

        while (n%i == 0ll) {

            pf = i;

            n /= i;

        }

        i += 2ll;

        while (n%i == 0ll) {

            pf = i;

            n /= i;

        }

        i -= 2ll;

    }

    if (n > 4) {

        pf = n;

    }

    cout << pf << '\n';

}
```
- Largest Palindrome which is product of 2-n digit numbers
```
/*
Any Palindrome with even digits must be divisible by 11. (Hint: 11 divisibility rule)
Any n digit number multiplication give result of digit 2n-1 or 2n and if we want the largest palindrome then we are looking for 2n digits, so divisible by 11.

when n is even:
    (9 n/2 times)(0 n times)(9 n/2 times)
when n is odd:
    well we have to check but we can avoid checking for small numbers
*/
void helper(int n){

    if (n&1) {

        int64_t hi = pow(10, n)-1ll;

        int64_t lo = pow(10, n-1);

        lo = hi - pow(10, (n/2)+1); // avoid small numbers

        cout << lo << ' ' << hi << endl;

        int64_t a = 0;

        int64_t b = 0;

        int64_t res = 0ll;

        for (int64_t i = hi; i >= lo; i--) {

            if (res >= i*hi) {

                // no point going ahead

                break;

            }

            for (int64_t j = i; j <= hi; j++) {

                int64_t temp = j*i*1ll;

                if((res < temp) && (res % 11 == 0) && is_even_palindrome(to_string(temp))) {

                    res = temp;

                    a = i;

                    b = j;

                    // cout << temp << " = " << a << " x " << b << '\n';

                }

            }

        }

        cout << res << " = " << a << " x " << b << '\n';

        cout << "-----------------\n";

    }

    else {

        string res = "";

        res = string(n/2, '9');

        res = res + string(n, '0') + res;

        cout << res << '\n';

        cout << "-----------------\n";

    }

  

}
```
- 