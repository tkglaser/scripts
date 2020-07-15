# Podcast script 001

## Abstract

* TODO: What is the podcast series about?

## Introduction

* David:
  * TODO
* Thomas:
  * Thomas is a Freelance Full Stack Engineer and Architect.
    He has worked for companies like Symantec, Actian and McLaren
    to name just a few. He's been writing Software since 2004 and is
    specialised on web technologies since 2011, primarily focused on
    the Microsoft Stack and Angular.
    In his spare time he enjoys reading, walking and travelling.

## Topic

* How architecting a web application has changed in the last 10 years.

## Content

* Let's look at example requirements:
  * ToDo app, items can be Created/Deleted/Ticked Off
  * Web App
  * All data behind a login
  * Non functional
    * Minimum hosting costs
    * Fully secure
    * Good performance
    * No scaling limits, able to scale up to millions of users

* Before the cloud?
  * SQL
  * Server-side code like ASP/MVC
  * Login: Hashed password / ASP Identity
  * Scaling? => Discuss

* Today (discuss for every point WHY this decision has been made)
  * This is a good case for an SPA, for example Angular
  * If you build a SPA, you need an API, we'll come to that
  * Use an external IDP like Azure Active Directory B2C and OpenID Connect
  * Database: Use NoSql like DynamoDB or CosmosDB (no scaling limits like SQL)
  * Typically the SPA will access the NoSql cluster DIRECTLY using a resource token (explain)

* How would one implement this in Azure for example?
* How much would it cost?