---
title: jiraGetProjectVersions
tags: [steps]
keywords: steps, versions
summary: "More about jiraGetProjectVersions step."
sidebar: jira_sidebar
permalink: jira_get_project_versions.html
folder: steps
---

## Overview

Query all versions by project id or key.

## Input

* **idOrKey** - project id or key.
* **site** - Optional, default: `JIRA_SITE` environment variable.
* **failOnError** - Optional. default: `true`.

## Output

Each step generates generic output, please refer to this [link](config.html#common-response--error-handling) for more information.

## Examples

* With default [site](config#environment-variables) from global variables.

  ```groovy
  node {
    stage('JIRA') {
      def versions = jiraGetProjectVersions idOrKey: 'TEST'
      echo versions.data.toString()
    }
  }
  ```
* `withEnv` to override the default site (or if there is not global site)

  ```groovy
  node {
    stage('JIRA') {
      withEnv(['JIRA_SITE=LOCAL']) {
        def versions = jiraGetProjectVersions idOrKey: 'TEST'
        echo versions.data.toString()
      }
    }
  }
  ```
* Without environment variables.

  ```groovy
    def versions = jiraGetProjectVersions idOrKey: 'TEST', site: 'LOCAL'
    echo versions.data.toString()
  ```

{% include links.html %}
