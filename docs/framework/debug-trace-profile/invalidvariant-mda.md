---
title: invalidVariant MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f97fb7f9bdb144f2b586c387f33211734f664eb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="invalidvariant-mda"></a>invalidVariant MDA
`invalidVariant` マネージ デバッグ アシスタント (MDA: Managed Debugging Assistant) は、ネイティブ コードまたはアンマネージ コードからマネージ コードへの呼び出し時に、無効な `VARIANT` 構造体が見つかるとアクティブ化されます。  
  
## <a name="symptoms"></a>症状  
 `VARIANT` からオブジェクトへのマーシャリングを含む、ネイティブ コードとマネージ コードの間の遷移中に、予期しない動作が発生します。  
  
## <a name="cause"></a>原因  
 ネイティブ コードが、不適切な `VARIANT` 構造体をマネージ コードに渡しています。  ランタイムは、この `VARIANT` をオブジェクトにマーシャリングしようとし、`VARIANT` が有効でない場合に MDA がアクティブ化されます。 無効な `VARIANT` には、`VARTYPE` VT_EMPTY &#124; VT_BYREF の `VARIANT` や、`VARTYPE` VT_VARIANT の `VARIANT` などがあります。  
  
## <a name="resolution"></a>解像度  
 `VARIANT` を渡すネイティブ コードまたはアンマネージ コードでは、`VARIANT` の形式と初期化が正しいことを確認する必要があります。  
  
## <a name="effect-on-the-runtime"></a>ランタイムへの影響  
 この MDA は、ランタイムの動作への影響はありません。  
  
## <a name="output"></a>出力  
 無効な `VARIANT` がアンマネージ モジュールによりマネージ コードに渡されたことを、ランタイムが検出したことを示す MDA メッセージです。  
  
## <a name="configuration"></a>構成  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [マネージ デバッグ アシスタントによるエラーの診断](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [相互運用マーシャリング](../../../docs/framework/interop/interop-marshaling.md)
