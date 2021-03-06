---
title: jiraGetComponent
tags: [steps]
keywords: steps, component
summary: "More about jiraGetComponent step."
sidebar: jira_sidebar
permalink: jira_get_component.html
folder: steps
---

## Overview

Get component by id.

## Input

* **id** - componentId.
* **site** - Optional, default: `JIRA_SITE` environment variable.
* **failOnError** - Optional. default: `true`.

Note: For more information about input, please refer to the model objects in the [api](https://github.com/jenkinsci/jira-steps-plugin/tree/master/src/main/java/org/thoughtslive/jenkins/plugins/jira/api) package.

## Output

Each step generates generic output, please refer to this [link](config.html#common-response--error-handling) for more information.

## Examples

* With default [site](config#environment-variables) from global variables.

  ```groovy
  node {
    stage('JIRA') {
      def component = jiraGetComponent id: '10024'
      echo component.data.toString()
    }
  }
  ```
* `withEnv` to override the default site (or if there is not global site)

  ```groovy
  node {
    stage('JIRA') {
      withEnv(['JIRA_SITE=LOCAL']) {
        def component = jiraGetComponent id: '10024'
        echo component.data.toString()
      }
    }
  }
  ```
* Without environment variables.

  ```groovy
    def component = jiraGetComponent site: 'LOCAL', id: '10024', failOnError: false
    echo component.data.toString()
  ```

{% include links.html %}
