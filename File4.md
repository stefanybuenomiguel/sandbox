[comment]: # (Welcome! This is an API documentation template. Please read the comments and delete them after use.)

# findNeedles() API Documentation
[comment]: # (Please replace the title above with the title of your API)
[comment]: # (Explain what this API does. If the API is an update of an existing product, explain briefly the main changes made to it.)
[comment]: # (Explain any dependencies and core requirements the API has.)
[comment]: # (Replace the text below with your text.)

The findNeedles() API is a Java method that prints the amount of occurrences of up to five words in a text. If more than five words are searched, it prints a message.

## Quick Start

This is a simple implementation of the code.

[comment]: # (Provide a simple implementation of the code for each feature. Replace the code below with your code. Pay attention to the markup and change ```java to the language of your code.)

```java
String[] needles = {"George", "John", "Paul", "Ringo", "Brian"};
String haystack = "The Beatles was a 1960's band. Their members were George (main guitar), John (second guitar), Paul (bass) and Ringo (drums)";
findNeedles(haystack, needles);
```

## Inputs

[comment]: # (Explain the requirements for the API call. Required and optional parameters should be specified.)

[comment]: # (Replace the code below with your parameters.)
This method requires two parameters:
`haystack`: a string of any size.
`needles`: the words te method should look for in the `haystack`. This is limited to 5 words.

### Outputs

[comment]: # (Explain what the user of the API should expect after running the code. This should cover successful cases and errors.)

[comment]: # (This is an explanation of a successful run. Replace the text below with your text.)

If `needles` length is less than or equal to five, the method logs each value along with the number of occurrences from haystack:

[comment]: # (Replace the code below with your output.)
```sh
needles[0]: number of occurrences
needles[1]: number of occurrences
needles[2]: number of occurrences
needles[3]: number of occurrences
needles[4]: number of occurrences
```

[comment]: # (This is an explanation of a failed run. Replace the text below with your text.)

If needles length is greater five, the method logs the following message:

[comment]: # (This is an explanation of a successful run. Replace the text below with your text.)

```sh 
“Too many words!”
```