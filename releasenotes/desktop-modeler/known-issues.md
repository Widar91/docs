---
title: "Known Issues"
space: "Release Notes"
toc-level: 1
category: "Desktop Modeler"
---

<div class="alert alert-info">{% markdown %}

This document describes known issues starting with Mendix version 7.0.2. For known issues in earlier Mendix versions, see the [Desktop Modeler release notes](index).

{% endmarkdown %}</div>

## 7.3

For details on this release, see [7.3 release notes](7.3).

### 7.3.0<a name="KI730"></a>

* When you have a conditionally visible container that contains a conditionally visible widget, the widget is not always initialized properly.

## 7.2

For details on this release, see [7.2 release notes](7.2).

### 7.2.0<a name="KI720"></a>

* Changes for reference set members that are read-only for the user are not correctly serialized from the server to the client (browser). This can lead to an `IllegalArgumentException` with this message: “Global identifier should be a number.” (Ticket 52317)
    * Fixed in [7.3.0](7.3#RN730).

## 7.1

For details on this release, see [7.1 release notes](7.1).

### 7.1.0<a name="KI710"></a>

#### Advanced conditional visibility/editability known issues

* Currently you can configure expression-based conditional visibilitity/editability on any element. But this will be ignored on elements outside of a data container: on data views, list views, and template grids. Note that you still cannot configure attribute-based conditions on such elements.

#### Other known issues

* The offline functionality for mobile apps is broken.
    * Fixed in [7.1.1](7.1#RN711).

## 7.0 

For details on this release, see [7.0 release notes](7.0).

### 7.0.2<a name="KI702"></a>

#### Stateless runtime known issues

* The `RuntimeStatistics` page in the administration module is broken, as the `System.Statistics` entity is not created anymore. This was used for an earlier version of horizontal scalability and has become obsolete. In a future version, the `System.Statistics` entity will be removed from the `System` module, and the `Administration.RuntimeStatistics` page and the `Administration.ViewStatistics` microflow will be removed automatically from the `Administration` module.
* Upgrading an anonymous user to a signed-in user does not transfer the session state yet.
* Pages showing objects that contain accessible hashed string attributes with empty values are broken. You cannot call a microflow or open a different page. Please note that this is not easy to model, so you might not encounter this issue.
* Hybrid apps will not start if they contain a reporting widget.
* Offline hybrid apps are not supported yet.

#### Other known issues

* Some users working on Windows 7 and 8.1 might experience issues during installation of the .NET Framework bundled with the Modeler installer. Installing .NET Framework from the [official Microsoft website](https://www.microsoft.com/en-us/download/details.aspx?id=53345) resolves these issues.
* Upgrading an anonymous user to a signed-in user does not transfer the state yet.
* In calculated attribute microflows, objects associated with `$currentUser` or `$currentSession` cannot be retrieved in the calculated microflow if the association has not been committed to the database.
* When triggering multiple microflows from the client concurrently that commit the same new object, you might get a “duplicate key violation” exception. This is due to a race condition. Triggering the microflow again should not raise an exception again. You can avoid this issue by configuring a blocking progress bar for the button or by using the **Disabled during action** property.
* In certain situations, OnChange microflows may not reflect changes done in the UI. Instead, an older version of the object will be used.
* Disallowing concurrent execution of microflows in a multi-node cluster environment does not work. The feature still works on a single node.
