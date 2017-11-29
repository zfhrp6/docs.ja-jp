---
title: moduloObjectHashcode MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1a3062365f41247c579f5420497946128b183a88
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="b21e9-102">moduloObjectHashcode MDA</span><span class="sxs-lookup"><span data-stu-id="b21e9-102">moduloObjectHashcode MDA</span></span>
<span data-ttu-id="b21e9-103">`moduloObjectHashcode` マネージ デバッグ アシスタント (MDA) は、<xref:System.Object.GetHashCode%2A> メソッドによって返されるハッシュ コードに対してモジュロ演算を実行するように、<xref:System.Object> クラスの動作を変更します。</span><span class="sxs-lookup"><span data-stu-id="b21e9-103">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="b21e9-104">この MDA の既定の係数は 1 であり、これにより <xref:System.Object.GetHashCode%2A> はすべてのオブジェクトに対して 0 を返すようになります。</span><span class="sxs-lookup"><span data-stu-id="b21e9-104">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="b21e9-105">症状</span><span class="sxs-lookup"><span data-stu-id="b21e9-105">Symptoms</span></span>  
 <span data-ttu-id="b21e9-106">新しいバージョンの共通言語ランタイム (CLR) に移行すると、プログラムが正しく動作しなくなります。</span><span class="sxs-lookup"><span data-stu-id="b21e9-106">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
-   <span data-ttu-id="b21e9-107">プログラムは、<xref:System.Collections.Hashtable> から正しくないオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="b21e9-107">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
-   <span data-ttu-id="b21e9-108"><xref:System.Collections.Hashtable> からの列挙の順序に、プログラムが動作しなくなる変更があります。</span><span class="sxs-lookup"><span data-stu-id="b21e9-108">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
-   <span data-ttu-id="b21e9-109">以前は等しかった 2 つのオブジェクトが、等しくなくなっています。</span><span class="sxs-lookup"><span data-stu-id="b21e9-109">Two objects that used to be equal are no longer equal.</span></span>  
  
-   <span data-ttu-id="b21e9-110">以前は等しくなかった 2 つのオブジェクトが、等しくなっています。</span><span class="sxs-lookup"><span data-stu-id="b21e9-110">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="b21e9-111">原因</span><span class="sxs-lookup"><span data-stu-id="b21e9-111">Cause</span></span>  
 <span data-ttu-id="b21e9-112"><xref:System.Collections.Hashtable> へのキーに対するクラスの <xref:System.Object.Equals%2A> メソッドの実装は、<xref:System.Object.GetHashCode%2A> メソッドの呼び出しの結果を比較することによりオブジェクトの等価性をテストするため、プログラムが <xref:System.Collections.Hashtable> から正しくないオブジェクトを取得している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b21e9-112">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="b21e9-113">それぞれのフィールドの値が異なる場合であっても、2 つのオブジェクトのハッシュ コードが同じになる場合があるので、オブジェクトの等価性のテストにハッシュ コードを使うことはできません。</span><span class="sxs-lookup"><span data-stu-id="b21e9-113">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="b21e9-114">実際にはまれなことですが、ハッシュ コードの衝突が発生します。</span><span class="sxs-lookup"><span data-stu-id="b21e9-114">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="b21e9-115">このことによる <xref:System.Collections.Hashtable> のルックアップへの影響としては、等しくない 2 つのキーが等しいものと見なされ、正しくないオブジェクトが <xref:System.Collections.Hashtable> から返されます。</span><span class="sxs-lookup"><span data-stu-id="b21e9-115">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="b21e9-116">パフォーマンス上の理由から、<xref:System.Object.GetHashCode%2A> の実装はランタイム バージョンによって変更される場合があり、あるバージョンでは発生しない競合が後のバージョンでは発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b21e9-116">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="b21e9-117">ハッシュ コードが競合するときのバグがコードにあるかどうかをテストするには、この MDA を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b21e9-117">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="b21e9-118">この MDA を有効にすると、<xref:System.Object.GetHashCode%2A> メソッドは 0 を返すようになり、結果としてすべてのハッシュ コードが競合します。</span><span class="sxs-lookup"><span data-stu-id="b21e9-118">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="b21e9-119">この MDA を有効にすることによるプログラムへの唯一の影響は、プログラムの実行が遅くなることです。</span><span class="sxs-lookup"><span data-stu-id="b21e9-119">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="b21e9-120">キー変更のハッシュ コードの計算に使われるアルゴリズムがランタイムのあるバージョンから別のバージョンに変更された場合、<xref:System.Collections.Hashtable> からの列挙の順序が変わる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b21e9-120">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="b21e9-121">ハッシュ テーブルからのキーまたは値の列挙順序にプログラムが依存しているかどうかは、この MDA を有効にすることでテストできます。</span><span class="sxs-lookup"><span data-stu-id="b21e9-121">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="b21e9-122">解像度</span><span class="sxs-lookup"><span data-stu-id="b21e9-122">Resolution</span></span>  
 <span data-ttu-id="b21e9-123">オブジェクト ID の代わりに、ハッシュ コードを使わないでください。</span><span class="sxs-lookup"><span data-stu-id="b21e9-123">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="b21e9-124">ハッシュ コードを比較しないように、<xref:System.Object.Equals%2A?displayProperty=nameWithType> メソッドのオーバーライドを実装します。</span><span class="sxs-lookup"><span data-stu-id="b21e9-124">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="b21e9-125">ハッシュ テーブル内のキーまたは値の列挙の順序への依存関係を作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="b21e9-125">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="b21e9-126">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="b21e9-126">Effect on the Runtime</span></span>  
 <span data-ttu-id="b21e9-127">この MDA を有効にすると、アプリケーションの速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="b21e9-127">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="b21e9-128">この MDA は、返されたハッシュ コードを取得し、代わりに係数で除算したときの余りを返します。</span><span class="sxs-lookup"><span data-stu-id="b21e9-128">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="b21e9-129">出力</span><span class="sxs-lookup"><span data-stu-id="b21e9-129">Output</span></span>  
 <span data-ttu-id="b21e9-130">この MDA に出力はありません。</span><span class="sxs-lookup"><span data-stu-id="b21e9-130">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="b21e9-131">構成</span><span class="sxs-lookup"><span data-stu-id="b21e9-131">Configuration</span></span>  
 <span data-ttu-id="b21e9-132">`modulus` 属性では、ハッシュ コードで使う係数を指定します。</span><span class="sxs-lookup"><span data-stu-id="b21e9-132">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="b21e9-133">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="b21e9-133">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b21e9-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="b21e9-134">See Also</span></span>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.Equals%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="b21e9-135">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="b21e9-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
