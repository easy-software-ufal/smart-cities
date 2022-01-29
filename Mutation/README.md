# Mutation Operators in Java Streams
Mutation testing is nowadays a consolidated work throughout the academy and there has been some programs that use the advent of the Mutation Operators to generate in-depth statistics and measurements of how good your test suite is. Inside the Java literature there has been some advancement in this area by the work of programs as PITest and µJava, but those programs do not have any Mutation Operators to work with the **Streams API**.

In face of this, our work aims to seek solutions in terms of mutation operators that function well with the Java Streams API.
## The Investigation 🕵️‍♂️
In the beginning of the research, we thought that streams and lambdas were the same thing. So, we started by applying mutants on lambdas.

To assure that even without knowing (i.e. without documenting) PITest would not mess with lambda calls, we set sail to verify it by testing.

First, we needed to find a repository that used the target API. Using the GitHub search inside the browser, we manually found the [java-8-lambdas-exercises](https://github.com/RichardWarburton/java-8-lambdas-exercises) repository by Richard Warburton, and we tried running the PIT, but we encountered some problems in the running.

Because of this, we adapted this [repository](https://github.com/eas5/java-8-lambdas-exercises) to work with PITest and we got some interesting 
results:

![](media/pitReport.png?raw=true "PITEST REPORTS")
Looking further in this report, we were able to conclude that PITest really does not operates on lambdas (nor in streams). 

## But what if we made a manual mutant? 🤔
We tried making a manual mutant and with it we seek out to find if PITest would show some kind of report or a sign that the mutant has not been killed or was even detected.
We found a class named OrderDomain and we applied a mutation inside of it. The .mapToLong method was changed to a .mapToInt method and we ran the PITest through this mutant.

![](media/orderDomain.png?raw=true "ORDERDOMAIN")

It was **not killed** by PITest.

At a first moment, we thought this was a lambda call, but in further analysis, we concluded that it was indeed streams, because the countFeature method returns a .stream() call.
![](media/countFeature.png?raw=true "ORDERDOMAIN")
With this, we could conclude that even with exhaustive work of PITest, the risk of faults that is related to the Streams API has not been touched by the program.


# Why the mutant is NOT KILLED? 💀
Knowing for sure that the mutant has not been killed by PIT, we wanted to understand why. Reading the Java 13 [documentation](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/util/stream/package-summary.html), we could understand that we were able to swap the calls because of the category of the method.

There's two categories of calls inside the Stream API. The first one is the **intermediary** and the second one is the **terminal**.

**Intermediary** methods can be called any moment inside the stream pipeline and they do not interfere with the continuity of it. In the other way, the **terminal** ones close the pipeline, preventing any kind of interation between the stream and the rest of the program.

So, if two methods would have the same type of return and are in the same category, they could be changed without compromising the whole application.

With this in mind, we could pave the way to find new mutation operators.

# Discovering new operators 🔍

Usign the Java 13 documentation, we separated the methods by category and we thought of ways to mutate the code and make it unkillable by the test suite.

INTERMEDIARY:
* .filter
* .map
* .limit(n)
* .skip(n)
* .peek
* .mapToInt
* .mapToDouble
* .mapToLong
* .flatMap
* .flatMapToInt
* .flatMapToLong
* .flatMapToDouble
* .distinct
* .sorted
* .takeWhile




