---
title: "方法 : DEVPATH を使用してアセンブリを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 70448f7ce4c00274dde14bace603e5c8852bf148
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="171b1-102">方法 : DEVPATH を使用してアセンブリを指定する</span><span class="sxs-lookup"><span data-stu-id="171b1-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="171b1-103">開発者は、複数のアプリケーションの構築、共有アセンブリが正常に動作するかどうかを確認する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="171b1-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="171b1-104">開発サイクル中に、グローバル アセンブリ キャッシュにアセンブリを配置継続的に、代わりに、開発者は、アセンブリのビルド出力ディレクトリを指す DEVPATH 環境変数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="171b1-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="171b1-105">たとえば、MySharedAssembly と呼ばれる共有アセンブリをビルドして、出力ディレクトリは C:\MySharedAssembly\Debug です。</span><span class="sxs-lookup"><span data-stu-id="171b1-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="171b1-106">C:\MySharedAssembly\Debug は DEVPATH 変数にすることができます。</span><span class="sxs-lookup"><span data-stu-id="171b1-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="171b1-107">指定する必要がありますし、 [ \<developmentMode >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)マシン構成ファイル内の要素。</span><span class="sxs-lookup"><span data-stu-id="171b1-107">You must then specify the [\<developmentMode>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="171b1-108">この要素は、アセンブリの検索に DEVPATH を使用する共通言語ランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="171b1-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="171b1-109">共有アセンブリは、ランタイムによって探索可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="171b1-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="171b1-110">アセンブリ参照の使用を解決するためのプライベート ディレクトリを指定する、 [ \<codeBase > 要素](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)または[ \<probing > 要素](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)」の説明に従って、構成ファイルで[アセンブリの場所を指定する](../../../docs/framework/configure-apps/specify-assembly-location.md)です。</span><span class="sxs-lookup"><span data-stu-id="171b1-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) or [\<probing> Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  <span data-ttu-id="171b1-111">アプリケーションのディレクトリのサブディレクトリに、アセンブリを格納することもできます。</span><span class="sxs-lookup"><span data-stu-id="171b1-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="171b1-112">詳細については、「 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="171b1-112">For more information, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="171b1-113">これは開発専用の高度な機能です。</span><span class="sxs-lookup"><span data-stu-id="171b1-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="171b1-114">次の例では、DEVPATH 環境変数で指定したディレクトリ内のアセンブリを検索するランタイムを発生させる方法を示します。</span><span class="sxs-lookup"><span data-stu-id="171b1-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="171b1-115">例</span><span class="sxs-lookup"><span data-stu-id="171b1-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="171b1-116">この設定の既定値は false。</span><span class="sxs-lookup"><span data-stu-id="171b1-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="171b1-117">この設定を使用して、開発時のみです。</span><span class="sxs-lookup"><span data-stu-id="171b1-117">Use this setting only at development time.</span></span> <span data-ttu-id="171b1-118">ランタイムは、DEVPATH で見つかった厳密な名前のアセンブリのバージョンをチェックしません。</span><span class="sxs-lookup"><span data-stu-id="171b1-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="171b1-119">最初に見つかったアセンブリは単に使用します。</span><span class="sxs-lookup"><span data-stu-id="171b1-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="171b1-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="171b1-120">See Also</span></span>  
 [<span data-ttu-id="171b1-121">.NET Framework アプリの構成</span><span class="sxs-lookup"><span data-stu-id="171b1-121">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
