---
title: jiraGetRemoteIssueLinks
tags: [steps]
keywords: steps, remote, issuelinks
summary: "More about jiraGetRemoteIssueLinks step."
sidebar: jira_sidebar
permalink: jira_get_remote_issuelinks.html
folder: steps
---

## Overview

Query issue's remote links by global id.

## Input

* **idOrKey** - issue id or key.
* **globalId** - global application id (Optional).
* **site** - Optional, default: `JIRA_SITE` environment variable.
* **failOnError** - Optional. default: `true`.

## Output

Each step generates generic output, please refer to this [link](config.html#common-response--error-handling) for more information.

## Examples

* With default [site](config#environment-variables) from global variables.

  ```groovy
  node {
    stage('JIRA') {
      def issueLink = jiraGetRemoteIssueLinks idOrKey: 'TEST-27', globalId: '10000'
      echo issueLink.data.toString()
    }
  }
  ```
* `withEnv` to override the default site (or if there is not global site)

  ```groovy
  node {
    stage('JIRA') {
      withEnv(['JIRA_SITE=LOCAL']) {
        def issueLink = jiraGetRemoteIssueLinks idOrKey: 'TEST-27', globalId: '10000'
        echo issueLink.data.toString()
      }
    }
  }
  ```
* Without environment variables.

  ```groovy
    def issueLink = jiraGetRemoteIssueLinks idOrKey: 'TEST-27', globalId: '10000', site: 'LOCAL', failOnError: false
    echo issueLink.data.toString()
  ```

{% include links.html %}
