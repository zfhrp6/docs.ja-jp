---
title: "&lt;削除&gt;要素&lt;configSections&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf2cb49fbeb01ad176a1d24d711cebc97ba14004
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="bbe19-102">\<削除 > 要素を\<configSections ></span><span class="sxs-lookup"><span data-stu-id="bbe19-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="bbe19-103">定義済みのセクション、またはセクション グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="bbe19-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="bbe19-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="bbe19-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="bbe19-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="bbe19-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="bbe19-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<削除 >**</span><span class="sxs-lookup"><span data-stu-id="bbe19-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bbe19-107">構文</span><span class="sxs-lookup"><span data-stu-id="bbe19-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="bbe19-108">属性</span><span class="sxs-lookup"><span data-stu-id="bbe19-108">Attribute</span></span>

|           | <span data-ttu-id="bbe19-109">説明</span><span class="sxs-lookup"><span data-stu-id="bbe19-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="bbe19-110">**name**</span><span class="sxs-lookup"><span data-stu-id="bbe19-110">**name**</span></span>  | <span data-ttu-id="bbe19-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="bbe19-111">Required attribute.</span></span><br><br><span data-ttu-id="bbe19-112">セクション、または削除するセクション グループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="bbe19-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="bbe19-113">親要素</span><span class="sxs-lookup"><span data-stu-id="bbe19-113">Parent element</span></span>

|     | <span data-ttu-id="bbe19-114">説明</span><span class="sxs-lookup"><span data-stu-id="bbe19-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="bbe19-115">**\<configSections >**要素</span><span class="sxs-lookup"><span data-stu-id="bbe19-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="bbe19-116">構成セクションと名前空間宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="bbe19-116">Contains configuration section and namespace declarations.</span></span> |

# <a name="child-elements"></a><span data-ttu-id="bbe19-117">子要素</span><span class="sxs-lookup"><span data-stu-id="bbe19-117">Child elements</span></span>

<span data-ttu-id="bbe19-118">なし</span><span class="sxs-lookup"><span data-stu-id="bbe19-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="bbe19-119">コメント</span><span class="sxs-lookup"><span data-stu-id="bbe19-119">Remarks</span></span>

<span data-ttu-id="bbe19-120">使用することができます、 **\<削除 >**セクションおよびセクション グループを構成ファイルの階層内の上位レベルで定義されているアプリケーションから削除する要素。</span><span class="sxs-lookup"><span data-stu-id="bbe19-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="bbe19-121">例</span><span class="sxs-lookup"><span data-stu-id="bbe19-121">Example</span></span>

<span data-ttu-id="bbe19-122">次の例を使用する方法を示しています、 **\<削除 >**マシン構成ファイルで定義されたセクションを削除するアプリケーション構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="bbe19-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="bbe19-123">マシン構成ファイルのコードは、次のセクションを宣言して **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="bbe19-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
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

<span data-ttu-id="bbe19-124">アプリケーション構成ファイルのコードは、次の削除、  **\<sampleSection >**セクションです。</span><span class="sxs-lookup"><span data-stu-id="bbe19-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="bbe19-125">削除した後、アプリケーションがの設定を取得できません **\<sampleSection >**です。</span><span class="sxs-lookup"><span data-stu-id="bbe19-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="bbe19-126">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="bbe19-126">Configuration file</span></span>

<span data-ttu-id="bbe19-127">この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。</span><span class="sxs-lookup"><span data-stu-id="bbe19-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="bbe19-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbe19-128">See also</span></span>

[<span data-ttu-id="bbe19-129">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="bbe19-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
