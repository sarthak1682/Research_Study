---
{"dg-publish":true,"permalink":"/coursework/so-se24/dl4science/runge-kutta-time-stepping-schemes/","noteIcon":""}
---

---
[Learning the Runge-Kutta Method 1. Basic Runge-Kutta - YouTube](https://www.youtube.com/watch?v=8_PnCSsA_BQ)

known function at time t_0 and an expr. of derivative, want value of function at t_1.
divide into 4 steps: t_0, half_way, half_way, t_1. 
halfway has twice the accuracy of t_0, t_1, hence double the weight 
ans = k1 + 2(k2+k3) + k4, the errors in the calculations cancel such that the err is step^4