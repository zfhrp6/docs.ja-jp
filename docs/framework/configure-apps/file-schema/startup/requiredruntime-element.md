---
title: "&lt;requiredRuntime&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 633769573253d7516bc50f0210c30376e6aa230a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltrequiredruntimegt-element"></a><span data-ttu-id="a0c23-102">&lt;requiredRuntime&gt;要素</span><span class="sxs-lookup"><span data-stu-id="a0c23-102">&lt;requiredRuntime&gt; Element</span></span>
<span data-ttu-id="a0c23-103">バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0c23-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="a0c23-104">この要素は推奨されておらず、使用できなくする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0c23-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="a0c23-105">[ `supportedRuntime` ](supportedruntime-element.md)要素を使用してください。</span><span class="sxs-lookup"><span data-stu-id="a0c23-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>
  
 <span data-ttu-id="a0c23-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a0c23-106">\<configuration></span></span>  
<span data-ttu-id="a0c23-107">\<スタートアップ ></span><span class="sxs-lookup"><span data-stu-id="a0c23-107">\<startup></span></span>  
<span data-ttu-id="a0c23-108">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="a0c23-108">\<requiredRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c23-109">構文</span><span class="sxs-lookup"><span data-stu-id="a0c23-109">Syntax</span></span>  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0c23-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a0c23-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a0c23-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a0c23-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0c23-112">属性</span><span class="sxs-lookup"><span data-stu-id="a0c23-112">Attributes</span></span>  
  
|<span data-ttu-id="a0c23-113">属性</span><span class="sxs-lookup"><span data-stu-id="a0c23-113">Attribute</span></span>|<span data-ttu-id="a0c23-114">説明</span><span class="sxs-lookup"><span data-stu-id="a0c23-114">Description</span></span>|  
|---------------|-----------------|  
|`version`|<span data-ttu-id="a0c23-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="a0c23-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a0c23-116">このアプリケーションをサポートする .NET Framework のバージョンを指定する文字列値。</span><span class="sxs-lookup"><span data-stu-id="a0c23-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="a0c23-117">文字列値は、.NET Framework のインストールのルート ディレクトリ名と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0c23-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="a0c23-118">文字列値の内容は解析されません。</span><span class="sxs-lookup"><span data-stu-id="a0c23-118">The contents of the string value are not parsed.</span></span>|  
|`safemode`|<span data-ttu-id="a0c23-119">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="a0c23-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a0c23-120">ランタイム スタートアップ コードがランタイムのバージョンを確認するためのレジストリを検索するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a0c23-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|  
  
## <a name="safemode-attribute"></a><span data-ttu-id="a0c23-121">セーフ モード属性</span><span class="sxs-lookup"><span data-stu-id="a0c23-121">safemode Attribute</span></span>  
  
|<span data-ttu-id="a0c23-122">値</span><span class="sxs-lookup"><span data-stu-id="a0c23-122">Value</span></span>|<span data-ttu-id="a0c23-123">説明</span><span class="sxs-lookup"><span data-stu-id="a0c23-123">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a0c23-124">ランタイム スタートアップ コードは、レジストリを検索します。</span><span class="sxs-lookup"><span data-stu-id="a0c23-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="a0c23-125">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="a0c23-125">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="a0c23-126">ランタイム スタートアップ コードは、レジストリでは検索しません。</span><span class="sxs-lookup"><span data-stu-id="a0c23-126">The runtime startup code does not look in the registry.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a0c23-127">子要素</span><span class="sxs-lookup"><span data-stu-id="a0c23-127">Child Elements</span></span>  
 <span data-ttu-id="a0c23-128">なし。</span><span class="sxs-lookup"><span data-stu-id="a0c23-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a0c23-129">親要素</span><span class="sxs-lookup"><span data-stu-id="a0c23-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a0c23-130">要素</span><span class="sxs-lookup"><span data-stu-id="a0c23-130">Element</span></span>|<span data-ttu-id="a0c23-131">説明</span><span class="sxs-lookup"><span data-stu-id="a0c23-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a0c23-132">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="a0c23-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`startup`|<span data-ttu-id="a0c23-133">含まれています、`<requiredRuntime>`要素。</span><span class="sxs-lookup"><span data-stu-id="a0c23-133">Contains the `<requiredRuntime>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0c23-134">コメント</span><span class="sxs-lookup"><span data-stu-id="a0c23-134">Remarks</span></span>  
 <span data-ttu-id="a0c23-135">ランタイムのバージョン 1.0 をサポートするために構築されたアプリケーションを使用する必要があります、`<requiredRuntime>`要素。</span><span class="sxs-lookup"><span data-stu-id="a0c23-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="a0c23-136">1.1 以降、ランタイムのバージョンを使用して構築されたアプリケーションを使用する必要があります、`<supportedRuntime>`要素。</span><span class="sxs-lookup"><span data-stu-id="a0c23-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0c23-137">使用する場合、 [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)構成ファイルを指定する関数を使用する必要があります、`<requiredRuntime>`ランタイムのすべてのバージョンの要素。</span><span class="sxs-lookup"><span data-stu-id="a0c23-137">If you use the [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="a0c23-138">`<supportedRuntime>`を使用するときに、要素は無視されます[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0c23-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
 <span data-ttu-id="a0c23-139">`version`属性文字列は指定されたバージョンの .NET Framework のインストール フォルダーの名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0c23-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="a0c23-140">この文字列は解釈されません。</span><span class="sxs-lookup"><span data-stu-id="a0c23-140">This string is not interpreted.</span></span> <span data-ttu-id="a0c23-141">ランタイム スタートアップ コードが一致するフォルダーを見つけられない場合、ランタイムが読み込まれていません。スタートアップ コードは、エラー メッセージが表示され、終了します。</span><span class="sxs-lookup"><span data-stu-id="a0c23-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0c23-142">Microsoft Internet Explorer でホストされているアプリケーションのスタートアップ コードは無視されます、`<requiredRuntime>`要素。</span><span class="sxs-lookup"><span data-stu-id="a0c23-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0c23-143">例</span><span class="sxs-lookup"><span data-stu-id="a0c23-143">Example</span></span>  
 <span data-ttu-id="a0c23-144">次の例では、構成ファイルでランタイムのバージョンを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a0c23-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0c23-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0c23-145">See Also</span></span>  
 [<span data-ttu-id="a0c23-146">スタートアップ設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="a0c23-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="a0c23-147">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="a0c23-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="a0c23-148">\<PaveOver> 使用するランタイム バージョンの指定</span><span class="sxs-lookup"><span data-stu-id="a0c23-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)
