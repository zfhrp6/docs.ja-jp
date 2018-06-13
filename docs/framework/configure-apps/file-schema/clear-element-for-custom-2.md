---
title: '&lt;オフ&gt;NameValueSectionHandler と DictionarySectionHandler 要素'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: a1cbd682faa4c60e50bc3b73b58ef226dd599da2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358236"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="5267d-102">\<オフ > NameValueSectionHandler と DictionarySectionHandler 要素</span><span class="sxs-lookup"><span data-stu-id="5267d-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="5267d-103">セクション内のすべての以前に定義された設定を消去します。</span><span class="sxs-lookup"><span data-stu-id="5267d-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="5267d-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5267d-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="5267d-105">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="5267d-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="5267d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<オフ >**</span><span class="sxs-lookup"><span data-stu-id="5267d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="5267d-107">構文</span><span class="sxs-lookup"><span data-stu-id="5267d-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="5267d-108">属性</span><span class="sxs-lookup"><span data-stu-id="5267d-108">Attributes</span></span>

<span data-ttu-id="5267d-109">なし</span><span class="sxs-lookup"><span data-stu-id="5267d-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="5267d-110">親要素</span><span class="sxs-lookup"><span data-stu-id="5267d-110">Parent element</span></span>

|     | <span data-ttu-id="5267d-111">説明</span><span class="sxs-lookup"><span data-stu-id="5267d-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="5267d-112">**\<sectionName >** 要素</span><span class="sxs-lookup"><span data-stu-id="5267d-112">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="5267d-113">使用するカスタム構成セクションの設定を定義、<xref:System.Configuration.NameValueSectionHandler>と<xref:System.Configuration.DictionarySectionHandler>クラスです。</span><span class="sxs-lookup"><span data-stu-id="5267d-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5267d-114">子要素</span><span class="sxs-lookup"><span data-stu-id="5267d-114">Child elements</span></span>

<span data-ttu-id="5267d-115">なし</span><span class="sxs-lookup"><span data-stu-id="5267d-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="5267d-116">コメント</span><span class="sxs-lookup"><span data-stu-id="5267d-116">Remarks</span></span>

<span data-ttu-id="5267d-117">使用することができます、 **\<オフ >** 構成ファイルの階層内の上位レベルで定義されているアプリケーションからのすべての設定を削除する要素。</span><span class="sxs-lookup"><span data-stu-id="5267d-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="5267d-118">例</span><span class="sxs-lookup"><span data-stu-id="5267d-118">Example</span></span>

<span data-ttu-id="5267d-119">この例は、マシン構成ファイルとアプリケーション構成ファイルを定義し、使用する方法を示しています、 **\<オフ >** で以前に定義されたセクションをオフにするアプリケーション構成ファイル内の要素、マシン構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="5267d-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="5267d-120">マシン構成ファイルのコードは、次のセクションを宣言して **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="5267d-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="5267d-121">次のアプリケーション構成ファイルのコードからすべての設定を削除する **\<mySection >** です。</span><span class="sxs-lookup"><span data-stu-id="5267d-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="5267d-122">アプリケーションを取得できませんで宣言されていた設定のいずれかで、  **\<mySection >** マシン構成ファイルのセクションです。</span><span class="sxs-lookup"><span data-stu-id="5267d-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="5267d-123">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="5267d-123">Configuration file</span></span>

<span data-ttu-id="5267d-124">この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。</span><span class="sxs-lookup"><span data-stu-id="5267d-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="5267d-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="5267d-125">See also</span></span>

[<span data-ttu-id="5267d-126">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="5267d-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
