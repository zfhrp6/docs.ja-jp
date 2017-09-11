---
title: "軽減策: EventSource.WriteEvent メソッドの呼び出し"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 327a9fdb-ba8e-40f7-89e5-4c89b46e594f
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 270f89183bced5d07598b1731f18acf90ec9715a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-eventsourcewriteevent-method-calls"></a><span data-ttu-id="825af-102">軽減策: EventSource.WriteEvent メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="825af-102">Mitigation: EventSource.WriteEvent Method Calls</span></span>
<span data-ttu-id="825af-103">[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] は、 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> から派生したクラスの ETW イベント メソッドと基底クラスの <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> メソッド間のコントラクトを強制します。</span><span class="sxs-lookup"><span data-stu-id="825af-103">The [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] enforces a contract between an ETW event method in a class that is derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> and  the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method of its base class.</span></span> <span data-ttu-id="825af-104">ETW イベント メソッドは、 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> メソッドをイベント メソッドに渡された同じ引数が続くイベント ID に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="825af-104">The ETW event method must pass the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method the event ID followed by the same arguments that were passed to the event method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="825af-105">影響</span><span class="sxs-lookup"><span data-stu-id="825af-105">Impact</span></span>  
 <span data-ttu-id="825af-106">次の方法で定義される ETW イベント メソッドはコントラクトを中断します。</span><span class="sxs-lookup"><span data-stu-id="825af-106">An ETW event method defined in the following way breaks the contract:</span></span>  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message, "-");  
}  
```  
  
 <span data-ttu-id="825af-107">このコントラクトに違反している場合、 <xref:System.IndexOutOfRangeException> オブジェクトが進行中の <xref:System.Diagnostics.Tracing.EventListener> データを読み取ると <xref:System.Diagnostics.Tracing.EventSource> 例外が実行時にスローされます。</span><span class="sxs-lookup"><span data-stu-id="825af-107">When this contract is violated, an <xref:System.IndexOutOfRangeException> exception is thrown at run time if an <xref:System.Diagnostics.Tracing.EventListener> object reads <xref:System.Diagnostics.Tracing.EventSource> data in process.</span></span>  
  
 <span data-ttu-id="825af-108">この ETW イベント メソッドの定義は、次のパターンに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="825af-108">The definition for this ETW event method should follow this pattern:</span></span>  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message);  
}  
```  
  
## <a name="mitigation"></a><span data-ttu-id="825af-109">軽減策</span><span class="sxs-lookup"><span data-stu-id="825af-109">Mitigation</span></span>  
 <span data-ttu-id="825af-110">必要なパターンに準拠するように既存のコードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="825af-110">You must modify existing code to conform to the required pattern.</span></span>  
  
 <span data-ttu-id="825af-111">次のように、 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> メソッドを呼び出すための 2 つのメソッドを定義して変更する必要があるコードの量を次のように最小限にできます。</span><span class="sxs-lookup"><span data-stu-id="825af-111">You can minimize the amount of code that you have to change by defining two methods for calling the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method, as follows:</span></span>  
  
```  
[NonEvent]  
public void Info2(string message)  
{  
   Info2Internal(message, "-");  
}  
  
public void Info2Internal(string message, string prefix)  
{  
   WriteEvent(2, message, prefix);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="825af-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="825af-112">See Also</span></span>  
 [<span data-ttu-id="825af-113">ランタイムの変更点</span><span class="sxs-lookup"><span data-stu-id="825af-113">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)

