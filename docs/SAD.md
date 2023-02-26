# System Architecture Decision for Viva La Carte

## Introduction

This document outlines the architecture and design of a software system to create customized food lists that meet specific nutritional requirements, with the aim of providing an inexpensive tool to help individuals make positive food choices tailored to their nutritional goals. The system will be built as a modular monolith using Domain-Driven Design (DDD) and .NET Core with C#.

The goal of this project is to create an app that helps users automate their grocery shopping by providing meal plans and recipes based on user-defined nutrition data and time period. The app will allow registered users to create a social profile and interact with others, and there will be a role for professionals such as dietitians, nutritionists, chefs, and personal fitness trainers. Additionally, retailers will be able to publish products for sale on the app as ingredients for recipes.

## Problem Statement

Diet is an essential aspect of health, and people are increasingly taking notice of it. Traditionally, registered dietitians could be hired to plan meals and food choices to help reach nutritional goals, but this specialized advice is cost-prohibitive for the average person. Therefore, what is needed is an inexpensive tool that allows the average health-conscious consumer a way to make positive food choices tailored to a set of nutritional goals. This project aims to provide an algorithm that produces a list of food items that will meet specific nutritional requirements.

## Solution Overview

The proposed solution is to build a fully functional e-commerce and lifestyle web application using the core scoring algorithm implemented in our method. The application will be designed as a modular monolith that allows for user management, recipe management, sharing, meal planning, shopping, and any other features appropriate for the problems being solved.

## System Architecture

The app will use a Modular Monolithic Architecture with Domain-Centric Design and Test-Driven Development and Vertical Slices. Each module will be encapsulated as a separate, independent and autonomous .NET projects with internal and private defaults for encapsulation and an interface to expose a RESTful API.

### Modular Monolith

The application will be designed as a modular monolith to support autonomy, maintainability, and readability. All modules must run in one single process as a single application. The modules' boundaries will be set using DDD Bounded Contexts, which in this scenario maps 1:1 to domains, and DDD tactical patterns will be used to implement most modules.

## Domain-Driven Design

DDD tactical patterns will be used to implement most modules, including:

- Entity: An object that has a unique identity and can be distinguished from other objects.
- Value Object: An object that has no identity and is defined by its attributes or values.
- Aggregate: A cluster of objects that are treated as a single unit.
- Repository: An object that acts as a collection of entities.
- Domain Event: An object that represents something that has happened in the domain.
- Factory: An object that creates other objects.
- Service: An object that performs a specific operation or set of operations.
- Specification: An object that defines a set of criteria that an object must meet to be considered valid.
.NET Core Platform and C# Language

The application will be implemented in C# object-oriented language in the .NET Core framework.

## Bounded Contexts
The modules will be divided using DDD Bounded Contexts, which in this scenario maps 1:1 to domains. The following bounded contexts have been identified:

- User Management: This bounded context will handle user authentication, registration, and profile management.
- Recipe Management: This bounded context will manage recipes, including user-submitted recipes, and enable users to share recipes with others.
- Meal Planning: This bounded context will generate customized food lists that meet specific nutritional requirements based on users' inputs.
- Shopping: This bounded context will handle the shopping and delivery of the food items required for the generated meal plans.
- Pantry: This bounded context will allow users to track the foods that they currently have in their house and share their data with anyone via social media-style solutions.

## Communication Strategy

The modules' communication will be handled using synchronous communication, and REST APIs will be used for inter-module communication.

## Infrastructure Code

The infrastructure code will be designed to be more advanced, providing the following features:

- Logging
- Caching
- Exception Handling
- Health Check
- Configuration
- Security

## API

The API will serve as the entry point to the system and will mainly be implemented as a web service (REST) that accepts HTTP requests and returns HTTP responses. Its main responsibility will be to forward requests to the appropriate module. The API should be very thin with no logic for application or business. The code should only be related to processing HTTP requests and routing.

## Module Startup API

Module Startup API is an interface through which a given module can be initialized. The module should be self-contained and able to initialize itself with the appropriate configuration parameters needed for its operation. We do NOT configure a given module in the API or another module host, but we initiate its initialization at startup.

## Module API

Module API is an interface for communicating with the given module (except initialization). Such a module API can be created with the traditional approach: a list of methods (e.g., CustomerService.GetCustomer, OrderService.AddOrder). The module API should be as small as possible and expose only what is needed, making it more stable.

## Infrastructure Layer

The infrastructure layer is where the implementation of secondary components is located. Secondary adapters are responsible for communication with the external dependencies (in-process and out-of-process): databases, events bus or mediator patterns, and other modules.

## Domain Model

The Domain Model should have Persistence Ignorance and be written in Ubiquitous Language. It should be completely testable and applicable only in the Bounded Context of the domain. Each module will be different, and one may have a more complicated domain while the other may only implement CRUD operations. Therefore, the application architecture for these modules will be different, and we should respect each functionality separately.

## State of the Module

Each module must have its own state, which means that its data must be private. We don’t want to use Shared Database Pattern. This is a key attribute needed to achieve the autonomy and modularity of a module. If we want to know the state of the module or change it, we have to do it through the interface. There are no shortcuts.

## Reporting Database

We can use a separate Reporting Database and provide data in the form of separate views on the module database in a special integration scheme – only for this kind of integration. In this way, we create a concept of API on top of the database.

