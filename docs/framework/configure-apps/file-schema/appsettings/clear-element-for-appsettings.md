---
title: "&lt;オフ&gt;要素&lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ac1e9a86d0c3e1bb1f23b753fd9867effef03ce5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="9ca0b-102">\<オフ > 要素を\<appSettings ></span><span class="sxs-lookup"><span data-stu-id="9ca0b-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="9ca0b-103">カスタム アプリケーションの設定を消去します。</span><span class="sxs-lookup"><span data-stu-id="9ca0b-103">Clears custom application settings.</span></span>

<span data-ttu-id="9ca0b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="9ca0b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="9ca0b-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="9ca0b-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="9ca0b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<オフ >**</span><span class="sxs-lookup"><span data-stu-id="9ca0b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9ca0b-107">構文</span><span class="sxs-lookup"><span data-stu-id="9ca0b-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="9ca0b-108">属性</span><span class="sxs-lookup"><span data-stu-id="9ca0b-108">Attributes</span></span>

<span data-ttu-id="9ca0b-109">なし</span><span class="sxs-lookup"><span data-stu-id="9ca0b-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="9ca0b-110">親要素</span><span class="sxs-lookup"><span data-stu-id="9ca0b-110">Parent element</span></span>

|     | <span data-ttu-id="9ca0b-111">説明</span><span class="sxs-lookup"><span data-stu-id="9ca0b-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9ca0b-112">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="9ca0b-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="9ca0b-113">ファイルのパス、XML Web サービス Url、またはその他のカスタム アプリケーションの構成情報など、カスタム アプリケーションの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9ca0b-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9ca0b-114">子要素</span><span class="sxs-lookup"><span data-stu-id="9ca0b-114">Child elements</span></span>

<span data-ttu-id="9ca0b-115">なし</span><span class="sxs-lookup"><span data-stu-id="9ca0b-115">None</span></span>

## <a name="example"></a><span data-ttu-id="9ca0b-116">例</span><span class="sxs-lookup"><span data-stu-id="9ca0b-116">Example</span></span>

<span data-ttu-id="9ca0b-117">次の例では、カスタム構成設定を消去する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9ca0b-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="9ca0b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ca0b-118">See also</span></span>

[<span data-ttu-id="9ca0b-119">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="9ca0b-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
