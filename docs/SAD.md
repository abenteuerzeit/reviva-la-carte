# System Architecture Decision for Viva La Carte

## Introduction

The goal of this project is to create an app that helps users automate their grocery shopping by providing meal plans and recipes based on user-defined nutrition data and time period. The app will allow registered users to create a social profile and interact with others, and there will be a role for professionals such as dietitians, nutritionists, chefs, and personal fitness trainers. Additionally, retailers will be able to publish products for sale on the app as ingredients for recipes.

## System Architecture

The app will use a Modular Monolithic Architecture with Domain-Centric Design and Test-Driven Development and Vertical Slices. Each module will be encapsulated as a separate, independent and autonomous .NET projects with internal and private defaults for encapsulation and an interface to expose a RESTful API.

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

