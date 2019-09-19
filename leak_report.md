# Leak report

 46 bytes in 6 blocks of memory are lost. Freeing the variable "cleaned" in the function is_clean() will fix the issue. This is because "cleaned" uses "str" which calls upon strip(), whose output allocates memory. That memory doesn't need to be used after cleaned is used for the last time, so freeing it then is optimal.