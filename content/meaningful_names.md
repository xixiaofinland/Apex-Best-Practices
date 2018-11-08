# Meaningful Names

>There are only two hard things in Computer Science: cache invalidation and naming things. -- Phil Karlton

As Apex programmers, we need to give names everywhere in software, such as variables, functions, classes, parameters, triggers etc.. We do so much of it, yet few of us consider it important.

Either good names or bad names, computers don't really care. They execute regardless how things are named. This gives programmers execuses to not put good names. After all, the program runs as expected, why to do the extra?

In addition, in many situations customers of your software do not have the proper skill to review your code. Their acceptance test is "it works". Because of this, many programmers aim for "working", instead of "being clean and tidy".

This is wrong. Why is it wrong? Simple. Because softwares are expensive to create and tend to have a long lifespan, like decades. The software are reviewed, maintained, and extended by people, including yourself! In another word, we are crafting programs first for people, then for computers. People go first, no exception. The easier it is to understand what your software is doing, the more appeciation, you get for long.

Professional programmers know the criticality of giving good names and are willing to spend time to think, pick, repick, repick (again) names to improve the readability. Do practice your skill on naming stuff from now on. it pays off soon.

"OK, I got you. But what are good names?" you may start asking. Good question! I think it has to be with features below among others:

- Intention-revealing
- No disinformation
- Consistent per concept
- With meanful context

## Intention-revealing

As the title says, the name reveals what it is.

Let's see an example with bad revealing:

```java
public static List<Integer> removeThem(List<Integer> a){
	List<Integer> b = new List<Integer>();
	for(Integer i : a){
		if( i >= 18){
			b.add(i);
		}
	}
	return b;
}
```

By reading above code, we immediately raise our hand with questions:

- What kind of things are in `List<Integer> a`?
- What is the significance of `18`?
- What does this function `removeThem` mean?

The namings do a bad job on revealing their intentions. Readers need to check where this function is called to obtain more context to figure out the answers to these questions.

The refactored code below is better.

```java
public static List<Integer> removeUnderAge(List<Integer> customerAges){
	private static final LEGAL_AGE = 18;
	List<Integer>  legalAgedCustomers = new List<Integer>();
	for(Integer age : customerAges){
		if( age >= LEGAL_AGE){
			legalAgedCustomers.add(age);
		}
	}
	return legalAgedCustomers;
}
```

A even better solution is to have a `Customer` class with the `age` integer property.

## No disinformation

If the thing under the name is not something or does not do something, do NOT put that disinformation in, refactoring it immediately.

2 examples with disinformation:

```java
//a map or a list?
Map<Id, Account> myAccountList;
```

```java
//singlar or plural?
List<Version__c> versionLang = [SELECT ID from Version__c LIMIT 10];
```

```java
//WTF, Ids or objects?
Set<Id> myObjects = new Set<Id>();
```

Disinformation drives people misunderstand the code. But nobody makes names perfectly in the first go all the time, and there is no need to strive for that either.

What we do is we create names, implement the logic, read it back, refactoring.

## Consistant per concept

Same concept should always use the same keyword. For instance, pick one from `fetch`, `get`, and `retrieve`, stick to it in the entire software.

## With meaningful context

Many names are too broad, it'd be better to restrict and show the context to the readers.

```java
//better use customerAge to add the context?
Integer age;
```

Though better that `a`, `Age` is still a very general naming in the above example. Age for what? it doesn't tell. `customerAge` instead windows down the scope and specifies the domain.

## Final words

Choose a descrptive, to-the-point, and concise name is difficult, especially for non-native English speakers. But this is more of an attitude rather than technical issue. We all see English native prgorammers with aweful naming skills.

Don't leave a reading mess for others, this is unprofessional. Think about how much you are appreciated when readers intepret your intention in the software like reading an English articles, with a big smile on the face.

To learn more about good namings, go and read Robert C. Martin's book [Clean Code](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882).


