---
title: "&lt;appSettings&gt;要素&lt;構成&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cebb9ba7ebeb483233276324289a4ddc5a0bc381
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="appsettings-element-for-configuration"></a><span data-ttu-id="2ac3e-102">\<appSettings > 要素を\<構成 ></span><span class="sxs-lookup"><span data-stu-id="2ac3e-102">\<appSettings> element for \<configuration></span></span>

<span data-ttu-id="2ac3e-103">カスタム アプリケーションの設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-103">Contains custom application settings.</span></span> <span data-ttu-id="2ac3e-104">これは、.NET Framework で提供される定義済みの構成セクションです。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-104">This is a predefined configuration section provided by the .NET Framework.</span></span>

<span data-ttu-id="2ac3e-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2ac3e-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="2ac3e-106">&nbsp;&nbsp;**\<appSettings >**</span><span class="sxs-lookup"><span data-stu-id="2ac3e-106">&nbsp;&nbsp;**\<appSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2ac3e-107">構文</span><span class="sxs-lookup"><span data-stu-id="2ac3e-107">Syntax</span></span>

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a><span data-ttu-id="2ac3e-108">属性</span><span class="sxs-lookup"><span data-stu-id="2ac3e-108">Attribute</span></span>

|           | <span data-ttu-id="2ac3e-109">説明</span><span class="sxs-lookup"><span data-stu-id="2ac3e-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="2ac3e-110">**file**</span><span class="sxs-lookup"><span data-stu-id="2ac3e-110">**file**</span></span>  | <span data-ttu-id="2ac3e-111">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-111">Optional attribute.</span></span><br><br><span data-ttu-id="2ac3e-112">カスタム アプリケーションの構成設定を含む外部ファイルへの相対パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-112">Specifies a relative path to an external file containing custom application configuration settings.</span></span> <span data-ttu-id="2ac3e-113">指定したファイルには、同じ種類設定で指定されているにはが含まれています、 **\<追加 >**、 **\<削除 >**、および**\<オフ >。**これらの要素と同じキー/値ペアが書式設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-113">The specified file contains the same kind of settings that are specified in the **\<add>**, **\<remove>**, and **\<clear>** elements and uses the same key/value pair format as those elements.</span></span><br><br><span data-ttu-id="2ac3e-114">指定されたパスは、主要な構成ファイルに相対です。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-114">The path specified is relative to the main configuration file.</span></span> <span data-ttu-id="2ac3e-115">Windows フォーム アプリケーションでは、これは、バイナリ フォルダー (など*bin/デバッグ*)、アプリケーション構成ファイルの場所ではありません。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-115">For a Windows Forms application, this is the binary folder (such as */bin/debug*), not the location of the application configuration file.</span></span> <span data-ttu-id="2ac3e-116">アプリケーション ルートに対する相対パスは、Web フォーム アプリケーションの場所、 *web.config*ファイルが置かれています。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-116">For Web Forms applications, the path is relative to the application root, where the *web.config* file is located.</span></span><br><br><span data-ttu-id="2ac3e-117">指定したファイルが見つからない場合、ランタイムは属性を無視されます。 注意してください。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-117">Note that the runtime ignores the attribute if the specified file can not be found.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="2ac3e-118">親要素</span><span class="sxs-lookup"><span data-stu-id="2ac3e-118">Parent element</span></span>

|     | <span data-ttu-id="2ac3e-119">説明</span><span class="sxs-lookup"><span data-stu-id="2ac3e-119">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2ac3e-120">**\<構成 >**要素</span><span class="sxs-lookup"><span data-stu-id="2ac3e-120">**\<configuration>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="2ac3e-121">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2ac3e-122">子要素</span><span class="sxs-lookup"><span data-stu-id="2ac3e-122">Child elements</span></span>

|     | <span data-ttu-id="2ac3e-123">説明</span><span class="sxs-lookup"><span data-stu-id="2ac3e-123">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2ac3e-124">**\<add>**</span><span class="sxs-lookup"><span data-stu-id="2ac3e-124">**\<add>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | <span data-ttu-id="2ac3e-125">カスタム アプリケーション設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-125">Adds a custom application setting.</span></span> |
| [<span data-ttu-id="2ac3e-126">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="2ac3e-126">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | <span data-ttu-id="2ac3e-127">定義済みのアプリケーションのすべての設定を消去します。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-127">Clears all previously defined application settings.</span></span> |
| [<span data-ttu-id="2ac3e-128">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="2ac3e-128">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | <span data-ttu-id="2ac3e-129">定義済みのアプリケーション設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-129">Removes a previously defined application setting.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2ac3e-130">コメント</span><span class="sxs-lookup"><span data-stu-id="2ac3e-130">Remarks</span></span>

<span data-ttu-id="2ac3e-131"> **\<AppSettings >**要素がデータベース接続文字列、ファイルのパス、XML Web サービス Url の他のカスタム構成情報など、カスタム アプリケーションの構成情報を格納します。アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-131">The **\<appSettings>** element stores custom application configuration information, such as database connection strings, file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> <span data-ttu-id="2ac3e-132">指定されたキーと値のペア、  **\<appSettings >**要素は、コードを使用して、<xref:System.Configuration.ConfigurationSettings>クラスです。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-132">The key/value pairs specified in the **\<appSettings>** element are accessed in code using the <xref:System.Configuration.ConfigurationSettings> class.</span></span>

<span data-ttu-id="2ac3e-133">使用することができます、**ファイル**属性、  **\<appSettings >**の要素、 *Web.config*とアプリケーション構成ファイル。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-133">You can use the **file** attribute in the **\<appSettings>** element of the *Web.config* and application configuration files.</span></span> <span data-ttu-id="2ac3e-134">この属性で指定された設定を上書きまたは追加の設定を提供する構成ファイルを指定する、  **\<appSettings >**要素。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-134">This attribute specifies a configuration file that provides additional settings or overrides the settings specified in the **\<appSettings>** element.</span></span> <span data-ttu-id="2ac3e-135">**ファイル**属性をソース コントロール チーム開発などのシナリオで、ユーザーがアプリケーション構成ファイルで指定されたプロジェクトの設定をオーバーライドするときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-135">The **file** attribute can be used in source control team development scenarios, such as when a user wants to override the project settings specified in an application configuration file.</span></span>

<span data-ttu-id="2ac3e-136">指定された構成ファイル、**ファイル**属性のルート ノードが必要です **\<appSettings >**なく**\<構成 >**.</span><span class="sxs-lookup"><span data-stu-id="2ac3e-136">Configuration files specified by the **file** attribute must have a root node of **\<appSettings>** rather than **\<configuration>**.</span></span>

## <a name="example"></a><span data-ttu-id="2ac3e-137">例</span><span class="sxs-lookup"><span data-stu-id="2ac3e-137">Example</span></span>

<span data-ttu-id="2ac3e-138">次の例は、カスタム アプリケーション設定を定義する外部アプリケーション設定ファイル (*custom.config*) を示しています。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-138">The following example shows an external application settings file (*custom.config*) that defines a custom application setting:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

<span data-ttu-id="2ac3e-139">次の例は、外部設定ファイルで設定を使用して、独自のアプリケーション設定を設定するアプリケーション構成ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-139">The following example shows an application configuration file that consumes the setting in the external settings file and sets an application setting of its own:</span></span>

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="2ac3e-140">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="2ac3e-140">Configuration file</span></span>

<span data-ttu-id="2ac3e-141">この要素は、アプリケーション構成ファイル、マシン構成ファイルで使用できます (*Machine.config*)、および*Web.config*アプリケーション ディレクトリ レベルではないファイル。</span><span class="sxs-lookup"><span data-stu-id="2ac3e-141">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ac3e-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ac3e-142">See also</span></span>

[<span data-ttu-id="2ac3e-143">.NET Framework の構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="2ac3e-143">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
