---
title: ".NET Framework クラス ライブラリの互換性のために残されている機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7afe9496ca116ed0c330c4ff9e7c3a855249cf14
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="what39s-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="a3dd4-102">.NET Framework クラス ライブラリの互換性のために残されている機能</span><span class="sxs-lookup"><span data-stu-id="a3dd4-102">What&#39;s Obsolete in the .NET Framework Class Library</span></span>
<span data-ttu-id="a3dd4-103">.NET Framework は進化しています。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-103">The .NET Framework changes over time.</span></span> <span data-ttu-id="a3dd4-104">バージョンが新しくなるたびに、新しい機能を提供する新しい型と新しいメンバーが追加されています。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="a3dd4-105">既存の型とそのメンバーも変更されています。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="a3dd4-106">たとえば、一部の型は、その型がサポートするテクノロジが新しいテクノロジに置き換えられることで重要度が下がり、一部のメソッドは、より便利な新しいメソッドまたはより多くの機能を備えた新しいメソッドに置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are either more convenient or more full-featured.</span></span>  
  
 <span data-ttu-id="a3dd4-107">.NET Framework と共通言語ランタイムでは、下位互換性をサポートするように努めています (.NET Framework の特定のバージョンで開発したアプリケーションを、.NET Framework の次期バージョンで実行できるようにするためです)。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-107">The .NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of the .NET Framework to run on the next version of the .NET Framework).</span></span> <span data-ttu-id="a3dd4-108">そのため、型または型のメンバーを単純に削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="a3dd4-109">そこで、.NET Framework では、型または型のメンバーが使用されなくなったことを示すために、その型またはメンバーを旧式 (互換性のために残されている) または非推奨として指定しています。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-109">Instead, the .NET Framework indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="a3dd4-110">型またはメンバーを非推奨とする場合は、開発者がその型またはメンバーが削除予定であることを認識してその削除に対応できるように、指定を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="a3dd4-111">ただし、そのような型またはメンバーを使用する既存のコードは、.NET Framework の次期バージョンで引き続き実行できます。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-111">However, existing code that uses the type or member continues to run in the new version of the .NET Framework.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3dd4-112">*旧式*と*非推奨*という用語は、.NET Framework の型とメンバーに対して使用する場合は同じ意味です。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-112">The terms *obsolete* and *deprecated* have the same meaning when applied to the types and members of the .NET Framework.</span></span>  
  
## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="a3dd4-113">ObsoleteAttribute 属性</span><span class="sxs-lookup"><span data-stu-id="a3dd4-113">The ObsoleteAttribute Attribute</span></span>  
 <span data-ttu-id="a3dd4-114">.NET Framework では、型または型のメンバーが旧式であることを示すために、その型またはメンバーに <xref:System.ObsoleteAttribute> 属性を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="a3dd4-115">この属性が型またはメンバーに適用されている場合、その型またはメンバーは .NET Framework の将来のバージョンで削除される予定であることを意味します。ただし、そのメンバーを使用するコンパイル済みコードに影響はありません。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-115">Applying the attribute to a type or member indicates that that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>  
  
 <span data-ttu-id="a3dd4-116">型または型のメンバーが旧式であることを示す以外に、<xref:System.ObsoleteAttribute> は、その型またはメンバーが含まれているソース コードをコンパイラで処理する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="a3dd4-117">コードをコンパイルするが警告メッセージを出力するようにすることも、旧式の型またはメンバーの使用をエラーとして扱うこともできます。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="a3dd4-118">前者の場合、コードを正常にコンパイルできますが、警告メッセージによって型またはメンバーが旧式であることが示されます。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="a3dd4-119">後者の場合、コンパイルは失敗します。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-119">In the second case, compilation fails.</span></span>  
  
 <span data-ttu-id="a3dd4-120">コンパイルで警告メッセージではなくエラーが生成される場合でも、<xref:System.ObsoleteAttribute> は実行時の動作には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="a3dd4-121">つまり、旧式の型またはメンバーを使用しているが正常にコンパイルされたアプリケーションは、常に正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="a3dd4-122">旧式の型またはメンバーを使用するアプリケーションを再コンパイルしようとした場合にのみ失敗します。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>  
  
## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="a3dd4-123">旧式の型とメンバーを処理する方法</span><span class="sxs-lookup"><span data-stu-id="a3dd4-123">How to Handle Obsolete Types and Members</span></span>  
 <span data-ttu-id="a3dd4-124">既存のコードをアップグレードし、再コンパイルする場合に、コンパイラの警告を生成する旧式の型またはメンバーをアプリケーションで使用しても、まったく問題ありません。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="a3dd4-125">ただし、コンパイラの警告メッセージを確認して、アプリケーション コードを変更する必要があるかどうか判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="a3dd4-126">代わりとなる適切な方法がメッセージに示されていない場合は、次のいずれかの操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>  
  
-   <span data-ttu-id="a3dd4-127">可能であれば、コードを変更して旧式の型またはメンバーの使用を止めます。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-127">Change your code by removing the use of the type or member, if possible.</span></span>  
  
     <span data-ttu-id="a3dd4-128">または</span><span class="sxs-lookup"><span data-stu-id="a3dd4-128">-or-</span></span>  
  
-   <span data-ttu-id="a3dd4-129">このテクノロジ分野に関するドキュメントを確認して、非推奨の機能の使用に対する対応方法を決定します。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>  
  
 <span data-ttu-id="a3dd4-130">既存のコードは、.NET Framework の新しいバージョンに対して再コンパイルすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="a3dd4-131">代わりに、既存のコンパイル済みコードの実行対象である .NET Framework のバージョンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="a3dd4-132">たとえば、[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] に対してコンパイルされた app1.exe というアプリケーションがあり、このアプリケーションを [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] を対象に実行する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-132">For example, suppose that you have an application named app1.exe that was compiled against the [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], but you want the application to run against the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="a3dd4-133">この場合、次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-133">This requires the following steps:</span></span>  
  
1.  <span data-ttu-id="a3dd4-134">メイン実行可能ファイルの構成ファイルを作成し、その名前を *appName*.exe.config にします。*appName* は、アプリケーションの実行可能ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="a3dd4-135">このトピックの例の app1.exe というアプリケーションの場合は、app1.exe.config という名前の構成ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-135">For the application named app1.exe in our example, you would create a configuration file named app1.exe.config.</span></span>  
  
2.  <span data-ttu-id="a3dd4-136">次のコードを構成ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-136">Add the following to the configuration file.</span></span>  
  
    ```xml  
    <configuration>  
       <startup>   
          <supportedRuntime version="v4.0" />  
       </startup>  
    </configuration>  
    ```  
  
 <span data-ttu-id="a3dd4-137">.NET Framework の特定のバージョンを対象とするために `version` 属性に割り当てることができる文字列値を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="a3dd4-137">The following table lists the string values that you can assign to the `version` attribute to target a specific version of the .NET Framework.</span></span>  
  
|<span data-ttu-id="a3dd4-138">.NET Framework のバージョン</span><span class="sxs-lookup"><span data-stu-id="a3dd4-138">.NET Framework version</span></span>|<span data-ttu-id="a3dd4-139">`version` 文字列</span><span class="sxs-lookup"><span data-stu-id="a3dd4-139">`version` string</span></span>|
|-|-|  
|<span data-ttu-id="a3dd4-140">4.7</span><span class="sxs-lookup"><span data-stu-id="a3dd4-140">4.7</span></span>|<span data-ttu-id="a3dd4-141">v4.0</span><span class="sxs-lookup"><span data-stu-id="a3dd4-141">v4.0</span></span>|  
|<span data-ttu-id="a3dd4-142">4.6 (4.6.1 と 4.6.2 を含む)</span><span class="sxs-lookup"><span data-stu-id="a3dd4-142">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="a3dd4-143">v4.0</span><span class="sxs-lookup"><span data-stu-id="a3dd4-143">v4.0</span></span>|  
|<span data-ttu-id="a3dd4-144">4.5 (4.5.1 および 4.5.2 を含む)</span><span class="sxs-lookup"><span data-stu-id="a3dd4-144">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="a3dd4-145">v4.0</span><span class="sxs-lookup"><span data-stu-id="a3dd4-145">v4.0</span></span>|  
|<span data-ttu-id="a3dd4-146">4</span><span class="sxs-lookup"><span data-stu-id="a3dd4-146">4</span></span>|<span data-ttu-id="a3dd4-147">v4.0</span><span class="sxs-lookup"><span data-stu-id="a3dd4-147">v4.0</span></span>|  
|<span data-ttu-id="a3dd4-148">3.5</span><span class="sxs-lookup"><span data-stu-id="a3dd4-148">3.5</span></span>|<span data-ttu-id="a3dd4-149">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="a3dd4-149">v2.0.50727</span></span>|  
|<span data-ttu-id="a3dd4-150">2.0</span><span class="sxs-lookup"><span data-stu-id="a3dd4-150">2.0</span></span>|<span data-ttu-id="a3dd4-151">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="a3dd4-151">v2.0.50727</span></span>|  
|<span data-ttu-id="a3dd4-152">1.1</span><span class="sxs-lookup"><span data-stu-id="a3dd4-152">1.1</span></span>|<span data-ttu-id="a3dd4-153">v1.1.4322</span><span class="sxs-lookup"><span data-stu-id="a3dd4-153">v1.1.4322</span></span>|  
|<span data-ttu-id="a3dd4-154">1</span><span class="sxs-lookup"><span data-stu-id="a3dd4-154">1.0</span></span>|<span data-ttu-id="a3dd4-155">v1.0.3705</span><span class="sxs-lookup"><span data-stu-id="a3dd4-155">v1.0.3705</span></span>|  
  
## <a name="obsolete-lists-for-the-net-framework-45-and-46"></a><span data-ttu-id="a3dd4-156">.NET Framework 4.5 および 4.6 の互換性のために残されている機能の一覧</span><span class="sxs-lookup"><span data-stu-id="a3dd4-156">Obsolete Lists for the .NET Framework 4.5 and 4.6</span></span>  
 [<span data-ttu-id="a3dd4-157">互換性のために残されている型</span><span class="sxs-lookup"><span data-stu-id="a3dd4-157">Obsolete Types</span></span>](../../../docs/framework/whats-new/obsolete-types.md)  
  
 [<span data-ttu-id="a3dd4-158">互換性のために残されているメンバー</span><span class="sxs-lookup"><span data-stu-id="a3dd4-158">Obsolete Members</span></span>](../../../docs/framework/whats-new/obsolete-members.md)  
  
## <a name="obsolete-lists-for-previous-versions"></a><span data-ttu-id="a3dd4-159">以前のバージョンの互換性のために残されている機能の一覧</span><span class="sxs-lookup"><span data-stu-id="a3dd4-159">Obsolete Lists for Previous Versions</span></span>  
 [<span data-ttu-id="a3dd4-160">.NET Framework 4 で互換性のために残されている型</span><span class="sxs-lookup"><span data-stu-id="a3dd4-160">Obsolete Types in the .NET Framework 4</span></span>](http://go.microsoft.com/fwlink/?LinkId=224224)  
  
 [<span data-ttu-id="a3dd4-161">.NET Framework 4 で互換性のために残されているメンバー</span><span class="sxs-lookup"><span data-stu-id="a3dd4-161">Obsolete Members in the .NET Framework 4</span></span>](http://go.microsoft.com/fwlink/?LinkId=224227)  
  
 [<span data-ttu-id="a3dd4-162">.NET Framework 3.5 Obsolete List (.NET Framework 3.5 の互換性のために残されている機能の一覧)</span><span class="sxs-lookup"><span data-stu-id="a3dd4-162">.NET Framework 3.5 Obsolete List</span></span>](http://go.microsoft.com/fwlink/?LinkId=163710)  
  
 [<span data-ttu-id="a3dd4-163">.NET Framework 2.0 Obsolete List (.NET Framework 2.0 の互換性のために残されている機能の一覧)</span><span class="sxs-lookup"><span data-stu-id="a3dd4-163">.NET Framework 2.0 Obsolete List</span></span>](http://go.microsoft.com/fwlink/?LinkID=125264)  
  
## <a name="see-also"></a><span data-ttu-id="a3dd4-164">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3dd4-164">See Also</span></span>  
 [<span data-ttu-id="a3dd4-165">\<<supportedRuntime> 要素</span><span class="sxs-lookup"><span data-stu-id="a3dd4-165">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)

