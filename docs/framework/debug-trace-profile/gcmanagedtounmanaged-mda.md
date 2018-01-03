---
title: gcManagedToUnmanaged MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d461ff702f756df6d599d7082edc6c5c4719c537
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged MDA
`gcManagedToUnmanaged` マネージ デバッグ アシスタント (MDA: Managed Debugging Assistant) は、スレッドがマネージ コードからアンマネージ コードに遷移する時に、毎回ガベージ コレクションがなされるようにします。  
  
## <a name="symptoms"></a>症状  
 アンマネージ ユーザー コンポーネントは、COM に公開されたマネージ オブジェクトを使おうとすると、アクセス違反をスローします。 COM オブジェクトはリリース済みのように表示されます。 アクセス違反は非確定です。  
  
## <a name="cause"></a>原因  
 アンマネージ コンポーネントがマネージ COM オブジェクトを正しくカウントする参照でない場合、ランタイムは、アンマネージ コンポーネントがオブジェクトへの参照を保持していると、COM に公開されたマネージ オブジェクトを収集できます。 ランタイムはガベージ コレクション中に <xref:System.Runtime.InteropServices.Marshal.Release%2A> を呼び出すので、ユーザー コンポーネントがガベージ コレクションの発生前にオブジェクトを使用すると、それは収集されないことになります。 これが非確定の原因です。  
  
## <a name="resolution"></a>解決策  
 このアシスタントを有効にすると、オブジェクトが収集の対象になってから <xref:System.Runtime.InteropServices.Marshal.Release%2A> が呼び出されるまでの時間が短縮し、収集されるオブジェクトへのアクセスを最初に試みるアンマネージ コンポーネントの追跡に役立ちます。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 スレッドがマネージ コードからアンマネージ コードに遷移する時に、毎回ガベージ コレクションがなされるようになります。  
  
## <a name="output"></a>出力  
 この MDA は、出力を生成しません。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)  
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
