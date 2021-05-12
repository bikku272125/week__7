# week__7
# Write a program for given case: Given r red, b blue, and g green balls, find the total number of the arrangements in a row such that no two balls of the same color end up together.  Input:  r = 1, b = 1, g = 1   Output: Total number of arrangements are 6   The arrangements are [bgbr, bgrb, brbg, brgb, gbrb, rbgb]   Input:  r = 2, b = 3, g = 1   Output: 10   The arrangements are [bgbrbr, bgrbrb, brbgbr, brbgrb, brbrbg, brbrgb, brgbrb, gbrbrb, rbgbrb, rbrbgb]


def f(r ,b , g, prev):
    if r < 0 or b < 0 or g < 0 :
        return 0
    if r == 0 and b ==0 and g == 0:
        return 1
    if prev == 'r':
        return f(r , b - 1 , g , 'b') + f(r , b , g-1 , 'g')
    if prev == 'b':
        return f(r - 1, b , g , 'r') + f(r , b , g - 1 , 'g')
    if prev == 'g':
        return f(r-1,b,g,'r') + f(r,b-1,g,'b')
def totalWays(r ,b ,g):
    return f( r - 1 , b, g, 'r') + f(r ,b - 1 , g, 'b') + f(r , b, g -1, 'g') 
if __name__ == '__main__':
    (r ,b ,g) = (2 ,3 ,1)
    r=int(input('enter number of red balls'))
    b=int(input('enter number of blue balls'))
    g=int(input('enter number of green balls'))
print("The total number of distinct arrangements are", totalWays(r,b,g));  
