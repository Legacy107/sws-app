# Overview

This is an application to view a list of companies' stock prices. The application is built using NestJS, TypeORM and GraphQL for the backend and NextJS for the frontend.

The backend can be accessed via the [GraphQL playground](http://4.157.74.152:8000/graphql) and the frontend can be access via [https://sws-frontend.vercel.app/](https://sws-frontend.vercel.app/)

The instructions for running the application locally can be found in the README files in the backend and frontend directories.

# Improvements

## Caching for Get Many Companies

Since the workload is read-heavy, caching can be implemented to improve the performance of fetching multiple companies. By storing the results of frequently requested data in a cache (e.g., Redis), we can reduce the load on the database and speed up response times.

## Redundant Last Price Column

Adding a redundant column for the last price in the companies table can improve the performance of queries that need the latest stock price. Instead of scanning the entire price table to find the last price, the application can directly retrieve it from the companies table.

## Pre-calculate and Cache Price Fluctuation

Since the price fluctuation is updated only once per day, it is more efficient to pre-calculate this value and store it in a cache or an additional table. This approach avoids recalculating the fluctuation every time it is requested, thus improving the application's performance.

## CI/CD Pipeline

If not for the time constraint, a CI/CD pipeline would have been setup to automate the deployment process for the backend application. For now, the deployment is done by building the docker image and manully deploying it to Azure. In addtion, a CI pipeline can be setup to automatically build and run tests using GitHub Actions.