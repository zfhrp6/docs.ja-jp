---
title: "&lt;configSections&gt;要素&lt;構成&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 145a2a5cc23758c9fd2211c2da7fee0bbd736f0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="693a1-102">\<configSections > 要素を\<構成 ></span><span class="sxs-lookup"><span data-stu-id="693a1-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="693a1-103">構成セクションと名前空間宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="693a1-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="693a1-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="693a1-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="693a1-105">&nbsp;&nbsp;**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="693a1-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="693a1-106">属性</span><span class="sxs-lookup"><span data-stu-id="693a1-106">Attributes</span></span>

<span data-ttu-id="693a1-107">なし</span><span class="sxs-lookup"><span data-stu-id="693a1-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="693a1-108">親要素</span><span class="sxs-lookup"><span data-stu-id="693a1-108">Parent element</span></span>

|     | <span data-ttu-id="693a1-109">説明</span><span class="sxs-lookup"><span data-stu-id="693a1-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="693a1-110">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="693a1-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="693a1-111">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="693a1-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="693a1-112">子要素</span><span class="sxs-lookup"><span data-stu-id="693a1-112">Child elements</span></span>

|     | <span data-ttu-id="693a1-113">説明</span><span class="sxs-lookup"><span data-stu-id="693a1-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="693a1-114">**\<セクション >**</span><span class="sxs-lookup"><span data-stu-id="693a1-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="693a1-115">構成セクションの宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="693a1-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="693a1-116">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="693a1-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="693a1-117">構成セクションの名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="693a1-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="693a1-118">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="693a1-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="693a1-119">定義済みのセクション、またはセクション グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="693a1-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="693a1-120">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="693a1-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="693a1-121">以前に定義されたセクションおよびセクション グループのすべてをクリアします。</span><span class="sxs-lookup"><span data-stu-id="693a1-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="693a1-122">コメント</span><span class="sxs-lookup"><span data-stu-id="693a1-122">Remarks</span></span>

<span data-ttu-id="693a1-123">この要素は、構成ファイルでは場合、の最初の子要素があります、 **\<構成 >**要素。</span><span class="sxs-lookup"><span data-stu-id="693a1-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="693a1-124">例</span><span class="sxs-lookup"><span data-stu-id="693a1-124">Example</span></span>

<span data-ttu-id="693a1-125">次の例では、構成セクションを定義してそのセクションの設定を定義する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="693a1-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="693a1-126">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="693a1-126">Configuration file</span></span>

<span data-ttu-id="693a1-127">この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。</span><span class="sxs-lookup"><span data-stu-id="693a1-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="693a1-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="693a1-128">See also</span></span>

[<span data-ttu-id="693a1-129">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="693a1-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
