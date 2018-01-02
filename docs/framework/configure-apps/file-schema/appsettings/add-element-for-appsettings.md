---
title: "&lt;追加&gt;要素&lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d080a7c63ddda0577e66d2e7ddd433c7fd5fdbd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="f160f-102">\<追加 > 要素を\<appSettings ></span><span class="sxs-lookup"><span data-stu-id="f160f-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="f160f-103">カスタム アプリケーション設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="f160f-103">Adds a custom application setting.</span></span>

<span data-ttu-id="f160f-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f160f-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="f160f-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f160f-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="f160f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<追加 >**</span><span class="sxs-lookup"><span data-stu-id="f160f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f160f-107">構文</span><span class="sxs-lookup"><span data-stu-id="f160f-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="f160f-108">属性</span><span class="sxs-lookup"><span data-stu-id="f160f-108">Attributes</span></span>

|           | <span data-ttu-id="f160f-109">説明</span><span class="sxs-lookup"><span data-stu-id="f160f-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f160f-110">**key**</span><span class="sxs-lookup"><span data-stu-id="f160f-110">**key**</span></span>   | <span data-ttu-id="f160f-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="f160f-111">Required attribute.</span></span><br><br><span data-ttu-id="f160f-112">追加するキーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f160f-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="f160f-113">**value**</span><span class="sxs-lookup"><span data-stu-id="f160f-113">**value**</span></span> | <span data-ttu-id="f160f-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="f160f-114">Required attribute.</span></span><br><br><span data-ttu-id="f160f-115">追加するキーの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="f160f-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f160f-116">親要素</span><span class="sxs-lookup"><span data-stu-id="f160f-116">Parent element</span></span>

|     | <span data-ttu-id="f160f-117">説明</span><span class="sxs-lookup"><span data-stu-id="f160f-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f160f-118">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="f160f-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="f160f-119">ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f160f-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f160f-120">子要素</span><span class="sxs-lookup"><span data-stu-id="f160f-120">Child elements</span></span>

<span data-ttu-id="f160f-121">なし</span><span class="sxs-lookup"><span data-stu-id="f160f-121">None</span></span>

## <a name="example"></a><span data-ttu-id="f160f-122">例</span><span class="sxs-lookup"><span data-stu-id="f160f-122">Example</span></span>

<span data-ttu-id="f160f-123">次の例では、アプリケーションの名前のカスタム構成設定を追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f160f-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="f160f-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f160f-124">See also</span></span>

[<span data-ttu-id="f160f-125">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="f160f-125">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
