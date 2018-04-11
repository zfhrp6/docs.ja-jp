---
title: SingleTagSectionHandler のカスタム要素
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8ee722c7d5db9d58ab1a91f4b1299912981510af
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/10/2018
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="7674f-102">SingleTagSectionHandler のカスタム要素</span><span class="sxs-lookup"><span data-stu-id="7674f-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="7674f-103">定義されているカスタム構成セクションの設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="7674f-103">Defines settings in a custom configuration section that is defined by a</span></span> <section> <span data-ttu-id="7674f-104">要素と使用、<xref:System.Configuration.SingleTagSectionHandler>クラスです。</span><span class="sxs-lookup"><span data-stu-id="7674f-104">element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="7674f-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7674f-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="7674f-106">&nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="7674f-106">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="7674f-107">構文</span><span class="sxs-lookup"><span data-stu-id="7674f-107">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="7674f-108">属性</span><span class="sxs-lookup"><span data-stu-id="7674f-108">Attributes</span></span>

<span data-ttu-id="7674f-109">属性および属性値は、ユーザー定義を示します。</span><span class="sxs-lookup"><span data-stu-id="7674f-109">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="7674f-110">親要素</span><span class="sxs-lookup"><span data-stu-id="7674f-110">Parent element</span></span>

|     | <span data-ttu-id="7674f-111">説明</span><span class="sxs-lookup"><span data-stu-id="7674f-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7674f-112">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="7674f-112">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="7674f-113">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="7674f-113">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7674f-114">子要素</span><span class="sxs-lookup"><span data-stu-id="7674f-114">Child elements</span></span>

<span data-ttu-id="7674f-115">なし</span><span class="sxs-lookup"><span data-stu-id="7674f-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="7674f-116">コメント</span><span class="sxs-lookup"><span data-stu-id="7674f-116">Remarks</span></span>

<span data-ttu-id="7674f-117"> **\<SectionName >**要素は、カスタムの要素によって定義された、 [ **\<セクション >** ](~/docs/framework/configure-apps/file-schema/section-element.md)にタグを付ける、 [ **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)要素。</span><span class="sxs-lookup"><span data-stu-id="7674f-117">The **\<sectionName>** element is a custom element defined by a [**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) tag in the [**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="7674f-118">構成システムを返します、<xref:System.Collections.IDictionary>オブジェクトを呼び出すとき<xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="7674f-118">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="7674f-119">例</span><span class="sxs-lookup"><span data-stu-id="7674f-119">Example</span></span>

<span data-ttu-id="7674f-120">次の例と呼ばれるカスタム要素の宣言 **\<sampleSection >**によって読み取られた設定を格納している、<xref:System.Configuration.SingleTagSectionHandler>クラス。</span><span class="sxs-lookup"><span data-stu-id="7674f-120">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="7674f-121">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="7674f-121">Configuration file</span></span>

<span data-ttu-id="7674f-122">この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。</span><span class="sxs-lookup"><span data-stu-id="7674f-122">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="7674f-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="7674f-123">See also</span></span>

[<span data-ttu-id="7674f-124">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="7674f-124">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
