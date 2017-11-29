---
title: "セキュリティと競合状態"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c092113f670c5799d98dcb13c9c713bbd1a47fb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="b7c68-102">セキュリティと競合状態</span><span class="sxs-lookup"><span data-stu-id="b7c68-102">Security and Race Conditions</span></span>
<span data-ttu-id="b7c68-103">問題の別の領域は、競合状態によって生じるセキュリティ ホールが発生する可能性です。</span><span class="sxs-lookup"><span data-stu-id="b7c68-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="b7c68-104">これが発生するいくつかの方法はあります。</span><span class="sxs-lookup"><span data-stu-id="b7c68-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="b7c68-105">次のサブトピックをアウトラインの主要な落とし穴を開発者が回避する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7c68-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="b7c68-106">Dispose メソッドでの競合状態</span><span class="sxs-lookup"><span data-stu-id="b7c68-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="b7c68-107">クラスの場合**Dispose**メソッド (詳細については、次を参照してください[ガベージ コレクション](../../../docs/standard/garbage-collection/index.md)) が同期されていない可能性が内のそのクリーンアップ コード**Dispose**実行できる複数の。1 回、次の例で示すようにします。</span><span class="sxs-lookup"><span data-stu-id="b7c68-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()   
{  
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="b7c68-108">この**Dispose**実装が同期されていない、可能性が`Cleanup`によって最初に 1 つのスレッドとし、2 番目のスレッドの前に呼び出される`_myObj`に設定されている**null**です。</span><span class="sxs-lookup"><span data-stu-id="b7c68-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="b7c68-109">動作に依存これは、セキュリティが脅かされるかどうかと、`Cleanup`コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="b7c68-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="b7c68-110">非同期の主な課題**Dispose**実装は、ファイルなどのリソース ハンドルを使用します。</span><span class="sxs-lookup"><span data-stu-id="b7c68-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="b7c68-111">不適切な廃棄には、間違ったを識別するハンドルを使用する多くの場合、セキュリティの脆弱性につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b7c68-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="b7c68-112">コンス トラクターでの競合状態</span><span class="sxs-lookup"><span data-stu-id="b7c68-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="b7c68-113">一部のアプリケーションでは、そのクラス コンス トラクターが完全に実行する前にクラス メンバーにアクセスするには、他のスレッドがあります。</span><span class="sxs-lookup"><span data-stu-id="b7c68-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="b7c68-114">すべてのクラス コンス トラクターがないセキュリティの問題が発生するか必要な場合は、スレッドを同期場合かどうかを確認するを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7c68-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="b7c68-115">キャッシュされたオブジェクトの競合状態</span><span class="sxs-lookup"><span data-stu-id="b7c68-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="b7c68-116">セキュリティ情報をキャッシュしたり、コード アクセス セキュリティを使用するコード[Assert](../../../docs/framework/misc/using-the-assert-method.md)操作される恐れがありますも競合状態、クラスの他の部分が適切に同期していない場合、次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="b7c68-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()   
{  
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
    {  
        DoSomethingTrusted();  
    }  
    else   
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 <span data-ttu-id="b7c68-117">その他のパスがある場合`DoOtherWork`同一のオブジェクトと別のスレッドから呼び出すことができますを過去の需要、信頼されていない呼び出し元がずれることです。</span><span class="sxs-lookup"><span data-stu-id="b7c68-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="b7c68-118">コードがセキュリティ情報をキャッシュする場合は、この脆弱性を確認することを確認します。</span><span class="sxs-lookup"><span data-stu-id="b7c68-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="b7c68-119">ファイナライザーでの競合状態</span><span class="sxs-lookup"><span data-stu-id="b7c68-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="b7c68-120">競合状態は、そのファイナライザーで解放し、静的またはアンマネージ リソースを参照するオブジェクトでも発生することができます。</span><span class="sxs-lookup"><span data-stu-id="b7c68-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="b7c68-121">複数のオブジェクトは、クラスのファイナライザーで操作されるリソースを共有している場合、オブジェクトは、そのリソースへのすべてのアクセスを同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7c68-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c68-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7c68-122">See Also</span></span>  
 [<span data-ttu-id="b7c68-123">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b7c68-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
