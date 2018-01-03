---
title: failedQI MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc717f1500d202ae2590adb61b0376e93eba0944
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="failedqi-mda"></a>failedQI MDA
`failedQI` マネージ デバッグ アシスタント (MDA: Managed Debugging Asssitant) は、ランタイムがランタイム呼び出し可能ラッパー (RCW: Runtime Callable Wrapper) の代わりに COM インターフェイス ポインター上の `QueryInterface` を呼び出し、その `QueryInterface` 呼び出しに失敗するとアクティブ化されます。  
  
## <a name="symptoms"></a>症状  
 RCW でのキャストに失敗します。または、RCW からの COM 呼び出しが予期せず失敗します。  
  
## <a name="cause"></a>原因  
  
-   正しくないコンテキストから呼び出しが実行されました。  
  
-   呼び出しが正しくないコンテキストで試行されたため、登録されたプロキシが `QueryInterface` 呼び出しに失敗しています。  
  
-   OLE 所有のプロキシがエラー HRESULT を返しました。  
  
## <a name="resolution"></a>解像度  
 COM 規則についての MSDN ドキュメントを参照してください。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 `QueryInterface` 呼び出しに失敗すると、コンテキストが切り替えられ、エラー時に正しくないコンテキストであったことを確認するために、`QueryInterface` 呼び出しが再試行されます。  
  
## <a name="output"></a>出力  
 インターフェイスのマネージ名、インターフェイスの GUID、およびエラー HRESULT です。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)
