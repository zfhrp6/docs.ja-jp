---
title: "&lt;sectionGroup&gt;要素&lt;configSections&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 654a6e639a24120e1e0c993ebe36f14e75b46a12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="38f1e-102">\<sectionGroup > 要素を\<configSections ></span><span class="sxs-lookup"><span data-stu-id="38f1e-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="38f1e-103">構成セクションの名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="38f1e-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="38f1e-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="38f1e-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="38f1e-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="38f1e-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="38f1e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="38f1e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="38f1e-107">構文</span><span class="sxs-lookup"><span data-stu-id="38f1e-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="38f1e-108">属性</span><span class="sxs-lookup"><span data-stu-id="38f1e-108">Attribute</span></span>

|           | <span data-ttu-id="38f1e-109">説明</span><span class="sxs-lookup"><span data-stu-id="38f1e-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="38f1e-110">**name**</span><span class="sxs-lookup"><span data-stu-id="38f1e-110">**name**</span></span>  | <span data-ttu-id="38f1e-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="38f1e-111">Required attribute.</span></span><br><br><span data-ttu-id="38f1e-112">定義しているセクション グループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="38f1e-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="38f1e-113">親要素</span><span class="sxs-lookup"><span data-stu-id="38f1e-113">Parent element</span></span>

|     | <span data-ttu-id="38f1e-114">説明</span><span class="sxs-lookup"><span data-stu-id="38f1e-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="38f1e-115">**\<configSections >**要素</span><span class="sxs-lookup"><span data-stu-id="38f1e-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="38f1e-116">構成セクションと名前空間宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="38f1e-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="38f1e-117">子要素</span><span class="sxs-lookup"><span data-stu-id="38f1e-117">Child elements</span></span>

|     | <span data-ttu-id="38f1e-118">説明</span><span class="sxs-lookup"><span data-stu-id="38f1e-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="38f1e-119">**\<セクション >**</span><span class="sxs-lookup"><span data-stu-id="38f1e-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="38f1e-120">構成セクションの宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="38f1e-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="38f1e-121">コメント</span><span class="sxs-lookup"><span data-stu-id="38f1e-121">Remarks</span></span>

<span data-ttu-id="38f1e-122">セクション グループを宣言すると、構成セクションのコンテナー タグを作成し、他のユーザーによって定義された構成セクションの名前付けの競合がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="38f1e-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="38f1e-123">入れ子にすることができます **\<sectionGroup >**相互内の要素。</span><span class="sxs-lookup"><span data-stu-id="38f1e-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="38f1e-124">例</span><span class="sxs-lookup"><span data-stu-id="38f1e-124">Example</span></span>

<span data-ttu-id="38f1e-125">次の例では、セクション グループを宣言し、セクション グループ内のセクションを宣言する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="38f1e-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="38f1e-126">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="38f1e-126">Configuration file</span></span>

<span data-ttu-id="38f1e-127">この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。</span><span class="sxs-lookup"><span data-stu-id="38f1e-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="38f1e-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="38f1e-128">See also</span></span>

[<span data-ttu-id="38f1e-129">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="38f1e-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
