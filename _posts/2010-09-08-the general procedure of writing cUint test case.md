---
title: 使用CUnit写测试程序的一般步骤
tags: [Programming]
description: 使用CUnit写测试程序的一般步骤
---

# 使用CUnit写测试程序的一般步骤

## A. 使用CUnix写测试程序的一般步骤

1.编写测试函数。

2.编写setup/clearup函数。-在运行Suite的前后调用。

3.初始化Test Registry。-调用[CU_initialize_registry()](http://cunit.sourceforge.net/doc/test_registry.html)

4.添加Suites至Test Registry。-调用[CU_add_suite()](http://cunit.sourceforge.net/doc/managing_tests.html)

5.添加测试函数至Suites。-调用[CU_add_test()](http://cunit.sourceforge.net/doc/managing_tests.html)

6.指定运行测试的接口。-e.g. [CU_console_run_tests](http://cunit.sourceforge.net/doc/running_tests.html)

7.销毁注册的Test Registry。-调用[CU_cleanup_registry](http://cunit.sourceforge.net/doc/test_registry.html)




> A typical sequence of steps for using the CUnit framework is: 

> 1. Write functions for tests (and suite init/cleanup if necessary).

> 2. Initialize the test registry - [CU_initialize_registry()](http://cunit.sourceforge.net/doc/test_registry.html#init)

> 3. Add suites to the test registry - [CU_add_suite()](http://cunit.sourceforge.net/doc/managing_tests.html#addsuite)

> 4. Add tests to the suites - [CU_add_test()](http://cunit.sourceforge.net/doc/managing_tests.html#addtest)

> 5. Run tests using an appropriate interface, e.g. [CU_console_run_tests](http://cunit.sourceforge.net/doc/running_tests.html#console)

> 6. Cleanup the test registry - [CU_cleanup_registry](http://cunit.sourceforge.net/doc/test_registry.html#cleanup)



## B.Cunit结构如下：

```html
                     Test Registry
                            |
             ------------------------------
             |                            |
          Suite '1'      . . . .       Suite 'N'
             |                            |
       ---------------             ---------------
       |             |             |             |
    Test '11' ... Test '1M'     Test 'N1' ... Test 'NM'
```

## C.

以上说明为一般步骤，比较繁复一点。但实际上，可以使用CUNIT的**shortcut**模式来编写测试程序。

即自己直接编写测试集合（suites），各个单测试组（suite），实现各个测试函数。

 

### 0. **编写测试函数**

`void testFatal(void)`

`{`

  CU_TEST_FATAL(CU_TRUE);

  fprintf(stderr, "/nFatal assertion failed to abort test in testFatal/n");

  exit(1);

`}`

 

### 1. 单个测试组`(test_array)`的定义

`CU_TestInfo tests_fata_test_arrayl[] =`

`{`

  { "testFatal", testFatal },

`//    测试函数名，测试函数名（实现）`

 

​    CU_TEST_INFO_NULL,

`};`

 

//单个测试suite中可以有很多个测试函数

 

### **2.**  **定义测试集`suites`**

`CU_SuiteInfo suites[] =`

`{`

`\#if 0`

  { "suite_success_both",    suite_success_init,    suite_success_clean,        tests_success },

  { "suite_success_init",      suite_success_init,    NULL,                                tests_success },

  { "suite_success_clean",  NULL,                       suite_success_clean,         tests_success },

  { "test_failure",                 NULL,                       NULL,                                 tests_failure },

  { "suite_failure_both",      suite_failure_init,      suite_failure_clean,             tests_suitefailure }, /* tests should not run */

  { "suite_failure_init",         suite_failure_init,     NULL,                                  tests_suitefailure }, /* tests should not run */

`\#endif`

  { "TestFatal",                   NULL,                      NULL,                                   tests_fata_test_arrayl  },

`//    测试组(suite)的名字，测试组初始化函数，测试组清除函数，               单个测试组(test_array)的定义`

 

`CU_SUITE_INFO_NULL,`

`};`

 

### **3.** **注册测试`suites`**

`/* Register suites. */`

`if (CU_register_suites(suites)!= CUE_SUCCESS)`

`{`

​            fprintf(stderr, "suite registration failed - %s/n",

​                        CU_get_error_msg());

​            exit(EXIT_FAILURE);

`}`

 

## **D.**

至此前期的主要准备工作已经完成，但是要使用cuint还需要一些步骤：

Cunit 被编译成静态库，测试时使用该库提供的测试工具集。此外在运行测试程序时，CUint提供了几种不同的接口：

| **Automated** | Output to xml file             | Non-interactive |
| ------------- | ------------------------------ | --------------- |
| **Basic**     | Flexible programming interface | Non-interactive |
| **Console**   | Console interface (ansi C)     | Interactive     |
| **Curses**    | Graphical interface (Unix)     | Interactive     |

Console是可以人机交互的。

 

### 在console模式下构建测试程序：

编写main()函数，一般格式如下： 

`int main(int argc, char* argv[])`

{ 

​     /*初始化registry */

​    if (CUE_SUCCESS != CU_initialize_registry())

​      return CU_get_error();

​    //registry在使用前必须初始化，用户需要在调用任何Cunit函数之前调用该函数。

 

​    /* Register all suites and tests */

​    if (CUE_SUCCESS != CU_register_suites(suites))

​    {

​        CU_cleanup_registry();            

​        return CU_get_error();

​    }    

​    //所有以CU_SuiteInfo定义的测试组都可以通过单次调用上述函数注册

 

​    /*** This starts the test run: */        

​      CU_console_run_tests();//run all tests 

​    //以console模式执行所有的测试case

​    CU_cleanup_registry();

 

​    return CU_get_error();

 

`}`
