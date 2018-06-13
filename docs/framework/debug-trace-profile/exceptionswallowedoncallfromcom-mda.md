---
title: exceptionSwallowedOnCallFromCom MDA
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b4c1cbf075ef96073061679b6d062075490f5e4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390609"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom MDA
アンマネージ HRESULT 戻り値型を持たないメソッドを介して COM から呼び出された 共通言語ランタイム (CLR) コードから、例外がスローされると、`exceptionSwallowedOnCallFromCOM` マネージ デバッグ アシスタント (MDA) がアクティブ化されます。  
  
## <a name="symptoms"></a>症状  
 COM からマネージ コンポーネントを呼び出すと、値 FALSE または 0 が返されます。 あるいは、メソッドの戻り値の型が void の場合、メソッド実行中に例外がスローされたという通知がない可能性があります。 この場合、例外は自動的にキャッチされ、COM 呼び出し元に実行が戻ります。  
  
## <a name="cause"></a>原因  
 例外がスローされましたが、それを報告する有効な方法がありません。  
  
## <a name="resolution"></a>解決策  
 情報提供専用です。必ずしもバグを示すものではありません。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 この MDA は CLR に影響しません。 自動的にキャッチされた例外を報告するだけです。  
  
## <a name="output"></a>出力  
 メソッド名、型名、例外メッセージが含まれている情報メッセージ。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)
