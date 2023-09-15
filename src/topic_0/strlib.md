# simpio.h

该接口定义了动态分配字符串的通用库。传统 C 字符串与使用此接口定义的字符串之间的主要区别是：

- `strlib.h` 接口负责内存分配，确保有足够的空间来保存每个字符串操作的结果。
- `strlib.h` 接口的客户端应将所有字符串视为不可变，并避免写入字符数组。

## 接口

| 函数                           | 功能                                                                                                                   |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| `ConcatString(s1, s2)`         | 通过将两个字符串首尾相连进行连接                                                                                       |
| `IthChar(s, i)`                | 返回字符串 `s` 中位置 `i` 的字符                                                                                       |
| `SubString(s, p1, p2)`         | 返回 `s` 索引区间为 `[p1, p2]` 的子字符串                                                                              |
| `CharToString(ch)`             | 接受单个字符并返回由该字符组成的单字符字符串                                                                           |
| `StringLength(s)`              | 返回字符串 `s` 的长度                                                                                                  |
| `CopyString(s)`                | 将字符串 `s` 复制到动态内存中并返回新字符串                                                                            |
| `StringEqual(s1, s2)`          | 如果字符串 `s1` 和 `s2` 相等，则返回 true                                                                              |
| `StringCompare(s1, s2)`        | 如果字符串 `s1` 按字典顺序位于 `s2` 之前，则返回 `-1`；如果相等，则返回 `0`；如果 `s1` 位于 `s2` 之后，则返回 `+1`     |
| `FindChar(ch, text, start)`    | 从位置 `start` 开始，在字符串 `text` 中搜索的字符 `ch`，并返回该字符出现的第一个索引；如果未找到匹配项，则返回 `-1`    |
| `FindString(str, text, start)` | 从位置 `start` 开始，在字符串 `text` 中搜索字符串 `str`，并返回该字符串出现的第一个索引；如果未找到匹配项，则返回 `-1` |
| `ConvertToLowerCase(s)`        | 返回一个新字符串，其中所有字母字符都转换为小写                                                                         |
| `ConvertToUpperCase(s)`        | 返回一个新字符串，其中所有字母字符都转换为大写                                                                         |
| `IntegerToString(n)`           | 将整数转换为相应的数字字符串                                                                                           |
| `StringToInteger(s)`           | 将数字字符串转换为整数                                                                                                 |
| `RealToString(d)`              | 将浮点数转换为相应的数字字符串                                                                                         |
| `StringToReal(s)`              | 将数字字符串转换为浮点数                                                                                               |

## 接口详情

```c
/* Section 1 -- Basic string operations */

/*
 * Function: ConcatString
 * Usage: s = ConcatString(s1, s2);
 * --------------------------
 * This function concatenates two strings by joining them end
 * to end.  For example, ConcatString("ABC", "DE") returns the string
 * "ABCDE".
 */

string ConcatString(string s1, string s2);

/*
 * Function: IthChar
 * Usage: ch = IthChar(s, i);
 * --------------------------
 * This function returns the character at position i in the
 * string s.  It is included in the library to make the type
 * string a true abstract type in the sense that all of the
 * necessary operations can be invoked using functions. Calling
 * IthChar(s, i) is like selecting s[i], except that IthChar
 * checks to see if i is within the range of legal index
 * positions, which extend from 0 to StringLength(s).
 * IthChar(s, StringLength(s)) returns the null character
 * at the end of the string.
 */

char IthChar(string s, int i);

/*
 * Function: SubString
 * Usage: t = SubString(s, p1, p2);
 * --------------------------------
 * SubString returns a copy of the substring of s consisting
 * of the characters between index positions p1 and p2,
 * inclusive.  The following special cases apply:
 *
 * 1. If p1 is less than 0, it is assumed to be 0.
 * 2. If p2 is greater than the index of the last string
 *    position, which is StringLength(s) - 1, then p2 is
 *    set equal to StringLength(s) - 1.
 * 3. If p2 < p1, SubString returns the empty string.
 */

string SubString(string s, int p1, int p2);

/*
 * Function: CharToString
 * Usage: s = CharToString(ch);
 * ----------------------------
 * This function takes a single character and returns a
 * one-character string consisting of that character.  The
 * CharToString function is useful, for example, if you
 * need to concatenate a string and a character.  Since
 * ConcatString requires two strings, you must first convert
 * the character into a string.
 */

string CharToString(char ch);

/*
 * Function: StringLength
 * Usage: len = StringLength(s);
 * -----------------------------
 * This function returns the length of s.
 */

int StringLength(string s);

/*
 * Function: CopyString
 * Usage: newstr = CopyString(s);
 * ------------------------------
 * CopyString copies the string s into dynamically allocated
 * storage and returns the new string.  This function is not
 * ordinarily required if this package is used on its own,
 * but is often necessary when you are working with more than
 * one string package.
 */

string CopyString(string s);

/* Section 2 -- String comparison functions */

/*
 * Function: StringEqual
 * Usage: if (StringEqual(s1, s2)) ...
 * -----------------------------------
 * This function returns true if the strings s1 and s2 are
 * equal.  For the strings to be considered equal, every
 * character in one string must precisely match the
 * corresponding character in the other.  Uppercase and
 * lowercase characters are considered to be different.
 */

bool StringEqual(string s1, string s2);

/*
 * Function: StringCompare
 * Usage: if (StringCompare(s1, s2) < 0) ...
 * -----------------------------------------
 * This function returns a number less than 0 if string s1
 * comes before s2 in alphabetical order, 0 if they are equal,
 * and a number greater than 0 if s1 comes after s2.  The
 * ordering is determined by the internal representation used
 * for characters, which is usually ASCII.
 */

int StringCompare(string s1, string s2);

/* Section 3 -- Search functions */

/*
 * Function: FindChar
 * Usage: p = FindChar(ch, text, start);
 * -------------------------------------
 * Beginning at position start in the string text, this
 * function searches for the character ch and returns the
 * first index at which it appears or -1 if no match is
 * found.
 */

int FindChar(char ch, string text, int start);

/*
 * Function: FindString
 * Usage: p = FindString(str, text, start);
 * ----------------------------------------
 * Beginning at position start in the string text, this
 * function searches for the string str and returns the
 * first index at which it appears or -1 if no match is
 * found.
 */

int FindString(string str, string text, int start);

/* Section 4 -- Case-conversion functions */

/*
 * Function: ConvertToLowerCase
 * Usage: s = ConvertToLowerCase(s);
 * ---------------------------------
 * This function returns a new string with all
 * alphabetic characters converted to lower case.
 */

string ConvertToLowerCase(string s);

/*
 * Function: ConvertToUpperCase
 * Usage: s = ConvertToUpperCase(s);
 * ---------------------------------
 * This function returns a new string with all
 * alphabetic characters converted to upper case.
 */

string ConvertToUpperCase(string s);

/* Section 5 -- Functions for converting numbers to strings */

/*
 * Function: IntegerToString
 * Usage: s = IntegerToString(n);
 * ------------------------------
 * This function converts an integer into the corresponding
 * string of digits.  For example, IntegerToString(123)
 * returns "123" as a string.
 */

string IntegerToString(int n);

/*
 * Function: StringToInteger
 * Usage: n = StringToInteger(s);
 * ------------------------------
 * This function converts a string of digits into an integer.
 * If the string is not a legal integer or contains extraneous
 * characters, StringToInteger signals an error condition.
 */

int StringToInteger(string s);

/*
 * Function: RealToString
 * Usage: s = RealToString(d);
 * ---------------------------
 * This function converts a floating-point number into the
 * corresponding string form.  For example, calling
 * RealToString(23.45) returns "23.45".  The conversion is
 * the same as that used for "%G" format in printf.
 */

string RealToString(double d);

/*
 * Function: StringToReal
 * Usage: d = StringToReal(s);
 * ---------------------------
 * This function converts a string representing a real number
 * into its corresponding value.  If the string is not a
 * legal floating-point number or if it contains extraneous
 * characters, StringToReal signals an error condition.
 */

double StringToReal(string s);
```