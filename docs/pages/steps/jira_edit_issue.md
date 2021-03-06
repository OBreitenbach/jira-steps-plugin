---
title: jiraEditIssue
tags: [steps]
keywords: steps, issue
summary: "More about jiraEditIssue step."
sidebar: jira_sidebar
permalink: jira_edit_issue.html
folder: steps
---

## Overview

Updates an existing issue based on given input, which should have some minimal information on that object.

## Input

* **idOrKey** - issue id or key.
* **issue** - issue to be created.
* **site** - Optional, default: `JIRA_SITE` environment variable.
* **failOnError** - Optional. default: `true`.

**Note**: Since 1.2.0 newIssue and editIssue steps supports all the fields that any jira instance supports including custom fields.

## Output

Each step generates generic output, please refer to this [link](config.html#common-response--error-handling) for more information.

## Examples

* With default [site](config#environment-variables) from global variables.

  ```groovy
  node {
    stage('JIRA') {
      # Look at IssueInput class for more information.
      def testIssue = [fields: [ // id or key must present for project.
                                 project: [id: '10000'],
                                 summary: 'New JIRA Created from Jenkins.',
                                 description: 'New JIRA Created from Jenkins.',
                                 customfield_1000: 'customValue',
                                 // id or name must present for issuetype.
                                 issuetype: [id: '3']]]

      response = jiraEditIssue idOrKey: 'TEST-01', issue: testIssue

      echo response.successful.toString()
      echo response.data.toString()
    }
  }
  ```

* `withEnv` to override the default site (or if there is not global site)

  ```groovy
  node {
    stage('JIRA') {
      withEnv(['JIRA_SITE=LOCAL']) {
        # Look at IssueInput class for more information.
        def testIssue = [fields: [ project: [id: '10000'],
                                   summary: 'New JIRA Created from Jenkins.',
                                   description: 'New JIRA Created from Jenkins.',
                                   issuetype: [id: '3']]]

        response = jiraEditIssue idOrKey: 'TEST-01', issue: testIssue

        echo response.successful.toString()
        echo response.data.toString()
      }
    }
  }
  ```
* Without environment variables.

  ```groovy
  # Look at IssueInput class for more information.
  def testIssue = [fields: [ project: [id: '10000'],
                             summary: 'New JIRA Created from Jenkins.',
                             description: 'New JIRA Created from Jenkins.',
                             issuetype: [id: '3']]]

  response = jiraEditIssue idOrKey: 'TEST-01', issue: testIssue, site: 'LOCAL'

  echo response.successful.toString()
  echo response.data.toString()
  ```

{% include links.html %}
