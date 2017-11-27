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
ms.openlocfilehash: 2b00af6f7d735d5db8fd746205ba225253cad133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="210b3-102">\<追加 > 要素を\<appSettings ></span><span class="sxs-lookup"><span data-stu-id="210b3-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="210b3-103">カスタム アプリケーション設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="210b3-103">Adds a custom application setting.</span></span>

<span data-ttu-id="210b3-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="210b3-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="210b3-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="210b3-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="210b3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<追加 >**</span><span class="sxs-lookup"><span data-stu-id="210b3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="210b3-107">構文</span><span class="sxs-lookup"><span data-stu-id="210b3-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="210b3-108">属性</span><span class="sxs-lookup"><span data-stu-id="210b3-108">Attributes</span></span>

|           | <span data-ttu-id="210b3-109">説明</span><span class="sxs-lookup"><span data-stu-id="210b3-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="210b3-110">**key**</span><span class="sxs-lookup"><span data-stu-id="210b3-110">**key**</span></span>   | <span data-ttu-id="210b3-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="210b3-111">Required attribute.</span></span><br><br><span data-ttu-id="210b3-112">追加するキーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="210b3-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="210b3-113">**value**</span><span class="sxs-lookup"><span data-stu-id="210b3-113">**value**</span></span> | <span data-ttu-id="210b3-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="210b3-114">Required attribute.</span></span><br><br><span data-ttu-id="210b3-115">追加するキーの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="210b3-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="210b3-116">親要素</span><span class="sxs-lookup"><span data-stu-id="210b3-116">Parent element</span></span>

|     | <span data-ttu-id="210b3-117">説明</span><span class="sxs-lookup"><span data-stu-id="210b3-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="210b3-118">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="210b3-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="210b3-119">ファイル パス、XML Web サービス URL、またはアプリケーションのその他のカスタム構成情報など、カスタム アプリケーションの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="210b3-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="210b3-120">子要素</span><span class="sxs-lookup"><span data-stu-id="210b3-120">Child elements</span></span>

<span data-ttu-id="210b3-121">なし</span><span class="sxs-lookup"><span data-stu-id="210b3-121">None</span></span>

## <a name="example"></a><span data-ttu-id="210b3-122">例</span><span class="sxs-lookup"><span data-stu-id="210b3-122">Example</span></span>

<span data-ttu-id="210b3-123">次の例では、アプリケーションの名前のカスタム構成設定を追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="210b3-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="210b3-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="210b3-124">See also</span></span>

[<span data-ttu-id="210b3-125">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="210b3-125">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
