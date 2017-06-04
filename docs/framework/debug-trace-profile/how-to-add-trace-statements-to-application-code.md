---
title: "How to: Add Trace Statements to Application Code | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "tracing [.NET Framework], conditional writes based on switches"
  - "trace statements"
  - "WriteLineIf method"
  - "tracing [.NET Framework], adding trace statements"
  - "Assert method, tracing code"
  - "trace switches, conditional writes based on switches"
  - "WriteIf method"
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# How to: Add Trace Statements to Application Code
トレースで最も使用頻度の高いメソッドは、出力をリスナーに書き込むメソッドである **Write**、**WriteIf**、**WriteLine**、**WriteLineIf**、**Assert**、および **Fail** です。  これらのメソッドは、次の 2 つのカテゴリに分類できます。**Write**、**WriteLine**、および **Fail** は、すべての出力を無条件に生成します。それに対して、**WriteIf**、**WriteLineIf**、および **Assert** は、ブール条件をテストし、条件の値に基づいて出力を生成したり生成しなかったりします。  **WriteIf** と **WriteLineIf** は条件が `true` の場合に出力を生成し、**Assert** は条件が `false` の場合に出力を生成します。  
  
 トレースおよびデバッグの方法をデザインするときは、出力の表示方法について検討する必要があります。  複数の **Write**  ステートメントにより、関連のない情報が埋め尽くされたログが作成されると、それは読みにくいものになります。  その一方で、**WriteLine** を使用して関連のあるステートメントを別々の行に出力すると、どの情報が関連し合っているかを読み取るのが困難になります。  一般に、複数のソースからの情報を結合する場合には複数の **Write** ステートメントを使用して 1 つの情報メッセージを作成し、単一の完全なメッセージを作成する場合には **WriteLine** ステートメントを使用します。  
  
### 完結した行を書き込むには  
  
1.  <xref:System.Diagnostics.Trace.WriteLine%2A> メソッドまたは <xref:System.Diagnostics.Trace.WriteLineIf%2A> メソッドを呼び出します。  
  
     このメソッドが返すメッセージの末尾には、キャリッジ リターンが追加されます。したがって、次回の **Write**、**WriteIf**、**WriteLine**、または **WriteLineIf** が返すメッセージは、次の行から開始されます。  
  
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
  
### 完結しない行を書き込むには  
  
1.  <xref:System.Diagnostics.Trace.Write%2A> メソッドまたは <xref:System.Diagnostics.Trace.WriteIf%2A> メソッドを呼び出します。  
  
     **Write**、**WriteIf**、**WriteLine**、または **WriteLineIf** によって次に書き込まれるメッセージは、今回の **Write** または **WriteIf** ステートメントによって書き込まれるメッセージと同じ行から開始されます。  
  
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
  
### メソッドの実行前または実行後に特定の条件が存在するかどうかを確認するには  
  
1.  <xref:System.Diagnostics.Trace.Assert%2A> メソッドを呼び出します。  
  
    ```vb  
    Dim I As Integer = 4  
    Trace.Assert(I = 5, "I is not equal to 5.")  
  
    ```  
  
    ```csharp  
    int I = 4;  
    System.Diagnostics.Trace.Assert(I == 5, "I is not equal to 5.");  
  
    ```  
  
    > [!NOTE]
    >  **Assert** は、トレースとデバッグの両方で使用できます。  この例では、呼び出し履歴を **Listeners** コレクションのリスナーに出力しています。  詳細については、「[マネージ コードのアサーション](../Topic/Assertions%20in%20Managed%20Code.md)」および「<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>」を参照してください。  
  
## 参照  
 <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=fullName>   
 <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=fullName>   
 [Tracing and Instrumenting Applications](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)   
 [How to: Create, Initialize and Configure Trace Switches](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)   
 [Trace Switches](../../../docs/framework/debug-trace-profile/trace-switches.md)   
 [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md)