---
title: jiraGetProjectComponents
tags: [steps]
keywords: steps, components
summary: "More about jiraGetProjectComponents step."
sidebar: jira_sidebar
permalink: jira_get_project_components.html
folder: steps
---

## Overview

Query all components by project id or key.

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
      def components = jiraGetProjectComponents idOrKey: 'TEST'
      echo components.data.toString()
    }
  }
  ```
* `withEnv` to override the default site (or if there is not global site)

  ```groovy
  node {
    stage('JIRA') {
      withEnv(['JIRA_SITE=LOCAL']) {
        def components = jiraGetProjectComponents idOrKey: 'TEST'
        echo components.data.toString()
      }
    }
  }
  ```
* Without environment variables.

  ```groovy
    def components = jiraGetProjectComponents idOrKey: 'TEST', site: 'LOCAL'
    echo components.data.toString()
  ```

{% include links.html %}
