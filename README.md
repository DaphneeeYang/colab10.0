# colab10.0
# Zhuqing Yang (zhuqingy) Section E #############
# Colab10
# Partner: Shuyuan Ding (shuyuand)###############

import math
import string
import copy
import random

#################################################
# Helper functions
#################################################

def almostEqual(d1, d2, epsilon=10**-7):
    # note: use math.isclose() outside 15-112 with Python version 3.5 or later
    return (abs(d2 - d1) < epsilon)

import decimal
def roundHalfUp(d):
    # Round to nearest with ties going away from zero.
    rounding = decimal.ROUND_HALF_UP
    # See other rounding options here:
    # https://docs.python.org/3/library/decimal.html#rounding-modes
    return int(decimal.Decimal(d).to_integral_value(rounding=rounding))

#################################################
# Colab10 problems
########################

def evalAns(lst,sym):
    if sym == "+":
        return lst[0]+lst[1]
    elif sym == "-":
        return lst[0]-lst[1]
    elif sym == "*":
        return lst[0]*lst[1]
    elif sym == "/":
        return lst[0]/lst[1]

def evalPrefixNotation(lst):
    if len(lst) == 1:
        return [lst[0]]
    elif len(lst) == 0:
        return []
    else:
        sym1 = lst.pop(0)
        if isinstance(lst[0],int):
            if isinstance(lst[1],int):
                tempans = evalAns(lst[:2],sym1)
                return [tempans]+evalPrefixNotation(lst[2:])
            else:
                return [evalAns([lst[0]]+evalPrefixNotation(lst[1:]),sym1)]
        else:
            return [evalAns(evalPrefixNotation(lst),sym1)]


def findLargestFile(path):
    return 42

def solveSudoku(board):
    return 42

    

    
#################################################
# Colab10 Test Functions
#################################################    

def testEvalPrefixNotation():
    print("Testing evalPrefixNotation()...", end="")
    assert(evalPrefixNotation(['*',2,3]) == 6)
    assert(evalPrefixNotation(['+','*',2,3,'*',1,4]) == 10)
    assert(evalPrefixNotation(['*', '+', 2, '*', 3, '-', 8, 7, '+', '*', 2, 2, 5]) == 8)
    print("Passed!")

#################################################
# Colab10 Main
#################################################

def testAll():
    testBookClass()
    testBirdClasses()
    testAlternatingSum()
    testPowersOf3ToN()

def main():
    testAll()

#if __name__ == '__main__':
#    main()
