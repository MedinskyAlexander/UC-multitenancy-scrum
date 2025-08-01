# GitHub Issues Import - UG Casino Multitenancy

This file contains all user stories formatted as GitHub issues for easy import into the UC-multitenancy-scrum repository.

## Epic 1: Database Schema Enhancement

### Issue #1: Enhanced Domain Entity
**Labels:** `epic-1`, `database`, `foundation`, `story-points-13`

**Title:** Enhanced Domain Entity for Multitenancy

**Description:**
As a system architect  
I want to enhance the Domain entity with complete tenant metadata  
So that we can store tenant-specific configuration and branding  

**Acceptance Criteria:**
- [ ] Domain entity includes tenant_code, display_name, status fields
- [ ] Support for branding configuration (logo, colors, theme)
- [ ] Localization settings (language, currency, timezone)
- [ ] SEO metadata fields
- [ ] Operational settings (max_players, maintenance_message)
- [ ] Database migration script with backward compatibility

**Epic:** Database Schema Enhancement  
**Story Points:** 13  
**Priority:** High  

---

### Issue #2: Core Entity Tenant Context
**Labels:** `epic-1`, `database`, `foundation`, `story-points-21`

**Title:** Add domain_id to Core Entities

**Description:**
As a system architect  
I want to add domain_id foreign keys to all core entities  
So that we can establish tenant data relationships  

**Acceptance Criteria:**
- [ ] Add domain_id column to player, external_game_session, integration_transaction
- [ ] Create proper foreign key relationships
- [ ] Maintain nullable domain_id during migration phase
- [ ] Add validation triggers for data consistency
- [ ] Create composite indexes for performance

**Epic:** Database Schema Enhancement  
**Story Points:** 21  
**Priority:** High  

---

### Issue #3: Tenant Configuration Tables
**Labels:** `epic-1`, `database`, `foundation`, `story-points-13`

**Title:** Create Tenant-Specific Configuration Tables

**Description:**
As a system administrator  
I want tenant-specific property and feature flag tables  
So that I can override global configurations per tenant  

**Acceptance Criteria:**
- [ ] Create tenant_property table with domain_id, property_name, property_value
- [ ] Create tenant_feature_flag table with advanced configuration options
- [ ] Include rollout percentage and target audience capabilities
- [ ] Add proper indexes and constraints
- [ ] Support for JSON configuration data

**Epic:** Database Schema Enhancement  
**Story Points:** 13  
**Priority:** High  

---

### Issue #4: Performance Indexes
**Labels:** `epic-1`, `database`, `performance`, `story-points-8`

**Title:** Optimize Database Indexes for Tenant Queries

**Description:**
As a system architect  
I want optimized database indexes for tenant queries  
So that multi-tenant queries perform efficiently  

**Acceptance Criteria:**
- [ ] Composite indexes on (domain_id, primary_key) for all tenant tables
- [ ] Covering indexes for common query patterns
- [ ] Partial indexes for active records only
- [ ] GIN indexes for JSON configuration columns
- [ ] Performance benchmarking shows <100ms query response

**Epic:** Database Schema Enhancement  
**Story Points:** 8  
**Priority:** Medium  

---

### Issue #5: Admin Multi-Tenancy Schema
**Labels:** `epic-1`, `database`, `admin`, `story-points-13`

**Title:** Enhanced Admin User Schema for Multi-Tenancy

**Description:**
As an admin system designer  
I want enhanced admin user schema for multi-tenant access  
So that admin users can be scoped to specific domains  

**Acceptance Criteria:**
- [ ] Add is_super_admin flag to admin.user table
- [ ] Create user_domain_access table for domain assignments
- [ ] Create user_domain_role table for domain-specific roles
- [ ] Migration script for existing admin users
- [ ] Proper indexes and constraints

**Epic:** Database Schema Enhancement  
**Story Points:** 13  
**Priority:** High  

---

### Issue #6: Database Migration Scripts
**Labels:** `epic-1`, `database`, `devops`, `story-points-8`

**Title:** Reliable Database Migration Scripts

**Description:**
As a DevOps engineer  
I want reliable database migration scripts  
So that schema changes can be applied safely in production  

**Acceptance Criteria:**
- [ ] Migration scripts follow naming convention (5XX_MULTITENANCY_*.sql)
- [ ] Scripts are idempotent and can be run multiple times
- [ ] Proper rollback scripts for emergency situations
- [ ] Scripts tested on staging with production-like data
- [ ] Documentation for manual verification steps

**Epic:** Database Schema Enhancement  
**Story Points:** 8  
**Priority:** Medium  

---

### Issue #7: Data Validation Framework
**Labels:** `epic-1`, `database`, `validation`, `story-points-5`

**Title:** Tenant Data Consistency Validation

**Description:**
As a system architect  
I want validation functions to ensure tenant data consistency  
So that we can detect and prevent cross-tenant data issues  

**Acceptance Criteria:**
- [ ] PostgreSQL functions to validate tenant consistency
- [ ] Triggers to prevent cross-tenant data relationships
- [ ] Validation queries to check data integrity
- [ ] Automated consistency checking procedures
- [ ] Error reporting and alerting mechanisms

**Epic:** Database Schema Enhancement  
**Story Points:** 5  
**Priority:** Medium  

---

## Epic 2: Tenant Context Infrastructure

### Issue #8: Tenant Context Manager
**Labels:** `epic-2`, `backend`, `infrastructure`, `story-points-13`

**Title:** ThreadLocal Tenant Context Management

**Description:**
As a backend developer  
I want a TenantContext class for managing tenant information  
So that tenant context is available throughout the request lifecycle  

**Acceptance Criteria:**
- [ ] TenantContext class with ThreadLocal storage
- [ ] TenantInfo class with complete tenant metadata
- [ ] Methods for setting, getting, and clearing tenant context
- [ ] Exception handling for missing tenant context
- [ ] Thread safety and memory leak prevention

**Epic:** Tenant Context Infrastructure  
**Story Points:** 13  
**Priority:** High  

---

### Issue #9: Tenant Resolution Filter
**Labels:** `epic-2`, `backend`, `infrastructure`, `story-points-21`

**Title:** HTTP Request Tenant Resolution

**Description:**
As a backend developer  
I want a servlet filter that resolves tenant from request  
So that tenant context is automatically established for each request  

**Acceptance Criteria:**
- [ ] Filter resolves tenant from domain/host header
- [ ] Support for explicit tenant header (X-Tenant-Code)
- [ ] Handles unknown/inactive tenants appropriately
- [ ] Sets tenant context before request processing
- [ ] Clears context after request completion
- [ ] Proper error handling and logging

**Epic:** Tenant Context Infrastructure  
**Story Points:** 21  
**Priority:** High  

---

### Issue #10: Tenant Cache Service
**Labels:** `epic-2`, `backend`, `caching`, `story-points-13`

**Title:** Redis-Based Tenant Caching

**Description:**
As a backend developer  
I want Redis-based caching for tenant information  
So that tenant resolution is fast and efficient  

**Acceptance Criteria:**
- [ ] Redis caching with 30-minute TTL for tenant data
- [ ] Cache invalidation when tenant configuration changes
- [ ] Fallback to database when cache misses
- [ ] Cache warming for active tenants
- [ ] Metrics for cache hit rates (target >95%)

**Epic:** Tenant Context Infrastructure  
**Story Points:** 13  
**Priority:** High  

---

### Issue #11: Tenant Validation Framework
**Labels:** `epic-2`, `backend`, `security`, `story-points-8`

**Title:** Method-Level Tenant Validation

**Description:**
As a backend developer  
I want validation mechanisms for tenant operations  
So that cross-tenant access is prevented  

**Acceptance Criteria:**
- [ ] @TenantSecured annotation for method-level validation
- [ ] Aspect for automatic tenant context validation
- [ ] Validation of method parameters for tenant consistency
- [ ] Error handling and security logging
- [ ] Integration with Spring Security

**Epic:** Tenant Context Infrastructure  
**Story Points:** 8  
**Priority:** High  

---

### Issue #12: Error Handling and Exceptions
**Labels:** `epic-2`, `backend`, `error-handling`, `story-points-5`

**Title:** Tenant Operation Exception Handling

**Description:**
As a backend developer  
I want proper exception handling for tenant operations  
So that tenant-related errors are handled gracefully  

**Acceptance Criteria:**
- [ ] TenantContextException for missing context
- [ ] TenantNotFoundException for unknown tenants
- [ ] TenantAccessException for cross-tenant access attempts
- [ ] Proper HTTP status codes and error messages
- [ ] Logging and monitoring integration

**Epic:** Tenant Context Infrastructure  
**Story Points:** 5  
**Priority:** Medium  

---

### Issue #13: Integration Tests
**Labels:** `epic-2`, `testing`, `integration`, `story-points-8`

**Title:** Tenant Context Integration Testing

**Description:**
As a QA engineer  
I want comprehensive integration tests for tenant context  
So that tenant resolution works correctly end-to-end  

**Acceptance Criteria:**
- [ ] Tests for domain-based tenant resolution
- [ ] Tests for header-based tenant resolution
- [ ] Tests for tenant context lifecycle
- [ ] Tests for error scenarios (unknown tenant, etc.)
- [ ] Performance tests for tenant resolution speed

**Epic:** Tenant Context Infrastructure  
**Story Points:** 8  
**Priority:** Medium  

---

## Epic 3: Multi-Tenant Properties Manager

### Issue #14: Enhanced Properties Manager
**Labels:** `epic-3`, `backend`, `configuration`, `story-points-21`

**Title:** Tenant-Aware Properties Management

**Description:**
As a backend developer  
I want to enhance PropertiesManager to support tenant context  
So that properties can be overridden per tenant  

**Acceptance Criteria:**
- [ ] MultiTenantPropertiesManager extends current interface
- [ ] Property resolution: tenant-specific → global → default
- [ ] Support for all property types (string, int, boolean, JSON)
- [ ] Backward compatibility with existing code
- [ ] Comprehensive unit tests

**Epic:** Multi-Tenant Properties Manager  
**Story Points:** 21  
**Priority:** High  

---

### Issue #15: Tenant Property Repository
**Labels:** `epic-3`, `backend`, `data-layer`, `story-points-8`

**Title:** Repository Layer for Tenant Properties

**Description:**
As a backend developer  
I want repository layer for tenant properties  
So that tenant-specific properties can be stored and retrieved  

**Acceptance Criteria:**
- [ ] TenantPropertyRepository with standard CRUD operations
- [ ] Queries for finding properties by tenant and name
- [ ] Batch operations for bulk property updates
- [ ] Proper error handling and validation
- [ ] Integration with existing data layer patterns

**Epic:** Multi-Tenant Properties Manager  
**Story Points:** 8  
**Priority:** High  

---

### Issue #16: Property Caching Strategy
**Labels:** `epic-3`, `backend`, `caching`, `story-points-13`

**Title:** Redis Caching for Tenant Properties

**Description:**
As a backend developer  
I want Redis caching for tenant properties  
So that property lookups are fast and efficient  

**Acceptance Criteria:**
- [ ] 15-minute TTL for tenant property cache
- [ ] Cache keys include tenant context
- [ ] Cache invalidation on property updates
- [ ] Cache warming for frequently accessed properties
- [ ] Metrics and monitoring for cache performance

**Epic:** Multi-Tenant Properties Manager  
**Story Points:** 13  
**Priority:** High  

---

### Issue #17: Property Management APIs
**Labels:** `epic-3`, `backend`, `api`, `story-points-13`

**Title:** REST APIs for Property Management

**Description:**
As an admin user  
I want APIs to manage tenant-specific properties  
So that I can configure tenant settings  

**Acceptance Criteria:**
- [ ] REST endpoints for property CRUD operations
- [ ] Input validation and error handling
- [ ] Authorization checks for property management
- [ ] Batch operations for multiple properties
- [ ] API documentation and examples

**Epic:** Multi-Tenant Properties Manager  
**Story Points:** 13  
**Priority:** Medium  

---

### Issue #18: Property Hierarchy Resolution
**Labels:** `epic-3`, `backend`, `configuration`, `story-points-5`

**Title:** Property Inheritance Rules

**Description:**
As a system administrator  
I want clear property inheritance rules  
So that property resolution is predictable  

**Acceptance Criteria:**
- [ ] Documented property resolution hierarchy
- [ ] Tenant property overrides global property
- [ ] Global property overrides default value
- [ ] Null/empty handling for property values
- [ ] Logging for property resolution debugging

**Epic:** Multi-Tenant Properties Manager  
**Story Points:** 5  
**Priority:** Low  

---

## Epic 4: Enhanced Security Framework

### Issue #19: Tenant Security Aspect
**Labels:** `epic-4`, `backend`, `security`, `story-points-13`

**Title:** Method-Level Tenant Security Validation

**Description:**
As a security engineer  
I want method-level tenant validation  
So that cross-tenant access is automatically prevented  

**Acceptance Criteria:**
- [ ] @TenantSecured annotation for automatic validation
- [ ] AOP aspect for tenant context checking
- [ ] Validation of method parameters for tenant consistency
- [ ] Security logging for all tenant access attempts
- [ ] Integration with existing security framework

**Epic:** Enhanced Security Framework  
**Story Points:** 13  
**Priority:** High  

---

### Issue #20: Enhanced Spring Security Config
**Labels:** `epic-4`, `backend`, `security`, `story-points-21`

**Title:** Multi-Tenant Spring Security Configuration

**Description:**
As a security engineer  
I want Spring Security configuration for multi-tenancy  
So that authentication and authorization work with tenant context  

**Acceptance Criteria:**
- [ ] TenantPermissionEvaluator for hasPermission() checks
- [ ] Enhanced security context with tenant information
- [ ] Tenant-aware CORS configuration
- [ ] Support for tenant-specific authentication providers
- [ ] Admin user domain access validation

**Epic:** Enhanced Security Framework  
**Story Points:** 21  
**Priority:** High  

---

### Issue #21: Admin User Multi-Tenancy
**Labels:** `epic-4`, `backend`, `admin`, `story-points-21`

**Title:** Domain-Scoped Admin User System

**Description:**
As an admin system designer  
I want admin users to be scoped to specific domains  
So that admin access can be controlled per tenant  

**Acceptance Criteria:**
- [ ] AdminUser entity enhanced with domain access
- [ ] Super admin vs domain admin distinction
- [ ] UserDomainAccess and UserDomainRole entities
- [ ] Authentication checks for domain access
- [ ] Role assignments per domain

**Epic:** Enhanced Security Framework  
**Story Points:** 21  
**Priority:** High  

---

### Issue #22: Tenant Audit Service
**Labels:** `epic-4`, `backend`, `audit`, `story-points-13`

**Title:** Comprehensive Tenant Audit Logging

**Description:**
As a compliance officer  
I want comprehensive audit logging for tenant operations  
So that all tenant activities are tracked  

**Acceptance Criteria:**
- [ ] TenantAuditService for logging all operations
- [ ] Tenant context included in all audit records
- [ ] Integration with existing audit framework
- [ ] Configurable audit levels per tenant
- [ ] Retention policies for audit data

**Epic:** Enhanced Security Framework  
**Story Points:** 13  
**Priority:** High  

---

### Issue #23: Security Integration Tests
**Labels:** `epic-4`, `testing`, `security`, `story-points-8`

**Title:** Security Testing for Tenant Isolation

**Description:**
As a security engineer  
I want comprehensive security tests  
So that tenant isolation is validated  

**Acceptance Criteria:**
- [ ] Tests for cross-tenant access prevention
- [ ] Tests for admin user domain restrictions
- [ ] Tests for tenant-aware permission evaluation
- [ ] Penetration testing for security vulnerabilities
- [ ] Performance tests for security overhead

**Epic:** Enhanced Security Framework  
**Story Points:** 8  
**Priority:** High  

---

### Issue #24: Authentication Enhancement
**Labels:** `epic-4`, `backend`, `authentication`, `story-points-5`

**Title:** Tenant-Aware Authentication Flows

**Description:**
As a security engineer  
I want tenant-aware authentication flows  
So that login works correctly in multi-tenant context  

**Acceptance Criteria:**
- [ ] Login success/failure handlers with tenant context
- [ ] Session management with tenant information
- [ ] OAuth2 integration with tenant context
- [ ] Password reset with tenant validation
- [ ] Security headers with tenant information

**Epic:** Enhanced Security Framework  
**Story Points:** 5  
**Priority:** Medium  

---

## Instructions for GitHub Import

1. **Create Repository:**
   ```bash
   # Via GitHub CLI
   gh repo create MedinskyAlexander/UC-multitenancy-scrum --public --description "UG Casino Multitenancy - Scrum Planning"
   ```

2. **Import Issues:**
   - Copy each issue from this file
   - Create new issue in GitHub
   - Add appropriate labels and milestones
   - Assign to epic milestones

3. **Set Up Labels:**
   ```
   epic-1, epic-2, epic-3, epic-4
   database, backend, frontend, testing, security
   foundation, infrastructure, api, admin
   story-points-5, story-points-8, story-points-13, story-points-21
   ```

4. **Create Milestones:**
   - Phase 1: Foundation (Epics 1-4)
   - Phase 2: Data Layer (Epics 5-7)
   - Phase 3: Admin Interface (Epics 8-11)  
   - Phase 4: Advanced Features (Epic 12)

5. **Set Up Project Board:**
   - Columns: Backlog, Sprint Planning, In Progress, Review, Done
   - Add all issues to Backlog
   - Create epic cards linking to related issues

This structure provides a complete GitHub project setup with all user stories properly formatted for import and project management.