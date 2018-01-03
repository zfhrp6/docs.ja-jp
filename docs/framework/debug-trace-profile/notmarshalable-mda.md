---
title: notMarshalable MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 489f0e2ff4dc1eeaa9721ec6cf59faad0bee2ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="notmarshalable-mda"></a>notMarshalable MDA
共通言語ランタイム (CLR: Common Language Runtime) がコンテキスト間でインターフェイスをマーシャリングするときに、有効な登録済みのプロキシやスタブのない COM インターフェイス ポインター、または不正な `IMarshal` インターフェイスの実装を検出すると、`notMarshalable` マネージ デバッグ アシスタント (MDA: Managed Debugging Assistant) がアクティブになります。  
  
## <a name="symptoms"></a>症状  
 呼び出しが処理されないか、COM インターフェイス ポインターの不正なコンテキストで発生します。  
  
## <a name="cause"></a>原因  
 コンテキスト間でインターフェイスのマーシャリングを試みたときに、有効な登録済みのプロキシやスタブがないか、`IMarshal` が不正です。  
  
## <a name="resolution"></a>解像度  
 プロキシ スタブを登録済みであることと、`IMarshal` の実装が有効であることを確認します。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 この MDA は、ランタイムに影響しません。  
  
## <a name="output"></a>出力  
 問題を説明するメッセージ。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)
