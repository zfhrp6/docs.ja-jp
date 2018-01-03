---
title: ".NET ネイティブの一般的なトラブルシューティング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e92e99b978d12c32cc46b9133621875f35af634
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="net-native-general-troubleshooting"></a><span data-ttu-id="17e0b-102">.NET ネイティブの一般的なトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="17e0b-102">.NET Native General Troubleshooting</span></span>
<span data-ttu-id="17e0b-103">このトピックでは、[!INCLUDE[net_native](../../../includes/net-native-md.md)]でアプリを開発するときに発生する可能性のある問題のトラブルシューティング方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="17e0b-103">This topic describes how to troubleshoot potential issues that you might encounter when developing apps with [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="17e0b-104">**問題:** ビルド出力ウィンドウが正しく更新されない。</span><span class="sxs-lookup"><span data-stu-id="17e0b-104">**Issue:** Your build output window isn't properly updated.</span></span>  
  
     <span data-ttu-id="17e0b-105">**解決方法:** ビルド出力ウィンドウは、ビルドが完了するまで更新されません。</span><span class="sxs-lookup"><span data-stu-id="17e0b-105">**Resolution:** The build output window isn't updated until the build completes.</span></span> <span data-ttu-id="17e0b-106">ビルドには数分かかる場合があるため、更新が表示されるまでに遅延が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="17e0b-106">Build times may be up to several minutes, so you might experience a delay in seeing the updates.</span></span>  
  
-   <span data-ttu-id="17e0b-107">**問題:** ARM 用のアプリの製品ビルド時間が長くなった。</span><span class="sxs-lookup"><span data-stu-id="17e0b-107">**Issue:** Your app’s retail build time for ARM has increased.</span></span>  
  
     <span data-ttu-id="17e0b-108">**解決方法:** ARM デバイスにアプリを配置する場合、[!INCLUDE[net_native](../../../includes/net-native-md.md)] インフラストラクチャが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="17e0b-108">**Resolution:** When you deploy an app to your ARM device, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] infrastructure is invoked.</span></span> <span data-ttu-id="17e0b-109">このコンパイルは、リフレクションなどの非静的セマンティクスの実行が継続された状態で、多数の最適化を実行します。</span><span class="sxs-lookup"><span data-stu-id="17e0b-109">This compilation performs a large number of optimizations while ensuring that non-static semantics such as reflection continue to work.</span></span> <span data-ttu-id="17e0b-110">さらに、パフォーマンスの最適化のために、.NET Framework でアプリが使用する部分は静的リンクされるため、コンパイルしてネイティブ コードにも含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="17e0b-110">In addition, the portion of the .NET Framework that the app uses is statically linked in for optimal performance and has to be compiled into native code as well.</span></span> <span data-ttu-id="17e0b-111">このため、コンパイルの時間が長くなります。</span><span class="sxs-lookup"><span data-stu-id="17e0b-111">This is why compilation takes longer.</span></span>  
  
     <span data-ttu-id="17e0b-112">ただし、標準的な開発用コンピューター上で、ほとんどのアプリの標準的なコンパイルにかかる時間は 1 分以内です。</span><span class="sxs-lookup"><span data-stu-id="17e0b-112">However, compilation times are still within a minute of standard compilation for most apps on a standard development machine.</span></span>  <span data-ttu-id="17e0b-113">通常、標準的な開発用コンピューターでは、.NET Framework のネイティブ イメージを生成するだけで数分かかります。</span><span class="sxs-lookup"><span data-stu-id="17e0b-113">Typically, just generating native images for the .NET Framework on a standard development machine takes several minutes.</span></span>  <span data-ttu-id="17e0b-114">生成されるコードを改善するための最適化をすべて行い、.NET Framework を含めても、通常、アプリのビルド時間は 1 ～ 2 分です。</span><span class="sxs-lookup"><span data-stu-id="17e0b-114">Even with all the optimizations to improve the generated code and with including the .NET Framework, app build times are typically a minute or two.</span></span>  
  
     <span data-ttu-id="17e0b-115">現在も、マルチスレッド コンパイルやその他の最適化を調査して、コンパイルのパフォーマンスを改善する取り組みが続いています。</span><span class="sxs-lookup"><span data-stu-id="17e0b-115">We are continuing to work on improving compilation performance by investigating multi-threaded compilation and other optimizations.</span></span>  
  
-   <span data-ttu-id="17e0b-116">**問題:** アプリが [!INCLUDE[net_native](../../../includes/net-native-md.md)] を使用してコンパイルされたかどうかわからない。</span><span class="sxs-lookup"><span data-stu-id="17e0b-116">**Issue:** You don’t know if your app was compiled using [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
     <span data-ttu-id="17e0b-117">**解決方法:** [!INCLUDE[net_native](../../../includes/net-native-md.md)] コンパイラが起動された場合、ビルド時間が長くなり、タスク マネージャーに ILC.exe や nutc_driver.exe などのさまざまな [!INCLUDE[net_native](../../../includes/net-native-md.md)] コンポーネント プロセスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="17e0b-117">**Resolution:** If the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler is invoked, you'll notice longer build times, and Task Manager will show various [!INCLUDE[net_native](../../../includes/net-native-md.md)] component processes such as ILC.exe and nutc_driver.exe.</span></span>  
  
     <span data-ttu-id="17e0b-118">[!INCLUDE[net_native](../../../includes/net-native-md.md)] でのプロジェクトのビルドが正常に完了すると、obj\\*config*\ *arch*\\*projectname*.ilc\out に出力が生成されます。最終的なネイティブ パッケージ コンテンツは、bin\\*arch*\\*config*\AppX にあります。</span><span class="sxs-lookup"><span data-stu-id="17e0b-118">After you successfully build your project with [!INCLUDE[net_native](../../../includes/net-native-md.md)], you'll find the output under obj\\*config*\ *arch*\\*projectname*.ilc\out.  The final native package contents can be found under bin\\*arch*\\*config*\AppX.</span></span> <span data-ttu-id="17e0b-119">アプリを配置した場合、最終的なネイティブ パッケージ コンテンツは \bin\\*arch*\\*config*\AppX にあります。</span><span class="sxs-lookup"><span data-stu-id="17e0b-119">The final native package contents are under \bin\\*arch*\\*config*\AppX if you have deployed the app.</span></span>  
  
-   <span data-ttu-id="17e0b-120">**問題:** .NET Native を使用してアプリをコンパイルすると、.NET Native を使用せずにコンパイルしたときにはスローされないランタイム例外 (通常は [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) または [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外) がスローされる。</span><span class="sxs-lookup"><span data-stu-id="17e0b-120">**Issue:** Your .NET Native-compiled app is throwing runtime exceptions (typically [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) or [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions) that it did not throw when compiled without .NET Native.</span></span>  
  
     <span data-ttu-id="17e0b-121">**解決方法:** これらの例外は、リフレクションを介して使用できるはずのメタデータまたは実装コードが .NET Native では提供されなかったためにスローされます </span><span class="sxs-lookup"><span data-stu-id="17e0b-121">**Resolution:** The exceptions are thrown because .NET Native did not provide either the metadata or the implementation code that is otherwise available through reflection.</span></span> <span data-ttu-id="17e0b-122">(詳細については、「[.NET ネイティブとコンパイル](../../../docs/framework/net-native/net-native-and-compilation.md)」を参照してください)。例外を取り除くには、[ランタイム ディレクティブ (rd.xml) ファイル](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)にエントリを追加して、.NET Native ツール チェーンがメタデータまたは実装コードを実行時に使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="17e0b-122">(For more information, see [.NET Native and Compilation](../../../docs/framework/net-native/net-native-and-compilation.md).) To eliminate the exception, you have to add an entry to your [runtime directives (rd.xml) file](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md) so that the .NET Native tool chain can make the metadata or implementation code available at runtime.</span></span> <span data-ttu-id="17e0b-123">次の 2 つのトラブルシューティング ツールを使用して、ランタイム ディレクティブ ファイルに追加する必要があるエントリを生成できます。</span><span class="sxs-lookup"><span data-stu-id="17e0b-123">Two troubleshooters are available that will generate the necessary entry to add to your runtime directives file:</span></span>  
  
    -   <span data-ttu-id="17e0b-124">[MissingMetadataException トラブルシューティング ツール](http://dotnet.github.io/native/troubleshooter/type.html) (型の場合)。</span><span class="sxs-lookup"><span data-stu-id="17e0b-124">The [MissingMetadataException troubleshooter](http://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>  
  
    -   <span data-ttu-id="17e0b-125">[MissingMetadataException トラブルシューティング ツール](http://dotnet.github.io/native/troubleshooter/method.html) (メソッドの場合)。</span><span class="sxs-lookup"><span data-stu-id="17e0b-125">The [MissingMetadataException troubleshooter](http://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>  
  
     <span data-ttu-id="17e0b-126">詳細については、「[リフレクションおよび .NET ネイティブ](../../../docs/framework/net-native/reflection-and-net-native.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17e0b-126">For more information, see [Reflection and .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e0b-127">参照</span><span class="sxs-lookup"><span data-stu-id="17e0b-127">See Also</span></span>  
 [<span data-ttu-id="17e0b-128">Windows ストア アプリの .NET ネイティブへの移行</span><span class="sxs-lookup"><span data-stu-id="17e0b-128">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
