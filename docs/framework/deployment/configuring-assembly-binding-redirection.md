---
title: "アセンブリ バインディングのリダイレクトの構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b53673d1ddb1de7fed087b4c5cb125e50f11b918
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-assembly-binding-redirection"></a><span data-ttu-id="0815d-102">アセンブリ バインディングのリダイレクトの構成</span><span class="sxs-lookup"><span data-stu-id="0815d-102">Configuring Assembly Binding Redirection</span></span>
<span data-ttu-id="0815d-103">既定では、アプリケーションは、アプリケーションのコンパイルに使用したランタイム バージョンと共に出荷された .NET Framework アセンブリのセットを使用します。</span><span class="sxs-lookup"><span data-stu-id="0815d-103">By default, applications use the set of .NET Framework assemblies that shipped with the runtime version used to compile the application.</span></span> <span data-ttu-id="0815d-104">アプリケーション構成ファイルで .NET Framework アセンブリの特定のバージョンのアセンブリ バインディング参照をリダイレクトするには [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) 要素の **appliesTo** 属性を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0815d-104">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an application configuration file to redirect assembly binding references to a specific version of the .NET Framework assemblies.</span></span> <span data-ttu-id="0815d-105">このオプションの属性は、.NET Framework のバージョン番号を使用して、どのバージョンに適用するのかを示します。</span><span class="sxs-lookup"><span data-stu-id="0815d-105">This optional attribute uses a .NET Framework version number to indicate which version it applies to.</span></span> <span data-ttu-id="0815d-106">**appliesTo** 属性が指定されていない場合、**\<assemblyBinding>** 要素は、.NET Framework のすべてのバージョンに適用されます。</span><span class="sxs-lookup"><span data-stu-id="0815d-106">If no **appliesTo** attribute is specified, the **\<assemblyBinding>** element applies to all versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="0815d-107">**appliesTo** 属性は .NET Framework Version 1.1 で導入されたものであり、.NET Framework Version 1.0 では無視されます。</span><span class="sxs-lookup"><span data-stu-id="0815d-107">The **appliesTo** attribute was introduced in the .NET Framework version 1.1; it is ignored by the .NET Framework version 1.0.</span></span> <span data-ttu-id="0815d-108">これは **appliesTo** 属性が指定されている場合でも、.NET Framework version 1.0 を使用している場合 **\<assemblyBinding>** のすべての要素が適用されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0815d-108">This means that all **\<assemblyBinding>** elements are applied when using the .NET Framework version 1.0, even if an **appliesTo** attribute is specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0815d-109">**appliesTo** 属性は、アセンブリ バインディングのリダイレクトをランタイムの特定のバージョンに制限するために使用します。</span><span class="sxs-lookup"><span data-stu-id="0815d-109">Use the **appliesTo** attribute to limit assembly binding redirection to a specific version of the runtime.</span></span>  
  
 <span data-ttu-id="0815d-110">たとえば、.NET Framework Version 1.0 アセンブリのアセンブリ バインディングをリダイレクトするには、アプリケーション構成ファイルに次の XML コードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0815d-110">For example, to redirect assembly binding for a .NET Framework version 1.0 assembly, you would include the following XML code in your application configuration file.</span></span>  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 <span data-ttu-id="0815d-111">**\<assemblyBinding>** 要素は、順番が区別されます。</span><span class="sxs-lookup"><span data-stu-id="0815d-111">The **\<assemblyBinding>** elements are order-sensitive.</span></span> <span data-ttu-id="0815d-112">最初に .NET Framework Version 1.0 のアセンブリのアセンブリ バインディング リダイレクト情報を入力し、その次に .NET Framework Version 1.1 のアセンブリのアセンブリ バインディング リダイレクト情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="0815d-112">You should enter assembly binding redirection information for any .NET Framework version 1.0 assemblies first, followed by assembly binding redirection information for any .NET Framework version 1.1 assemblies.</span></span> <span data-ttu-id="0815d-113">最後に、 **appliesTo** 属性を使用せず、すべてのバージョンの .NET Framework に適用される .NET Framework アセンブリ リダイレクトのアセンブリ バインディング リダイレクト情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="0815d-113">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="0815d-114">リダイレクトで矛盾が発生した場合は、構成ファイル内で最初に一致したリダイレクト ステートメントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0815d-114">In case of a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>  
  
 <span data-ttu-id="0815d-115">たとえば、ある参照を .NET Framework Version 1.0 のアセンブリにリダイレクトし、別の参照を .NET Framework Version 1.1 のアセンブリにリダイレクトするには、次の擬似コードに示すパターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="0815d-115">For example, to redirect one reference to a .NET Framework version 1.0 assembly and another reference to a .NET Framework version 1.1 assembly, you would use the pattern shown in the following pseudocode.</span></span>  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
<! — .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
    <! — .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
<!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a><span data-ttu-id="0815d-116">構成ファイル エラーのデバッグ</span><span class="sxs-lookup"><span data-stu-id="0815d-116">Debugging Configuration File Errors</span></span>  
 <span data-ttu-id="0815d-117">ランタイムは、アプリケーション ドメインが作成されるときに構成ファイルを一度解析し、コードをアプリケーション ドメインに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="0815d-117">The runtime parses configuration files once when an application domain is created, and loads code into that application domain.</span></span> <span data-ttu-id="0815d-118">共通言語ランタイムは、エントリを無視することによって構成ファイルに含まれるエラーを処理します。</span><span class="sxs-lookup"><span data-stu-id="0815d-118">The common language runtime handles errors in a configuration file by ignoring the entry.</span></span> <span data-ttu-id="0815d-119">構成ファイルに不正な XML が含まれる場合、ランタイムは構成ファイル全体を無視します。</span><span class="sxs-lookup"><span data-stu-id="0815d-119">The runtime ignores the entire configuration file if it contains malformed XML.</span></span> <span data-ttu-id="0815d-120">無効な XML に対しては、無効なセクションだけを無視します。</span><span class="sxs-lookup"><span data-stu-id="0815d-120">For invalid XML, only the invalid sections are ignored.</span></span>  
  
 <span data-ttu-id="0815d-121">アセンブリ バインディングのリダイレクトが発生しているかどうかを調べることによって、構成ファイルが使用されているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="0815d-121">You can determine whether a configuration file is being used by determining whether assembly binding redirects are occurring.</span></span> <span data-ttu-id="0815d-122">[アセンブリ バインディング ログ ビューアー (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) を使用して、読み込まれたアセンブリを調べます。</span><span class="sxs-lookup"><span data-stu-id="0815d-122">Use the [Assembly Binding Log Viewer (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to see which assemblies are being loaded.</span></span> <span data-ttu-id="0815d-123">すべてのアセンブリ バインドを見るには、レジストリで **ForceLog** のエントリを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0815d-123">To see all assembly binds, you must set an entry for **ForceLog** in the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0815d-124">参照</span><span class="sxs-lookup"><span data-stu-id="0815d-124">See Also</span></span>  
 [<span data-ttu-id="0815d-125">方法: 自動バインディング リダイレクトを有効/無効にする</span><span class="sxs-lookup"><span data-stu-id="0815d-125">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
