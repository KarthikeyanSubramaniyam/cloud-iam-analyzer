# AWS IAM Effective Permissions & Least-Privilege Analyzer

<p align="center">
  <img src="https://img.shields.io/badge/Security-Defensive_Auditor-blue?style=flat" alt="Type">
  <img src="https://img.shields.io/badge/Status-Architectural_Showcase-success?style=flat" alt="Status">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white" alt="Python">
</p>

> 🔒 **Technical Showcase & Architecture Specification**  
> *This repository provides public architectural documentation, system specifications, and implementation summaries. Full production source code, internal test suites, and proprietary algorithms are maintained in a secure private repository.*

---

## 📌 Executive Summary

**Category**: Identity & Access Management (IAM)  
**Tech Stack**: `Python 3.10+ · AWS IAM Policy Evaluation Engine · Least Privilege · SCPs`  

Comprehensive IAM analyzer evaluating permission boundaries, service control policies (SCPs), and effective access rights to enforce Least Privilege.

---

## 🎯 The Problem It Solves

In multi-account AWS environments, determining an identity's true effective permissions requires resolving Service Control Policies (SCPs), Permission Boundaries, Session Policies, and Resource Policies simultaneously.

---

## ⚙️ How the Engine Works

1. **Multi-Layer Policy Resolution**: Parses Organizational SCPs, identity-based policies, role trust policies, and boundary statements.
2. **Effective Access Evaluation**: Calculates the intersection of all permission layers to determine true executable API actions.
3. **Unused & Excessive Privilege Flagging**: Compares granted permissions against historical CloudTrail activity to identify dormant privileges.
4. **High-Risk Action Flagging**: Flags sensitive actions (`s3:DeleteBucket`, `kms:ScheduleKeyDeletion`, `iam:Delete*`) granted without explicit MFA conditions.
5. **Policy Optimization**: Generates stripped-down, least-privilege replacement policies tailored to actual usage.

---

## 🚀 Key Capabilities

- Resolves multi-layer policy intersections (SCPs + Boundaries + Identity)
- Highlights dormant, high-risk permissions ready for revocation
- Identifies cross-account role assumption vulnerabilities
- Generates right-sized IAM policies based on actual access needs

---

## 🏗️ System Data Flow & Architecture

```
+-----------------------------------+
|  Target Input / Configuration    |
|  (JSON Snapshots / Policies)      |
+-----------------+-----------------+
                  |
                  v
+-----------------------------------+
|  1. Schema Normalization Engine   |
|  Validates types & formats        |
+-----------------+-----------------+
                  |
                  v
+-----------------------------------+
|  2. Core Analytical Pipeline      |
|  Heuristic rule evaluation,       |
|  invariant checks & drift diffs   |
+-----------------+-----------------+
                  |
                  v
+-----------------------------------+
|  3. Risk Classification           |
|  Assigns severity: INFO / HIGH    |
+-----------------+-----------------+
                  |
                  v
+-----------------------------------+
|  4. Structured Findings & Report  |
|  Root cause, evidence &           |
|  actionable remediation steps     |
+-----------------------------------+
```

---

## 📄 Findings Output Structure

The engine generates structured, machine-parsable JSON reports adhering to this standard audit schema:

```json
{
  "results": [
    {
      "resource": "resource-identifier",
      "severity": "HIGH",
      "check": "CHECK_IDENTIFIER",
      "detail": "Descriptive analysis of the identified security posture issue.",
      "remediation": "Actionable step-by-step guidance to restore compliant state.",
      "evidence": {
        "observed_field": "value",
        "required_policy": "enforced_policy"
      }
    }
  ],
  "count": 1,
  "scope": "Comprehensive defensive security audit"
}
```

---

## 🔒 Source Code & Enterprise Inquiries

To protect proprietary intellectual property and client operational security:
* **Public Repository**: Contains comprehensive architecture specifications, schemas, and design overviews.
* **Private Repository**: Contains the complete production implementation, continuous integration pipelines, and full regression test suites.

For architectural questions or enterprise inquiries, connect via [LinkedIn](https://www.linkedin.com/in/karthikeyansubramaniam04/) or visit the [Portfolio Site](https://karthikeyansubramaniyam.github.io).
