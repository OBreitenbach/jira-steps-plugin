---
title: jiraGetFields
tags: [steps]
keywords: steps, fields
summary: "More about jiraGetFields step."
sidebar: jira_sidebar
permalink: jira_get_fields.html
folder: steps
---

## Overview

Query all fields in the given site.

## Input

* **site** - Optional, default: `JIRA_SITE` environment variable.
* **failOnError** - Optional. default: `true`.

## Output

Each step generates generic output, please refer to this [link](config.html#common-response--error-handling) for more information.

## Examples

* With default [site](config#environment-variables) from global variables.

  ```groovy
  node {
    stage('JIRA') {
      def fields = jiraGetFields()
      echo fields.data.toString()
    }
  }
  ```
* `withEnv` to override the default site (or if there is not global site)

  ```groovy
  node {
    stage('JIRA') {
      withEnv(['JIRA_SITE=LOCAL']) {
        def fields = jiraGetFields()
        echo fields.data.toString()
      }
    }
  }
  ```
* Without environment variables.

  ```groovy
    def fields = jiraGetFields(), site: 'LOCAL'
    echo fields.data.toString()
  ```

{% include links.html %}
