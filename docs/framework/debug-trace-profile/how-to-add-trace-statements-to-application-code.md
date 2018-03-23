---
title: '方法 : アプリケーション コードにトレース ステートメントを追加する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
caps.latest.revision: ''
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 134e03a1438e4c9399962a245eb44eec9dd02924
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="834ca-102">方法 : アプリケーション コードにトレース ステートメントを追加する</span><span class="sxs-lookup"><span data-stu-id="834ca-102">How to: Add Trace Statements to Application Code</span></span>
<span data-ttu-id="834ca-103">トレースで最も使用頻度の高いメソッドは、出力をリスナーに書き込むメソッドである **Write**、**WriteIf**、**WriteLine**、**WriteLineIf**、**Assert**、および **Fail** です。</span><span class="sxs-lookup"><span data-stu-id="834ca-103">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="834ca-104">これらのメソッドは、次の 2 つのカテゴリに分類できます。**Write**、**WriteLine**、および **Fail** はすべて出力を無条件に生成します。それに対して、**WriteIf**、**WriteLineIf**、および **Assert** はブール条件をテストし、条件の値に基づいて書き込みを行ったり行わなかったりします。</span><span class="sxs-lookup"><span data-stu-id="834ca-104">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="834ca-105">**WriteIf** と **WriteLineIf** は条件が `true` の場合に出力を生成し、**Assert** は条件が `false` の場合に出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="834ca-105">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="834ca-106">トレースおよびデバッグの方法をデザインするときは、出力の表示方法について検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="834ca-106">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="834ca-107">関連のない情報で埋め尽くされた複数の **Write** ステートメントの場合、読みにくいログが作成されます。</span><span class="sxs-lookup"><span data-stu-id="834ca-107">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="834ca-108">その一方で、**WriteLine** を使用して関連のあるステートメントを別々の行に出力すると、どの情報が関連し合っているかを読み取るのが困難になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="834ca-108">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="834ca-109">一般に、複数のソースからの情報を結合する場合には複数の **Write** ステートメントを使用して 1 つの情報メッセージを作成し、単一の完全なメッセージを作成する場合には **WriteLine** ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="834ca-109">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="834ca-110">完結した行を書き込むには</span><span class="sxs-lookup"><span data-stu-id="834ca-110">To write a complete line</span></span>  
  
1.  <span data-ttu-id="834ca-111"><xref:System.Diagnostics.Trace.WriteLine%2A> メソッドまたは <xref:System.Diagnostics.Trace.WriteLineIf%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="834ca-111">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="834ca-112">このメソッドが返すメッセージの末尾には、キャリッジ リターンが追加されます。したがって、次回の **Write**、**WriteIf**、**WriteLine**、または **WriteLineIf** が返すメッセージは、次の行から開始されます。</span><span class="sxs-lookup"><span data-stu-id="834ca-112">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,   
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="834ca-113">完結しない行を書き込むには</span><span class="sxs-lookup"><span data-stu-id="834ca-113">To write a partial line</span></span>  
  
1.  <span data-ttu-id="834ca-114"><xref:System.Diagnostics.Trace.Write%2A> メソッドまたは <xref:System.Diagnostics.Trace.WriteIf%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="834ca-114">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="834ca-115">**Write**、**WriteIf**、**WriteLine** または **WriteLineIf** によって次に書き込まれるメッセージは、今回の **Write** または **WriteIf** ステートメントによって書き込まれるメッセージと同じ行から開始されます。</span><span class="sxs-lookup"><span data-stu-id="834ca-115">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,   
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="834ca-116">メソッドの実行前または実行後に特定の条件が存在するかどうかを確認するには</span><span class="sxs-lookup"><span data-stu-id="834ca-116">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1.  <span data-ttu-id="834ca-117"><xref:System.Diagnostics.Trace.Assert%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="834ca-117">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="834ca-118">**Assert** は、トレースとデバッグの両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="834ca-118">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="834ca-119">この例では、呼び出し履歴を **Listeners** コレクションのリスナーに出力しています。</span><span class="sxs-lookup"><span data-stu-id="834ca-119">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="834ca-120">詳細については、「[マネージ コードのアサーション](/visualstudio/debugger/assertions-in-managed-code)」および「<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="834ca-120">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="834ca-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="834ca-121">See Also</span></span>  
 <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="834ca-122">アプリケーションのトレースとインストルメント</span><span class="sxs-lookup"><span data-stu-id="834ca-122">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="834ca-123">方法 : トレース スイッチを作成、初期化、および構成する</span><span class="sxs-lookup"><span data-stu-id="834ca-123">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [<span data-ttu-id="834ca-124">トレース スイッチ</span><span class="sxs-lookup"><span data-stu-id="834ca-124">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="834ca-125">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="834ca-125">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
