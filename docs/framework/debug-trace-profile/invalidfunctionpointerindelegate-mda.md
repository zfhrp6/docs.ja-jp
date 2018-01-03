---
title: invalidFunctionPointerInDelegate MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bfd63890369d51fb42871e06807483b6e713d81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate MDA
ネイティブ関数ポインターに対するデリゲートを作成するときに、無効な関数ポインターが渡されると、`invalidFunctionPointerInDelegate` マネージ デバッグ アシスタント (MDA) がアクティブ化されます。  
  
## <a name="symptoms"></a>症状  
 関数ポインターでデリゲートを使用すると、アクセス違反または予期しないメモリの破損が発生します。  
  
## <a name="cause"></a>原因  
 無効な関数ポインターが指定されました。  
  
## <a name="resolution"></a>解決策  
 有効な関数ポインターを指定します。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 この MDA は CLR に影響しません。  
  
## <a name="output"></a>出力  
 無効な関数ポインター。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)
