---
title: アセンブリを指定する&#39;s 場所
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 65bd075115e33486e86e8081b01b96db665e9da5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758270"
---
# <a name="specifying-an-assembly39s-location"></a><span data-ttu-id="2ca8b-102">アセンブリを指定する&#39;s 場所</span><span class="sxs-lookup"><span data-stu-id="2ca8b-102">Specifying an Assembly&#39;s Location</span></span>
<span data-ttu-id="2ca8b-103">これにはアセンブリの場所を指定する 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="2ca8b-104">使用して、 [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="2ca8b-105">使用して、 [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="2ca8b-106">使用することも、 [.NET Framework 構成ツール (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764)をアセンブリの場所を指定するか、共通言語ランタイム アセンブリを探すための場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](http://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="2ca8b-107">使用して、 \<codeBase > 要素</span><span class="sxs-lookup"><span data-stu-id="2ca8b-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="2ca8b-108">使用することができます、  **\<codeBase >** のみマシン構成ファイルまたはパブリッシャー ポリシー ファイルでもアセンブリのバージョンをリダイレクトする要素。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="2ca8b-109">ランタイムは、使用するアセンブリ バージョンを判断した場合は、バージョンを決定する、ファイルからコード ベース設定が適用されます。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="2ca8b-110">コード ベースが指定されていない場合、ランタイムは、通常の方法で、アセンブリをプローブします。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="2ca8b-111">詳細については、「[ランタイム アセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)です。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="2ca8b-112">次の例では、アセンブリの場所を指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-112">The following example shows how to specify an assembly's location.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="2ca8b-113">**バージョン**属性が必要ですがすべて厳密な名前のアセンブリのアセンブリの厳密な名前が付いていない場合は省略されます。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="2ca8b-114">**\<CodeBase >** 要素が必要です、 **href**属性。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="2ca8b-115">バージョン範囲を指定することはできません、  **\<codeBase >** 要素。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ca8b-116">厳密な名前ではないアセンブリ コード ベースのヒントを指定している場合、ヒントは、アプリケーション ベースまたはアプリケーション ベース ディレクトリのサブディレクトリを指す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="2ca8b-117">使用して、 \<probing > 要素</span><span class="sxs-lookup"><span data-stu-id="2ca8b-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="2ca8b-118">ランタイムが調査で基本コードを持たないアセンブリを検索します。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="2ca8b-119">調査の詳細については、次を参照してください。[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)です。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="2ca8b-120">使用することができます、 [ \<probing >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)アプリケーション構成ファイルの要素をランタイムがアセンブリを検索するときに検索するサブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="2ca8b-121">次の例では、ランタイムが検索するディレクトリを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="2ca8b-122">**PrivatePath**属性には、ランタイムがアセンブリを検索するディレクトリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="2ca8b-123">アプリケーションが C:\Program files \myapp にある場合は、ランタイムは C:\Program Files\MyApp\Bin、C:\Program Files\MyApp\Bin2\Subbin および C:\Program Files\MyApp\Bin3 でコード ベースが指定されていないアセンブリを検索します。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="2ca8b-124">指定したディレクトリ**privatePath**アプリケーション ベース ディレクトリのサブディレクトリにある必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ca8b-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca8b-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ca8b-125">See Also</span></span>  
 [<span data-ttu-id="2ca8b-126">共通言語ランタイムのアセンブリ</span><span class="sxs-lookup"><span data-stu-id="2ca8b-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="2ca8b-127">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="2ca8b-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="2ca8b-128">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="2ca8b-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="2ca8b-129">.NET Framework アプリの構成</span><span class="sxs-lookup"><span data-stu-id="2ca8b-129">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
