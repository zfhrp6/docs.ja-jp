---
title: "&lt;オフ&gt;要素&lt;configSections&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 70fc73c9e97274ac1165950038ee509fa8f2f9c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="28813-102">\<オフ > 要素を\<configSections ></span><span class="sxs-lookup"><span data-stu-id="28813-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="28813-103">以前に定義されたセクションおよびセクション グループのすべてをクリアします。</span><span class="sxs-lookup"><span data-stu-id="28813-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="28813-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="28813-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="28813-105">&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="28813-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="28813-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<オフ >**</span><span class="sxs-lookup"><span data-stu-id="28813-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="28813-107">構文</span><span class="sxs-lookup"><span data-stu-id="28813-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="28813-108">属性</span><span class="sxs-lookup"><span data-stu-id="28813-108">Attribute</span></span>

|           | <span data-ttu-id="28813-109">説明</span><span class="sxs-lookup"><span data-stu-id="28813-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="28813-110">**name**</span><span class="sxs-lookup"><span data-stu-id="28813-110">**name**</span></span>  | <span data-ttu-id="28813-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="28813-111">Required attribute.</span></span><br><br><span data-ttu-id="28813-112">セクション、または削除するセクション グループの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="28813-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="28813-113">親要素</span><span class="sxs-lookup"><span data-stu-id="28813-113">Parent element</span></span>

|     | <span data-ttu-id="28813-114">説明</span><span class="sxs-lookup"><span data-stu-id="28813-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="28813-115">**\<configSections >**要素</span><span class="sxs-lookup"><span data-stu-id="28813-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="28813-116">構成セクションと名前空間宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="28813-116">Contains configuration section and namespace declarations.</span></span> |

# <a name="child-elements"></a><span data-ttu-id="28813-117">子要素</span><span class="sxs-lookup"><span data-stu-id="28813-117">Child elements</span></span>

<span data-ttu-id="28813-118">なし</span><span class="sxs-lookup"><span data-stu-id="28813-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="28813-119">コメント</span><span class="sxs-lookup"><span data-stu-id="28813-119">Remarks</span></span>

<span data-ttu-id="28813-120">**\<オフ >**要素または構成ファイルの階層の上位レベルにある現在の構成ファイルで既に定義されているアプリケーションからすべてのセクションおよびセクション グループを削除します。</span><span class="sxs-lookup"><span data-stu-id="28813-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="28813-121">例</span><span class="sxs-lookup"><span data-stu-id="28813-121">Example</span></span>

<span data-ttu-id="28813-122">この例は、マシン構成ファイルとアプリケーション構成ファイルを定義し、使用する方法を示しています、 **\<オフ >**で以前に定義されたセクションをオフにするアプリケーション構成ファイル内の要素、マシン構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="28813-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="28813-123">マシン構成ファイルのコードは、次に 2 つのセクションを宣言しています **\<sampleSection >**と **\<anotherSampleSection >**アプリケーションの前に読み取り、構成ファイル:</span><span class="sxs-lookup"><span data-stu-id="28813-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="28813-124">次のアプリケーション構成ファイルのコードでは、以前に宣言されたすべてのセクションを消去します。</span><span class="sxs-lookup"><span data-stu-id="28813-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="28813-125">アプリケーションがマシン構成ファイルで宣言されていたセクションでは、のいずれかの設定を取得または使用できません。</span><span class="sxs-lookup"><span data-stu-id="28813-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="28813-126">ただしから設定を使用して、  **\<anotherSection >**後にあるため、 **\<オフ >**要素。</span><span class="sxs-lookup"><span data-stu-id="28813-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="28813-127">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="28813-127">Configuration file</span></span>

<span data-ttu-id="28813-128">この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。</span><span class="sxs-lookup"><span data-stu-id="28813-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="28813-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="28813-129">See also</span></span>

[<span data-ttu-id="28813-130">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="28813-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
