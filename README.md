# Count Consonants in String Iterative and Recursive

        package main

        import (
            "fmt"
            "unicode"
        )

        // New type for checking letter is vowel
        type Vowels []rune

        // All vowels
        var vowels = Vowels{'a', 'e', 'i', 'o', 'u'}

        // The method for checkin; like 'in' in python
        func (v Vowels) Has(a rune) bool {
            for _, b := range v {
                if b == a {
                    return true
                }
            }
            return false
        }

        // Iterative function for counting of consonants
        func iterativeCountConsonants(inputStr string) int {
            str := []rune(inputStr)
            conCount := 0
            for i := 0; i < len(str); i++ {
                if !vowels.Has(unicode.ToLower(str[i])) && unicode.IsLetter(str[i]) {
                    conCount += 1
                }
            }
            return conCount
        }

        // Recursive function for counting of consonants
        func recursiveCountConsonants(inputStr string) int {
            if inputStr == "" {
                return 0
            }

            str := []rune(inputStr)

            if !vowels.Has(unicode.ToLower(str[0])) && unicode.IsLetter(str[0]) {
                return 1 + recursiveCountConsonants(string(str[1:]))
            } else {
                return recursiveCountConsonants(string(str[1:]))
            }
        }

        // Testing
        func main() {
            inputStr := "Lekan"
            fmt.Println(inputStr)
            fmt.Println(iterativeCountConsonants(inputStr))
            fmt.Println(recursiveCountConsonants(inputStr))
            inputStr = "Lekan ProGraMinG"
            fmt.Println(inputStr)
            fmt.Println(iterativeCountConsonants(inputStr))
            fmt.Println(recursiveCountConsonants(inputStr))
        }
