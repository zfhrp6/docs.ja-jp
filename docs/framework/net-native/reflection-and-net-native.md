---
title: "リフレクションおよび .NET ネイティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e248071a0d35c5552976e5e4663094b76ee162e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="reflection-and-net-native"></a><span data-ttu-id="2ffd9-102">リフレクションおよび .NET ネイティブ</span><span class="sxs-lookup"><span data-stu-id="2ffd9-102">Reflection and .NET Native</span></span>
<span data-ttu-id="2ffd9-103">.NET Framework では、マネージ開発はリフレクション API を介してメタプログラミングをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-103">In the .NET Framework, managed development supports metaprogramming through the reflection API.</span></span> <span data-ttu-id="2ffd9-104">リフレクションによって、アプリ内のオブジェクトの検査、検査で検出されたオブジェクトでのメソッドの呼び出し、実行時の新しい型の生成、およびその他多数の動的コード シナリオのサポートが可能になります。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-104">Reflection allows you to inspect objects in an app, call methods on objects discovered through inspection, generate new types at run time, and supports many other dynamic code scenarios.</span></span> <span data-ttu-id="2ffd9-105">シリアル化と逆シリアル化もサポートしているため、オブジェクトのフィールド値を保持して、後で復元できます。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-105">It also supports serialization and deserialization, which allows an object's field values to be persisted and later restored.</span></span> <span data-ttu-id="2ffd9-106">これらすべてのシナリオで、使用可能なメタデータに基づいてネイティブ コードを生成するために .NET Framework Just-In-Time (JIT) コンパイラが必要です。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-106">These scenarios all require the .NET Framework just-in-time (JIT) compiler to generate native code based on available metadata.</span></span>  
  
 <span data-ttu-id="2ffd9-107">[!INCLUDE[net_native](../../../includes/net-native-md.md)] ランタイムには JIT コンパイラは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-107">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime doesn't include a JIT compiler.</span></span> <span data-ttu-id="2ffd9-108">そのため、必要なネイティブ コードすべてを事前に生成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-108">As a result, all necessary native code must be generated in advance.</span></span> <span data-ttu-id="2ffd9-109">生成するコードを決定するために一連のヒューリスティックが使用されますが、これらのヒューリスティックでは、可能性のあるすべてのメタプログラミング シナリオに対処できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-109">A set of heuristics is used to determine what code should be generated, but these heuristics cannot cover all possible metaprogramming scenarios.</span></span>  <span data-ttu-id="2ffd9-110">このため、[ランタイム ディレクティブ](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)を使って、これらのメタプログラミング シナリオにヒントを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-110">Therefore, you must provide hints for these metaprogramming scenarios by using [runtime directives](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span> <span data-ttu-id="2ffd9-111">必要なメタデータまたは実装コードを実行時に使うことができない場合、アプリは [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)、[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)、または [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-111">If the necessary metadata or implementation code is not available at runtime, your app throws a [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), or [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) exception.</span></span> <span data-ttu-id="2ffd9-112">次の 2 つのトラブルシューティング ツールを使用すると、この例外を排除するランタイム ディレクティブ ファイルの適切なエントリが生成されます。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-112">Two troubleshooters are available that will generate the appropriate entry for your runtime directives file that eliminates the exception:</span></span>  
  
-   <span data-ttu-id="2ffd9-113">[MissingMetadataException トラブルシューティング ツール](http://dotnet.github.io/native/troubleshooter/type.html) (型の場合)。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-113">The [MissingMetadataException troubleshooter](http://dotnet.github.io/native/troubleshooter/type.html) for types.</span></span>  
  
-   <span data-ttu-id="2ffd9-114">[MissingMetadataException トラブルシューティング ツール](http://dotnet.github.io/native/troubleshooter/method.html) (メソッドの場合)。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-114">The [MissingMetadataException troubleshooter](http://dotnet.github.io/native/troubleshooter/method.html) for methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ffd9-115">ランタイム ディレクティブ ファイルが必要となる理由の背景を含む .NET ネイティブのコンパイルの概要については、「 [.NET ネイティブとコンパイル](../../../docs/framework/net-native/net-native-and-compilation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-115">For an overview of the .NET Native compilation process that provides background on why a runtime directives file is needed, see [.NET Native and Compilation](../../../docs/framework/net-native/net-native-and-compilation.md).</span></span>  
  
 <span data-ttu-id="2ffd9-116">また、[!INCLUDE[net_native](../../../includes/net-native-md.md)]では、.NET Framework クラス ライブラリのプライベート メンバーに対するリフレクションを実行できません。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-116">In addition, [!INCLUDE[net_native](../../../includes/net-native-md.md)] doesn't allow you to reflect over private members of the .NET Framework class library.</span></span> <span data-ttu-id="2ffd9-117">たとえば、.NET Framework クラス ライブラリ型のフィールドを取得するために <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> プロパティを呼び出すと、パブリックまたはプロテクト フィールドのみが返されます。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-117">For example, a call to the <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> property to retrieve the fields of a .NET Framework class library type returns only public or protected fields.</span></span>  
  
 <span data-ttu-id="2ffd9-118">次のトピックに、アプリでリフレクションとシリアル化をサポートするために必要な概念を説明したドキュメントとリファレンス ドキュメントを示します。</span><span class="sxs-lookup"><span data-stu-id="2ffd9-118">The following topics provide the conceptual and reference documentation that you need to support reflection and serialization in your apps:</span></span>  
  
-   [<span data-ttu-id="2ffd9-119">リフレクションに依存する API</span><span class="sxs-lookup"><span data-stu-id="2ffd9-119">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [<span data-ttu-id="2ffd9-120">リフレクション API リファレンス</span><span class="sxs-lookup"><span data-stu-id="2ffd9-120">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [<span data-ttu-id="2ffd9-121">ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス</span><span class="sxs-lookup"><span data-stu-id="2ffd9-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="2ffd9-122">参照</span><span class="sxs-lookup"><span data-stu-id="2ffd9-122">See Also</span></span>  
 [<span data-ttu-id="2ffd9-123">.NET ネイティブによるアプリのコンパイル</span><span class="sxs-lookup"><span data-stu-id="2ffd9-123">Compiling Apps with .NET Native</span></span>](../../../docs/framework/net-native/index.md)  
 [<span data-ttu-id="2ffd9-124">.NET ネイティブとコンパイル</span><span class="sxs-lookup"><span data-stu-id="2ffd9-124">.NET Native and Compilation</span></span>](../../../docs/framework/net-native/net-native-and-compilation.md)
