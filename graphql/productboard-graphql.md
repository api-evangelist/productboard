# Productboard GraphQL Schema

## Overview

This document describes a conceptual GraphQL schema for the Productboard product management platform. Productboard provides a Public REST API at https://api.productboard.com (v1 and v2), and this schema represents the platform's core domain objects — features, components, objectives, roadmaps, insights, customer feedback, integrations, and workspace configuration — modeled as a GraphQL type system.

Official documentation: https://developer.productboard.com/

## Schema Source

This schema was derived from the Productboard Public API documentation and REST endpoint surface. Productboard does not currently publish an official GraphQL endpoint; this schema is a conceptual representation intended to capture the full domain model for tooling, search, and integration purposes.

## Core Domains

### Features

Features are the primary unit of work in Productboard. They represent ideas, improvements, or tasks that product teams want to build. Features have a status lifecycle (new, in-progress, released, etc.), belong to components and product areas, and can be linked to customer notes, objectives, and releases.

Key types: `Feature`, `FeatureDetails`, `FeatureStatus`, `FeatureType`, `FeatureOwner`, `FeatureTag`, `FeatureComponent`, `FeatureObjective`, `FeatureNote`

### Components and Product Areas

Components represent logical groupings of features within a product. Product areas provide a hierarchical structure for organizing components and features. The `ComponentHierarchy` type captures parent-child relationships.

Key types: `Component`, `ComponentDetails`, `ProductArea`, `ComponentHierarchy`

### Objectives and OKRs

Objectives connect features to strategic goals. Key results track measurable outcomes tied to each objective. Teams use this layer to ensure the features being built actually advance company-level priorities.

Key types: `Objective`, `ObjectiveDetails`, `OKR`, `KeyResult`, `KeyResultValue`

### Insights and Customer Feedback

Notes capture raw customer feedback. Insights are synthesized conclusions drawn from multiple notes. Highlights and sentiment annotations help teams process qualitative signals at scale.

Key types: `Insight`, `InsightDetails`, `InsightHighlight`, `InsightSentiment`, `NoteTag`, `NoteTopic`, `UserFeedback`, `CustomerRequest`, `PortalSubmission`, `PortalNote`

### Roadmaps

Roadmaps provide a visual, time-oriented view of features and releases. Columns organize features by time period or category. Roadmap-specific prioritization links features to their display order and swimlane.

Key types: `Roadmap`, `RoadmapDetails`, `RoadmapColumn`, `RoadmapFeature`, `RoadmapPriority`, `Column`, `ColumnDetails`, `ColumnType`

### Releases

Releases group features scheduled for a particular delivery window. Release groups aggregate multiple releases into a higher-level milestone.

Key types: `Release`, `ReleaseDetails`, `ReleaseGroup`

### Workspace and Users

A workspace is the top-level organizational container in Productboard. Segments allow teams to slice customer data by attributes such as plan, company size, or industry.

Key types: `Workspace`, `WorkspaceDetails`, `Segment`, `SegmentDetails`

### Companies and Customers

Companies represent B2B accounts. Customer requests link company contacts to specific feature requests, enabling teams to quantify demand by account size or ARR.

Key types: `CustomerCompany`, `CustomerRequest`

### Integrations

Productboard connects to Jira, Asana, Zendesk, Salesforce, and other tools via push integrations. Each integration type captures configuration and sync state.

Key types: `PushIntegration`, `JiraIntegration`, `AsanaIntegration`, `ZendeskIntegration`, `SalesforceIntegration`

### Authentication

API keys and tokens authenticate requests. Webhooks subscribe to platform events and deliver payloads to external endpoints.

Key types: `APIKey`, `Token`, `Webhook`

## Authentication

Authentication uses a Bearer token (Public API Access Token) obtained from the Productboard workspace settings, or OAuth2 for multi-tenant integrations.

Reference: https://developer.productboard.com/reference/authentication

## Named Types

The schema defines 63 named GraphQL types covering the full Productboard domain model. See `productboard-schema.graphql` for the complete type definitions.
