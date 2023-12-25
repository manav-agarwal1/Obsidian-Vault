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
- 
