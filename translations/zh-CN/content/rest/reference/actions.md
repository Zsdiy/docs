---
title: 操作
intro: '通过 Actions API，您可以管理和控制组织或仓库的 {% data variables.product.prodname_actions %}。'
redirect_from:
  - /v3/actions
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
topics:
  - API
miniTocMaxHeadingLevel: 3
---


{% data variables.product.prodname_actions %} API 允许您使用 REST API 来管理 {% data variables.product.prodname_actions %}。 {% data reusables.actions.actions-authentication %} {% data variables.product.prodname_github_apps %} 需要在每个端点中提及的权限。 更多信息请参阅“[{% data variables.product.prodname_actions %} 文档](/actions)”。

{% for operation in currentRestOperations %}
  {% unless operation.subcategory %}{% include rest_operation %}{% endunless %}
{% endfor %}

## 构件

构件 API 允许您下载、删除和检索有关工作流程构件的信息。 {% data reusables.actions.about-artifacts %}更多信息请参阅“[使用构件持久化工作流程](/actions/automating-your-workflow-with-github-actions/persisting-workflow-data-using-artifacts)”。

{% data reusables.actions.actions-authentication %} {% data reusables.actions.actions-app-actions-permissions-api %}

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'artifacts' %}{% include rest_operation %}{% endif %}
{% endfor %}

{% ifversion fpt or ghes > 2.22 or ghae or ghec %}
## 权限

Permissions API 允许您为允许哪些企业、组织和存储库运行 {% data variables.product.prodname_actions %} 以及允许运行哪些操作设置权限。{% ifversion fpt or ghec or ghes %} 更多信息请参阅“[使用限制、计费和管理](/actions/reference/usage-limits-billing-and-administration#disabling-or-limiting-github-actions-for-your-repository-or-organization)”。{% endif %}

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'permissions' %}{% include rest_operation %}{% endif %}
{% endfor %}
{% endif %}

## 密码

密码 API 允许您创建、更新、删除和检索有关加密密码的信息。 {% data reusables.actions.about-secrets %}更多信息请参阅“[创建和使用加密密码](/actions/automating-your-workflow-with-github-actions/creating-and-using-encrypted-secrets)”。

{% data reusables.actions.actions-authentication %} {% data variables.product.prodname_github_apps %} 必须具有`密码`权限才可使用此 API。 经过身份验证的用户必须对仓库具有协作者权限才可创建、更新或读取密码。

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'secrets' %}{% include rest_operation %}{% endif %}
{% endfor %}

## 自托管运行器

{% data reusables.actions.ae-self-hosted-runners-notice %}

自托管运行器 API 允许您注册、查看和删除自托管的运行器。 {% data reusables.actions.about-self-hosted-runners %} 更多信息请参阅“[托管您自己的运行器](/actions/hosting-your-own-runners)”。

{% data reusables.actions.actions-authentication %} {% data variables.product.prodname_github_apps %} 必须对仓库具有`管理`权限，或者对组织具有 `organization_self_hosted_runners` 权限。 经过身份验证的用户必须具有对存储库或组织的管理员访问权限或者企业的 `manage_runners:enterprise` 作用域才能使用此 API。

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'self-hosted-runners' %}{% include rest_operation %}{% endif %}
{% endfor %}

## 自托管运行器组

{% data reusables.actions.ae-self-hosted-runners-notice %}

自托管运行器组 API 允许您管理自托运行器组。 更多信息请参阅“[使用组管理对自托管运行器的访问](/actions/hosting-your-own-runners/managing-access-to-self-hosted-runners-using-groups)”。

{% data reusables.actions.actions-authentication %} {% data variables.product.prodname_github_apps %} 必须对仓库具有`管理`权限，或者对组织具有 `organization_self_hosted_runners` 权限。 经过身份验证的用户必须具有对存储库或组织的管理员访问权限或者企业的 `manage_runners:enterprise` 作用域才能使用此 API。

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'self-hosted-runner-groups' %}{% include rest_operation %}{% endif %}
{% endfor %}

## 工作流程

工作流程 API 允许您查看仓库的工作流程。 {% data reusables.actions.about-workflows %} 更多信息请参阅“[使用 GitHub Actions 自动化工作流程](/actions/automating-your-workflow-with-github-actions)”。

{% data reusables.actions.actions-authentication %} {% data reusables.actions.actions-app-actions-permissions-api %}

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'workflows' %}{% include rest_operation %}{% endif %}
{% endfor %}

## 工作流程作业

工作流程作业 API 允许您查看日志和工作流程作业。 {% data reusables.actions.about-workflow-jobs %} 更多信息请参阅“[GitHub Actions 的工作流程语法](/actions/automating-your-workflow-with-github-actions/workflow-syntax-for-github-actions)”。

{% data reusables.actions.actions-authentication %} {% data reusables.actions.actions-app-actions-permissions-api %}

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'workflow-jobs' %}{% include rest_operation %}{% endif %}
{% endfor %}

## 工作流程运行

工作流程运行 API 允许您查看、重新运行、取消和查看工作流程运行的日志。 {% data reusables.actions.about-workflow-runs %} 更多信息请参阅“[管理工作流程运行](/actions/automating-your-workflow-with-github-actions/managing-a-workflow-run)”。

{% data reusables.actions.actions-authentication %} {% data reusables.actions.actions-app-actions-permissions-api %}

{% for operation in currentRestOperations %}
  {% if operation.subcategory == 'workflow-runs' %}{% include rest_operation %}{% endif %}
{% endfor %}
