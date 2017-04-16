---
title: "invalidApartmentStateChange MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), invalid apartment state"
  - "managed debugging assistants (MDAs), invalid apartment state"
  - "InvalidApartmentStateChange MDA"
  - "invalid apartment state changes"
  - "threading [.NET Framework], apartment states"
  - "apartment states"
  - "threading [.NET Framework], managed debugging assistants"
  - "COM apartment states"
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# invalidApartmentStateChange MDA
`invalidApartmentStateChange` マネージ デバッグ アシスタント \(MDS: Managed Debugging Assistant\) は、次の 2 つの問題のいずれかによってアクティブになります。  
  
-   COM によって既に初期化されているスレッドの COM アパートメントの状態が、異なるアパートメント状態に変更されようとしました。  
  
-   スレッドの COM アパートメントの状態が予期せず変更されました。  
  
## 症状  
  
-   スレッドの COM アパートメントの状態が、要求された状態と異なります。  これにより、現在とは異なるスレッド処理モデルの COM コンポーネントで、プロキシが使用されることがあります。  そのため、アパートメント間マーシャリングがセットアップされていないインターフェイスを通じて COM オブジェクトが呼び出されるときに、<xref:System.InvalidCastException> がスローされる場合があります。  
  
-   スレッドの COM アパートメントの状態が、想定と異なります。  これにより、[ランタイム呼び出し可能ラッパー](../../../docs/framework/interop/runtime-callable-wrapper.md) \(RCW\) で呼び出しが行われたときに、RPC\_E\_WRONG\_THREAD 値が HRESULT で <xref:System.Runtime.InteropServices.COMException> が発生したり、<xref:System.InvalidCastException> が発生したりすることがあります。  また、一部のシングルスレッド COM コンポーネントは、複数のスレッドから同時にアクセスされてしまうこともあり、その結果、破損やデータの損失が発生することもあります。  
  
## 原因  
  
-   スレッドは既に初期化されていて、別の COM アパートメント状態になっています。  スレッドのアパートメント状態は、明示的にも暗黙的にも設定できることに注意してください。  明示的な操作には、<xref:System.Threading.Thread.ApartmentState%2A?displayProperty=fullName> プロパティ、<xref:System.Threading.Thread.SetApartmentState%2A> メソッド、および <xref:System.Threading.Thread.TrySetApartmentState%2A> メソッドが含まれます。  <xref:System.Threading.Thread.Start%2A> メソッドを使用して作成されたスレッドは、スレッドが開始する前に <xref:System.Threading.Thread.SetApartmentState%2A> が呼び出されない限り、暗黙的に <xref:System.Threading.ApartmentState> に設定されます。  また、アプリケーションのメイン スレッドは、<xref:System.STAThreadAttribute> 属性がメイン スレッドで指定されていない限り、暗黙的に <xref:System.Threading.ApartmentState> に初期化されます。  
  
-   異なる同時実行モデルの `CoUninitialize` メソッド \(または `CoInitializeEx` メソッド\) が、スレッドで呼び出されました。  
  
## 解決策  
 スレッドの実行開始前に、スレッドのアパートメント状態を設定します。または、アプリケーションのメイン スレッドに、<xref:System.STAThreadAttribute> 属性または <xref:System.MTAThreadAttribute> 属性を適用します。  
  
 2 番目の原因の場合は、`CoUninitialize` メソッドを呼び出すコードを変更して、スレッドが終了するまで呼び出しを遅延させ、スレッドによって使用中のままとなっている RCW とその基本となる COM コンポーネントがないようにすることが理想的です。  ただし、`CoUninitialize` メソッドを呼び出すコードを変更できない場合、この方法で初期化されていないスレッドから RCW を使用しないでください。  
  
## ランタイムへの影響  
 この MDA は、CLR への影響はありません。  
  
## 出力  
 現在のスレッドの COM アパートメント状態、およびコードに適用しようとした状態です。  
  
## 構成  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## 使用例  
 この MDA をアクティブにできる状況のコード例を次に示します。  
  
```  
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)