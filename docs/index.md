# CrOSSD

The Critical Open-Source Software Database (CrOSSD) is an open-source software (OSS) project
meant to assist a variety of stakeholders to make informed decisions about which OSS projects to
use, assist or support.

By collecting and continuously monitoring a growing catalogue of OSS projects according to a
selection of curated metrics, CrOSSD gives a comprehensive overview of the state of the observed
projects: How stable are they? How often are they updated? How many active contributors are
there? Do they come from different organisations? The answers to these questions (and more)
allow lay users and software developers to decide which projects they want to include in their
own codebase and which projects might benefit from their involvement and assistance as well as
funding agencies or companies to allocate funding or support to critically important OSS
projects in need of help.

## Features

- Different crawlers for retrieving data about repositories and calculating our metrics
- Web UI for presenting calculated metrics for projects
- API endpoints to query the collected projects and metrics
- Resource definitions for running components in a Kubernetes cluster
- Setup script for MicroK8s
