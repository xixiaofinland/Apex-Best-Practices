# Code Architetecture

## Purpose

I have seen many programmers proclaiming that we don't need to think about architecture when the solution is simple. However, in most of cases there is no clear border between "simple" and "complex" progjects. Projects grow from simple to complex gradually.

Here is my opinion. Unless you are 100% sure that you are creating throw-away tryout code, always bear in mind with the architecture for day one. Always.

## Seperation of Concerns

Seperation of concerns is a design pattern that was introduced by Martin Fowler, and has been well implemented and open sourced by financeforce.com.

In Andrew Fawcett's great book [Force.com Enterprise Architecture](https://www.amazon.com/Force-com-Enterprise-Architecture-Andrew-Fawcett/dp/1782172998), both the concept and the implementation are discussed in fine-grained.

I'm going to recommend you to learn seperation of concerns concpet and apply it into every single project you are working in.

Seperation of concerns comprises three layers, each of which is to be explained below.

### Service layer

Service layer is an abstract layer sitting between callers (e.g. triggers, web services, batch job, future calls, VisualForce pages, Lightning components...) and the business logic. It is a hard bundary that we, programmers, set up on purpose.

Service layer is the entry point for all execution context, it encapsulates business logic inside.

The benefits of having a service layer are:

- create a hard bundary between caller and business logic.
- allow to easily reuse the same service functions across callers as service layer is agnostic and unbiased.
- programmers know where to look for the entry point and extend functionality.
