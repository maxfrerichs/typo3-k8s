# Kubernetes deployment for TYPO3 [WIP]

## About
This is a simple example Kubernetes-based deployment for TYPO3 with MariaDB. WARNING: Do not use this in any kind of production enviroment

## Project goals
Explore possible advantages and disadvantages of a Kubernetes-based deployment of TYPO3.

## How-to
* Pull this repository
* cd typo3-k8s/
* Build and tag image like this (docker build t3docker -t typo3)
* Run kubectl apply -k ./
* Wait a moment...
* :rocket: Voilà! (or not)
